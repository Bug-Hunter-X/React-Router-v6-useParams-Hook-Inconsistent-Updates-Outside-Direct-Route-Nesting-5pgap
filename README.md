# React Router v6 useParams Hook Inconsistent Updates Outside Direct Route Nesting

This repository demonstrates a subtle bug in React Router v6 where the `useParams` hook doesn't reliably update when used in a component not directly nested within a route's path. This leads to stale parameter values after navigation.

## Bug Description

When `useParams` is used within a component that's indirectly nested or not directly under a route, the parameter values might not update consistently after a route change.  This can result in incorrect data display or application behavior.

## Reproduction

1. Clone this repository.
2. Run `npm install`.
3. Run `npm start`.
4. Observe that navigating between routes does not always update the values displayed from `useParams` within the `MyComponent` component.

## Solution

The solution involves ensuring that the component using `useParams` is either directly nested within the relevant route's component, or to lift state up to the nearest parent component which is correctly placed within the relevant route's component.  This ensures the `useParams` hook always receives and utilizes the correct context.

See `bugSolution.js` for a corrected implementation.