# Older Releases

## v1.5.4 (March 2025)  

### Update 
- API Version update to 62  
  
## v1.5.3 (February 2025)  

### Bug  
- fix where multiple tags across many categories with the same name are blocking the removal of a tag link  

## v1.5.2 (October 2025)  

### Update 
- Allow for Experience Cloud Tag viewing Component to be accessible via FLOW  
- Update to slds-pill to include slds-var-m-right_xx-small (improved UI)  
- Update to slds-pill label within read-only tag to include slds-var-p-around_xx-small (improved UI)  
- Update to help text on Available Objects via Custom Label  
- API Version move from 59 to 61  

## v1.5.1 (May 2025) 

### Bug 
- When a tag is active but has no target objects configured a null pointer exception is thrown when viewing all tags  

## v1.5.0 (April 2024) 

### New 
- Limit number of Tags than can he selected within the component  
- Configure component to filter based on 1 specific Tag Category  
- View All Tags modal  
- Request a tag when component is linked to 1 category will link the request to that specific category  

## v1.4.0 (March 2024)  
### New 
- Flag on LWC Component that allows you to switch off the ability to request a Tag  
- RecordTriggered Flow on Tag that runs when a Tag has been set to Active and it has a Related Record Id and  
- Requested Object Name, it will create the Tag Link against the record  
- InvocableMethod to support with this process  
- LWC Component for Experience Cloud rollout of Tags  
### Update 
- Update to tagComponent to support running it within a flow  
- Includes a sample flow to show how it displays  

## v1.3.0 (February 2024)  
### New 
- Introduction of Tag Category / Categories  
### Update 
- Update to component to support configuration options  
- Set Component Title  
- Set Component Icon - based on Lighting Design System Icons   
- Set display categories  
- Set forced read only (for when tags are managed via background process or you want to prevent editing / amending of tags on specific record  
### Core App Update  
- New Home page with sample Report Chart embedded  
- Search Layouts updated on all objects  
- List views actions cleaned up  
- Test class coverage increase  
- API Version increase to 59  

## v1.2.2 (January 2024)  
### Update 
- Updated test classes based on recent secure permission errors  

## v1.2.1 (March 2023)  
### Update 
- Test classes to support DML Exception  
- Update to Documentation based on Salesforce Unlocked Package Bug  

## v1.2.0 (March 2023)  
### New 
- Search for Tag and Request addition 
- UI On Tag to Support setting Objects a Tag is available on  
### Update 
- Bump API Versions to 57 across application  

## v1.1.0 (April 2021)  
### New 
 - Set Objects that Tags are available on  

 