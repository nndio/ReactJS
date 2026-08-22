# Redux Toolkit Theme Switcher

A React application built with **Redux Toolkit** and **Vite** as a practical exercise for learning global state management.

The project extends the Redux Toolkit Vite template by adding a dedicated **theme slice** that manages the application's light and dark themes.

## Features

* Global state management with Redux Toolkit
* Light / dark theme switching
* Dedicated `themeSlice`
* `toggleTheme` Redux action
* `selectTheme` selector
* Typed Redux hooks with `useAppDispatch` and `useAppSelector`
* Redux store configured with `combineSlices`
* Existing counter functionality
* Asynchronous quote fetching with Redux Toolkit Query
* Responsive theme changes using inline styles
* Production build with Vite

## Technologies

* React
* TypeScript
* Redux Toolkit
* React Redux
* Redux Toolkit Query
* Vite
* ESLint

## Project Structure

```text
src/
├── app/
│   ├── createAppSlice.ts
│   ├── hooks.ts
│   └── store.ts
│
├── features/
│   ├── counter/
│   │   ├── Counter.tsx
│   │   └── counterSlice.ts
│   │
│   ├── quotes/
│   │   ├── Quotes.tsx
│   │   └── quotesApiSlice.ts
│   │
│   └── theme/
│       └── themeSlice.ts
│
├── App.css
├── App.tsx
├── index.css
├── main.tsx
└── ...
```

## Theme State

The theme is managed through a dedicated Redux Toolkit slice:

```ts
type Theme = "light" | "dark"
```

The initial state is:

```ts
const initialState: ThemeState = {
  theme: "light",
}
```

The `toggleTheme` action switches between the two available themes:

```ts
toggleTheme: state => {
  state.theme = state.theme === "light" ? "dark" : "light"
}
```

The current theme is accessed through the `selectTheme` selector.

## Redux Store

The theme slice is registered in the Redux store together with the existing counter and quotes API slices:

```ts
const rootReducer = combineSlices(
  counterSlice,
  quotesApiSlice,
  themeSlice,
)
```

This allows the theme state to be accessed globally throughout the application.

## Typed Redux Hooks

The project uses pre-typed Redux hooks provided by the Redux Toolkit template:

```ts
const dispatch = useAppDispatch()
const theme = useAppSelector(selectTheme)
```

This provides type safety when dispatching actions and accessing the Redux state.

## Theme Switching

The application contains a button that dispatches the `toggleTheme` action:

```tsx
<button
  type="button"
  onClick={() => dispatch(toggleTheme())}
>
  {isDarkTheme ? "☀️ Light theme" : "🌙 Dark theme"}
</button>
```

The application's background and text colors are updated according to the current theme.

## Getting Started

### Clone the repository

```bash
git clone <repository-url>
cd my-app
```

### Install dependencies

```bash
npm install
```

### Start the development server

```bash
npm run dev
```

The application will be available at:

```text
http://localhost:5173/
```

## Production Build

To create a production build:

```bash
npm run build
```

The project successfully builds with TypeScript and Vite.

## Learning Objectives

This project was created to practice:

* Redux Toolkit fundamentals
* Creating and configuring Redux slices
* Managing global application state
* Creating Redux actions and selectors
* Connecting slices to the Redux store
* Using `useAppDispatch` and `useAppSelector`
* Working with `combineSlices`
* Understanding the basic architecture of Redux Toolkit applications
* Using Redux Toolkit Query for asynchronous data fetching

## Assignment Requirements

The implementation satisfies the following requirements:

* [x] Create a Slice for theme management
* [x] Connect the Slice to the Redux store
* [x] Create an action for changing the theme
* [x] Create a selector for accessing the theme
* [x] Add a button for switching the application theme
* [x] Change the application background color according to the selected theme

## License

This project was created for educational and portfolio purposes.
