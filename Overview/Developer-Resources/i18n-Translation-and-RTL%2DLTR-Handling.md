#Adding Localization Support for HTML elements
- To have localization support for Html elements add a **i18n** tag like below
`<p i18n>text</p>`
`<input label="text" i18n-label/>`
- Now run command **npm run i18n-extract**(found in package.json) which will generate xlf files with translation units under **locales** folder of main application.
_messages.ar.xlf(arabic) , messages.en-US.xlf(english) , messages.xlf(default)_
- Once xlf files are generated open **messages.ar.xlf** file and update the target element value to arabic for sepecific translation unit that was already generated from the above step like below
`<trans-unit id="GUID" datatype="html"><source>text</source><target>نص</target>....</trans-unit>`

#Adding Localization Support for text in Code(TS files)
- To have localization support for the text in code add **$localize** decorator to that specific string value like below
_public static successMessage = $localize\`:@@succes_message:verified successfully\`_
- Next a translation unit should be manually added in both  and messages.en-US.xlf with id **success_message**like below
_**messages.ar.xlf**_
`<trans-unit id='success_message'><source>verified successfully<source><target>تم التحقق بنجاح</target></trans-unit>`
_**messages.en-US.xlf**_
`<trans-unit id='success_message'><source>verified successfully<source><target>verified successfully</target></trans-unit>`

#Localization changes in library projects
- In some cases, if **i18n tag** or **$localize** decoratorare added for localization in **_library projects_** below are the steps to generate translation units for the same.
- Navigate to the library project where i18n tag or $localize decorator is added.
- Link the library project to the main applications**(marketplace or eservices or account)** where it is being used refer https://web.microsoftstream.com/video/4c40a1ff-0400-b9eb-9ded-f1eb2d5e65e6
- Once library linking is done navigate to main application and run below command
`npm run i18n-extract`
**NOTE**: Translation units will be generated automatically only for i18n tags added in html. In case of code translations using $localize a trans-unit should be maually added.

#Debug Localization
- Once the Localization resource files are updated run below commands to serve/open the application in specific language
**_For Arabic version_**:
`ng serve --configuration=production-ar`
**_For English version_**:
`ng serve --configuration=production-en-US`

# RTL Handling for HTML Controls
### Add **i18n-dir** tag with **dir="ltr"** to the div element.
`<div class="container-fluid" i18n-dir dir="ltr">...</div>`
### Run **npm run i18n-extract** command to generate locale specific files and change the target element value to "rtl" like below in Arabic locale file.
`<trans-unit id="" datatype="html><source>ltr</source><target>rtl</target>....</trans-unit>`

# RTL Handling for Kendo Controls
- ### Provide RTL value as true in providers.
  - `import { RTL } from '@progress/kendo-angular-l10n';`
  - `providers:[{provide:RTL, useValue:true}]`
# Kendo UI Components Support for RTL
- Please go to [Kendo UI components support for RTL](https://www.telerik.com/kendo-angular-ui/components/globalization/globalization-support/) to know more.ug