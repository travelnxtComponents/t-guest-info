# t-guest-info Specification

### Component Use
```html
    <t-passenger-group
             pax-list = {{paxList}}
            product-list=[[product-list]]
            resources=[[resources]] >
    </t-passenger-group>

    <t-passenger-info 
                allow-contact-number
                allow-email
                allow-loyalty
                >
    </t-passenger-info>
    
    <t-loyalty-group>
    </t-loyalty-group>

```

## Property Details
### Product List
```json
[
    {
        "id" : "123123",
        "name" : "El Cortez Hotel &amp; Casino",        
        "rooms" : [
                {
                    "id" : "ypHtxnfawEWvbhtBo2ZKOw",
                    "name": "Deluxe room",
                    /*if this property value false, then need pax details for all passenger*
                    "onlyLeadPaxInfo" : true,
                    "criteria" : {
                        "checkIn" : "05/22/2017",
                        "checkOut" : "05/28/2017",
                        "stayDuration" : 2,
                        "traveller" : {
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
```json
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
```json
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
            "errorMsg": "Please select a title",
        },
        "firstName": {
            "value": "",
            "title": "First name",
            "errorMsg": "Firstname is required",
        },
        "lastName": {
            "value": "",
            "title": "Last name",
            "errorMsg": "Lastname is required",
        },
        "email": {
            "value": "",
            "title": "Email address",
            "info": "We'll send you email confirmation on this address",
            "errorMsg": "Please enter a valid email address",
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
            "errorMsg": "Countrycode is required",
        },
        "contactNumber": {
            "value": "",
            "title": "Contact number",
            "info": "In case of any notifications our agent will reach you on this number",
            "errorMsg": "Contact number is required",
        }
    }
}
```


### Methods
```javascript
isValid() - returns boolean as per validation status
getState() - returns current passenger info state object as data 
setState("<data object>") - set current passenger info state  
```

### Events
```javascript
Fired when isValid is called or in responce to t-passenger-info-validate event 
t-passenger-info-status - {"isValid":true,"code":"pax1"}
```

### Listen
```javascript
t-passenger-info-validate  - {}} //this will trigger validation in component
```


### Styles
```javascript
Need variable for defining text colour for lable, input and terms
Need variable for defining background colour
Need variable for defining terms text colour
```

## Test Cases
- Component should work across all major browsers - Chrome / Mozilla / Safari / Opera / IE etc.
- Verify all exposed public properties are working independently and with complex combination.
- Verify all exposed methods and events are working.
- Same set of code should work across three views i.e. Desktop/ Tablet and Mobile
- Validations should work for Mandatory fields
- User-info component should work separately for single and mult passengers.
- User-info component items are - Header stripe, 2 line placeholder, title, firstname, lastname, email, contact code and phone.
- "2 line placeholder" -If no content givem, system should handle the space/alignment.
- Header stipe will display- Room name, bed type and occupany.
- Adult 1, Adult 2.... label will appear only if multiple passenger information is required.
- When to capture all passengers information will be derived form APIs.
- "Choose guest" dropdown will be available from room 2 and will popluate the passengers list entered in room 1 & so on to other rooms.
- After selection of guest from dropdown will show information in expanded view with cross icon and click on cross will reset to previous position
- All label like Adult 1 (12+ yrs), child 1 (< 11 yrs) etc. and validation error messages will be managed from resources.
- For now user info compoenent is showing Title, first and last name in single line but suppose some business owner don't want to capture "title" in user-info, In that case business owner can hide "title" field and "first" & "last" name field should equally distribute the vacant position. Similar behavior applies to other fields.

## Steps to Start
- Set Github repository at your end for this project, we will merge them later
- You can use Google/Vaadin's elements (like calender element and textboxes etc.)

## Performance standard
- Any component if opened via [web page tester](https://www.webpagetest.org/), it should load under 500ms (milli seconds).

## Documents
- Visual designs for components - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/228211081
- API access : Url - http://demo.travelnxt.com/dev
- Tavisca Elements - https://github.com/atomelements and https://github.com/travelnxtelements
- Vaadin elements - https://vaadin.com/docs/-/part/elements/elements-getting-started.html
- Google - https://elements.polymer-project.org/browse?package=google-web-components
- Tavisca Web component style Guide - https://drive.google.com/open?id=0B7BT_2nBFNYVR2tscE9pRnVJYmc
