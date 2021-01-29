# build-task

I need to create a build task that creates some duplicate files (with filename changes and some content changes) in a dist/ directory for deploy according to the config I set up in `duplicate_config.json`.

## Templates

So, we have two basic templates: `src/templates/product.template.html` and `src/sections/product-sections-template.html` (which is included in the first file).

## Example output of build task

### Files

In the `duplicate_config.json`, I can see that I need to create duplicate files in dist/ for "abc-1", "abc-2", and "def-3". So, let's take "abc-1" as an example. After running through the build process, I would end up with the following new files in dist/:

`dist/templates/product.template.abc-1.html`

`dist/templates/product.template.html`

AND

`dist/sections/product-sections-template-abc-1.html`

`dist/sections/product-sections-template.html`

### File contents

Since the section is used inside the template, the reference inside the template also needs to be updated (you can see this inside the `src/templates/product.template.html` file. So, we need to update that line in the new duplicated template to be:

`{% section 'product-sections-template-abc-1' %}`
