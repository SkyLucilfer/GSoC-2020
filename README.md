# Improving Godot's i18n support

Localization is part of game development if one wishes to make their games more accessible to a wider audience. The process of localization involves text translation, audio translation and even cultural adjustment for specific regions.

This GSoC project aims at improving Godot's support for text translation. In Godot, we have two ways of importing translation - by using CSV or PO files. CSV is simple to understand and use. It provides one to one translation for a string key, i.e. for a given sentence there is one translation that maps to the sentence. PO files are a bit more complicated to understand, but they can handle translation involving plurals and context. Translation involving plurals can be tricky because different languages have different plural rules. PO files are capable of encoding these information.

During this GSoC period, I have been able to implement two features so far. Both of the features aim to improve Godot's support for PO files.

## POT Generation
![](https://github.com/SkyLucilfer/GSoC-2020/blob/master/TranslationParserPlugin.png)

POT files are templates for PO files. When we have a POT file, we can convert it to PO files of different languages, for example fr.po, ru.po etc. using a PO editor or gettext tools.

Users can now generate POT files through the Godot's Editor. This feature can be found under "Project Settings" tab. Users can include the files that contain translatable strings, click "Generate POT", and the translatable strings in the files will be extracted and written into a POT file.

Furthermore, a plugin system is implemented which allows users to define their custom parsers to extract the translatable strings. With this, users can write their own parsers to extend the POT generation system to handle files with different formats. 

To find out more about the pull request for this feature: https://github.com/godotengine/godot/pull/39415


## Plurals and context support
Plurals and context support has been one of the features that is missing from Godot's i18n system. Users can now use the newly added API for translating plurals and providing context in a translation. The added APIs are:
- For project:
  - tr_n(message, plural_message, n, context = "")

- For Editor:
  - TTRN(message, plural_message, n, context = "")
  - DTRN(message, plural_message, n, context = "")
  - RTRN(message, plural_message, n, context = "")

- All existing translation functions can now add context with the last argument too.
  - tr(message, context = "")
  - TTR(message, context = "")

To find out more about the pull request for this feature: https://github.com/godotengine/godot/pull/40443

