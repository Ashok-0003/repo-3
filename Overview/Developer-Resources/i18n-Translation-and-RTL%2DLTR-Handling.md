#Adding Localization Support for HTML elements
- To have localization support for Html elements add a **i18n** tag like below
`<p i18n>text</p>`
`<input label="text" i18n-label/>`
- Now run command **npm run i18n-extract**(found in package.json) which will generate xlf files with translation units under **locales** folder of main application.
_messages.ar.xlf(arabic) , messages.en-US.xlf(english) , messages.xlf(default)_
- Once xlf files are generated open **messages.ar.xlf** file and update the target element value to arabic for sepecific translation unit that was already generated from the above step like below
`<trans-unit id="GUID" datatype="html"><source>text</source><target>نص</target>....</trans-unit>`



# RTL Handling for HTML Controls
### Add **i18n-dir** tag with **dir="ltr"** to the div element.
`<div class="container-fluid" i18n-dir dir="ltr">...</div>`
### Run **ng xi18n** command to generate locale specific files and change the target element value to "rtl" like below in Arabic locale file.
`<trans-unit id="" datatype="html><source>ltr</source><target>rtl</target>....</trans-unit>`

If two css files are used for extra control on English and Arabic Styling [rtlcss](https://rtlcss.com/) will be helpful.
# RTL Handling for Kendo Controls
- ### Provide RTL value as true in providers.
  - `import { RTL } from '@progress/kendo-angular-l10n';`
  - `providers:[{provide:RTL, useValue:true}]`
# Kendo UI Components Support for RTL
- Please go to [Kendo UI components support for RTL](https://www.telerik.com/kendo-angular-ui/components/globalization/globalization-support/) to know more.