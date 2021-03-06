---
id: getting-started
title: Getting Started
---

## Create a new app

Assuming that you have installed [create-react-app](https://github.com/facebook/create-react-app), you can run:

```console
create-react-app search-app
cd search-app
```

Then, install the library.

```console
npm install @inveniosoftware/react-searchkit
```

## Bootstrap it

Open the App component `src/App.js` file and add the main `react-searchkit` component.

First, import the main component `ReactSearchKit`.
```jsx
import { ReactSearchKit } from "react-searchkit";
```

Then, replace the content of `render()` to render [ReactSearchKit](components/react_search_kit.md). You should have something similar to:

```jsx
import React, { Component } from "react";
import { ReactSearchKit } from "react-searchkit";

class App extends Component {
  render() {
    return (
      <ReactSearchKit>
        <h1>My search UI</h1>
      </ReactSearchKit>
    );
  }
}

export default App;
```

## Plug backend API

Change the `ReactSearchKit` props to define the backend. For this example we are going to use [Zenodo APIs](https://zenodo.org).

```jsx
render() {
  return (
    <ReactSearchKit
      searchConfig={{
        url: 'https://zenodo.org/api/records/',
        timeout: 5000,
        headers: { Accept: 'application/vnd.zenodo.v1+json' },
      }}
    >
      <h1>My search UI</h1>
    </ReactSearchKit>
  );
}
```

> Note: by default, `React SearchKit` is compatible with an [Invenio](https://inveniosoftware.org) backend. To plug your backend, you can define your configuration or provide your own API implementation. See [ReactSearchKit](components/react_search_kit.md) API documentation for more details.

## Add the first component

Import the [SearchBar](components/search_bar.md) component.

```jsx
import { ReactSearchKit, SearchBar } from "react-searchkit";
```

Then, add the component as a child of `ReactSearchKit`.

```jsx
import React, { Component } from "react";
import { ReactSearchKit, SearchBar } from "react-searchkit";

class App extends Component {
  render() {
    return (
      <ReactSearchKit>
        <div style={{ margin: "2em auto", width: "50%" }}>
          <SearchBar />
        </div>
      </ReactSearchKit>
    );
  }
}

export default App;
```

The page should look like to this:

![Screenshot showing search bar component](assets/getting_started_search.png)

If you hit `Search`, you should see a network request happens with the search query string you have input.

## Display the results

Import the [ResultsList](components/results_list.md) component.

```jsx
import { ReactSearchKit, SearchBar, ResultsList } from "react-searchkit";
```

Then, add the component below the search bar.

```jsx
import React, { Component } from "react";
import { ReactSearchKit, SearchBar, ResultsList } from "react-searchkit";

class App extends Component {
  render() {
    return (
      <ReactSearchKit>
        <div style={{ margin: "2em auto", width: "50%" }}>
          <SearchBar />
          <ResultsList />
        </div>
      </ReactSearchKit>
    );
  }
}

export default App;
```

After reload, you should the list of results when you insert a query string and hit `Search`.

![Screenshot showing results list component](assets/getting_started_resultslist.png)
