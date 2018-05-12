---
layout: post
title:  "Configuring GitLab CI to run Angular5 e2e Tests"
date:   2018-05-11 19:37:56 +1100
categories: article
title-image: HTML_5.png
---

Recently I had the responsibility of setting up testing for an existing Angular5 project using Protractor, Jasmine and Kama. The project had existing unit tests, but no End to End (e2e) tests.

To configure Kama we need to add PhantomJS and the PhantomJS launcher, adjust `karma.conf.js` and enable the es6 polyfills in `src/polyfills.ts`.

For e2e testing we need to configure protractor to run the tests in a headless browser in `protractor.conf.js`. Then we can make a few small changes to a standard `.gitlab-ci.yml` and we are ready to run `ng e2e` tests in GitLab CI.

## Les get started

To start our project we run:

```
ng new GitLab-Angular-e2e-CI
cd GitLab-Angular-e2e-CI/
```

now running the tests we find that Karma and Protractor both launch chrome browsers to run the tests.

```
ng test --single-run
ng e2e
```

## Karma Configuration

Lets install the dependencies and plugins to let Karma run without a browser window:

#### package.json
```
 "devDependencies": {
    ...
    "karma-phantomjs-launcher": "^1.0.4",
    "phantomjs-prebuilt": "^2.1.16",
    ...
```

#### karma.conf.js
```
    plugins: [
      ...
      require('karma-phantomjs-launcher'),
    ...
    browsers: ['Chrome', 'PhantomJS'],
```


#### src/polyfills.ts
```
import 'core-js/es6/symbol';
import 'core-js/es6/object';
import 'core-js/es6/function';
import 'core-js/es6/parse-int';
import 'core-js/es6/parse-float';
import 'core-js/es6/number';
import 'core-js/es6/math';
import 'core-js/es6/string';
import 'core-js/es6/date';
import 'core-js/es6/array';
import 'core-js/es6/regexp';
import 'core-js/es6/map';
import 'core-js/es6/weak-map';
import 'core-js/es6/set';
```



After updating npm our unit tests are ready for CI and can run headless with the command:
```
npm install
ng test --single-run --browser PhantomJS
```


Now we'll' enable Protractor to do the same:

## Protractor Configuration

Modify the protractor capabilities to target a headless chrome browser. This has the added benefit of running without popping up a browser when running `ng e2e` locally during development.

#### protractor.conf.js
```
  capabilities: {
    browserName: 'chrome',
    chromeOptions: {
       args: ["--no-sandbox", "--headless", "--disable-gpu", "--window-size=800,600" ]
     }
  },
```


## GitLab CI Configuration

Add the test_e2e_with_lab job to your CI pipeline to run in parallel with the regular `angular test` test suite. While the rest of the build and test process will happen on the **node:latest** docker image, the test_e2e_with_lab job will run on the **trion/ng-cli-e2e** image as it was the docker image with the most pre-installed dependencies for the basic e2e setup with a global install of protractor required to push it over the edge (despite protractor already being in the projects dev dependencies).

#### .gitlab-ci.yml
```
variables:
  DEPENDENCY_PATH: "./node_modules"
  NG_CLI_PATH: "./node_modules/@angular/cli/bin/ng"

image: node:latest

cache:
  paths:
    - node_modules/

stages:
  - install_dependencies
  - test

install_dependencies:
  stage: install_dependencies
  script:
    - npm install --quiet

  artifacts:
    paths:
      - $DEPENDENCY_PATH

test_with_lab:
  stage: test
  script: $NG_CLI_PATH test --browser PhantomJS --single-run --progress=false

test_e2e_with_lab:
  image: trion/ng-cli-e2e
  stage: test
  script:
    - npm rebuild node-sass --force
    - npm install -g protractor
    - $NG_CLI_PATH e2e --progress=false
```

## Job Done!

Now your project should be running `ng test` and `ng e2e` test suites on every push to master and on every branch pushed for review.

You can checkout a minimal example at [GitLab-Angular-e2e-CI](https://gitlab.com/puzzleduck/GitLab-Angular-e2e-CI)

Next time we'll look at adding coverage reporting and vulnerability code analysis.
