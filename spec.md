# t-guest-info Specification

### Component Use
```javascript
<t-passenger-info data=[[data]] resources=[[resources]] settings=[[settings]]>
</t-passenger-info>
```

### Settings
```javascript
{
    "showAllPaxDetails": false,
    "ëmailRegEx":"",
    "code":"pax1",
    "maxInputLength":100
}
```

### Data
```javascript
{
    "title": "Room 1",
    "subTitle": " - Strip View, 1 King Bed | 2 Adults, 2 children",
    "terms": [
        "FREE cancellation before 11:59 on April 25,2017",
        "You can cancel or change for free."
    ],
    "paxDetails": [
        {
            "title": "",
            "firstName": "",
            "lastName": "",
            "type": "Adult"
        },
        {
            "title": "",
            "firstName": "",
            "lastName": "",
            "type": "Child"
        }
    ],
    "contactInfo": {
        "email": "",
        "countryCode": "",
        "phone": ""
    }
}
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
