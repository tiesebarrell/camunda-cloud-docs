# Camunda Cloud Documentation

This repository contains the sources of the Camunda Cloud Documentation. The framework used for this is [Docusaurus](https://docusaurus.io/).

## Running the documentation locally

Change to the `website` directory and run `npm run start`:

```bash
cd website
npm run start
```

You can now browse the docs under [http://localhost:3000/](http://localhost:3000/). Docusaurus will automatically detect when you change a file and refresh the page in the browser.

## Publishing

All commits to the branch `gh-pages` are automatically published to GitHub Pages. Locall you can use the following command as well:

```bash
cd website
GIT_USER=${user} CURRENT_BRANCH=master USE_SSH=true npm run publish-gh-pages
```

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/3.0/80x15.png"></a> The content on this site is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/">Creative Commons Attribution-ShareAlike 3.0 Unported License</a>.

## Writing docs

There are two places to consider:

1. The documentation itself is located in the `docs` directory.
2. The framework in the folder `website`.

### Documentation

- All Markdown files are located in the `docs` folder. Each markdown file has a header, which contains an ID and a title.
- Images or other files are stored in the folder `docs/assets`.

### Framework

- Structure of the documentation: [website/sidebars.json](./website/sidebars.json)
- Starting page: [website/pages/en/index.js](./website/pages/en/index.js)
- Help: [website/pages/en/help.js](./website/pages/en/help.js)
- Users: [website/pages/en/users.js](./website/pages/en/users.js)
- Footer: [website/core/footer.js](./website/core/footer.js)
