# ApexTools Coding Examples

This page provides practical examples of how `ApexTools` can be used in real Salesforce implementations.

The examples are written with a **nonprofit and grant management** focus, using scenarios such as:

- grant applications
- funding requests
- reviewer assignments
- programme delivery
- applicant communications

Some examples use sample object names such as `Grant_Application__c` and `Review_Assignment__c`.  
If your org uses different objects, replace those API names with your own.

---

## Example 1: Keep Grant Application Triggers Lightweight

One of the simplest ways to use `ApexTools` is to keep trigger logic minimal and let `MetaTriggerManager` route execution to the right handler classes.

### Trigger

```apex
trigger GrantApplicationTrigger on Grant_Application__c (
    before insert,
    before update,
    after insert,
    after update
) {
    (new MetaTriggerManager(Grant_Application__c.SObjectType)).handle();
}
```

### Handler Class

This example sets a default status when a new grant application is created.

```apex
public with sharing class GrantApplicationBeforeInsertHandler implements BeforeInsert {
    public void handleBeforeInsert(List<SObject> newList) {
        for (Grant_Application__c application : (List<Grant_Application__c>) newList) {
            if (String.isBlank(application.Status__c)) {
                application.Status__c = 'Draft';
            }
        }
    }
}
```

### Use Case

A nonprofit may want every new funding request or grant application to start with a consistent status without filling triggers with hardcoded logic.

---

## Example 2: Run Post-Submission Processing for Grant Applications

This example shows an `AfterInsert` handler that could be used after a grant application is submitted.

```apex
public with sharing class GrantApplicationAfterInsertHandler implements AfterInsert {
    public void handleAfterInsert(List<SObject> newList) {
        List<Task> acknowledgementTasks = new List<Task>();

        for (Grant_Application__c application : (List<Grant_Application__c>) newList) {
            if (application.Status__c == 'Submitted') {
                acknowledgementTasks.add(new Task(
                    Subject = 'Send applicant acknowledgement',
                    WhatId = application.Id,
                    ActivityDate = Date.today().addDays(1),
                    Priority = 'Normal',
                    Status = 'Not Started'
                ));
            }
        }

        if (!acknowledgementTasks.isEmpty()) {
            insert acknowledgementTasks;
        }
    }
}
```

### Use Case

When a funding request is submitted, a programme or grants team may want follow-up tasks created automatically for staff.

---

## Example 3: Log Failed Updates During Grant Award Processing

`ApexLogger` is useful when batch processes or service classes update large numbers of records and you want a consistent log of failures.

```apex
public with sharing class GrantAwardService {
    public static void markApplicationsAsAwarded(List<Grant_Application__c> applications) {
        for (Grant_Application__c application : applications) {
            application.Status__c = 'Awarded';
            application.Decision_Date__c = Date.today();
        }

        Database.SaveResult[] results = Database.update(applications, false);

        ApexLogger logger = new ApexLogger();
        logger.setClassName('GrantAwardService');
        logger.setRecordsProcessed(new List<SObject>(applications));
        logger.setSaveResults(results);
        logger.processSaveResults();
    }
}
```

### Use Case

If some grant applications fail validation during a bulk award process, `ApexLogger` can store the results in `Apex_Log__c` for later review.

---

## Example 4: Log Flow Errors from a Grant Review Process

If a Flow handles reviewer assignments or grant approvals, `ApexLoggerInvocable` can be used to write structured error records when something goes wrong.

```apex
List<ApexLoggerInvocable.ApexLoggerFlowErrorInput> inputs =
    new List<ApexLoggerInvocable.ApexLoggerFlowErrorInput>();

ApexLoggerInvocable.ApexLoggerFlowErrorInput input =
    new ApexLoggerInvocable.ApexLoggerFlowErrorInput();

input.flowAPIName = 'Grant_Review_Assignment_Flow';
input.runningUserId = UserInfo.getUserId();
input.faultMessage = 'Reviewer assignment failed because no reviewer pool was found.';
input.faultElement = 'Create_Reviewer_Assignments';
input.recordId = 'a001234567890ABC';

inputs.add(input);

List<ApexLoggerInvocable.ApexLoggerFlowLogOutput> outputs =
    ApexLoggerInvocable.logFlowErrorToApexLog(inputs);
```

### Use Case

This is useful when a grant review Flow fails and the team wants a reportable log rather than relying only on Flow error emails.

---

## Example 5: Build Dynamic Queries for Funding Requests

`QueryBuilder` can simplify dynamic SOQL when query fields vary by context.

