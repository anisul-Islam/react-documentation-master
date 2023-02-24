# React Documentation

- prerequisities: HTML, CSS, Javascript
- React.js official Site: https://reactjs.org/

## Part-1 (Introduction to React)

## [1. Introduction to React](https://youtu.be/fRXL0X2WSK4)

### 1.1 What is React?

- React is a flexible, efficent Open Source UI Based JavaScript Library.
- It is developed by Facebook in 2013 for building user interface.

### 1.2 Why React?

- It helps us to create reusable components (small and isloated pieces of code using html, css, js). It helps us to render UI. Think about youtube's website.
- Single Page Application (SPA) allows us to render as much as we need for reducing unnecessary rendering such as loading navbar, footer etc. in all the pages
- think about html tag and creating your own tag with react
- Load fast - Why React.js is faster? - virtual DOM compares with previous states
- Allows us to use external plugin
- Example of React app - facebook, twitter, airbnb, netflix
- competitor - Vue.js, Angular (more full-fledged / developed no need 3rd party library just like react-router-dom)

## [2. Environment setup](https://youtu.be/4wjI8fh77GM)

- VSCode
- node.js (Download LTS: Long Term Support one)
  (npm is included in node.js by default)
- React Developer tools extention for google, firefox, edge
- Extension: ES7 react, JS JSX snippets + “editior.snipperSuggestions”: “top”, react developer tools, material theme, setup eslint and prettier

## [3. First react app](https://youtu.be/2Ec3h0z51aI)

### 3.1 Method 1: add React to a website with CDN

- **Code Example - 1 (create React app)**

  ```html
  <!-- without JSX -->
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Document</title>
      <script
        crossorigin
        src="https://unpkg.com/react@18/umd/react.development.js"
      ></script>
      <script
        crossorigin
        src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"
      ></script>

      <style>
        .title {
          background-color: brown;
          color: white;
          text-align: center;
        }
      </style>
    </head>
    <body>
      <div id="root"></div>

      <script>
        const headingElement = React.createElement(
          "h1",
          { id: "heading", className: "title" },
          "Welcome to React"
        );
        const root = ReactDOM.createRoot(document.getElementById("root"));
        root.render(headingElement);
      </script>
    </body>
  </html>
  ```

- **Code Example - 2 (create React app)**

  ```html
  <!-- With JSX -->
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Document</title>

      <!-- adding React  -->
      <script
        crossorigin
        src="https://unpkg.com/react@18/umd/react.development.js"
      ></script>

      <!-- adding ReactDOM  -->
      <script
        crossorigin
        src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"
      ></script>

      <!-- add the babel and allow jsx  -->
      <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>

      <style>
        .title {
          background-color: brown;
          color: white;
          text-align: center;
        }
      </style>
    </head>
    <body>
      <div id="root"></div>

      <script type="text/babel">
        const root = ReactDOM.createRoot(document.getElementById("root"));
        root.render(
          <h1 id="heading" className="title">
            Welcome to React
          </h1>
        );
      </script>
    </body>
  </html>
  ```

### 3.2 Method 2: create and run react app with npx

```js
// create react app command
npx create-react-app appName

// run react app command
cd appName
npm start
```

- show how to run and stop the react app

### 3.3 understand File structure

