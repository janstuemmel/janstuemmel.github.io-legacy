This article will be a part of a series of my experiences how to build, test, release and deploy software in general with modern tools and services like github, gitlab, npm, react etc. This part is focused on **testing**.

## Start a rocket

During this process we will build a simple notification component for react applications, test it and release it on npm, i will explane the setup and guide you through integration and unit tests. I will not use the *jest* testing framework, i think it isn't yet ready for proper integration tests on frontend modules.

Instead we're using some of these:

* **mocha**, a minimalistic testing framework
* **sinon**, as add-in for mocha
* **karma**, the automatic test-runner
* **karma-browserify**, browserifies our application for testing purposes
* **karma-test-container-support**, see what you get on your tests
* **gulp**, our taskrunner

So lets start with building our application structure:

```sh
npm init # and answer a few questions with whitespaces :)
touch .gitignore index.js karma.conf.js indexSpec.js
```

...then install a few dependencies (i lied, a lot!)

```sh
npm install --save react react-dom
npm install ...^C # fuck that, i bet you know how to install node modules
tail -n 31 package.json
  "devDependencies": {
    "babel-preset-es2015": "^6.16.0",
    "babel-preset-react": "^6.16.0",
    "babelify": "^7.3.0",
    "browserify": "^13.1.0",
    "chai": "^3.5.0",
    "gulp": "^3.9.1",
    "gulp-notify": "^2.2.0",
    "gulp-sourcemaps": "^1.6.0",
    "gulp-uglify": "^2.0.0",
    "gulp-util": "^3.0.7",
    "karma": "^1.3.0",
    "karma-browserify": "^5.1.0",
    "karma-chai": "^0.1.0",
    "karma-mocha": "^1.2.0",
    "karma-mocha-reporter": "^2.2.0",
    "karma-phantomjs-launcher": "^1.0.2",
    "karma-sinon-chai": "^1.2.4",
    "mocha": "^3.1.2",
    "phantomjs-prebuilt": "^2.1.13",
    "sinon": "^1.17.6",
    "sinon-chai": "^2.8.0",
    "vinyl-buffer": "^1.0.0",
    "vinyl-source-stream": "^1.1.0",
    "watchify": "^3.7.0"
  },
  "dependencies": {
    "react": "^15.3.2",
    "react-dom": "^15.3.2"
  }
}
```

Ok i must admit that its a bit more then just `jest` as a dev dependency, but you will see the benefits of using karma with launchers and the test container.
