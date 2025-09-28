# scoutaloud site

## Zola

This site is built with [zola static site generator](https://www.getzola.org/documentation/getting-started/overview/) using the Papaya theme.

## Architecture

Right now there is only one area of the site with content: the travel section.

Sections are set up in the [config.toml](./config.toml) inside menu_items. I have commented out the original sections for projects and blog for now.

To add entries to a section, find the corresponding directory inside `./content` and add it there.

### Travels

For travels, add one directory for each trip. Inside, create an index.md file stating `title`, `template` and `date` in the front matter. This will be the main page for the trip which will be linked to from the url `/travels`. Further pages for that trip should be added to the same directory. Link to those pages from the index file like so: `[link-name](file-name/)`.

## Papaya

The [Papaya theme](https://www.getzola.org/themes/papaya/) is set up for two types of content: blog and project types.

The theme lives in `/themes`. If there is need to change one of the theme's templates, it is best to follow this procedure:

>Copy the file from `/themes/papaya/templates` to `/templates` and then make changes in this file. Zola will use the files inside the root's templates folder preferentially and ignore files of the same name in the themes directory.