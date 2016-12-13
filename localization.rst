Localization
============

It is possible to attain a localized version of a Saiku view in the Saiku standalone version.
Follow these steps:
In the admin pane, add following to the datasource: "DynamicSchemaProcessor=mondrian.i18n.LocalizingDynamicSchemaProcessor;locale=en_US;"
Go to WEB-INF/classes/mondrian.properties and enable the LocalizingDynamicSchemaProcessor by adding following line: "mondrian.rolap.localePropFile=locale.locale". This line tells that you will add a folder 'locale' that contains files prefixed with 'locale' containing the translations.
Create the folder 'locale' in WEB-inf/classes/ and add some files:
locale_en_US.properties
locale_fr_FR.properties
Provide translations in your mondrian schema by changing variable names with the ${} notation.
Provide these translations in the properties files of step 3.
Test your set-up
From this point, you can manually check whether your translations work by changing the locale in the datasource definition.
Enable the ChangeLocale plugin by going to the Saiku Settings.js file and adding 'ChangeLocale' to the PLUGINS array:
PLUGINS: [
"Chart",
"ChangeLocale"
],
Make sure the locales are mapped in the settings.js file:
Settings.MONDRIAN_LOCALES = {
"English": "en_US",
"Dutch": "nl_BE",
"French": "fr_FR"
};
A new button  will appear which will change the locale in the data source definition and reload the connection with the translations.
The headers will not be translated in cause you use a Mondrian version prior to 4.3.0.1-SPARK. 
