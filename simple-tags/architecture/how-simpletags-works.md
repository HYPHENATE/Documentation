# How SimpleTags Works

SimpleTags provides a flexible tagging framework that allows Salesforce records to be classified using reusable tags.  
Unlike native tagging approaches that rely on text fields or limited platform features, SimpleTags stores tagging relationships as **structured records**, which enables powerful reporting and automation.

At a high level, the system works by combining a simple data model, configurable metadata, and Lightning components.

---

## Step 1: Create Tag Categories

Tag Categories organise tags into logical groups.  
They make it easier for users to browse and understand available tags.

Examples of categories might include:

| Category | Example Tags |
|------|------|
| Programme Area | Health, Education, Community Development |
| Campaign Type | Fundraising, Awareness |
| Expertise Area | Climate Science, Mental Health |

Categories help ensure the tagging system remains **structured and manageable** as the number of tags grows.

---

## Step 2: Create Tags

Tags represent the individual classification values applied to records.

Each tag:

- belongs to a **Tag Category**
- can optionally be **restricted to specific objects**
- has a **status** to control whether it is available for use

Example tags:

| Tag | Category |
|------|------|
| Climate Action | Programme Area |
| Youth Development | Programme Area |
| Fundraising | Campaign Type |

Tags provide the actual labels used to classify records.

---

## Step 3: Restrict Tags to Objects (Optional)

Tags can optionally be configured so that they only apply to specific Salesforce objects.

For example:

| Tag | Available Objects |
|------|------|
| Climate Action | Opportunity, Funding Request |
| Volunteer Engagement | Contact |
| Fundraising | Campaign |

Restricting tags ensures users only see **relevant tags for the record they are working on**.

---

## Step 4: Configure Tag Links

The **Tag Link** object stores the relationship between a tag and a record.

Because Salesforce objects vary, SimpleTags uses metadata to determine which lookup field on the Tag Link object should be used.

This configuration is stored in:

```
Tag_Meta__mdt
```

Each metadata record defines:

- the object name
- the corresponding lookup field on `Tag_Link__c`

This allows the system to support **many different objects without hardcoding relationships**.

---

## Step 5: Apply Tags to Records

Once configuration is complete, users can apply tags to records using the provided components.

Examples include:

- internal Lightning components on record pages
- Experience Cloud tagging components
- Flow-based tagging interfaces

Users can:

- add tags
- remove tags
- browse available tags
- request new tags (if enabled)

---

## Step 6: Reporting and Insights

Because tag relationships are stored as **structured records**, they can easily be used in reporting.

Administrators can create **custom report types** that include:

```
Record → Tag Link → Tag → Tag Category
```

This enables reporting such as:

| Report | Example Insight |
|------|------|
| Funding Requests by Theme | Understand which strategic areas receive the most applications |
| Campaigns by Tag | Analyse campaign performance by category |
| Records by Programme Area | Track activity across organisational programmes |

---

## Architecture Overview

The SimpleTags data model follows a simple structure:

```
Tag Category
     ↓
Tag
     ↓
Tag Link
     ↓
Record
```

This model allows:

- flexible classification
- cross-object tagging
- scalable reporting structures

---

## Why This Approach Works

SimpleTags improves on other tagging approaches by:

| Capability | Benefit |
|------|------|
| Structured relationships | Enables robust reporting |
| Metadata-driven object support | Allows tagging across many objects |
| Category organisation | Keeps tags easy to browse |
| Flexible UI components | Works across internal and Experience Cloud interfaces |

This architecture makes SimpleTags suitable for use cases such as:

- grant management and thematic reporting
- campaign categorisation
- reviewer expertise tagging
- programme classification

---

## Related Documentation

- [Data Model Overview](/simple-tags/custom-objects/overview)
- [Tag Category](/simple-tags/custom-objects/tag-category)
- [Tag](/simple-tags/custom-objects/tag)
- [Tag Link](/simple-tags/custom-objects/tag-link)
- [Tag Meta](/simple-tags/custom-objects/tag-meta)
