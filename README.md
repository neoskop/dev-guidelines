# Neoskop Development Guidelines

_A collection of guidelines, best practices and tools used in development at
[Neoskop](https://www.neoskop.de)._

> **Note**: This repository serves as a living document, representing essential guidelines concerning our development workflow.
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
  - [Documentation](#documentation)
  - [Checklist](#checklist)

## General Thoughts

- When writing code we …

  - focus on code that gets the job done.
  - value comprehensibility and ease of maintenance over writing "clever code".
  - do not focus on perfect code, but code that strikes the best balance of **value for our time**.

## Linting

We make sure to always lint our code before committing stuff to a repository. The sample
configuration files in this repository could be taken as a fair starting point. Many rules
are certainly a matter of taste, so feel free to adjust. Just make sure to include linting
files in your repositories, so other developers can use it when jumping in your code.

- **JavaScript**

  - We use [ESLint](https://eslint.org/) as the linting tool for JavaScript and JSX.
  - Here is a possible configuration: [eslint.json](configs/eslint.json)

- **TypeScript**

  - We use [ESLint](https://eslint.org/) as the linting tool for TypeScript and TSX.
  - We use [codelyzer](https://github.com/mgechev/codelyzer) in our Angular projects.
  - Here is a possible configuration: [eslint.json](configs/eslint.json)

- **CSS**
  - We use [stylelint](https://stylelint.io/) as the linting tool for our stylesheets.
  - Here is a possible configuration: [.stylelintrc.json](configs/.stylelintrc)

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
  - see [1.3 Linting CSS](#linting)

**[⬆ back to top](#table-of-contents)**

## Build Tools / Libraries

- **JavaScript / TypeScript**

  - We test which package manager is currently the best, [Yarn](https://yarnpkg.com/en/) or [Npm](https://npmjs.com/), we found out that yarn is slower and npm now also enables "workspaces" used in our mono repos.
  - We only use exact version numbers in our **package.json** (no ~ or ^) use `npm config set save-prefix ' '`
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
  - We are currently evaluating [Gatsby](https://github.com/gatsbyjs/gatsby) as our go-to-library for static site generation with React.

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

- We use [Docker](https://www.docker.com) to build and ship our applications and deploy our applications to [Kubernetes](https://www.kubernetes.io).
  - We deliver a **Dockerfile** as well as a **docker-compose.yml** file for multi-container applications that is ready for use in development.
  - We commit the Kubernetes manifests we use to the same repository as the application's code.
  - To ensure that our applications keep running and don't impact others in the same cluster, our manifests include [Readiness and Liveness probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) as well as [Resource requests and limits](https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/)
  - We realize that containerizing an application is no silver bullet against security threats and thus use the [CIS Docker CE Benchmark v1.1.0](https://www.cisecurity.org/benchmark/docker/) / [Docker Bench for Security](https://github.com/docker/docker-bench-security) to audit our images and containers
- We use [Buddy](https://app.buddy.works/) for continuous integration and continuous delivery. Integrate your tests with Buddy whenever possible to prevent corrupt deployments.

**[⬆ back to top](#table-of-contents)**

## Versioning

- Always have a .gitignore.
- **Do not** commit sensitive data.
- We use Karma's best practices for [semantic commit messages](http://karma-runner.github.io/2.0/dev/git-commit-msg.html). It makes scanning the log easier and allows for an easier generation of changelogs.
- You may write commit messages in **German or English**, just be consistent throughout your projects.
- Feel free to evaluate tools for optimized Git workflows, e.g. [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/).

**[⬆ back to top](#table-of-contents)**

## Documentation

- We write README files for all our projects.
- Every developer should be able to run the application following the instructions in the README file.
- Stick to easy step by step instructions and do not make assumptions about the user's foreknowledge.

**[⬆ back to top](#table-of-contents)**

## Checklist

- **Linting**
  - [ ] Are linting configuration files available and under version control?
    - [ ] JavaScript: eslint.json
    - [ ] TypeScript: tslint.json
    - [ ] Stylesheets: .stylelintrc
  - [ ] Is linting configured with your IDE?
- **Formatting**
  - [ ] Is a Prettier configuration file available and under version control?
  - [ ] Is Prettier configured with your IDE?
- **Build Tools / Libraries**
  - [ ] Are you using Yarn as the package manager?
    - [ ] Is the yarn.lock file under version control?
    - [ ] Are dependencies defined using exact version numbers (no ^ or ~ in version numbers)?
  - [ ] Are you using Webpack for bundling?
  - [ ] Are you using PostCSS with postcss-preset-env or LibSass for CSS transformations?
- [ ] **Testing**
  - [ ] Did you configure automatic unit and e2e test suites?
- [ ] **Deployment**
  - [ ] Are there working Docker files to run the application on server and locally?
  - [ ] Do the sources include recent and valid Kubernetes manifests to re-deploy the application from scratch?
  - [ ] Are Buddy build and deployment tasks available?
  - [ ] Have tests been integrated with Buddy?
- [ ] **Versioning**
  - [ ] Is there a .gitignore excluding all neccessary files?
  - [ ] Did you make sure NOT to commit sensitive data?
  - [ ] Did you enforce semantic commit messages through commit hooks or the like?
- [ ] **Documentation**
  - [ ] Did you write a README.md containing step by step instructions to run the application?

**[⬆ back to top](#table-of-contents)**
