# Neoskop Development Guidelines

_A collection of guidelines, best practices and tools used in development at
[Neoskop](https://www.neoskop.de)._

> **Note**: This repository serves as a living document, representing our development workflow.
> _Please use pull requests to keep this document up to date and challenge outdated or obsolete
> contents whenever you see fit._

## Table of Contents

- [Neoskop Development Guidelines](#neoskop-development-guidelines)
  - [Table of Contents](#table-of-contents)
  - [General Thoughts](#general-thoughts)
  - [Linting](#linting)
  - [Formatting](#formatting)
  - [Build Tools / Libraries](#build-tools--libraries)
  - [Testing](#testing)
  - [Deployment](#deployment)
  - [Versioning](#versioning)
  - [Roadmap / TODO](#roadmap--todo)

## General Thoughts

- When writing code we …

  - focus on code that does what it is supposed to do.
  - value comprehensibility and ease of maintenance over writing "clever code".
  - do not focus on perfect code, but code that strikes the best balance of **value for our time**.

- This attitude may not be appropriate for open-source projects, but it is definitely appropriate for projects where cost and schedule are key factors.

## Linting

We make sure to always lint our code before committing stuff to a repository.

- **JavaScript**

  - We consider TypeScript, if possible ;)
  - We use [ESLint](https://eslint.org/) as the linting tool for JavaScript and JSX.
  - Our default configuration: [eslint.json](configs/eslint.json).

- **TypeScript**

  - We use [TSLint](https://palantir.github.io/tslint/) as the linting tool for TypeScript.
  - We use [codelyzer](https://github.com/mgechev/codelyzer) in our Angular projects.
  - Our default configuration: [tslint.json](configs/tslint.json)

- **CSS**
  - We use [stylelint](https://stylelint.io/) as the linting tool for our stylesheets.
  - Our default configuration: tbd.

**[⬆ back to top](#table-of-contents)**

## Formatting

Automatic formatting of code makes it easier for other developers to navigate our code.
We make sure our code gets formatted before committing changes to a repository.

- **JavaScript / TypeScript**

  - We use [Prettier](https://prettier.io/) to format our JavaScript/TypeScript code.
  - Our default configuration: [.prettierrc](configs/.prettierrc)
  - **Do** use the `--single-quote` option.
  - You **may** overwrite the `--print-width <int>` option.
  - **Do not** overwrite other options.

- **Java**

  - We use [google-java-format](https://github.com/google/google-java-format) to format our
    Java code.

- **HTML**

  - For now, we don't use a formatter for HTML.
  - Feel free to evaluate possible options.

- **CSS**
  - see [1.3 Linting CSS](#linting--css)

**[⬆ back to top](#table-of-contents)**

## Build Tools / Libraries

- **JavaScript / TypeScript**

  - We prefer [Yarn](https://yarnpkg.com/en/) as our package manager, due to its speed and "workspaces" feature used in our mono repos.
  - We use [Webpack](https://webpack.js.org/) as our code bundler.
  - For more advanced build steps we use **NPM scripts**. You may consider [Jake](http://jakejs.com/) for _really_ complex build steps.
  - We use **npm audit** to monitor our dependencies for vulnerabilities in projects using NPM >= 6. Otherwise we use [Snyk](https://snyk.io/).

- **Angular**

  - We use the [Angular CLI](https://cli.angular.io/) to bootstrap new projects.
  - You may eject the project, if you need to customize the Webpack configuration.
  - Consider [nrwl/nx](https://github.com/nrwl/nx) for large scale applications.

- **React**

  - We use [create-react-app](https://github.com/facebook/create-react-app) to bootstrap new projects.
  - You may eject the project, if you need to customize the Webpack configuration.
  - [Next.js](https://github.com/zeit/next.js/) is our go-to-library for static site generation with React.

- **Styles**

  - We use [PostCSS](http://postcss.org/) for CSS transformations.
  - We use [postcss-preset-env](https://preset-env.cssdb.org/) or [LibSass](https://sass-lang.com/libsass) for advanced css features.
  - Consider using [styled-components](https://github.com/styled-components/styled-components) for React
    component styles.

**[⬆ back to top](#table-of-contents)**

## Testing

- Whichever testing framework you use, you should be writing tests.
- Strive for a good amount of test coverage.
- Fixed a bug? Write a regression test to prevent it from breaking again.
- We use [Testcafe](https://devexpress.github.io/testcafe/) for our E2E tests.

**[⬆ back to top](#table-of-contents)**

## Deployment

- We use [Docker](https://www.docker.com) to build and ship our applications.
- We use [Buddy](https://app.buddy.works/) to manage our deployment pipelines. Integrate your tests with Buddy whenever possible to prevent corrupt deployments.

**[⬆ back to top](#table-of-contents)**

## Versioning

- Always have a .gitignore.
- **Do not** commit sensitive data.
- We use Karma's best practices for [semantic commit messages](http://karma-runner.github.io/2.0/dev/git-commit-msg.html). It makes scanning the log easier and allows for an easier generation of changelogs.
- You may write commit messages in **German or English**, just be consistent throughout your projects.
- Feel free to evaluate tools for optimized Git workflows, e.g. [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/).

**[⬆ back to top](#table-of-contents)**

## Roadmap / TODO

- optimize default configurations
- add examples for tool integration (IDEs, Plugins, Commit Hooks, ...)
