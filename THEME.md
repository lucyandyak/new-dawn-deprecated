# Lucy and Yak: Dawn Extensions

This document serves as a guide to extending the Dawn theme from Shopify.

This theme tracks the latest Dawn versions from Shopify and in order to keep on track the following guidelines are suggested to enable an easy upgrade path.

Any alterations are as far as possible to be layered over the exsiting theme without touching the original code if possible.

## Theme file extending

In the inevitable case that you need to extend an existing theme liquid file, a new file should be created in snippets with the following format "ly__{extend|replace}__{folder}__{filename}__{extra_info}.liquid"

e.g. Extending the theme.liquid you would create a file named "ly__extend__layout__theme__head.liquid" in snippets

This file will then contain your actual code changes and should be included in the original theme.liquid like so {% render 'ly__extend__layout__theme__head' %} this shoudl enable us to relatively easily search and find altered files in the codebase.

## Theme file replacing

Follow the steps above but name your file "{original filename}_ly.liquid", files named like this should sit under the original file in most directory listing and makle it easy to see that the file above is being overwritten.

Then in first line of your file (e.g. theme.liquid) render your new file and {% comment %} the remainder of the original file.

## Assets






