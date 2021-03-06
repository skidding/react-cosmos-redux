# react-cosmos-redux

[![Build](https://travis-ci.com/skidding/react-cosmos-redux.svg?branch=master)](https://travis-ci.com/skidding/react-cosmos-redux) [![Coverage](https://codecov.io/gh/skidding/react-cosmos-redux/branch/master/graph/badge.svg)](https://codecov.io/gh/skidding/react-cosmos-redux)

## Usage

Add `react-cosmos-redux` to your project's dev deps.

```jsx
import { ReduxMock } from 'react-cosmos-redux';

export default (
  <ReduxMock
    configureStore={state => createStore(reducer, state)}
    initialState={myMockedReduxState}
  >
    <MyConnectedComponent />
  </ReduxMock>
);
```

> Passing `initialState` is optional. You can also use the Redux mock to provide the Redux context with the initial state generated by your reducers.

You'll likely want to avoid passing `configureStore` in every fixture. Creating a thin wrapper will help you keep your fixtures clean.

```jsx
// Put this somewhere central (chances are you'll have some utils thingie)
const MyReduxMock = ({ children, initialState }) => (
  <ReduxMock configureStore={configureStore} initialState={initialState}>
    {children}
  </ReduxMock>
);

// Put this in fixtures for Redux-connected components
export default (
  <MyReduxMock initialState={myMockedReduxState}>
    <MyConnectedComponent />
  </MyReduxMock>
);
```
