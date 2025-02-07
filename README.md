[![Known Vulnerabilities](https://snyk.io/test/github/beenote/angular-material-datetimepicker/badge.svg)](https://snyk.io/test/github/beenote/angular-material-datetimepicker)
[![npm version](https://badge.fury.io/js/ng-material-datetimepicker.svg)](https://badge.fury.io/js/ng-material-datetimepicker)
[![Open Source Love](https://badges.frapsoft.com/os/mit/mit.svg?v=102)](https://github.com/ellerbrock/open-source-badge/)
[![dependencies Status](https://status.david-dm.org/gh/beenote/angular-material-datetimepicker.svg)](https://david-dm.org/beenote/angular-material-datetimepicker)
[![devDependencies Status](https://status.david-dm.org/gh/beenote/angular-material-datetimepicker.svg?type=dev)](https://david-dm.org/beenote/angular-material-datetimepicker?type=dev)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

# Angular Material DateTimePicker
Originally designed for Bootstrap Material, this has been modified to work with [Angular Material](https://material.angularjs.org/). This is an Android style date-time picker for Angular Material. Some added features include:

- Double or single click to select date and/or time
- Mouse click down with mouse move or touch move to select time
- Swipe left to go to next month or Swipe right to go to previous month
- Quick year and month menu selector
- Configurable first day of the week
- Support 24-hour format display
- Can disable dates, not selectable by user
- Highlight Week days (Business Days)
- Can disable minutes view
- 1 to 59 minute steps (normally 1, 5, 10, 15)
- Optionnal seconds clock
- Compatible with right-to-left direction
- Support RequireJS and Webpack
- Possibility to set a custom external template
- Support moment utc or ng-model-options timezone

## Updates
| Date       | Author      | Description                                            |
| ---------- | ----------- | ------------------------------------------------------ |
| 2018-06-15 | hexadecy    | Can hide Today button                                  |
| 2018-02-09 | hexadecy    | support ng-model-options timezone                      |
| 2018-01-29 | coennijhuis | min-date max-date validation when not using the picker |
| 2017-10-18 | paragraff   | custom template                                        |
| 2017-09-11 | hexadecy    | show-icon button with edit-input mode                  |
| 2017-08-19 | hexadecy    | Quick year and month menu selector                     |
| 2017-08-12 | hexadecy    | Add optionnal seconds clock                            |
| 2017-07-30 | hexadecy    | Highlight only week-days (business days)               |
| 2017-07-22 | hexadecy    | Mouse or touch move to select time, minute steps param |
| 2017-04-26 | hexadecy    | New 24-hour clock face                                 |
| 2017-04-17 | hexadecy    | Single click to select                                 |
| 2017-02-27 | hexadecy    | Can hide minutes view, Month next and prev buttons     |
| 2017-02-22 | hexadecy    | Fix for rtl website                                    |
| 2017-02-15 | hexadecy    | Fix inputs are not bluring after selection is made     |
| 2017-01-30 | hexadecy    | Add support for angular 1.6.x                          |
| 2015-11-12 | logbon72    | Adapted plugin for Angular Material                    |

### Dependencies
Depends on the following library:

- AngularJS Material
- AngularJS Animate
- AngularJS Aria
- AngularJS
- Moment

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular-animate.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular-messages.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.8.2/angular-aria.min.js"></script>
<link href="https://cdnjs.cloudflare.com/ajax/libs/angular-material/1.2.3/angular-material.min.css" rel="stylesheet" type="text/css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular-material/1.2.3/angular-material.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment-with-locales.min.js"></script>
```

## Installing with yarn or npm
```
yarn add ng-material-datetimepicker
npm i ng-material-datetimepicker
```

## CDN
```
<script src="https://unpkg.com/ng-material-datetimepicker/dist/angular-material-datetimepicker.min.js"></script>
<script src="https://unpkg.com/ng-material-datetimepicker/dist/angular-material-datetimepicker.min.js.map"></script>
<link href="https://unpkg.com/ng-material-datetimepicker/dist/material-datetimepicker.min.css rel="stylesheet" type="text/css">
```
or
```
<script src="https://cdn.jsdelivr.net/npm/ng-material-datetimepicker/dist/angular-material-datetimepicker.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/ng-material-datetimepicker/dist/angular-material-datetimepicker.min.js.map"></script>
<link href="https://cdn.jsdelivr.net/npm/ng-material-datetimepicker/dist/material-datetimepicker.min.css" rel="stylesheet" type="text/css">
```

## Live Example
Click [here](https://beenote.github.io/angular-material-datetimepicker/) to see live examples.

## Usage
Add the plugin module as a dependency to your AngularJS module:

```js
    angular.module('myAwesomeModule', [
      //other dependencies ignored
      'ngMaterialDatePicker'
    ]);
```

This plugin exposes a directive which should be used as an attribute for an input element. The directive is
`mdc-datetime-picker`. An example of this is given below:

```html
    <md-input-container flex-gt-md="30">
        <label>Timepicker Only</label>
        <input mdc-datetime-picker date="false" time="true" type="text" id="time" short-time="true"
               show-todays-date click-outside-to-close="true"
               placeholder="Time" auto-ok="true"
               min-date="minDate" minute-steps="1"
               format="hh:mm a"
               ng-change="vm.saveChange()"
               ng-model="time">
    </md-input-container>
```

### Directive Attributes
The directive accepts several attributes which are described below:

| Name                      | Type                    | Description                                                          |
| ------------------------- | ----------------------- | -------------------------------------------------------------------- |
| **ng-model**              | (String\|Date\|Moment   | Initial Date or model to assign the date to                          |
| **ng-change**             | Function                | A function to call when the input value changes                      |
| **format**                | String                  | [MomentJS Format](momentjs.com/docs/#/parsing/string-format/),defaults to `HH:mm` for time picker only, `YYYY-MM-DD` for date picker only and `YYYY-MM-DD HH:mm` for both timepicker and date picker |
| **short-time**            | Boolean                 | true => Display 12 hours AM\|PM (default: false)                     |
| **min-date**              | (String\|Date\|Moment)  | Minimum selectable date                                              |
| **max-date**              | (String\|Date\|Moment)  | Maximum selectable date                                              |
| **date**                  | Boolean	                | true => Has Datepicker (default: true)                               |
| **time**                  | Boolean                 | true => Has Timepicker (default: true)                               |
| **minutes**               | Boolean                 | true => Has Timepicker minutes (default: true)                       |
| **seconds**               | Boolean                 | true => Has Timepicker seconds (default: false)                      |
| **cancel-text**           | String                  | Text for the cancel button (default: Cancel)                         |
| **am-text**               | String                  | Text for the ante meridiem (default: AM)                             |
| **pm-text**               | String                  | Text for the post meridiem (default: PM)                             |
| **today-btn**             | Boolean                 | true => Show today button (default: true)                            |
| **today-text**            | String                  | Text for the today button (default: Today)                           |
| **ok-text**               | String                  | Text for the OK button (default: OK)                                 |
| **week-start**            | Number                  | First day of the week (default: 0 => Sunday)                         |
| **disable-dates**         | Date[]                  | Dates to be disabled or not selectable by user                       |
| **week-days**	            | Boolean                 | true => Highlight only week-days (default: false)                    |
| **show-todays-date**      | Attribute               | Show today's date (default: false)                                   |
| **disable-parent-scroll** | Boolean                 | true => Disable scrolling while the dialog is open (default : false) |
| **auto-ok**               | Boolean                 | true => Single click (default: false)                                |
| **edit-input**            | Boolean                 | true => Input editable and don't show dialog (default: false)        |
| **click-outside-to-close**| Boolean                 | true => A click outside close the dialog (default: false)            |
| **minute-steps**          | Number                  | 1 to 59 minute steps (default: 5)                                    |
| **show-icon**             | Boolean                 | true => Show calendar or time icon before (default: false)           |
| **show-clear**            | Boolean                 | true => clear (default: true if show-icon)                           |
| **template-url**          | String                  | You can set a custom HTML template (default: '')                     |
| **ng-model-options**      | timezone option         | For example: ng-model-options="{timezone: 'utc'}"                    |
| **day-of-week-len**       | Number                  | Day of the week length (default: 1 => S) Possible value 0-3          |
| **has-backdrop**          | Boolean                 | true => Has Backdrop (default: true)                                |

### UTC Time Zone
You should normally use the browser local time zone and use UTC only on the server side.
But if you have special case, you can set the model to a moment.utc() and it will stay a moment utc object.
You can also use the `format="YYYY-MM-DD HH:mmZ"` for parsing if your server returns an UTC date time.
Also, if you want your user to manually enter an UTC time use the `ng-model-options timezone` as in the demo.

### Set or update params by injecting `mdcDefaultParams` provider
To change params like the locale you can use this method instead of attributes for all datetimepicker:
```javascript
  mdcDefaultParams({lang: 'fr', cancelText: 'annuler', todayText: 'maintenant', okText: 'ok', dayOfWeekLen: 3});
  ...
  mdcDefaultParams({lang: 'en', cancelText: 'cancel', todayText: 'now', okText: 'ok', dayOfWeekLen: 3});
```
#### Notes
If you use https://github.com/lgalfaso/angular-dynamic-locale it will always override the locale.

### Date/Time Dialog Service
You can also use the Date Time picker as a service, using the `mdcDateTimeDialog` service. The dialog returns a promise which is resolved with the selected date-time value and rejected on cancellation. 

Example usage: 

```javascript
    someModule.controller('DemoCtrl', function ($scope, mdcDateTimeDialog) {

      $scope.displayDialog = function () {
        mdcDateTimeDialog.show({
          maxDate: $scope.maxDate,
          time: false
        }).then(function (date) {
          $scope.selectedDateTime = date;
          console.log('New Date / Time selected:', date);
        }, function() {
          console.log('Selection canceled');
        });
      };
    })
```

The `mdcDateTimeDialog.show` accepts almost the same options as the directive. 

```javascript
     {
       date: {boolean} =true,
       time: {boolean} =true,
       minutes: {boolean} =true,
       seconds: {boolean} =true,
       format: {string} ='YYYY-MM-DD',
       minDate: {strign} =null,
       maxDate: {string} =null,
       currentDate: {string} =null,
       lang: {string} =window.navigator.userLanguage || window.navigator.language || 'en',
       weekStart: {int} =0,
       shortTime: {boolean} =false,
       cancelText: {string} ='Cancel',
       todayBtn: {boolean} =true,
       todayText: {string} ='Today',
       showTodaysDate: {string} ='',
       okText: {string} ='OK',
       amText: {string} ='AM',
       pmText: {string} ='PM',
       disableDates: {date[]} =[],
       weekDays: {boolean} =false,
       disableParentScroll: {boolean} =false,
       autoOk: {boolean} =false,
       editInput: {boolean} =false,
       clickOutsideToClose: {boolean} =false,
       minuteSteps: {int} =5,
       showIcon: {boolean} =false,
       showClear: {boolean} =true,
       templateUrl: {string} =''
       targetEvent: {DOMClickEvent}=null,
       openFrom: {string|Element|object}=null,
       closeTo: {string|Element|object}=null,
       dayOfWeekLen: {int} =1,
       hasBackdrop: {boolean} =true
     }
```

### Theming
Copy this css code in your project to override default color.
```css
.dtp table.dtp-picker-days tr > td > a.selected,
.dtp table.dtp-picker-days tr > td > a.selected.hilite,
.dtp div.dtp-date, .dtp div.dtp-time, .dtp .dtp-hand.on,
.dtp .dtp-actual-meridien a.selected,
.dtp .dtp-picker-time > a.dtp-select-hour.selected {
  background: #2abab9;
}

.dtp table.dtp-picker-days tr > td > a.hilite:not(.selected),
.dtp div.dtp-actual-time.p60 span.selected {
  color: #2abab9;
}

.dtp div.dtp-year-btn, .dtp div.dtp-actual-year, .dtp div.dtp-actual-maxtime {
  color: #d0f0f0;
}

.dtp > .dtp-content > .dtp-date-view > header.dtp-header {
  background: #009796;
}

md-menu-content.dtp-month-list {
  background-color: #d0f0f0;
}

md-menu-content.dtp-year-list {
  background-color: #d0f0f0;
}

```

### Development
To run the demo:
```
yarn start
```

To build with esbuild:
```
yarn build
````

