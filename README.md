## Google Summer of Code 2020
This repository documents the progress of my work during GSoC 2020 with [Godot Engine](https://github.com/godotengine/godot).

&nbsp;

### Context
During this GSoC period, my responsibility was to enhance the internationalization (i18n) support in Godot. 

My main focus was to upgrade the support of gettext PO files. This included making the workflow of using PO files more user-friendly,
and also upgrading the translation system to capture PO files' full capability - plurals support, context support, and the ability to include translator comments.

&nbsp;

### Work done 
Below contains the major milestones of my GSoC work. The dates might not be exact, but they should depict the correct order of the work that has been done.

&nbsp;

9 Jun 2020 - Added POT generation in Editor.

23 Jun 2020 - Added plugin support in POT generation.

- [PR39415](https://github.com/godotengine/godot/pull/39415)

&nbsp;

16 July 2020 - Added plurals and context support in translation for game projects and Editor.

23 July 2020 - Updated POT generation to handle plurals and context.

7 August 2020 - Refactored the Translation class to have a proper class handling PO files.

13 August 2020 - Updated translation parser to use GDScript parser instead of RegEx.

- [PR40443](https://github.com/godotengine/godot/pull/40443)

&nbsp;

9 August 2020 - Created a tutorial for localization using PO files.

- [PR3935](https://github.com/godotengine/godot-docs/pull/3935)

&nbsp;

19 August 2020 - Added translators comments extraction for Editor.

- [PR41510](https://github.com/godotengine/godot/pull/41510)

&nbsp;

23 August 2020 - Added CSV plural support.

- [PR41519](https://github.com/godotengine/godot/pull/41519)

&nbsp;

27 August 2020 - Updated CSV translation tutorial.

- [PR3939](https://github.com/godotengine/godot-docs/pull/3939)

&nbsp;

29 August 2020 - Updated the existing translation demo project to include all the newly implemented features.

- [PR516](https://github.com/godotengine/godot-demo-projects/pull/516)

&nbsp;


### Future work

Users now should have a smooth workflow to get their games translated, both in using CSV files or PO files.

However, there are still some areas that could be worked on in the future.

- Make CSV files easy to update.

With what users have currently, it will be quite hard to track down new strings and deprecated strings when the CSV file gets updated. This will be especially tedious for the translators. It will be ideal to have some kind of mechanism to make it very apparent what needs rework. 

- Implement a feature to exclude out scene nodes that don't need to be translated.

In Unreal engine, they do it via something called a `FText` class, which allows more localization information to be recorded into a node. One of the information is whether to ignore translating the selected node.

