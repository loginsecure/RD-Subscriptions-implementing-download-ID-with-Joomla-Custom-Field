# Big thanks go out to Mohamed Abdelaziz (mabdelaziz77)

The original creator of the below code is [mabdelaziz77](https://github.com/mabdelaziz77) and we want to thank him for creating and above all sharing this code with the world. The code is efficient and quick to understand and it helped us a lot and we are sure it will help a lot of other people as well. So thank you very much!

# What is the Download ID Field?

This is a custom Form Field to help Joomla! extension developers to implement the Joomla Update System and meet the new [JED requirement](https://extensions.joomla.org/support/knowledgebase/item/joomla-update-system-requirement/ "Joomla! Update System requirement") for **PAID** extensions.

This field is developed to be used with [RD Subscriptions](https://rd-media.org/rd-subscriptions.html) packages, although it can be customized to work with other subscriptions and release/download managers.

## What do you need to modify in your extension?

```
language/en-GB/en-GB.mod_yourextension.ini (modify each language)
models/fields/downloadid.php (needs to be added)
mod_yourextension.xml 

```

## How To Use It?

First of all, download the downloadid.php file and add it in a proper folder inside your extension package we recommend models/fields, so the the relative path should be mod_yourextension/models/fields/downloadid.php

Now, the Download ID field is ready to be used as any other standard form field within your installation xml file.

This is an example of parts of a module installation file, let's say mod_yourextension.xml
So the workorder is: Add files, fieldset and then the updateserver.

```
<files>
  <folder>models</folder>
</files>

<updateservers>
  <server type="extension" priority="1" name="Your Extension"><![CDATA[http://domain.extension/index.php?option=com_rdsubs&view=updater&format=xml&cat=#&element=mod_yourextension&type=module]]></server>
</updateservers>
<!-- Where # is the catagory number. Use the RD Subscription build in Menu item: Joomla XML Feed to generate the correct links. -->

<config>
  <fields name="params">
    <fieldset name="subscription" addfieldpath="/modules/mod_yourextension/models/fields">
      <field
	name="dlid"
	type="downloadid"
	label="MOD_YOUREXTENSION_-AUTOUPDATESUBSCRIPTIONTOKEN-_LABEL"
	description="MOD_YOUREXTENSION_-AUTOUPDATESUBSCRIPTIONTOKEN-_DESC"
	default=""
	extension="Your Extension"
	key="key="
	/>
    </fieldset>
  </fields>
</config>
```

Important

The Download ID field has two important additional attributes, _**extension**_ and _**key**_ where:

_**extension**_: must be the same as the _name_ attribute of &lt;server&gt;, this is very important to set the update the correct record in the update_sites table.

_**key**_: has a default value of "key=" which is used with RD Subscriptions combination, of course you can give it any other value if needed with any other subs and release managers.

> Note:
>
> You can use the Download ID field as it is, without any guarantees.
