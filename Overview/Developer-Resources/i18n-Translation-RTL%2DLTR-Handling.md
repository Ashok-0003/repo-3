# RTL Handling for HTML Controls
### Add **i18n-dir** tag with **dir="ltr"** to the div element.
`<div class="container-fluid" i18n-dir dir="ltr">...</div>`
### Run **ng xi18n** command to generate locale specific files and change the target element value to "rtl" like below in Arabic locale file.
`<trans-unit id="" datatype="html><source>ltr</source><target>rtl</target>....</trans-unit>`
# RTL Handling for Kendo Controls
- ### Provide RTL value as true in providers.
  - `import { RTL } from '@progress/kendo-angular-l10n';`
  - `providers:[{provide:RTL, useValue:true}]`
# Kendo UI Components Support for RTL
- Please go to [Kendo UI components support for RTL](https://www.telerik.com/kendo-angular-ui/components/globalization/globalization-support/) to know more.