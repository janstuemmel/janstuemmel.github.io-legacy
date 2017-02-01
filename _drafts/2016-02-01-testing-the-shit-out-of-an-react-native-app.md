There is a big hype about reacvt native since a while. Devolopers created a bunch of nice applications, tools and libraries. But when it comes to testing the shit out of an application, there are only a few good guides. This blog post is about a few testing strategies.

## Introduction

There are three important scopes of testing for me, first pure functional unit testing, just testing return values of function calls and ansync api endpoint callbacks. Secondly, we go a step backwards and try test from a more whole perspective, like trying to find out wich calls are made from a component mount for example. Third, integration tests, the application sourcecode is a blackbox and we want to proof what happens when we push a button on the frontend.

You should be already familiar with common javascript utilities, we will focus on...

* jest
* enzyme
* iOS UITest

## Our example application

```js
// app/app.js
import React, { Component } from 'react';
import { View, Text } from 'react-native';


class App extends Component {

  constructor(props) {
    super(props);
    this.state = { value: 0 };
  }

  render() {
    return (
      <View>
        <Card label="Butter" value={1}>
        <Card label="Coffee" value={2}>
        <Card label="Limonde" value={3}>
      </View>
    );
  }
}

export default App;

const Card = ({ label, value }) => {
  return (
    <View>
      <Text>this.props.label</Text>
      <Text>this.props.value</Text>
    </View>
  );
}

export card Card;
```
