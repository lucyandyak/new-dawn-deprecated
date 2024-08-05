# Lucy and Yak: Dawn Extensions

This document serves as a guide to extending the Dawn theme from Shopify.

This theme tracks the latest Dawn versions from Shopify and in order to keep on track the following guidelines are suggested to enable an easy upgrade path.

Any alterations are as far as possible to be layered over the exsiting theme without touching the original code if possible.

## Theme file extending

In the inevitable case that you need to extend an existing theme liquid file, a new file should be created in snippets with the following format **"ly__{extend|replace}__{folder}__{filename}__{extra_info}.liquid"**

e.g. Extending the theme.liquid you would create a file named **"ly__extend__layout__theme__head.liquid"** in snippets

This file will then contain your actual code changes and should be included in the original theme.liquid like so **{% render 'ly__extend__layout__theme__head' %}** this should enable us to relatively easily search and find altered files in the codebase.

## Theme file replacing

Follow the steps above but name your file **"{original filename}__ly.liquid"**, files named like this should sit under the original file in most directory listing and makle it easy to see that the file above is being overwritten.

Then in first line of your file (e.g. theme.liquid) render your new file and {% comment %} the remainder of the original file.

## Assets

All CSS changes to be made in a separate file that consists of the original filename plus __ly e.g. **base.css becomes base_ls.css**

See base__ly.css for examples of how css to be laid out, please heavily comment css and organise into logical sections. Use liquid suffix where possible in order that we can leverage liquid tags in the css for pulling in settings etc. CSS to be rendered in templates using the assets tag which will strip out any comments and whitespace.

JS changes TBC

## Example 

Look at theme/layout.liquid (search __ly__extend) to see the included snippet

## Merging in Dawn (public) updates

If you would like to merge the latest Dawn updates into this theme then you should add the Dawn public repo like so to your remote:

`git remote add dawn-public https://github.com/Shopify/dawn.git`

Now checkout a new branch e,g, 

`git checkout -b merge/dawn-2024-08-05`

Now you may pull the latest updates from dawn public like so:

`git pull dawn-public main`

You may need to specifiy how Git handles merging in divergent branches e.g. to merge

`git config pull.rebase false`

Now fix any overwrites and clashes that may occur and now you can merge the merge/dawn-2024-08-05 into main.




