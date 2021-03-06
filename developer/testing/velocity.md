# Velocity
We're using the Meteor testing framework [Velocity](https://github.com/meteor-velocity/velocity). Velocity allows us to use different testing approaches as needed.  Currently we're using [Jasmine](https://github.com/Sanjo/meteor-jasmine) for the majority of tests.

Running tests in continuous integration mode:

```
VELOCITY_TEST_PACKAGES=1 meteor test-packages --driver-package velocity:html-reporter --velocity
```

Testing individual packages:

```
VELOCITY_TEST_PACKAGES=1 meteor test-packages --driver-package velocity:html-reporter package-to-test
```

As such, our testing falls into two locations:

## End to End
   Located in the `reaction/tests/jasmine/client/integration` folder, these tests cover UIX testing. These are relatively fragile tests as they are only testing core theme and UIX.

## Integration
   Tests for the individual reaction packages, are respectively located in `/tests/jasmine/server/integration`. Each package should have tests that cover their own functionality. These tests only cover UIX testing.

   These tests are run independently from the end to end tests, and can be run from the command line:

   `VELOCITY_TEST_PACKAGES=1 meteor test-packages --driver-package velocity:html-reporter package-to-test`

   To continuously test changes to the `core` package while using Reaction End to End tests simultaneously on another port:

```
   VELOCITY_TEST_PACKAGES=1 meteor test-packages --port 3006 reactioncommerce:core
```

Some Velocity setup tips:
- Uncomment `sanjo:jasmine` and the other testing packages found in the `/.meteor/packages` file in the Reaction path to use the browser testing console.
- You can set your `NODE_ENV` environment variable to 'development' to open up ports that velocity uses. The easiest way to do this is to run `export NODE_ENV="development"` before you start `meteor`
- If you run `meteor --test` your tests will only run once and will not re-run when you update files.

We'd like for new features to include at least basic integration test-coverage. If you are unsure about how to do this just ask and, we can point you in the right direction.
- Feature branches can be merged and released when they are feature incomplete, but soon we're planning on enforcing a passing test written for every pull request.*

_Writing tests is a great way to get to know the codebase a little better too._