```apex
String query = new QueryBuilder('Funding_Request__c')
    .addFields(new Set<String>{
        'Name',
        'Status__c',
        'Requested_Amount__c',
        'Programme__c'
    })
    .setWhereClause('Status__c = \'Submitted\'')
    .setOrderByClause('Requested_Amount__c DESC')
    .getQuery();

List<SObject> submittedRequests = Database.query(query);
```

### Use Case

A grants team may want to build configurable shortlist or review queries without rewriting SOQL in multiple places.

---

## Example 6: Use Field Sets for Flexible Reviewer Dashboards

`QueryBuilder` can also use field sets, which is useful when different programmes want different columns on review screens or exports.

```apex
String query = new QueryBuilder('Grant_Application__c')
    .addFieldSet('Reviewer_Summary')
    .setWhereClause('Status__c = \'Under Review\'')
    .setOrderByClause('CreatedDate DESC')
    .getQuery();

List<SObject> applicationsForReview = Database.query(query);
```

### Use Case

A foundation may manage multiple funding programmes and want administrators to control which application fields appear in reviewer processes.

---

## Example 7: Cache Picklist Values for Funding Programmes

`DescribeCache` is useful when you need repeated access to metadata such as picklist values.

```apex
List<String> programmeStatuses =
    DescribeCache.getPicklistValues('Grant_Application__c', 'Status__c');

System.debug(programmeStatuses);
```

### Use Case

This can support validation logic, configuration pages, or administrative screens that need current status values for grant applications.

---

## Example 8: Create Manual Shares for External Reviewers

`ShareObjectCreate` can be used to create share records for reviewers, committee members, or partner users.

```apex
Set<Id> applicationIds = new Set<Id>{
    Id.valueOf('a001234567890ABC'),
    Id.valueOf('a001234567890ABD')
};

Set<Id> reviewerUserIds = new Set<Id>{
    Id.valueOf('0051234567890AAA')
};

ShareObjectCreate shareCreator = new ShareObjectCreate(
    applicationIds,
    reviewerUserIds,
    'Read'
)
    .setTargetObjectType('Grant_Application__c')
    .setRowCause('Grant_Reviewer_Access__c');

shareCreator.createShareRecords();
shareCreator.insertShares();
```

### Use Case

If external reviewers need read-only access to a set of applications during an assessment period, this pattern can help automate access.

---

## Example 9: Remove Reviewer Access After a Decision

`ShareObjectDelete` can be used to revoke access when a review cycle ends.

```apex
ShareObjectDelete shareDelete = new ShareObjectDelete(
    Id.valueOf('a001234567890ABC'),
    Id.valueOf('0051234567890AAA')
)
    .setTargetObjectType('Grant_Application__c')
    .setRowCause('Grant_Reviewer_Access__c');

List<SObject> sharesToDelete = shareDelete.getShareRecords();
shareDelete.deleteShare();
```

### Use Case

Once a grant decision is final, temporary reviewer access may need to be removed to protect applicant confidentiality.

---

## Example 10: Use Metadata-Driven Sharing for Programme Roles

`MetaSharingHandler` is designed for more configurable sharing rules.

```apex
List<Id> usersToShareTo = new List<Id>{
    Id.valueOf('0051234567890AAA'),
    Id.valueOf('0051234567890AAB')
};

MetaSharingHandler sharingHandler = new MetaSharingHandler(usersToShareTo)
    .setParentId(Id.valueOf('a0B1234567890XYZ'))
    .isConfigRoleValid('Programme Reviewer')
    .buildRecordQueries('Programme Reviewer')
    .processSharing('Programme Reviewer')
    .insertShareRecords();

if (!sharingHandler.getIsSuccess()) {
    System.debug(sharingHandler.getErrorMessage());
}
```

### Use Case

A grants programme may define sharing rules by role, such as:

- programme reviewer
- finance approver
- regional grants manager

This allows access to be managed more consistently through metadata rather than hand-built sharing logic in each project.

---

## Example 11: Generate Test Data for Grant Applications

`TestRecordSource` can make test setup more consistent and reusable.

```apex
@IsTest
private class GrantApplicationServiceTest {
    @IsTest
    static void createsAwardDecision() {
        TestRecordSource source = new TestRecordSource();

        Grant_Application__c application =
            (Grant_Application__c) source.getObject(Grant_Application__c.SObjectType)
                .withInsert();

        System.assertNotEquals(null, application.Id);
    }
}
```

### Use Case