- discuss about package.json, node_modules, public, src
- [package-lock.json](https://medium.com/helpshift-engineering/package-lock-json-the-complete-guide-2ae40175ebdd#:~:text=different%20machines%2Fenvironments.-,package%2Dlock.,json%20file.) is for version control for packages. it keeps the record of node_modules tree so that when you clone and use npm i it will install exactly same versions for the packages even though their is a new versions. if you do not have package-lock.json then it will install from package.json
- keep only the index.js in src and then play with React.js
- change the title of the app inside index.html file

## Part-2 (JSX, Component, react component under the hood, Styling, Props, PropTypes, Conditional rendering, Fragment, react dev-tools, icons)

## [4. JSX and JS Expression](https://youtu.be/6-r6pBA4eUY)

- **JSX: stands for JavsScript XML which allows us to use write html-like syntax inside javascript and vice versa**
- react module has babbel inside of it that helps us to run jsx
- JSX is similar like HTML but it is more dynamic.
- JSX and React are independent things and they can be used independently.
- Rules for JSX

  - 1. We can return single element using JSX, for multiple elements we can use a wrapper. We can also use Fragment here.

    - why we can not return multiple elements in JSX needs to be rendered?
      - jsx is javascript object and we can return 2 objetcs from a function so we need to use array syntax and wrap everything inside one array
    - **Code Example - 3 (render single element)**

      ```js
      import React from "react";
      import ReactDOM from "react-dom/client";

      const root = ReactDOM.createRoot(document.getElementById("root"));
      root.render(<h2>Anis Ecommerce website</h2>);
      ```

    - **React render function can render only one element**
    - **Code Example - 4 (Rendering multiple elements)**

      ```js
      import React from "react";
      import ReactDOM from "react-dom/client";

      const root = ReactDOM.createRoot(document.getElementById("root"));

      root.render(
         <div>
          <header><h2>Anis Express</h2></header>
          <main>
          <aside>this is sidebar</aside>
            <section>
                <article>
                  <img
                    src="https://i.dummyjson.com/data/products/1/thumbnail.jpg"
                    alt="iPhone 9"
                  />
                  <h2>iPhone 9</h2>
                  <p>description: An apple mobile which is nothing like apple</p>
                  <p>Price: $549</p>
                  <p>rating: 4.69</p>
                  <p>brand: Apple</p>
                  <p>category: smartphones</p>
                  );
                <article>

                <article>
                  <img
                    src="https://i.dummyjson.com/data/products/2/thumbnail.jpg"
                    alt="iPhone X"
                  />
                  <h2>iPhone X</h2>
                  <p>description: SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...</p>
                  <p>Price: $899</p>
                  <p>rating: 4.44</p>
                  <p>brand: Apple</p>
                  <p>category: smartphones</p>
                  );
                <article>
            </section>
          </main>
          <footer>this is a footer</footer>
      </div>

      ```

      - React.Fragment or <> </> helps us to avoid div soup or unncessary div nesting
      - **Code Example - 5 (Fragment)**

        ```js
        <>
          <img
            src="https://i.dummyjson.com/data/products/1/thumbnail.jpg"
            alt="iPhone 9"
          />
          <h2>iPhone 9</h2>
          <p>description: An apple mobile which is nothing like apple",</p>
          <p>Price: $549</p>
          <p>rating: 4.69</p>
          <p>category: smartphones</p>
          );
        <>
        ```

  - 2. Remember to close all tags - `<img />`
  - 3. Camelcase - className

- We can use Javascript expression inside JSX
- **Code Example - 6 (JS Expression in JSX)**

  ```js
  import React from "react";
  import ReactDOM from "react-dom/client";

  const imageSource1 = "https://i.dummyjson.com/data/products/1/thumbnail.jpg";
  const title1 = "iPhone 9";
  const description1 = "An apple mobile which is nothing like apple";
  const price1 = 549;
  const rating1 = 4.69;
  const brand1 = "Apple";
  const category1 = "smartphones";

  const imageSource2 = "https://i.dummyjson.com/data/products/2/thumbnail.jpg";
  const title2 = "iPhone X";
  const description2 =
    "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...";
  const price2 = 899;
  const rating2 = 4.44;
  const brand2 = "Apple";
  const category2 = "smartphones";

  const root = ReactDOM.createRoot(document.getElementById("root"));

  root.render(
    <div>
      <header>
        <h2>Anis Express</h2>
      </header>

      <main>
        <aside>this is sidebar</aside>
        <section>
          <article>
            <img src={imageSource1} alt="iPhone 9" />
            <h2>{title1}</h2>
            <p>description: {description1}</p>
            <p>Price: {price1}</p>
            <p>rating: {rating1}</p>
            <p>brand: {brand1}</p>
            <p>category: {category1}</p>
          </article>
          <article>
            <img src={imageSource2} alt="iPhone 9" />
            <h2>{title2}</h2>
            <p>description: {description2}</p>
            <p>Price: {price2}</p>
            <p>rating: {rating2}</p>
            <p>brand: {brand2}</p>
            <p>category: {category2}</p>
          </article>
        </section>
      </main>
      <footer>this is a footer</footer>
    </div>
  );
  ```

## [5. How React works under the hood](https://youtu.be/kj0cxv_dC9M)

- **Code Example - 7 (React under the hood)**

```javascript
const Message = () => {
  // return <h3>Message </h3>;
  return React.createElement("h1", {}, "welcome");
};

const Todo = () => {
  return (
    // <article>
    //   <h2>Check students attendance</h2>
    //   <p>
    //     Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab, molestiae.
    //   </p>
    // </article>

    React.createElement(
      "article",
      {},
      React.createElement("h2", {}, "Check students attendance"),
      React.createElement(
        "p",
        {},
        " Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab, molestiae."
      )
    )
  );
};
```

## [6. Component](https://youtu.be/qgLZSNppJOU)

- **Component: A _reusable_, _nestable_ _building block_ constrcut with mainly Javascript function and HTML; CSS can be added**
- Component VS Function: Component should always start with capital letter and return JSX
- There are 2 main types of components: functional component and class component
- keep a blank line when importing your components for separting built in modules
- **Code Example - 8 (Create a reusable functional component)**

  ```javascript
  // reusable component
  import React from "react";
  import ReactDOM from "react-dom/client";

  const Products = () => {
    const imageSource1 =
      "https://i.dummyjson.com/data/products/1/thumbnail.jpg";
    const title1 = "iPhone 9";
    const description1 = "An apple mobile which is nothing like apple";
    const price1 = 549;
    const rating1 = 4.6;
    const brand1 = "Apple";
    const category1 = "smartphones";

    const imageSource2 =
      "https://i.dummyjson.com/data/products/2/thumbnail.jpg";
    const title2 = "iPhone X";
    const description2 =
      "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...";
    const price2 = 899;
    const rating2 = 4.44;
    const brand2 = "Apple";
    const category2 = "smartphones";

    return (
      <section>
        <article>
          <img src={imageSource1} alt="iPhone 9" />
          <h2>{title1}</h2>
          <p>description: {description1}</p>
          <p>Price: {price1}</p>
          <p>rating: {rating1}</p>
          <p>brand: {brand1}</p>
          <p>category: {category1}</p>
        </article>
        <article>
          <img src={imageSource2} alt="iPhone X" />
          <h2>{title2}</h2>
          <p>description: {description2}</p>
          <p>Price: {price2}</p>
          <p>rating: {rating2}</p>
          <p>brand: {brand2}</p>
          <p>category: {category2}</p>
        </article>
      </section>
    );
  };

  const root = ReactDOM.createRoot(document.getElementById("root"));
  root.render(
    <div>
      <header>
        <h2>Anis Express</h2>
      </header>
      <main>
        <aside>this is sidebar</aside>
        <Products />
        <Products />
      </main>
      <footer>this is a footer</footer>
    </div>
  );
  ```

- **Code Example - 9 (create Header, Sidebar, Footer component)**

  ```js
  const Header = () => {
    return (
      <header>
        <h2>Anis Express</h2>
      </header>
    );
  };
  const Sidebar = () => {
    return <aside>this is sidebar</aside>;
  };
  const Footer = () => {
    return <footer>this is a footer</footer>;
  };
  ```

- **Code Example - 10 (App root component, Nested components)**

```js
import React from "react";
import ReactDOM from "react-dom/client";

const Products = () => {
  const imageSource1 = "https://i.dummyjson.com/data/products/1/thumbnail.jpg";
  const title1 = "iPhone 9";
  const description1 = "An apple mobile which is nothing like apple";
  const price1 = 549;
  const rating1 = 4.6;
  const brand1 = "Apple";
  const category1 = "smartphones";

  const imageSource2 = "https://i.dummyjson.com/data/products/2/thumbnail.jpg";
  const title2 = "iPhone X";
  const description2 =
    "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...";
  const price2 = 899;
  const rating2 = 4.44;
  const brand2 = "Apple";
  const category2 = "smartphones";

  return (
    <section>
      <article>
        <img src={imageSource1} alt="iPhone 9" />
        <h2>{title1}</h2>
        <p>description: {description1}</p>
        <p>Price: {price1}</p>
        <p>rating: {rating1}</p>
        <p>brand: {brand1}</p>
        <p>category: {category1}</p>
      </article>
      <article>
        <img src={imageSource2} alt="iPhone X" />
        <h2>{title2}</h2>
        <p>description: {description2}</p>
        <p>Price: {price2}</p>
        <p>rating: {rating2}</p>
        <p>brand: {brand2}</p>
        <p>category: {category2}</p>
      </article>
    </section>
  );
};

const Header = () => {
  return (
    <header>
      <h2>Anis Express</h2>
    </header>
  );
};
const Sidebar = () => {
  return <aside>this is sidebar</aside>;
};
const Footer = () => {
  return <footer>this is a footer</footer>;
};

const App = () => {
  return (
    <div>
      <Header />
      <main>
        <Sidebar />
        <Products />
      </main>
      <Footer />
    </div>
  );
};

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

- **Code Example - 11 (export, import modular component)**

  - export default can be used once in a file where multiple exports can be used
  - importing export default does not require {} and you can name anything on the other hand only exports requires {} and naming is strict
  - export App component

  ```js
  // App.js

  import React from "react";
  import ReactDOM from "react-dom/client";

  const Products = () => {
    const imageSource1 =
      "https://i.dummyjson.com/data/products/1/thumbnail.jpg";
    const title1 = "iPhone 9";
    const description1 = "An apple mobile which is nothing like apple";
    const price1 = 549;
    const rating1 = 4.6;
    const brand1 = "Apple";
    const category1 = "smartphones";

    const imageSource2 =
      "https://i.dummyjson.com/data/products/2/thumbnail.jpg";
    const title2 = "iPhone X";
    const description2 =
      "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...";
    const price2 = 899;
    const rating2 = 4.44;
    const brand2 = "Apple";
    const category2 = "smartphones";

    return (
      <section>
        <article>
          <img src={imageSource1} alt="iPhone 9" />
          <h2>{title1}</h2>
          <p>description: {description1}</p>
          <p>Price: {price1}</p>
          <p>rating: {rating1}</p>
          <p>brand: {brand1}</p>
          <p>category: {category1}</p>
        </article>
        <article>
          <img src={imageSource2} alt="iPhone X" />
          <h2>{title2}</h2>
          <p>description: {description2}</p>
          <p>Price: {price2}</p>
          <p>rating: {rating2}</p>
          <p>brand: {brand2}</p>
          <p>category: {category2}</p>
        </article>
      </section>
    );
  };

  const Header = () => {
    return (
      <header>
        <h2>Anis Express</h2>
      </header>
    );
  };
  const Sidebar = () => {
    return <aside>this is sidebar</aside>;
  };
  const Footer = () => {
    return <footer>this is a footer</footer>;
  };
  const App = () => {
    return (
      <div>
        <Header />
        <main>
          <Sidebar />
          <Products />
        </main>
        <Footer />
      </div>
    );
  };

  export default App;

  // import in index.js
  import React from "react";
  import ReactDOM from "react-dom/client";
  import App from "./App";

  const root = ReactDOM.createRoot(document.getElementById("root"));
  root.render(<App />);
  ```

- More practice for export,import
  - **Code Example - 13 (More export, import)**
  - separate all the components

## [7. Adding CSS Styling part-1](https://youtu.be/02YWKDxLpwk)

- Inline styling
- CSS Stylesheet
- CSS module [why you should use css module]
- third party packages such as Material UI, styled components

- **Code Example - 14 (Styling component with CSS)**
- create and import App.css

  ```css
  /*code for the App.css */
  /* reset code and common starts here  */
  :root {
    --primary-color: rgb(11, 181, 48);
    --secondary-color: rgba(36, 122, 55, 0.9);
    --padding: 0.5rem;
    --transition: all 0.3s;
    --border-radius: 0.6rem;
    --box-shadow: 0.1rem 0.2rem 0.8rem rgba(205, 202, 202, 0.5);
  }
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    text-decoration: none;
    list-style-type: none;
    outline: none;
  }
  html {
    scroll-behavior: smooth;
  }
  .flex-space-around {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
  .flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  /* reset code and common ends here  */

  /* header starts here  */
  .header {
    height: 10vh;
    background-color: var(--primary-color);
    color: white;
  }
  /* header ends here  */

  /* main starts here  */
  main {
    height: 80vh;
  }
  .sidebar {
    flex: 1;
    padding: var(--padding);
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 1rem;
    align-self: flex-start;
    background-color: #e6e3e3;
    height: 100%;
    border-right: 1px solid var(--primary-color);
  }
  .main-content {
    flex: 3;
    height: 100%;
    padding: var(--padding);
    overflow: scroll;
  }
  .products {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 2rem;
    padding: 2rem 0;
  }
  .product__img {
    width: 100%;
    height: 15rem;
    filter: saturate(0);
    transition: var(--transition);
  }
  /* main ends here  */

  /* footer starts here  */
  .footer {
    min-height: 10vh;
    padding: var(--padding);
    background-color: var(--primary-color);
    color: white;
    font-size: 1.1rem;
  }
  /* footer ends here  */

  /* responsiveness starts here  */
  @media (max-width: 992px) {
    .flex-space-around,
    .flex-center {
      flex-direction: column;
      gap: 1rem;
      padding: 1rem 0;
    }
    .header {
      min-height: 10vh;
    }
    .sidebar {
      width: 100%;
    }
    .products {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }
  }

  @media (max-width: 768px) {
    .products {
      grid-template-columns: repeat(1, minmax(0, 1fr));
    }
  }
  /* responsiveness ends here  */
  ```

  ```js
  // App.js
  import React from "react";

  import Header from "./components/Header";
  import Sidebar from "./components/Sidebar";
  import Footer from "./components/Footer";
  import Products from "./components/Products";

  import "./App.css";

  const App = () => {
    return (
      <div>
        <Header />
        <main className="flex-center">
          <Sidebar />
          <div className="main-content">
            <Products />
          </div>
        </main>
        <Footer />
      </div>
    );
  };

  export default App;

  // Header.js
    import React from "react";

    const Header = () => {
      return (
        <header className="header flex-center">
          <h2 className="header__title">Anis Express</h2>
        </header>
      );
    };
    export default Header;

  // Sidebar.js
  import React from "react";

  const Sidebar = () => {
    return <aside className="sidebar">this is sidebar</aside>;
  };
  export default Sidebar;

  // Products.js
  import React from "react";


  const Products = () => {
    const imageSource1 =
      "https://i.dummyjson.com/data/products/1/thumbnail.jpg";
    const title1 = "iPhone 9";
    const description1 = "An apple mobile which is nothing like apple";
    const price1 = 549;
    const rating1 = 4.6;
    const brand1 = "Apple";
    const category1 = "smartphones";

    const imageSource2 =
      "https://i.dummyjson.com/data/products/2/thumbnail.jpg";
    const title2 = "iPhone X";
    const description2 =
      "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...";
    const price2 = 899;
    const rating2 = 4.44;
    const brand2 = "Apple";
    const category2 = "smartphones";

    return (
      <section className="products">
        <article className="product">
          <img src={imageSource1} alt="iPhone 9" className="product__img"/>
          <h2>{title1}</h2>
          <p>description: {description1}</p>
          <p>Price: {price1}</p>
          <p>rating: {rating1}</p>
          <p>brand: {brand1}</p>
          <p>category: {category1}</p>
        </article>
        <article className="product">
          <img src={imageSource2} alt="iPhone X" className="product__img"/>
          <h2>{title2}</h2>
          <p>description: {description2}</p>
          <p>Price: {price2}</p>
          <p>rating: {rating2}</p>
          <p>brand: {brand2}</p>
          <p>category: {category2}</p>
        </article>
      </section>
    );
  };
  export default Products;

  // Footer.js
  import React from "react";

    const Footer = () => {
      return (
        <footer className="footer flex-space-around">
          <div className="footer__left">
            <p className="footer__title">&copy;Copyright by Anisul Islam</p>
          </div>
          <div className="footer__right">
            <p>social media icons</p>
          </div>
        </footer>
      );
    };

    export default Footer;
  ```

## [8. Props and destructuring](https://youtu.be/GQx58yfYqxo)

- **props object: we can pass information from one component to another using props object. components communicate with each others via props. props is an object. props are like attributes in our HTML tag. props are readonly**
  - how to pass, recieve, set default props
  - how to pass JSX to component,
- **Code Example - 15 (Props sending)**

```js
import React from "react";
import Product from "./Product";

const Products = () => {
  const imageSource1 = "https://i.dummyjson.com/data/products/1/thumbnail.jpg";
  const title1 = "iPhone 9";
  const description1 = "An apple mobile which is nothing like apple";
  const price1 = 549;
  const rating1 = 4.6;
  const brand1 = "Apple";
  const category1 = "smartphones";

  const imageSource2 = "https://i.dummyjson.com/data/products/2/thumbnail.jpg";
  const title2 = "iPhone X";
  const description2 =
    "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...";
  const price2 = 899;
  const rating2 = 4.44;
  const brand2 = "Apple";
  const category2 = "smartphones";

  return (
    <section className="products">
      <Product
        imageSource={imageSource1}
        title={title1}
        description={description1}
        price={price1}
        rating={rating1}
        brand={brand1}
        category={category1}
      />
      <Product
        imageSource={imageSource2}
        title={title2}
        description={description2}
        price={price2}
        rating={rating2}
        brand={brand2}
        category={category2}
      />
    </section>
  );
};
export default Products;
```

- **Code Example - 16 (props recieveing & Destructuring)**

  ```js
  import React from "react";

  const Product = (props) => {
    const { imageSource, title, description, price, rating, brand, category } =
      props;
    return (
      <article className="product">
        <img src={thumbnail} alt="iPhone 9" className="product__img" />
        <div className="product__body">
          <h2 className="product__title">{title}</h2>
          <p className="product__description">description: {description}</p>
          <p className="product__price">Price: {price}</p>
          <p className="product__rating">rating: {rating}</p>
          <p className="product__brand">brand: {brand}</p>
          <p className="product__category">category: {category}</p>
        </div>
      </article>
    );
  };
  export default Product;
  ```

- **Code Example - 17 (props for complex data)**

  ```js
  // Products.js
  import React from "react";
  import Product from "./Product";

  const Products = () => {
    const products = [
      {
        id: 1,
        title: "iPhone 9",
        description: "An apple mobile which is nothing like apple",
        price: 549,
        discountPercentage: 12.96,
        rating: 4.69,
        stock: 94,
        brand: "Apple",
        category: "smartphones",
        thumbnail: "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
      },
      {
        id: 2,
        title: "iPhone X",
        description:
          "SIM-Free, Model A19211 6.5-inch Super Retina HD display with OLED technology A12 Bionic chip with ...",
        price: 899,
        discountPercentage: 17.94,
        rating: 4.44,
        stock: 34,
        brand: "Apple",
        category: "smartphones",
        thumbnail: "https://i.dummyjson.com/data/products/2/thumbnail.jpg",
      },
    ];
    return (
      <section className="products">
        <Product
          imageSource={products[0].thumbnail}
          title={products[0].title}
          description={products[0].description}
          price={products[0].price}
          rating={products[0].rating}
          brand={products[0].brand}
          category={products[0].category}
        />
        <Product
          imageSource={products[1].thumbnail}
          title={products[1].title}
          description={products[1].description}
          price={products[1].price}
          rating={products[1].rating}
          brand={products[1].brand}
          category={products[1].category}
        />
      </section>
    );
  };
  export default Products;
  ```

- create data.js in src folder and move all the todos dummy data there and import in App.js for using it.
- Can you load all the data from App.js to Products.js as props
- **Code Example - 18 (import data from another file and pass as props)**

```js
// App.js
import React from "react";

import Header from "./components/Header";
import Sidebar from "./components/Sidebar";
import Footer from "./components/Footer";
import Products from "./components/Products";
import { products } from "./data";

import "./App.css";

const App = () => {
  return (
    <div>
      <Header />
      <main className="flex-center">
        <Sidebar />
        <div className="main-content">
          <Products products={products} />
        </div>
      </main>
      <Footer />
    </div>
  );
};

export default App;

// Products.js
import React from "react";
import Product from "./Product";

const Products = ({ products }) => {
  return (
    <section className="products">
      <Product
        imageSource={products[0].thumbnail}
        title={products[0].title}
        description={products[0].description}
        price={products[0].price}
        rating={products[0].rating}
        brand={products[0].brand}
        category={products[0].category}
      />
      <Product
        imageSource={products[1].thumbnail}
        title={products[1].title}
        description={products[1].description}
        price={products[1].price}
        rating={products[1].rating}
        brand={products[1].brand}
        category={products[1].category}
      />
    </section>
  );
};
export default Products;
```

## [9. Mapping & rednering components](https://youtu.be/OwwmIzH7FzI)

- learn how to use map() and filter() from an array of Data.
- **Code Example - 19 (Map component with for loop)**

```js
import React from "react";
import Product from "./Product";

const Products = ({ products }) => {
  const productsElement = [];
  for (let index = 0; index < products.length; index++) {
    productsElement.push(
      <Product
        imageSource={products[index].thumbnail}
        title={products[index].title}
        description={products[index].description}
        price={products[index].price}
        rating={products[index].rating}
        brand={products[index].brand}
        category={products[index].category}
      />
    );
  }
  return <section className="products">{productsElement}</section>;
};
export default Products;
```

- **Code Example - 20 (Map component with forEach higher order Array function)**

  ```js
  import React from "react";
  import Product from "./Product";

  const Products = ({ products }) => {
    const productsElement = [];

    products.forEach((product) => {
      productsElement.push(
        <Product
          imageSource={product.thumbnail}
          title={product.title}
          description={product.description}
          price={product.price}
          rating={product.rating}
          brand={product.brand}
          category={product.category}
        />
      );
    });

    return <section className="products">{productsElement}</section>;
  };
  export default Products;
  ```

- **Code Example - 21 (Map component with map higher order Array function)**

  ```js
  import React from "react";
  import Product from "./Product";

  const Products = ({ products }) => {
    const productsElement = products.map((product) => {
      return (
        <Product
          imageSource={product.thumbnail}
          title={product.title}
          description={product.description}
          price={product.price}
          rating={product.rating}
          brand={product.brand}
          category={product.category}
        />
      );
    });

    return <section className="products">{productsElement}</section>;
  };
  export default Products;
  ```

## [10. Adding unique key to each child](https://youtu.be/Dj7ynTdhy1Q)

- we need to map each children of list uniquly so that react can identify them wor properly
- Keys are unique. we can use same keys for JSX nodes in different arrays.
- Where I can find key?

  - from database
  - generate locally - crypto.randomUUID() , uuid, nanoid

    - we can use index or any external package like [uuid](https://www.npmjs.com/package/uuid)
    - How to use uuid:

      ```js
      step 1: npm install uuid
      step 2: import { v4 as uuidv4 } from "uuid";
      step 3: uuidv4(); // ⇨ '9b1deb4d-3b7d-4bad-9bdd-2b0d7b3dcb6d'

      ```

- **Code Example - 22 (Adding unique key)**

  ```js
  // first use index
  // second use the available id
  // thirs use the uuid if id is not available inside the data

  import React from "react";
  import Product from "./Product";

  const Products = ({ products }) => {
    const productsElement = products.map((product) => {
      return (
        <Product
          key={product.id}
          imageSource={product.thumbnail}
          title={product.title}
          description={product.description}
          price={product.price}
          rating={product.rating}
          brand={product.brand}
          category={product.category}
        />
      );
    });

    return <section className="products">{productsElement}</section>;
  };
  export default Products;

  // get a uniqueId -> utility/getUniqueId.js
  import { v4 as uuidv4 } from "uuid";
  export const getUniqueId = () => uuidv4();

  // Now add the unique Id in App.js
  ```

## [11. More about props](https://youtu.be/Dj7ynTdhy1Q)

- default props
- jsx spread syntax
- **Code Example - 23 (jsx spread syntax)**

```js
import React from "react";
import Product from "./Product";

const Products = ({ products }) => {
  const productsElement = products.map((product) => {
    return <Product key={product.id} {...product} />;
  });

  return <section className="products">{productsElement}</section>;
};
export default Products;
```

- **Code Example - 24 (passing jsx as children)**

```js
import React from "react";

const Card = ({ children }) => {
  return <div className="card">{children}</div>;
};

export default Card;

import React from "react";
import Card from "./Card";

const Product = (props) => {
  const { thumbnail, title, description, price, rating, brand, category } =
    props;
  return (
    <Card>
      <article className="product">
        <img src={thumbnail} alt="iPhone 9" className="product__img" />
        <h2>{title}</h2>
        <p>description: {description}</p>
        <p>Price: {price}</p>
        <p>rating: {rating}</p>
        <p>brand: {brand}</p>
        <p>category: {category}</p>
      </article>
    </Card>
  );
};
export default Product;

```

## [12. PropTypes](https://youtu.be/mnPJrxHUarA)

- [documentation is here](https://reactjs.org/docs/typechecking-with-proptypes.html)
- **catch bugs with typechecking.**
- We can use Typescript or Flow for checking types in the entire application for sure but PropTypes can be the first guard here for checking types.

- default props is essential when first time running without any value passing to props

  ```js
    // lets think value can be primary or secondary one of two valyes
    <List background = 'primary' >

    // checking prop types
    background: PropTypes.oneOf([
      'primary',
      'secondary'
    ])
  ```

- **Code Example - 25 (PropTypes)**

  ```js
  // Todos.js
  import React from "react";
  import PropTypes from "prop-types";

  import Todo from "./Todo";

  const Todos = (props) => {
    const { todos } = props;

    const renderTodosElement = todos.map((todo) => (
      <Todo key={todo.id} todo={todo} />
    ));

    return <section className="todos">{renderTodosElement}</section>;
  };
  Todos.defaultProps = {
    todos: [],
  };
    Todos.propTypes = {
    todos: PropTypes.arrayOf(
      PropTypes.shape({
        id: PropTypes.string,
        title: PropTypes.string,
        desc: PropTypes.string,
      })
    ),
  };


  export default Todos;

  // Todo.js
  import React from "react";
  import PropTypes from "prop-types";

  const Todo = (props) => {
    const { todo } = props;
    return (
      <article className="todo" key={todo.id}>
        <h3>{todo.title}</h3>
        <p>{todo.desc} </p>
      </article>
    );
  };

  Todo.propTypes = {
    todo: PropTypes.shape({
      title: PropTypes.string,
      desc: PropTypes.string,
    }),
  };

  export default Todo;

  ```

## [13. Conditional rendering](https://youtu.be/roSfZjXp5us)

- rendering components based on if-else, element variable, ternary, short circuit

- **Code Example - 26 (Conditional rendering: element variable)**

  ```js
  // Inside App.js make adjustments
  let productsElement;
  if (products.length > 0) {
    productsElement = <Products products={products} />;
  } else {
    productsElement = <p>Product list is empty</p>;
  }
  return (
    <div>
      <Header />
      <main className="flex-center">
        <Sidebar />
        <div className="main-content">{productsElement}</div>
      </main>
      <Footer />
    </div>
  );
  ```

- **Code Example - 27 (Conditional rendering: iternary)**

  ```js
  // Inside App.js make adjustments
  let productsElement =
    products.length > 0 ? (
      <Products products={products} />
    ) : (
      <p>products list is empty</p>
    );

  return (
    <div>
      <Header />
      <main className="flex-center">
        <Sidebar />
        <div className="main-content">{productsElement}</div>
      </main>
      <Footer />
    </div>
  );

  // An alternative - we can use ternary inside return () function
  return (
    <div>
      <Header />
      <main className="flex-center">
        <Sidebar />
        <div className="main-content">
          {products.length > 0 ? (
            <Products products={products} />
          ) : (
            <p>products list is empty</p>
          )}
        </div>
      </main>
      <Footer />
    </div>
  );
  ```

- **Code Example - 28 (Conditional rendering: short circuit)**

  ```js
  // Inside App.js return() make following adjustments
  return (
    <div>
      <Header />
      <main>{products.length > 0 && <Products products={products} />}</main>
      <Footer />
    </div>
  );
  ```

## [14. Assignment 1: products-listing-app](https://github.com/anisul-Islam/react-assignment-1-products-listing-app)

## [15. Adding CSS Styling part-2](https://youtu.be/02YWKDxLpwk)

- Inline styling

  ```html
    <div style={{ width: "300px", backgroundColor: "pink" }}>
        Inline styling
      </div>
  ```

- CSS module

  - create a file name such as fileName.module.css as shown below

    ```css
    footer {
      height: 5vh;
      background-color: bisque;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .copyright {
      font-size: 0.9rem;
    }
    ```

  - use it in from another file as shown below

    ```js
    import React from "react";

    import styles from "./footer.module.css";

    const Footer = () => {
      return (
        <footer>
          <p className={styles.copyright}>
            All rights reserved by Anisul Islam
          </p>
        </footer>
      );
    };

    export default Footer;
    ```

## [16. developer tools and extension](https://youtu.be/m1paEcDlC5U)

## [17. add font awesome / react icons](https://youtu.be/jHDP6myBXRM)

- [How to use react-icons](https://react-icons.github.io/react-icons/)
- **Code Example - 29 (Adding & styling react icons )**

  ```js
  import React from "react";
  import { FaFacebookF, FaYoutube, FaTwitter } from "react-icons/fa";
  const Footer = () => {
    return (
      <footer className="footer flex-space-around">
        <div className="footer__left">
          <p className="footer__title">&copy;Copyright by Anisul Islam</p>
        </div>
        <div className="footer__right">
          <FaFacebookF />
          <FaYoutube />
          <FaTwitter />
        </div>
      </footer>
    );
  };

  export default Footer;

  // Product.js
  import React from "react";
  import { FaCartPlus } from "react-icons/fa";

  import Card from "./Card";

  const Product = (props) => {
    const { thumbnail, title, description, price, rating, brand, category } =
      props;
    return (
      <Card>
        <article className="product">
          <img src={thumbnail} alt="iPhone 9" className="product__img" />
          <div className="product__body">
            <h2 className="product__title">{title}</h2>
            <p className="product__description">description: {description}</p>
            <p className="product__price">Price: {price}</p>
            <p className="product__rating">rating: {rating}</p>
            <p className="product__brand">brand: {brand}</p>
            <p className="product__category">category: {category}</p>
            <button className="btn product__btn icon">
              <FaCartPlus className="icon" /> Add To Cart
            </button>
          </div>
        </article>
            </Card>
          );
        };
        export default Product;


  // App.css
  /* reset code and common starts here  */
    :root {
      --primary-color: rgb(11, 181, 48);
      --secondary-color: rgba(36, 122, 55, 0.9);
      --padding: 0.5rem;
      --transition: all 0.3s;
      --border-radius: 0.6rem;
      --box-shadow: 0.1rem 0.2rem 0.8rem rgba(205, 202, 202, 0.5);
    }
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      text-decoration: none;
      list-style-type: none;
      outline: none;
    }
    html {
      scroll-behavior: smooth;
    }
    .flex-space-around {
      display: flex;
      justify-content: space-around;
      align-items: center;
    }
    .flex-center {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .card {
      box-shadow: var(--box-shadow);
      border-radius: var(--border-radius);
      /* padding: var(--padding); */
      transition: var(--transition);
    }
    img {
      width: 100%;
      height: auto;
    }
    .btn {
      border: none;
      padding: var(--padding);
      border-radius: var(--border-radius);
      transition: all 0.3s;
      color: var(--secondary-color);
    }
    .btn:hover {
      background-color: orange;
      color: black;
    }
    /* reset code and common ends here  */

    /* header starts here  */
    .header {
      height: 10vh;
      background-color: var(--primary-color);
      color: white;
    }
    /* header ends here  */

    /* main starts here  */
    main {
      height: 80vh;
    }
    .sidebar {
      flex: 1;
      padding: var(--padding);
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 1rem;
      align-self: flex-start;
      background-color: #e6e3e3;
      height: 100%;
      border-right: 1px solid var(--primary-color);
    }
    .main-content {
      flex: 3;
      height: 100%;
      padding: var(--padding);
      overflow: scroll;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 2rem;
    }
    .product {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
    .product__body {
      padding: var(--padding);
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
    .product__img {
      width: 100%;
      height: 15rem;
      filter: saturate(0);
      transition: var(--transition);
    }
    /* main ends here  */

    /* footer starts here  */
    .footer {
      min-height: 10vh;
      padding: var(--padding);
      background-color: var(--primary-color);
      color: white;
      font-size: 1.1rem;
    }
    .footer__right {
      display: flex;
      gap: 1rem;
    }
    /* footer ends here  */

    /* responsiveness starts here  */
    @media (max-width: 992px) {
      .flex-space-around,
      .flex-center {
        flex-direction: column;
        gap: 1rem;
        padding: 1rem 0;
      }
      .header {
        min-height: 10vh;
      }
      .sidebar {
        width: 100%;
      }
      .products {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    @media (max-width: 768px) {
      .products {
        grid-template-columns: repeat(1, minmax(0, 1fr));
      }
    }
    /* responsiveness ends here  */
  ```

- How to use font awesome icons directly

  ```js
     // Add SVG Core
    npm i --save @fortawesome/fontawesome-svg-core

    // add Free icons styles
    npm i --save @fortawesome/free-solid-svg-icons
    npm i --save @fortawesome/free-regular-svg-icons
    npm i --save @fortawesome/free-brands-svg-icons

    // add the react component
    npm i --save @fortawesome/react-fontawesome@latest


    // usage
    import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
    import { faPlusCircle, faMinusCircle } from '@fortawesome/free-solid-svg-icons';
    import { faYoutube } from '@fortawesome/free-brands-svg-icons';

    <FontAwesomeIcon icon={faPlusCircle}></FontAwesomeIcon>

    // use className for styling icons

  ```

## Part-3 (event handler, state,useState hook, controlled component, state lifting, more on css, class component)

## [18. Adding Interactivity - event & event handler]

- Event: any user interaction like clicking button, hovering button, giving values in input field etc.
- Event handler: your response to user interactions. create a function for handling the interaction.
- state - value of anything can be changed based on your interaction and you may want to update UI based on state.
- **Code Example - 30 (event - onClick )**

  ```js
  <button
    className="btn product__btn"
    onClick={alert("product is added to the cart")} // not depends on user inetractivity
  >
    <FaCartPlus className="icon" /> Add To Cart
  </button>
  ```

- **Code Example - 31 (event Handler)**

  ```js
  const handleClick = () => {
    alert("product is added to the cart");
  };

  // method 1
  <button
    className="btn product__btn"
    onClick={() => {
      alert("product is added to the cart");
    }} // depends on user inetractivity as we definied the function and it is not running until we click the button
  >
    <FaCartPlus className="icon" /> Add To Cart
  </button>

  // method 2
  <button
    className="btn product__btn"
    onClick={handleClick} // do not call just define the function
  >
    <FaCartPlus className="icon" /> Add To Cart
  </button>

  // we can create own custom Button component
  import React from "react";

  const Button = (props) => {
    console.log(props);

    const handleClick = () => {
      // we can use condition for calling multiple functions
      props.onHandleAddProduct();
    };

   const handleAddProduct = (product) => {
    alert(JSON.stringify(product, null, 4));
  };

    return (
      <button className={props.className} onClick={props.onClick} type={props.type}>
      {props.children}
    </button>
    );
  };

  export default Button;

  // more simplified
  import React from "react";

  const Button = (props) => {
    return (
      <button className={props.className} onClick={props.onClick}>
        {props.children}
      </button>
    );
  };

  export default Button;
  ```

- **Code Example - 32 (Pass parameter with event )**

  ```js
  const handleAddProduct = (e, product) => {
    e.stopPropagation();
    console.log("Product Event: ", e);
    alert(JSON.stringify(product, null, 4));
  };

  <Button
    className="btn product__btn"
    onClick={(e) => {
      handleAddProduct(e, product);
    }}
  >
    <FaCartPlus className="icon" /> Add To Cart
  </Button>;
  ```

- **Code Example - 33 (onChange Event )**

  ```js
  import React from "react";

  const NewProduct = () => {
    const handleChange = (event) => {
      console.log(event.target.value);
    };
    return (
      <div className="new-user">
        <h2>Create Product</h2>

        <div className="form__control">
          <label htmlFor="title">Title: </label>
          <input
            className="form__input"
            type="text"
            placeholder="Enter product title"
            name="title"
            onChange={handleChange}
            required={true}
          />
        </div>

        <div className="form__control">
          <label htmlFor="price">Price: </label>
          <input
            className="form__input"
            type="number"
            placeholder="Enter product price here"
            name="price"
            onChange={handleChange}
            required={true}
          />
        </div>
      </div>
    );
  };

  export default NewProduct;
  ```

- **Code Example - 34 (More complex example of onChange Event )**

  ```js
  import React from "react";

  const NewProduct = () => {
    const inputs = [
      {
        id: 1,
        type: "text",
        name: "title",
        placeholder: "Enter product title",
        required: true,
      },
      {
        id: 2,
        type: "number",
        name: "price",
        placeholder: "Enter product price",
        required: true,
      },
    ];
    const handleChange = (event) => {
      console.log(event.target.value);
    };

    return (
      <div className="new-user">
        <h2>Create Product</h2>

        <input
          className="form__input"
          type={inputs[0].type}
          placeholder={inputs[0].placeholder}
          name={inputs[0].name}
          onChange={handleChange}
          required={inputs[0].required}
        />

        <input
          className="form__input"
          type={inputs[1].type}
          placeholder={inputs[1].placeholder}
          name={inputs[1].name}
          onChange={handleChange}
          required={inputs[1].required}
        />
      </div>
    );
  };

  // More simplified
  const NewProduct = () => {
    const inputs = [
      {
        id: 1,
        type: "text",
        name: "title",
        placeholder: "Enter product title",
        required: true,
      },
      {
        id: 2,
        type: "number",
        name: "price",
        placeholder: "Enter product price",
        required: true,
      },
    ];
    const handleChange = (event) => {
      console.log(event.target.value);
    };

    const renderInputs = inputs.map((input) => {
      return (
        <Input
          key={input.id}
          className="form__input"
          type={input.type}
          placeholder={input.placeholder}
          name={input.name}
          onChange={handleChange}
          required={input.required}
        />
      );
    });

    return (
      <div className="new-user">
        <h2>Create Product</h2>
        {renderInputs}
      </div>
    );
  };

  // more simplified
  <Input key={input.id} {...input} onChange={handleChange} />;

  // Input.js
  import React from "react";
  const Input = (props) => {
    const { onChange, ...inputProps } = props; // getting onChnage from props and putting rest of the things inside inputProps

    console.log([inputProps]);
    return (
      <input className="form__input" {...inputProps} onChange={onChange} />
    );
  };

  export default Input;
  ```

- **Code Example - 35 (Event Bubbling - child event can effect parent event )**

  ```js
  const handleAddProduct = (e, product) => {
    e.stopPropagation();
    console.log("Product Event: ", e);
    alert(JSON.stringify(product, null, 4));
  };
  ```

- **Code Example - 36 (onSubmit Event )**

## [19. useState Hooks](https://youtu.be/skUOiqcVurY)

- state is a memory for component where we can update value and re-render the component
- state is a global variable thats why when you even re-render it fetch the last updated value
- hooks are function which we can implement in our component - useState, useEffect
- useState() hook helps us to track state in a functional component.
- **Code Example - 36 (Counter App )**

  ```js
  // App.js
  import React from "react";

  import Counter from "./components/Counter";

  const App = () => {
    return (
      <div>
        <Counter />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // Counter.js
  import React, { useState } from "react";

  function Counter() {
    const [count, setCount] = useState(0);
    const handleIncrement = () => {
      setCount(count + 1); // setCount (count => count + 1)
    };

    return (
      <div>
        <h2>Counter: {count}</h2>
        <button onClick={handleIncrement}>+</button>
      </div>
    );
  }

  export default Counter;
  ```

  - we can also use name attribute for identifying element and use 1 function instead of many. from ebent handler we can use event.target.name and then decide what to do or not? - [1 handler for multiple elements] (https://github.com/anisul-Islam/react-counter-app-1-function/blob/master/src/components/Counter.js)

- **Code Example - 37 (store data in state )**

  ```js
  import React, { useState } from "react";
  import { FaCartPlus } from "react-icons/fa";
  import Button from "./Button";

  import Card from "./Card";

  const Product = (props) => {
    const { thumbnail, title, description, price, rating, brand, category } =
      props;
    const product = props;
    const [cartProducts, setCartProducts] = useState([]);
    const handleAddProduct = (e, product) => {
      e.stopPropagation();
      setCartProducts((prevState) => {
        return [...prevState, product];
      });
    };
    console.log(cartProducts);
    return (
      <Card>
        <article className="product">
          <img src={thumbnail} alt="iPhone 9" className="product__img" />
          <div className="product__body">
            <h2 className="product__title">{title}</h2>
            <p className="product__description">description: {description}</p>
            <p className="product__price">Price: {price}</p>
            <p className="product__rating">rating: {rating}</p>
            <p className="product__brand">brand: {brand}</p>
            <p className="product__category">category: {category}</p>
            {/* <button className="btn product__btn icon">
              <FaCartPlus className="icon" /> Add To Cart
            </button> */}
            <Button
              className="btn product__btn"
              onClick={(e) => {
                handleAddProduct(e, product);
              }}
            >
              <FaCartPlus className="icon" /> Add To Cart
            </Button>
          </div>
        </article>
      </Card>
    );
  };
  export default Product;
  ```

- **Code Example - 38 (why update data based on prevState?)**

  - update state based on prev value - `setCount (count => count + 1)`

  ```js
      const handleIncrement = (e) => {
        e.stopPropagation();

        setcount(count + 1);
        setcount(count + 1);
        setcount(count + 1);

        console.log("increment count: ", count);
      };

      const handleIncrement = (e) => {
          e.stopPropagation();

          setcount((count) => count + 1);
          setcount((count) => count + 1);
          setcount((count) => count + 1);

          console.log("increment count: ", count);
        };

      const handleIncrement = (e) => {
         e.stopPropagation();
        setTimeout(() => {
          <!-- setcount(count + 1); -->
          setcount((count) => count + 1);
        }, 3000);
        console.log("increment count: ", count);
      };
  ```

## [20. Assignment - 2: Counter App](https://github.com/anisul-Islam/react-assignment-2-counter-app)

## [21. Form Controlled components](https://youtu.be/kvGNlTh3rNQ)

- create a new resouce such as NewProduct, NewUser, NewTodo etc.
- **Code Example - 39 (get data from a form)**

  ```js

  ```

## [22. upating object in state](https://beta.reactjs.org/learn/updating-objects-in-state)

- **Code Example - 40 (updating object in state)**

  ```js
  import React, { useState } from "react";

  const NewUser = () => {
    const [user, setUser] = useState({
      name: "",
      email: "",
      password: "",
    });
    const handleChange = (event) => {
      event.stopPropagation();
      setUser((prevUser) => {
        return { ...prevUser, [event.target.name]: event.target.value };
      });
    };

    const handleSubmit = (event) => {
      event.preventDefault();
      console.log("submitted");
      alert(JSON.stringify(user));
    };

    return (
      <div>
        <form action="" className="form" onSubmit={handleSubmit}>
          <div className="form__control">
            <label htmlFor="name">name: </label>
            <input
              type="text"
              placeholder="Enter Name"
              name="name"
              value={user.name}
              onChange={handleChange}
              required={true}
            />
          </div>
          <div className="form__control">
            <label htmlFor="email">email: </label>
            <input
              type="email"
              placeholder="Enter Email"
              name="email"
              value={user.email}
              onChange={handleChange}
              required={true}
            />
          </div>
          <div className="form__control">
            <label htmlFor="password">password: </label>
            <input
              type="password"
              placeholder="Enter password"
              name="password"
              value={user.password}
              onChange={handleChange}
              required={true}
            />
          </div>
          <button type="submit">Add User</button>
        </form>
      </div>
    );
  };

  export default NewUser;
  ```

- **Code Example - 41 (updating nested object in state)**

  ```js

  ```

## [23. upating array in state](https://beta.reactjs.org/learn/updating-arrays-in-state)

- **Code Example - 42 (updating array in state)**

  ```js

  ```

## [24. data passing: child to parent component, state lifting](https://youtu.be/xdW2uFA-SOg)

- Another practical example: https://youtu.be/h7yq5lfDZc8
- [Freecodecamp doc](https://www.freecodecamp.org/news/what-is-lifting-state-up-in-react/)
- **Code Example - 43 (state lifting)**

  ```js
  // App.js
  step 1: create a callback function that will help us to get the data from child component
   const handleAddNewTodo = (newTodo) => {
    console.log(newTodo);
  };

   step 2: pass the function as props to child to component
  <AddTodo onHandleAddNewTodo={handleAddNewTodo} />

  step 3: receive the function props and use it for passing the data from child to parent
  // AddTodo.js
  import PropTypes from "prop-types";

  const handleSubmit = (event) => {
    event.preventDefault();
    const newTodo = { id: getUniqueId(), title, desc };
    setTitle("");
    setDesc("");
    props.onHandleAddNewTodo(newTodo);
  };

  AddTodo.propTypes = {
    onHandleAddNewTodo: PropTypes.func,
  };


  // Another Example
    function App() {
      const [users, setUsers] = useState([
        { name: 'alex', email: 'alex@gmail.com' },
      ]);

      console.log(users);

      return (
        <div className="container">
          <Test setUsers={setUsers} />
        </div>
        )
    }

    const Test = (props) => {
      const { setUsers } = props;

      const [user, setUser] = useState({ name: '', email: '' });
      const handleSubmit = (event) => {
        event.preventDefault();
        setUsers((users) => [...users, user]);
        setUser({
          name: '',
          email: '',
        });
      };
      const handleChange = (event) => {
        const name = event.target.name;
        setUser({ ...user, [name]: event.target.value });
      };
   }
  ```

  - **Code Example - 44 (state lifting and delete item)**

    ```js
    // App.js
    step 1: create a function that will help us to get the id from child component Todo.js
    const handleDeleteTodo = (id) => {
      console.log(id);
    };

    step 2: pass the function as props to App.js -> Todos.js -> Todo.js
    <Todos onHandleDeleteTodo={handleDeleteTodo} />

    step 3: After passing the function from App.js to Todo.js now lets handle the button click and get the id so that we pass the id to App.js with the help of the function onHandleDeleteTodo
    // Todo.js

    const { todo, onHandleDeleteTodo } = props;

    const handleDelete = (id) => {
      onHandleDeleteTodo(id);
    };

    <button
            className="btn"
            onClick={() => {
              handleDelete(todo.id);
            }}
          >
            <FaTrash className="icon" />
    </button>

    step 4: finally with the help of the id lets delete the item from todos state inside App.js

    const handleDeleteTodo = (id) => {
      setTodos(todos.filter((todo) => todo.id !== id));
    };
    ```

## [25. Form Validation without library](https://github.com/anisul-Islam/form-validation-without-library)

## [26. useRef hook - Uncontrolled component](https://youtu.be/l5z137GWakU)

- If we look at the AddTodo component then you will see we are not using those title and desc state inside the component that much so we can avoid state and make the component stateless
- **Code Example - 45 (useRef hook for getting form value)**

  ```js
  import React, { useRef } from "react";
  import PropTypes from "prop-types";

  import { getUniqueId } from "../utility/getUniqueId";

  const AddTodo = (props) => {
    const titleRef = useRef("");
    const descRef = useRef("");

    const handleSubmit = (event) => {
      event.preventDefault();
      const title = titleRef.current.value;
      const desc = descRef.current.value;
      const newTodo = { id: getUniqueId(), title, desc };
      props.onHandleAddNewTodo(newTodo);
      titleRef.current.value = "";
      descRef.current.value = "";
    };

    return (
      <div className="form-container">
        <form onSubmit={handleSubmit}>
          <h2 className="form-title">Add New Todo</h2>
          <div className="form-input">
            <label htmlFor="title">Todo Title: </label>
            <input
              type="text"
              name="title"
              id="title"
              ref={titleRef}
              required
              autoFocus
            />
          </div>
          <div className="form-input">
            <label htmlFor="desc">Todo description: </label>
            <textarea name="desc" id="desc" ref={descRef} required></textarea>
          </div>
          <div className="form-input">
            <button type="submit" className="btn form-btn">
              Add Todo
            </button>
          </div>
        </form>
      </div>
    );
  };

  AddTodo.propTypes = {
    onHandleAddNewTodo: PropTypes.func,
  };

  export default AddTodo;
  ```

## [27. dynamic styling in React](https://youtu.be/Eru9-kZfhw4)

- Now lets add some coditional styling
- **Code Example - 46 (conditional styling)**

  ```js
  import React, { useState, useEffect } from "react";
  import PropTypes from "prop-types";

  import { getUniqueId } from "../utility/getUniqueId";

  const AddTodo = (props) => {
    const [title, setTitle] = useState("");
    const [desc, setDesc] = useState("");

    const [isTitleValid, setIsTitleValid] = useState(false);
    const [isDescValid, setIsDescValid] = useState(false);

    useEffect(() => {
      if (title.trim().length > 3) {
        setIsTitleValid(true);
      }
      if (desc.trim().length > 9) {
        setIsDescValid(true);
      }
    }, [title, desc]);

    const handleTitleChange = (event) => {
      setTitle(event.target.value);
    };

    const handleDescriptionChange = (event) => {
      setDesc(event.target.value);
    };

    const handleSubmit = (event) => {
      event.preventDefault();

      const newTodo = { id: getUniqueId(), title, desc };
      props.onHandleAddNewTodo(newTodo);
      setTitle("");
      setDesc("");
    };

    return (
      <div className="form-container">
        <pre style={{ backgroundColor: "white" }}>
          {JSON.stringify({ id: getUniqueId(), title, desc }, undefined, 2)}
        </pre>
        <form onSubmit={handleSubmit}>
          <h2 className="form-title">Add New Todo</h2>
          <div className="form-input">
            <label htmlFor="title">Todo Title: </label>
            <input
              type="text"
              name="title"
              id="title"
              value={title}
              onChange={handleTitleChange}
              required
              autoFocus
            />
            {!isTitleValid && <p>Title Should be at least 4 characters</p>}
          </div>
          <div className="form-input">
            <label htmlFor="desc">Todo description: </label>
            <textarea
              name="desc"
              id="desc"
              value={desc}
              onChange={handleDescriptionChange}
              required
            ></textarea>
            {!isDescValid && (
              <p>Description Should be at least 10 characters</p>
            )}
          </div>
          <div className="form-input">
            <button
              type="submit"
              className="btn form-btn"
              disabled={!(isTitleValid && isDescValid)}
            >
              Add Todo
            </button>
          </div>
        </form>
      </div>
    );
  };

  AddTodo.propTypes = {
    onHandleAddNewTodo: PropTypes.func,
  };

  export default AddTodo;
  ```

## [28. Assignment - 3: Add New Product](https://github.com/anisul-Islam/react-assignment-3-add-new-product)

## [29. class component](https://youtu.be/fu76idgpuEI)

## [30. state, setState, event handler](https://youtu.be/9AtJ4dM2xOU)

- state is a js object for storing current situation of a component

- **Code Example - 47 (Counter App using class component)**

  ```js
  // App.js
  import React from "react";

  import Counter from "./components/Counter";

  const App = () => {
    return (
      <div>
        <Counter />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // Counter.js
  import React, { Component } from "react";

  export default class Counter extends Component {
    constructor(props) {
      super(props);

      this.state = {
        count: 0,
      };
    }

    handleIncrement = () => {
      this.setState({
        count: this.state.count + 1,
      });
    };

    render() {
      return (
        <div>
          <h2>Counter: {this.state.count}</h2>
          <button onClick={this.handleIncrement}>+</button>
        </div>
      );
    }
  }
  ```

## Part-4 (life cycle method of class component, useEffect Hook, custom hook, services)

## [31. life cycle methods of a class component](https://youtu.be/Yz5qTOmSt0M)

- **Code Example - 48 (life cycle methods of a class component)**

  ```js
  // Counter App
  import React, { Component } from "react";

  class Counter extends Component {
    constructor(props) {
      super(props);

      this.state = {
        count: 0,
      };
    }

    handleIncrement = () => {
      this.setState({
        count: this.state.count + 1,
      });
    };

    render() {
      return (
        <div>
          <h2>Count: {this.state.count}</h2>
          <button onClick={this.handleIncrement}>Increment</button>
        </div>
      );
    }
  }
  export default Counter;

  // LifeCycle Methods
  import React, { Component } from 'react';
  // mounting - constructor -> render -> componentDidMount() (it will be called once, API Call is recommended here)
  // updating - state/props ->  shouldComponentUpdate()-> render -> componentDidUpdate ->
  // unmounting -> componentDidUnmount()
  class LifeCycle extends Component {
      constructor(props) {
          super(props);
          console.log('constructor');
          this.state = {
              count: 0
          };
      }

      handleIncrement = () => {
          this.setState({
              count: this.state.count + 1
          });
      };
      componentDidMount() {
          console.log('componentDidMount');
      }
      componentDidUpdate() {
          console.log('componentDidUpdate');
      }
      shouldComponentUpdate() {
          console.log('shouldComponentUpdate()');
          return true;
      }

      render() {
          console.log('render');
          return (
              <div>
                  <h2>Count: {this.state.count}</h2>
                  <button onClick={this.handleIncrement}>Increment</button>
              </div>
          );
      }
  }
  export default LifeCycle;

  ```

## [32. useEffect Hook](https://youtu.be/XEU3jlV9syI)

- **Code Example - 49 (useEffect hook)**

  ```js
  import React, { useEffect, useState } from "react";

  // Rule: Don’t call Hooks inside loops, conditions, or nested functions

  // The useEffect Hook allows to perform side effects (fetching data, timers, directly manullay updating the DOM) in components.

  // useEffct = componentDidMount + componentDidUpdate + componentWillUnmount

  const UseEffectHook = () => {
    const [count, setCount] = useState(0);

    // useEffect(() => {
    //   //Runs on every render
    // });

    // useEffect(() => {
    //   //Runs only on the first render
    // }, []);

    // useEffect(() => {
    //   //Runs on the first render
    //   //And any time any dependency value changes
    // }, [prop, state]);

    //Runs on every render
    // useEffect(() => {
    //   console.log("useEffect: " + count);
    // });

    //Runs only on the first render
    // useEffect(() => {
    //   console.log(count);
    // }, []);

    //Runs on the first render and also when the dependecy value changes
    useEffect(() => {
      console.log(count);
    }, [count]);

    return (
      <div>
        <h1>Count: {count}</h1>
        <button
          onClick={() => {
            setCount((count) => count + 1);
          }}
        >
          +
        </button>
      </div>
    );
  };

  export default UseEffectHook;
  ```

  ```js
  // Another example
  import React, { useState, useEffect } from "react";

  const UseEffectExample = () => {
    const [count, setCount] = useState(0);
    const [greeting, setGreeting] = useState("good morning");
    useEffect(() => {
      console.log("hello from useeffect");
    }, [count]);

    return (
      <div>
        <h2>Count: {count}</h2>
        <button
          onClick={() => {
            setCount((count) => count + 1);
          }}
        >
          +
        </button>
        <button
          onClick={() => {
            setGreeting(greeting + "2");
          }}
        >
          greeting
        </button>
        <p>{greeting}</p>
      </div>
    );
  };

  export default UseEffectExample;
  ```

## [33. fatch data using useEffect Hook](https://youtu.be/Z-EkslDJTJI)

- **Code Example - 50 (fetch data using useEffect hook)**

  ```js
  import React, { useEffect, useState } from "react";

  import "./App.css";

  const App = () => {
    const [users, setUsers] = useState([]);
    const [isLoading, setIsLoading] = useState(false);
    const [error, setError] = useState(null);

    useEffect(() => {
      setIsLoading(true);
      fetch("https://jsonplaceholder.typicode.com/users")
        .then((res) => {
          if (!res.ok) {
            throw new Error("could not fetch the data");
          }
          return res.json();
        })
        .then((result) => {
          setUsers(result);
          setIsLoading(false);
        })
        .catch((error) => {
          setIsLoading(false);
          setError(error.message);
        });
    }, []);
    console.log(users);
    const renderUsers = users.map((user) => {
      const { id, name, username, email, phone, website } = user;
      return (
        <article key={id} style={{ margin: "2rem" }}>
          <h2>{id}</h2>
          <h3>{name}</h3>
          <p>{username}</p>
          <p>{email}</p>
          <p>{phone}</p>
          <p>{website}</p>
        </article>
      );
    });

    return (
      <div>
        {isLoading && <p>Loading...</p>}
        {error ? <p>{error}</p> : <section>{renderUsers}</section>}
      </div>
    );
  };

  export default App;
  ```

- **Code Example - 51 (fetch data using useEffect hook - async await)**

  ```js
  import React, { useEffect, useState } from "react";

  import "./App.css";

  const App = () => {
    const [users, setUsers] = useState([]);
    const [isLoading, setIsLoading] = useState(false);
    const [error, setError] = useState(null);

    const fetchUsers = async () => {
      try {
        const response = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        const result = await response.json();
        setUsers(result);
        setIsLoading(false);
      } catch (error) {
        setIsLoading(false);
        setError(error.message);
      }
    };

    useEffect(() => {
      setIsLoading(true);
      fetchUsers();
    }, []);

    const renderUsers = users.map((user) => {
      const { id, name, username, email, phone, website } = user;
      return (
        <article key={id} style={{ margin: "2rem" }}>
          <h2>{id}</h2>
          <h3>{name}</h3>
          <p>{username}</p>
          <p>{email}</p>
          <p>{phone}</p>
          <p>{website}</p>
        </article>
      );
    });

    return (
      <div>
        {isLoading && <p>Loading...</p>}
        {error ? <p>{error}</p> : <section>{renderUsers}</section>}
      </div>
    );
  };

  export default App;
  ```

## [34. how to create custom hook](https://youtu.be/ZWschU7H_20)

- **Code Example - 52 (custom hook)**

  ```js
  import React, { useState, useEffect } from "react";

  const useFetch = (URL) => {
    const [data, setData] = useState([]);
    const [isLoading, setIsLoading] = useState(false);
    const [error, setError] = useState(null);

    const fetchUsers = async () => {
      try {
        const response = await fetch(URL);
        const result = await response.json();
        setData(result);
        setIsLoading(false);
      } catch (error) {
        setIsLoading(false);
        setError(error.message);
      }
    };

    useEffect(() => {
      setIsLoading(true);
      fetchUsers();
    }, []);

    return { data, isLoading, error };
  };

  export default useFetch;
  ```

## [35. create services for making http requests]

- **Code Example - 53 (services for http requests)**

  ```js
  // UserService.js
  import axios from "axios";

  const BASE_URL = "https://jsonplaceholder.typicode.com";

  // using axios
  export const getAllUsers = async () => {
    const response = await axios.get(`${BASE_URL}/users/202`);
    return response.data;
  };

  // using fetch
  export const createUser = async () => {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
      method: "POST",
      body: JSON.stringify({
        title: "foo",
        body: "bar",
        userId: 1,
      }),
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    });
    return response;
  };

  // App.js
  import React, { useEffect, useState } from "react";
  import { ToastContainer, toast } from "react-toastify";
  import "react-toastify/dist/ReactToastify.css";

  import "./App.css";
  import { getAllUsers } from "./services/UserService";

  const App = () => {
    const [users, setUsers] = useState([]);
    const [isLoading, setIsLoading] = useState(false);
    const [error, setError] = useState(null);

    const fetchUsers = async () => {
      try {
        const result = await getAllUsers();
        console.log(result);
        setUsers(result);
        setIsLoading(false);
      } catch (err) {
        setIsLoading(false);
        setError(err.message);
        toast(err.message);
      }
    };

    useEffect(() => {
      setIsLoading(true);
      fetchUsers();
    }, []);

    const renderUsers = users.map((user) => {
      const { id, name, username, email, phone, website } = user;
      return (
        <article key={id} style={{ margin: "2rem" }}>
          <h2>{id}</h2>
          <h3>{name}</h3>
          <p>{username}</p>
          <p>{email}</p>
          <p>{phone}</p>
          <p>{website}</p>
        </article>
      );
    });

    return (
      <div>
        <ToastContainer />
        {isLoading && <p>Loading...</p>}
        {error ? <p>{error}</p> : <section>{renderUsers}</section>}
      </div>
    );
  };

  export default App;
  ```

## [36. Assignment 4 - fetch products](https://github.com/anisul-Islam/react-assignment-4-fetch-products)

## Part-5 (useReducer Hook, modal, dynamic styling)

## [37. useReducer hook](https://youtu.be/l_BhBNhNwhE)

- useState and useReducers helps us to manage states
- useReducer is a good choice if you have multiple & complex states (objects, arrays)
- useReducer is powerful when managing complex logic for updating the states
- useState is better if you are using state for simple purpose and handling string, boolean or number type.
- **Code Example - 54 (without useReducer)**

  ```js
  // without useReducer
  import React, { useState } from "react";

  // books, modalText, isModalOpen
  // add book - modalText
  // remove book - modalText
  const dummyBooks = [
    { id: 1, title: "book1" },
    { id: 2, title: "book2" },
  ];
  const Modal = ({ modalText }) => {
    return <p>{modalText}</p>;
  };
  const App = () => {
    // every time update 3 relevant states
    const [books, setBooks] = useState(dummyBooks);
    const [modalText, setModalText] = useState("");
    const [isModalOpen, setIsModalOpen] = useState(false);

    const [bookTitle, setBookTitle] = useState("");

    const handleAddBook = (event) => {
      event.stopPropagation();
      setBookTitle(event.target.value);
    };
    const handleDeleteBook = (event, id) => {
      event.stopPropagation();
      const filterBooks = books.filter((book) => book.id !== id);
      setBooks(filterBooks);
      setIsModalOpen(true);
      setModalText(" book is deleted");
    };

    const handleSubmit = (event) => {
      event.preventDefault();
      const newBook = { id: new Date().getTime().toString(), title: bookTitle };
      setBooks((prevBooks) => {
        return [...prevBooks, newBook];
      });
      setIsModalOpen(true);
      setModalText("New book is added");
    };

    return (
      <div>
        <form onSubmit={handleSubmit}>
          <input
            type="text"
            placeholder="enter book title"
            value={bookTitle}
            onChange={handleAddBook}
            required
          />
          <button type="submit">Add Book</button>
        </form>

        {isModalOpen && <Modal modalText={modalText} />}

        <section className="books">
          {books.map((book) => {
            const { id, title } = book;
            return (
              <article key={id} className="book">
                <h2>id: {id}</h2>
                <p>title: {title}</p>
                <button
                  onClick={(event) => {
                    handleDeleteBook(event, id);
                  }}
                >
                  Delete
                </button>
              </article>
            );
          })}
        </section>
      </div>
    );
  };

  export default App;
  ```

- **Code Example - 55 (with useReducer)**

  ```js
  import React, { useState, useReducer } from "react";

  // books, modalText, isModalOpen
  // add book - modalText
  // remove book - modalText
  const dummyBooks = [
    { id: 1, title: "book1" },
    { id: 2, title: "book2" },
  ];
  const Modal = ({ modalText }) => {
    return <p>{modalText}</p>;
  };

  // based on action type reducer will update the state & return the state
  const reducer = (state, action) => {
    // action object has action.type and action.payload
    switch (action.type) {
      case "ADD":
        const allBooks = [...state.books, action.payload];
        return {
          ...state,
          books: allBooks,
          isModalOpen: true,
          modalText: "new book is added",
        };
      case "DELETE":
        const filteredBooks = state.books.filter(
          (book) => book.id !== action.payload
        );
        return {
          ...state,
          books: filteredBooks,
          isModalOpen: true,
          modalText: "book is deleted",
        };

      default:
        return state;
    }
  };

  const initialState = {
    books: dummyBooks,
    isModalOpen: false,
    modalText: "",
  };

  const App = () => {
    // const [books, setBooks] = useState(dummyBooks);
    // const [modalText, setModalText] = useState('');
    // const [isModalOpen, setIsModalOpen] = useState(false);

    const [bookState, dispatch] = useReducer(reducer, initialState);

    const [bookTitle, setBookTitle] = useState("");

    const handleTitleChange = (event) => {
      event.stopPropagation();
      setBookTitle(event.target.value);
    };
    const handleDeleteBook = (event, id) => {
      event.stopPropagation();
      dispatch({ type: "DELETE", payload: id });
    };

    const handleSubmit = (event) => {
      event.preventDefault();
      const newBook = { id: new Date().getTime().toString(), title: bookTitle };
      dispatch({ type: "ADD", payload: newBook });
      setBookTitle("");
    };

    return (
      <div>
        <form onSubmit={handleSubmit}>
          <input
            type="text"
            placeholder="enter book title"
            value={bookTitle}
            onChange={handleTitleChange}
            required
          />
          <button type="submit">Add Book</button>
        </form>

        {bookState.isModalOpen && <Modal modalText={bookState.modalText} />}

        <section className="books">
          {bookState.books.map((book) => {
            const { id, title } = book;
            return (
              <article key={id} className="book">
                <h2>id: {id}</h2>
                <p>title: {title}</p>
                <button
                  onClick={(event) => {
                    handleDeleteBook(event, id);
                  }}
                >
                  Delete
                </button>
              </article>
            );
          })}
        </section>
      </div>
    );
  };

  export default App;

  // we can separate the reducer code
  ```

## [38. dynamic styling in react]

- **Code Example - 56 (dynamic styling)**

  ```js
  import React, { useState, useReducer, useEffect } from "react";
  import { reducer } from "./reducer";

  // books, modalText, isModalOpen
  // add book - modalText
  // remove book - modalText
  const dummyBooks = [
    { id: 1, title: "book1" },
    { id: 2, title: "book2" },
  ];
  const Modal = ({ modalText }) => {
    return <p>{modalText}</p>;
  };

  const initialState = {
    books: dummyBooks,
    isModalOpen: false,
    modalText: "",
  };

  const App = () => {
    // const [books, setBooks] = useState(dummyBooks);
    // const [modalText, setModalText] = useState('');
    // const [isModalOpen, setIsModalOpen] = useState(false);

    const error = true;

    const [bookState, dispatch] = useReducer(reducer, initialState);

    const [bookTitle, setBookTitle] = useState("");
    const [isValidTitle, setIsValidTitle] = useState(true);

    useEffect(() => {
      if (bookTitle.length < 2) {
        setIsValidTitle(false);
      } else {
        setIsValidTitle(true);
      }
    }, [bookTitle]);

    const handleTitleChange = (event) => {
      event.stopPropagation();
      setBookTitle(event.target.value);
    };
    const handleDeleteBook = (event, id) => {
      event.stopPropagation();
      dispatch({ type: "DELETE", payload: id });
    };

    const handleSubmit = (event) => {
      event.preventDefault();
      const newBook = { id: new Date().getTime().toString(), title: bookTitle };
      dispatch({ type: "ADD", payload: newBook });
      setBookTitle("");
    };

    return (
      <div>
        <form onSubmit={handleSubmit}>
          <input
            type="text"
            placeholder="enter book title"
            value={bookTitle}
            onChange={handleTitleChange}
            required
            style={{ backgroundColor: isValidTitle ? "" : "red" }}
          />
          <input
            type="text"
            placeholder="enter book title"
            value={bookTitle}
            onChange={handleTitleChange}
            required
            className={`${isValidTitle ? "valid" : "invalid"}`}
          />
          <p
            style={{
              color: error ? "red" : "green",
              backgroundColor: error ? "white" : "black",
            }}
          >
            Error
          </p>
          <button type="submit">Add Book</button>
        </form>

        {bookState.isModalOpen && <Modal modalText={bookState.modalText} />}

        <section className="books">
          {bookState.books.map((book) => {
            const { id, title } = book;
            return (
              <article key={id} className="book">
                <h2>id: {id}</h2>
                <p>title: {title}</p>
                <button
                  onClick={(event) => {
                    handleDeleteBook(event, id);
                  }}
                >
                  Delete
                </button>
              </article>
            );
          })}
        </section>
      </div>
    );
  };

  export default App;
  ```

## [39. react todo projects]

- [react todo project](https://github.com/anisul-Islam/react-todo-project)

## Part-6 (react routing)

- [react-routing-project](https://github.com/anisul-Islam/react-routing-project)
- react-router

## [40. Introduction to Routing](https://youtu.be/1_powatXjds)

## [41. Navigation and redirect](https://youtu.be/DooqgS1JDg0)

## [42. dynamic routing using useParams](https://youtu.be/g5B0Vq3jHbA)

## [43. useLocation hook](https://youtu.be/EKmr00ZKkCg)

## [44. route parameter, query parameter](https://youtu.be/uQtNSOUepVE)

## [44. https://youtu.be/MqFZ-tewuW0](https://youtu.be/MqFZ-tewuW0)

## Part-7 (CRUD Operations - http methods)

## [45. Read Users](https://youtu.be/gnHdHFqlfew)

## [46. Delete User](https://youtu.be/IX-1n_eHF0s)

## [47. Create User](https://youtu.be/JOAiEGOqAmo)

## [48. Update User](https://youtu.be/msrcslJPsjY)

## Part-8 (Optimization: React.memo(), useCallback(), useMemo())

## [40. react memo](https://youtu.be/pwh4oyGpVPk)

- It helps to avoid unnecessary components rendering

  ```js
       // App.js
       import React, { useState } from 'react';
        import Message from './components/Message';

        const App = () => {
          const [count, setCount] = useState(0);
          console.log('app rendering');
          return (
            <div>
              <h1>Welcome to Memo</h1>
              <h2>Count : {count}</h2>
              <button
                onClick={() => {
                  setCount((count) => count + 1);
                }}>
                Increment
              </button>
              <Message numberOfMessages={0} />
            </div>
          );
        };

        export default App;

    // Message.js
    import React, { memo } from 'react';
    import PropTypes from 'prop-types';
    const Message = (props) => {
      console.log('message rendering');
      return <div>Message {props.numberOfMessages}</div>;
    };

    Message.propTypes = {
      numberOfMessages: PropTypes.number
    };

    export default memo(Message);
  ```

## [41. useCallback Hook](https://youtu.be/t9qUJ0SRQuE)

- It helps to avoid unnecessary components rendering for defining callback methods
- only component will be rendered when some states or props change

  ```js
       // App.js
       import React, { useState, useCallback, useMemo } from 'react';
        import Message from './components/Message';

        const App = () => {
          const [count, setCount] = useState(0);
          console.log('app component rendering');

          const handleDataFromMessage = useCallback((data) => {
            console.log(data);
          }, []);

          return (
            <div>
              <h2>{numbers}</h2>
              <h2>Count : {count}</h2>
              <button
                onClick={() => {
                  setCount((count) => count + 1);
                }}>
                Increment
              </button>
              <Message onHandleDataFromMessage={handleDataFromMessage} />
            </div>
          );
        };

        export default App;


    // Message.js
    import React from 'react';
    import PropTypes from 'prop-types';
    const Message = ({ onHandleDataFromMessage }) => {
      console.log('message component rendering');
      onHandleDataFromMessage('hello I am from message component');
      return <div>Message</div>;
    };

    Message.propTypes = {
      onHandleDataFromMessage: PropTypes.func
    };

    export default React.memo(Message);

  ```

## [42. useMemo Hook](https://youtu.be/_namSWWPMeU)

- It helps to avoid taking unnecessary time for same kind of complex calculation for each rendering

  ```js
       // App.js
       import React, { useState, useCallback, useMemo } from 'react';
        import Message from './components/Message';

        const App = () => {
          const [count, setCount] = useState(0);
          console.log('app component rendering');

          const numbers = useMemo(() => {
            let number = 0;
            for (let index = 0; index < 5000000000; index++) {
              number++;
            }
            return number;
          }, []);

          return (
            <div>
              <h2>{numbers}</h2>
              <h2>Count : {count}</h2>
              <button
                onClick={() => {
                  setCount((count) => count + 1);
                }}>
                Increment
              </button>
            </div>
          );
        };

        export default App;


    // Message.js
    import React from 'react';
    import PropTypes from 'prop-types';
    const Message = ({ onHandleDataFromMessage }) => {
      console.log('message component rendering');
      onHandleDataFromMessage('hello I am from message component');
      return <div>Message</div>;
    };

    Message.propTypes = {
      onHandleDataFromMessage: PropTypes.func
    };

    export default React.memo(Message);

  ```

## Part-9 (props drilling, useContext Hook)

## [49. Props drilling](https://youtu.be/_JNIQXYSUu4)

## [50. useContext Hook](https://youtu.be/RYeRn5_xL7k)

## [51. Theme change project using useContext]

## Part-10 (redux, redex toolkit)

- check redux videos and then redux-toolkit
- how to use redux devtools

## [52. Counter App using Redux-toolkit](https://youtu.be/1aOGY0rRBQk)

## [53. Fetch data using Redux-toolkit](https://youtu.be/LoK2bQUPjsY)

## [54. Books CRUD APP using Redux-toolkit](https://youtu.be/No1FYwxK6Es)

- [Project's GitHub link](https://github.com/anisul-Islam/redux-toolkit-crud-app)

## Part-11 (React + Typescript)
