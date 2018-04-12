# Neoskop Development Guidelines

*A collection of guidelines, best practices and tools used in development at 
[Neoskop](https://www.neoskop.de).*

> **Note**: This repository serves as a living document, representing our development workflow.
  *Please use pull requests to keep this document up to date and challenge outdated or obsolete 
  contents whenever you see fit.*

## Table of Contents

  1. [Linting](#linting)
  1. [Formatting](#formatting)
  1. [Build Tools / Infrastructure](#build-tools)
  1. [Testing](#testing)
  1. [Deployment](#deployment)
  1. [Versioning](#versioning)

## Linting

  Make sure to always lint your code before committing stuff to a repository.

  - **JavaScript**
    
    - Use [ESLint](https://eslint.org/) as the linting tool for JavaScript and JSX.
    - Our default configuration can be found here: tbd.
  
  - **TypeScript**
    
    - Use [TSLint](https://palantir.github.io/tslint/) as the linting tool for TypeScript.
    - Use [codelyzer](https://github.com/mgechev/codelyzer) in your Angular projects.
    - Our default configuration: [tslint.json](configs/tslint.json)
    
  - **CSS**
      
      - Use [stylelint](https://stylelint.io/) as the linting tool for your stylesheets.
      - Our default configuration can be found here: tbd.
      
**[⬆ back to top](#table-of-contents)** 
    
## Formatting

  Automatic formatting of your code makes it easier for other developers to navigate your code.
  Make sure your code gets formatted before committing changes to a repository.

  - **JavaScript / TypeScript**
  
    - Use [Prettier](https://prettier.io/) to format your JavaScript/TypeScript code.
    - Our default configuration: [.prettierrc](configs/.editorconfig)
    - **Do** use the `--single-quote` option.
    - You **may** overwrite the `--print-width <int>` option.
    - **Do not** overwrite other options.
    
  - **Java**
        
    - Use [google-java-format](https://github.com/google/google-java-format) to format your 
    Java code.
    
  - **HTML**
    - For now, we don't use a formatter for HTML.
    - Feel free to evaluate possible options.
    
  - **CSS**
    - see [1.3 Linting CSS](#linting--css)

**[⬆ back to top](#table-of-contents)**

## Build Tools / Infrastructure
    
  - **JavaScript / TypeScript (Frontend)**
  
    - We prefer [Yarn](https://yarnpkg.com/en/) as our package manager, due to its speed and "workspaces" feature used 
    in our mono repos.
    - We use [Webpack](https://webpack.js.org/) as our code bundler.
    - For more advances build steps that are not easily achieved with Webpack, we use **NPM scripts**. You may consider
    [Jake](http://jakejs.com/) for *really* complex build steps.
    - Use [Snyk](https://snyk.io/) to monitor your dependencies for vulnerabilities.
    
  - **Angular**
  
    - Use the [Angular CLI](https://cli.angular.io/) to bootstrap new projects.
    - You may eject the project, if you need to customize the Webpack configuration.
    - Consider [nrwl/nx](https://github.com/nrwl/nx) for large scale applications.
    
  - **React**
  
    - Use [create-react-app](https://github.com/facebook/create-react-app) to bootstrap new projects.
    - You may eject the project, if you need to customize the Webpack configuration.
    
  - **Styles**
    - We use [PostCSS](http://postcss.org/) for CSS transformations.
    - Use [cssnext](http://cssnext.io/) or [LibSass](https://sass-lang.com/libsass) for advanced css features.
    - Consider using [styled-components](https://github.com/styled-components/styled-components) for your React
    component styles.
    
**[⬆ back to top](#table-of-contents)**

## Testing

  - Whichever testing framework you use, you should be writing tests.
  - Strive for a good amount of test coverage.
  - Fixed a bug? Write a regression test to prevent it from breaking again.
  - Use [Testcafe](https://devexpress.github.io/testcafe/) for your E2E tests.

**[⬆ back to top](#table-of-contents)**

## Deployment

  - tbd.

**[⬆ back to top](#table-of-contents)**

## Versioning

  - tbd.

**[⬆ back to top](#table-of-contents)**

## Todos

  - add default configurations
  - add examples for integrating tools in workflow (IDEs, commit hooks, ...)