This is useful when many grant-management tests need realistic base records but the team wants to avoid repeated hand-written setup logic.

---

## Example 12: Use Test Variants for Different Grant Scenarios

If metadata variants are configured, `TestRecordSource` can support different record setups.

```apex
@IsTest
private class GrantEligibilityServiceTest {
    @IsTest
    static void handlesSmallGrantProgramme() {
        TestRecordSource source = new TestRecordSource();

        Grant_Application__c application =
            (Grant_Application__c) source.getObject(Grant_Application__c.SObjectType)
                .asVariant('SmallGrant')
                .withInsert();

        System.assertEquals('Small Grant', application.Programme_Type__c);
    }
}
```

### Use Case

A nonprofit may run different funding streams such as emergency grants, community microgrants, and strategic programmes. Variants help tests reflect those differences.

---

## Example 13: Add Temporary Test Metadata in a Unit Test

You can also create temporary metadata definitions directly inside a test.

```apex
@IsTest
private class TemporaryGrantMetadataTest {
    @IsTest
    static void buildsApplicationFromExampleRecord() {
        TestRecordSource source = new TestRecordSource();

        Grant_Application__c exampleApplication = new Grant_Application__c(
            Name = 'Example Community Grant',
            Status__c = 'Draft'
        );

        source.addTemporaryMetadataFromInstance(exampleApplication, 100);

        Grant_Application__c builtApplication =
            (Grant_Application__c) source.getObject(Grant_Application__c.SObjectType)
                .withoutInsert();

        System.assertEquals('Example Community Grant', builtApplication.Name);
    }
}
```

### Use Case

This is helpful when building tests for a package or feature that should not depend on permanent metadata records already existing in the org.

---

## Example 14: Group Review Assignments by Grant and Status

`SObjectIndex` is useful when you need fast grouping and lookup of records.

```apex
List<Review_Assignment__c> assignments = [
    SELECT Id, Grant_Application__c, Status__c, Reviewer__c
    FROM Review_Assignment__c
    WHERE Grant_Application__c IN :applicationIds
];

SObjectIndex assignmentsByGrantAndStatus =
    new SObjectIndex(new List<String>{'Grant_Application__c', 'Status__c'});

assignmentsByGrantAndStatus.putAll(assignments);

List<SObject> pendingAssignments = assignmentsByGrantAndStatus.getAll(
    new Map<String, Object>{
        'Grant_Application__c' => Id.valueOf('a001234567890ABC'),
        'Status__c' => 'Pending'
    }
);
```

### Use Case

This can be useful when a grantmaking team needs to analyse which applications still need reviewer responses.

---

## Example 15: Use Case-Insensitive Indexing for Programme Names

`SObjectIndex` can also be made case-insensitive.

```apex
SObjectIndex programmesByName =
    new SObjectIndex('Name').setIsCaseInsensitive(true);

programmesByName.putAll([
    SELECT Id, Name
    FROM Programme__c
    WHERE Active__c = true
]);

Programme__c matchedProgramme =
    (Programme__c) programmesByName.get('community resilience');
```

### Use Case

This can help when importing programme mappings or matching partner-supplied values that are not consistently cased.

---

## Example 16: Parse Grant Portal JSON Payloads

`JSONParser` is useful when receiving nested JSON from an external grants portal or assessment system.

```apex
String payload = '{"application":{"reference":"GA-2026-001","applicant":{"name":"Community Futures Trust"},"scores":[{"section":"Need","value":4},{"section":"Impact","value":5}]}}';

JSONParser parser = new JSONParser(payload);

String reference = parser.get('application.reference').getStringValue();
String applicantName = parser.get('application.applicant.name').getStringValue();
Decimal impactScore = parser.get('application.scores.[1].value').getDecimalValue();
```

### Use Case

A nonprofit could use this when integrating with an external application portal, reviewer portal, or grant assessment service.

---

## Example 17: Load a Configured Class Dynamically

`TypeLoader` helps when a class name is stored in configuration or metadata.

```apex
String className = 'MyGrantScoringService';
Type configuredType = TypeLoader.getType(className);
Object scoringService = TypeLoader.getInstance(configuredType, null);
```

### Use Case

This pattern is useful when different grant programmes use different scoring or eligibility strategies and the implementation class is configured rather than hardcoded.

---

## Example 18: Send a Templated Award Email from Apex

`SendEmailV2` can be used directly when a grant is approved and the applicant needs to be notified.

