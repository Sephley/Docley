# Docley

## Requirements
- GitHub Runner

## Installation
- Create the file `mkdocs.yml` in the root of your repository with the following content:
```
site_name: My MkDocs Website
theme:
    name: bootstrap386
```
- Create a directory called `docs` with a file called `index.md`. The contents of this file will be displayed on your website.
- Copy the file from the `.github/workflows directory` into your own workflows directory.
- Enable GitHub pages in your repository settings | Make sure to deploy from the `gh-pages` branch from the `root` directory.

## Help
If you would like to edit for example the navigation bar, this can be configured in the `mkdocs.yml` file | See the [official documentation](https://www.mkdocs.org/user-guide/configuration/)
