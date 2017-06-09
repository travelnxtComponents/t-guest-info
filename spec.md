# t-guest-info Specification

### Component Use
```javascript
 <t-passenger-group
 panelist = {{paxList}}
 product-list=[[product-list]]
 resources=[[resources]] >
 t-passenger-group>

 <t-passenger-info allow-contact-number
 allow-email
 >
 t-passenger-info>
     <t-loyalty-group panelist=[[productPaxList]]>
 t-loyalty-group>

```javascript

## Property Details
### Product List
```javascript
[
 {
 "id" : "123123",
 "name" : "El Cortez Hotel &; Casino",
         // if true, then display the loyalty section
 "allowLoyalty": ture,
         "rooms" : [
 {
 "id" : "ypHtxnfawEWvbhtBo2ZKOw",
 "name": "Deluxe room",
                     //if this property value false, then need pax details for all passenger
 "onlyLeadPaxInfo" : true,
 "criteria" : {
 "checkIn" : "05/22/2017",
 "checkout" : "05/28/2017",
 "stayDuration" : 2,
 "traveler" : {
 "adult" : 2,
 "child" : 1
 }
 }
 }
 ],
 "policies" : [
 "FREE cancellation before 11:59PM on April 25, 2017"
 ]
 }
]
```
### Pax List
```javascript
[
 {
 "type" : "Adult",
 "title" : "Mr",
 "firstName" : "John",
 "lastName" : "Doe",
 "email" : "john@example.com",
 "contact" : "343453453",
 "contactCode" : "+91"
 }
]
```


### Resources
```javascript
{
 "icons": {
 "terms": "terms-ico"
 },
 "labels": {
 "adult": {
 "title": "Adult {count}",
 "info": "(12+ years)"
 },
 "child": {
 "title": "Child {count}",
 "info": "(upto 7 years)"
 }
 },
 "fields": {
 "title": {
 "values": [
 {
 "key": "Mr"
 },
 {
 "key": "Ms"
 }
 ],
 "selected": "Mr",
 "title": "Title",
 "errors": "Please select a title",
 },
 "firstName": {
 "value": "",
 "title": "First name",
 "errors": "Firstname is required",
 },
 "lastName": {
 "value": "",
 "title": "Last name",
 "errors": "Lastname is required",
 },
 "email": {
 "value": "",
 "title": "Email address",
 "info": "We'll send you email confirmation on this address",
 "errors": "Please enter a valid email address",
 },
 "countryCode": {
 "values": [
 {
 "key": "India +91",
 "value": "91"
 },
 {
 "key": "USA +1",
 "value": "1"
 }
 ],
 "title": "Country code",
 "errors": "Countrycode is required",
 },
 "contactNumber": {
 "value": "",
 "title": "Contact number",
 "info": "In case of any notifications our agent will reach you on this number",
 "errors": "Contact number is required",
 }
 }
}
```


### Methods
```javascript
invalid() - returns Boolean as per validation status
gestate() - returns current passenger info state object as data setState("<data object>") - set current passenger info state “`
```
### Events
```javascript
Fired when invalid is called or in response to t-passenger-info-validate event t-passenger-info-status - {"invalid":true,"code":"pax1"}
```
### Listen
```javascript
t-passenger-info-validate - {}} //this will trigger validation in component
```


### Styles
```javascript
Need variable for defining text color for label, input and terms
Need variable for defining background color
Need variable for defining terms text color
```

## Test Cases
- Component should work across all major browsers - Chrome / Mozilla / Safari / Opera / IE etc.
- Verify all exposed public properties are working independently and with complex combination.
- Verify all exposed methods and events are working.
- Same set of code should work across three views i.e. Desktop/ Tablet and Mobile
- Validations should work for Mandatory fields
- User-info component should work separately for single and multi passengers.
- User-info component items are - Header stripe, 2 line placeholders, title, first name, last name, email, contact code and phone.
- "2 line placeholder" -If no content given, system should handle the space/alignment.
- Header stripe will display- Room name, bed type and occupancy.
- Adult 1, Adult 2.... label will appear only if multiple passenger information is required.
- When to capture all passengers' information will be derived form APIs.
- "Choose guest" drop down will be available from room 2 and will populate the passengers list entered in room 1 & so on to other rooms.
- After selection of guest from drop down will show information in expanded view with cross icon and click on cross will reset to previous position
- All label like Adult 1 (12+ yrs), child 1 (< 11 yrs) etc. and validation error messages will be managed from resources.
- For now user info component is showing Title, first and last name in single line but suppose some business owner don't want to capture "title" in user-info, In that case business owner can hide "title" field and "first" & "last" name field should equally distribute the vacant position. Similar behavior applies to other fields.

## Steps to Start
- Set Github repository at your end for this project, we will merge them later
- You can use Google/Vaadin's elements (like calendar element and text boxes etc.)

## Performance standard
- Any component if opened via [web page tester](https://www.webpagetest.org/), it should load under 500ms (milli seconds).

## Documents
- Visual designs for components - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/228211081
- API access : URL - http://demo.travelnxt.com/dev
- Tavisca Elements - https://github.com/atomelements and https://github.com/travelnxtelements
- Vaadin elements - https://vaadin.com/docs/-/part/elements/elements-getting-started.html
- Google - https://elements.polymer-project.org/browse?package=google-web-components
- Tavisca Web component style Guide - https://drive.google.com/open?id=0B7BT_2nBFNYVR2tscE9pRnVJYmc
