# Configuration

## Step 1 - Tagging Requirements
Whilst the configuration is flexible the more you do up front the better. So before you start your configuration ensure you have a complete picture of which objects you want to implement tagging against. 
Account is preconfigured as a part of the installation.

##  Step 2 - Clone Permission Sets
If you are going to expand on the configuration of this application it is important that you clone/create your own local versions of the packages permission sets. These permission sets are where you will add any custom fields that you add to the Tag Category/Tag or Tag Link record.

## Step 3 - Create Lookup Fields on Tag Link object
- Go to **Setup** > **Object Manager**  
- Find the object **Tag Link* (Tag_Link__c)  
- With in **Fields & Relationships** select **New**  
- Select **Lookup Relationship**  
- Find the object you want to enable Tags on  
- Set **Field Name** and **API Name**  
- **IMPORTANT** Set **Description** explaining what this tag relationship is used for
    - A good example might be The Funding Programme is used to support with categorisation of funding themes    
- Add this field to existing custom report types that contain this entity is ticked  
- Configure security  
    - **Recommended**
        - Ensure the field Read/Edit is set on the custom permission set you created in the previous step.
    - Not Recommend
        - We should be assisting clients with the transition away from profiles to permission sets but if the client is still using profiles carefully select the projects of users that should have access to your new field/s
- Add to Tag Link Page layout  
- **DO NOT** add the custom related list - we use a custom LWC Component to render the tags and do not want staff interacting directly with the tags  
- Press **Save**  

## Step 4 - Create Custom Metadata
- Go to **Setup** > **Custom Metadata Types**  
- Select **Manage Records** on **Tag Meta**  
- Press **New**
- **Label** as the Object API Name that the New Tags will sit on  
    - e.g. Adding tags against the Funding Request in outbound funds Label = outfunds__Funding_Request__c  
- **Name** = Funding_Request  
- **Field API Name** = Funding_Request__c
- Press **Save**  

## Step 5 - Add Component to Lightning Pages
- **Setup** > **Object Manager**
- Find the Parent object that you created a Lookup relationship to on the Tag Link 
- Edit the associated Lightning Page that you want to make Tags Available on  
- Add the LWC Component **SimpleTags** 
- Review Component setup options here [Simple Tags Component](/components/simple-tags)  
- Press **Save**

## Step 6 - Assign Permissions
- Ensure that the permission set you cloned is applied to users that need the ability to tag records.
- Should you need or want to expand on who can managed or who has read only permissions then you should remove the permission sets
    - [Tag Manager](/permissions/tag-manager)
    - [Tag User](/permissions/tag-user)
    - [Tag Viewer](/permissions/tab-viewer)

## Step 7 - Use the Application
Read more about this within the [User Guide](/user-guide).