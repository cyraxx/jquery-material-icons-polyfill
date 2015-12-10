# Google Material Icons Webfont Polyfill for browsers without ligature support

Allows you to use the [Google Material Icons Webfont](https://www.google.com/design/icons/) the regular way
in browsers that don't support OpenType ligatures (such as IE8 and IE9) by replacing the ligatures with the
corresponding Unicode code points.

## How to use

Include the Material Icons Webfont and use it the regular way:

```
<i class="material-icons">face thumb_up</i>
```

To add support for older browsers then include jQuery and the polyfill and call the `materialIcons()`
function on the document:

```
<script src="jquery-material-icons-polyfill.js"></script>
<script>
	$(function() {
		$(document).materialIcons();
	});
</script>
```

If you dynamically add DOM elements with Material Icons you will need to call `materialIcons()` on the
newly added element or its container again.

**Please note:** The polyfill currently does not detect if the browser supports ligatures and runs even if it
does, resulting in a small performance impact. It is recommendable to run it only if needed, for example using
[Modernizr](https://modernizr.com):
```
if(!Modernizr.prefixed('fontFeatureSettings')) $(document).materialIcons();
```

## Known restrictions

With native ligature support it is possible to combine multiple icons in one tag without separation:
```
<i class="material-icons">facethumb_up</i>
```
This is not currently supported by the polyfill, icons need to be separated by white space.

## Updating the list of code points

A dictionary of code points is included at the top of the script and might need to be updated when Google releases
a new version of the icon font. The current list is available at
[Google's GitHub](https://raw.githubusercontent.com/google/material-design-icons/master/iconfont/codepoints).