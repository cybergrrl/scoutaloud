# scoutaloud site

## Quick Start for Developers

### Requirements

- Zola (tested with version 0.21.0)

### Setup

#### Install Zola

**macOS:**
```sh
brew install zola
```

ideally check that the version that is installed is 0.21.0. there might be ways to guarantee this.

**Linux:**
Download the latest release from [Zola releases](https://github.com/getzola/zola/releases) and extract the binary:
```sh
wget https://github.com/getzola/zola/releases/download/v0.21.0/zola-v0.21.0-x86_64-unknown-linux-gnu.tar.gz
tar xzf zola-v0.21.0-x86_64-unknown-linux-gnu.tar.gz
sudo mv zola /usr/local/bin/
```

#### Run the site locally

```sh
zola serve
```

This will start a local server, usually at http://127.0.0.1:1111

---

**Note:** If you use scripts to generate markdown files, see their specific requirements in their own repositories.

## Zola

This site is built with [zola static site generator](https://www.getzola.org/documentation/getting-started/overview/) using the Papaya theme.

## Architecture

Right now there is only one area of the site with content: the travel section.

Sections are set up in the [config.toml](./config.toml) inside menu_items. I have commented out the original sections for projects and blog for now.

To add entries to a section, find the corresponding directory inside `./content` and add it there.

### Travels

For travels, add one directory for each trip.

Inside, create an index.md file stating `title`, `template` and `date` in the front matter. This will be the main page for the trip which will be linked to from the url `/travels`. Further pages for that trip should be added to the same directory. Link to those pages from the index file like so: `[link-name](file-name/)`.

### Images

They can be linked to like so if they live in the same directory as the content file:

```

{{ img(path="./dubrovnik-1.jpg",
       alt="Dubrovnik seen from the sea",
       caption="Dubrovnik") }}
```

They can be hosted elsewhere and linked like so:

```

<figure>
  <img src="https://www.dropbox.com/scl/fi/j2d8fjoj5f8hzs0b6mlzd/2025-10-06-12.53.22.jpg?rlkey=u7sdpm1tc5nru20yqu0hf74zc&st=itvmhcjr&raw=1" alt="Dubrovnik seen from the walls" />
  <figcaption>Roofs of Dubrovnik from the walls</figcaption>
</figure>
```

>Note that for dropbox links to work, the link must first be created in Dropbox using the share button,  the share must be set to public, and then the resulting link must be edited: the `dl=0` at the end of the link must be changed to `raw=1`