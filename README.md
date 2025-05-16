# Workout Timer App

A React application that helps users calculate workout durations based on exercise type, sets, speed, and break lengths.

## Overview

This application allows users to:

- Select different workout types (with varying numbers of exercises)
- Adjust the number of sets
- Set their exercise pace (seconds per exercise)
- Configure break durations between sets
- Toggle sound notifications on/off

The app automatically calculates the total workout time based on these parameters, helping users plan their fitness routines effectively.

## React Performance Optimization

This project demonstrates the use of React's optimization features to prevent unnecessary re-renders:

### React.memo

The application uses `memo` from React to memoize components, preventing re-renders when props haven't changed:

1. **Calculator Component**: Wrapped with `memo` to prevent re-rendering when props remain the same:

```jsx
export default memo(Calculator);
```

2. **ToggleSounds Component**: Memoized to optimize rendering when the sound toggle state doesn't change:

```jsx
export default memo(ToggleSounds);
```

### useMemo Hook

The `useMemo` hook is used to memoize computed values, recalculating them only when dependencies change:

```jsx
const workouts = useMemo(
  () => [
    {
      name: 'Full-body workout',
      numExercises: partOfDay === 'AM' ? 9 : 8,
    },
    // other workout definitions...
  ],
  [partOfDay] // Only recalculate when partOfDay changes
);
```

This optimization ensures that the workout options are only recalculated when the time of day changes (AM/PM), preventing unnecessary recalculations during renders triggered by other state changes.

## Key Features

- Dynamic workout options that change based on time of day (AM/PM)
- Real-time workout duration calculation
- Configurable exercise parameters
- Sound toggle functionality
- Clean, user-friendly interface

## Running the Project

In the project directory, you can run:

### `npm start`

Runs the app in development mode at [http://localhost:3000](http://localhost:3000)

### `npm test`

Launches the test runner in interactive watch mode

### `npm run build`

Builds the app for production to the `build` folder

## Technologies Used

- React (with Hooks)
- CSS for styling
- JavaScript audio API for sound effects
