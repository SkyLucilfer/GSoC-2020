# Improving Godot's i18n support

Localization is part of game development if one wishes to make their games more accessible to a wider audience. The process of localization involves text translation, audio translation and maybe even cultural adjustment to specific regions.

This GSoC project aims at improving Godot's support for text translation. In Godot, we have 2 ways of importing translation - by using CSV or PO files. CSV is simple to understand and use. It provides one to one translation for a string key, i.e. for a given sentence there's one translation that maps to the sentence. PO files are a bit more complicated to understand, but they can handle translation involving plurals and context. Translation involving plurals can be tricky because different languages have different plural rules. PO files are capable of encoding these information.

The work that has been done so far involves improving Godot's support for PO files. 

## POT Generation
POT files are squelettes for PO files. When we have a POT file, we can convert it to PO files of different languages, for example fr.po, ru.po etc. 




Users can now generate translation template (POT) files through the Godot's Editor. This feature can be found under "Project Settings" tab. Users can include the files that contain translatable strings, click "Generate POT", and the transltable strings in the files will be extracted and written into a POT file.

Futhermore, a plugin system is implemented which allows users to define their custom parsers to extract the translatable strings. With this, users can write their own parsers to extend the POT generation system to handle files with different formats. 

To find out more about the pull request: https://github.com/godotengine/godot/pull/39415


## Plurals and context support
Plurals and context support has been one of the feature that is missing from Godot's i18n system. Users can now use the newly added API for translating plurals and providing context in a translation. The added APIs are:
- For project:
  - tr_n(message, plural_message, n, context = "")

- For Editor:
  - TTRN(message, plural_message, n, context = "")
  - DTRN(message, plural_message, n, context = "")
  - RTRN(message, plural_message, n, context = "")

- All existing translation functions can now add context with the last argument too.
  - tr(message, context = "")
  - TTR(message, context = "")
  - etc.

To find out more about the pull request: https://github.com/godotengine/godot/pull/40443

