# Docley
My personal Documentation
## Requirements
- GitHub Runner

## Installation
- Create a GitHub repository
- Create the file `mkdocs.yml` in the root of your repository with the following content:
```
site_name: My MkDocs Website
theme:
    name: bootstrap386
```
- Create a directory called `docs` with a file called `index.md`. The contents of this file will be displayed on your website.
- Create the directories `.github/workflows directory` and add a file called `ci.yml` with the following content:
```
name: deploy website
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v3
        with:
          key: mkdocs-bootstrap386-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-bootstrap386-
      - run: pip install mkdocs mkdocs-bootstrap386 
      - run: mkdocs gh-deploy --force
```
*note that if you are using a different theme, you will need to replace the mkdocs-bootstrap386 theme with the one you are using.*  
- Enable GitHub pages in your repository settings | Make sure to deploy from the `gh-pages` branch from the `root` directory.

## Help
If you would like to edit for example the navigation bar, or enable some plugins, this can be configured in the `mkdocs.yml` file | See the [official documentation](https://www.mkdocs.org/user-guide/configuration/)