```apex
SendEmailV2.ProcessEmailRequest request = new SendEmailV2.ProcessEmailRequest();
request.whatId = Id.valueOf('a001234567890ABC');
request.whoId = Id.valueOf('0031234567890AAA');
request.templateDeveloperName = 'Grant_Award_Notification';
request.saveAsActivity = true;
request.useSignature = false;
request.treatTargetObjectAsRecipient = true;

List<SendEmailV2.ProcessEmailResult> results =
    SendEmailV2.sendEmail(new List<SendEmailV2.ProcessEmailRequest>{ request });
```

### Use Case

This can support award notifications, decline communications, reviewer invitations, or missing-information reminders.

---

## Example 19: Send a Plain Email Reminder for Missing Documents

If no template is needed, a plain body can be sent instead.

```apex
SendEmailV2.ProcessEmailRequest request = new SendEmailV2.ProcessEmailRequest();
request.whatId = Id.valueOf('a001234567890ABC');
request.emailSubject = 'Additional information needed for your grant application';
request.emailBody = 'Please upload your latest governing document and budget before the review deadline.';
request.otherToContactIds = new List<String>{ 'applicant@example.org' };
request.saveAsActivity = true;
request.useSignature = true;
request.treatTargetObjectAsRecipient = false;

List<SendEmailV2.ProcessEmailResult> results =
    SendEmailV2.sendEmail(new List<SendEmailV2.ProcessEmailRequest>{ request });
```

### Use Case

This works well for operational messages where a full email template is unnecessary.

---

## Example 20: Seed Sandbox Data After Refresh

`PostCopySandboxScript` can be used to generate baseline data after a sandbox refresh.

```apex
global class GrantsSandboxPostCopy implements SandboxPostCopy {
    global void runApexClass(SandboxContext context) {
        PostCopySandboxDataGenerator.generateData(false);
    }
}
```

### Use Case

A grants team may want each refreshed sandbox to include sample programmes, applications, reviewers, and award records so that testing and demos can start quickly.

---

## Example 21: Combine Logging and Email for Award Processing

This example shows how package components can be combined in a more realistic service flow.

```apex
public with sharing class GrantDecisionService {
    public static void notifySuccessfulApplicants(List<Grant_Application__c> applications) {
        Database.SaveResult[] results = Database.update(applications, false);

        ApexLogger logger = new ApexLogger();
        logger.setClassName('GrantDecisionService');
        logger.setRecordsProcessed(new List<SObject>(applications));
        logger.setSaveResults(results);
        logger.processSaveResults();

        List<SendEmailV2.ProcessEmailRequest> emailRequests =
            new List<SendEmailV2.ProcessEmailRequest>();

        for (Grant_Application__c application : applications) {
            if (application.Status__c == 'Awarded' && application.Primary_Contact__c != null) {
                SendEmailV2.ProcessEmailRequest request =
                    new SendEmailV2.ProcessEmailRequest();
                request.whatId = application.Id;
                request.whoId = application.Primary_Contact__c;
                request.templateDeveloperName = 'Grant_Award_Notification';
                request.saveAsActivity = true;
                request.useSignature = false;
                request.treatTargetObjectAsRecipient = true;
                emailRequests.add(request);
            }
        }

        if (!emailRequests.isEmpty()) {
            SendEmailV2.sendEmail(emailRequests);
        }
    }
}
```

### Use Case

This is a good example of how `ApexTools` can act as a technical foundation layer rather than a single-purpose feature.

---

## Suggested Object Mapping for Nonprofit Teams

If you want to adapt these examples to a grantmaking or nonprofit implementation, a useful mapping might be:

| Example Object Name | Possible Real-World Meaning |
|------|------|
| `Grant_Application__c` | Funding request, application, proposal |
| `Programme__c` | Grant programme, funding stream, initiative |
| `Review_Assignment__c` | Reviewer allocation, assessment assignment |
| `Primary_Contact__c` | Applicant contact, lead contact |
| `Funding_Request__c` | Grant request, budget request, project request |

---

## Notes

- Some examples assume supporting metadata has already been configured.
- Some examples use placeholder IDs for readability.
- Email examples rely on the request classes exposed by `SendEmailV2`.
- Sharing examples use a placeholder custom row cause such as `Grant_Reviewer_Access__c`; replace this with a valid sharing reason in your org.
- Sharing examples should be validated carefully against your organisation's security model before production use.
- Test data examples are most valuable once your metadata-driven test generators are in place.

---

## Related Documentation

- [How ApexTools Works](/apex-tools/architecture/how-apextools-works.md)
- [Competitor Analysis](/apex-tools/architecture/competitor-analysis.md)