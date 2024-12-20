# Documentation

Building
==================
Before building, run the `prepare-build.sh` script, to copy the xmls provided by libqalculate

Button connection
==================

Most buttons are connected using a gdscript with the same name. Notable exceptions are Numbers, which connect to `button0.gd`, and certain functions that spawn parenthesis after their text (ex. ln, √, trig functions) which connect to `name_then_parenthesis.gd`. 

Functions
==================
Functions are retrieved from the functions.xml, then added to the Tree as TreeItems. When a TreeItem is activated it calls the `_on_functions_item_activated` function from the `input` with 3 arguments, the name of the function in libqalculate, the title for the popup, and the TreeItem. This is written in this way so that we're able to reuse the same function for the logarithm and summation buttons on tab 2, those buttons use null as third argument, as it isn't a TreeItem.

Units
==================

The unit list is generated using the `units.gd` script. It parses the `/usr/share/qalculate/units.xml` file to get the names and the categories, then using the `_unit_abbreviation()` function from the cpp code, it gets the name/symbol that qalculate understands when using it as input, it's stored in the TreeItem of the unit as metadata in column 0. the `_unit_abbreviation()` function is called through the enter button, since instancing the gdextension class again causes issues like [#1](https://gitlab.com/mike7d7/calculator/-/issues/1#).

Android
==================

In the `libs-build/` folder, there's the `build-libs-android.sh` script, which compiles all native libraries for Android.
You shouldn't have to manually run this script, as it is run by `prepare-build.sh`.

Icons
==================

Icons used are modified versions of Cosmic Icons
Modifications:
- Change color to #f5f5f5
- Change size to be the same as font size
"[Cosmic Icons](http://github.com/pop-os/cosmic-icons)" by [System76](http://system76.com/) is licensed under [CC-SA-4.0](http://creativecommons.org/licenses/by-sa/4.0/)

Colors
==================

Colors are based on [Catppuccin's](https://github.com/catppuccin/catppuccin/blob/main/docs/style-guide.md#language-defaults) color's for code editors.
