---
title: "Building Reusable List Components in React"
datePublished: Tue Feb 27 2024 02:30:26 GMT+0000 (Coordinated Universal Time)
cuid: clt3r33h400010ajs92p7fsdz
slug: building-reusable-list-components-in-react
canonical: https://www.linkedin.com/pulse/building-reusable-list-components-react-annamalai-palani-gbsif%3FtrackingId=c0M7UdX1ntISkm4oUZXVqQ%253D%253D/?trackingId=c0M7UdX1ntISkm4oUZXVqQ%3D%3D
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/UYsBCu9RP3Y/upload/777b151afc68e4d998348758b01f1811.jpeg
tags: software-development, programming-blogs, reactjs

---

In React development, it's common to encounter scenarios where you need to display lists of similar components with varying styles or content. For instance, you might have a list of authors, each with different information like name, age, country, and books authored. To efficiently handle such cases, we can leverage React's component composition and props passing.

Let's consider a scenario where we have an array of authors, each represented by an object containing their details like name, age, country, and books they've written. We want to create two distinct styles for displaying these authors: a large card displaying all details including their books, and a smaller card with just the name and age.

Firstly, we define our array of authors:

```typescript
export const authors = [
  {
    name: "Sarah Waters",
    age: 55,
    country: "United Kingdom",
    books: ["Fingersmith", "The Night Watch"],
  },
  {
    name: "Haruki Murakami",
    age: 71,
    country: "Japan",
    books: ["Norwegian Wood", "Kafka on the Shore"],
  },
  {
    name: "Chimamanda Ngozi Adichie",
    age: 43,
    country: "Nigeria",
    books: ["Half of a Yellow Sun", "Americanah"],
  },
];
```

Next, we create our two different styles of author list items: LargeAuthorListItem and SmallAuthorListItem. The former displays all details including books, while the latter only shows name and age.

```typescript
export const LargeAuthorListItem = ({ author }) => {
  const { name, age, country, books } = author;
  return (
    <>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>Country: {country}</p>
      <p>
        Books:{" "}
        {books.map((book, index) => (
          <span key={index}>{book}</span>
        ))}
      </p>
    </>
  );
};

export const SmallAuthorListItem = ({ author }) => {
  const { name, age } = author;
  return (
    <>
      <h2>{name}</h2>
      <p>Age: {age}</p>
    </>
  );
};
```

Now, to make these components reusable and versatile, we create a RegularList component. This component takes in an array of items, a prop specifying the source of data (in our case, "author"), and the type of item component to render.

```typescript
export const RegularList = ({ items, sourceName, ItemComponent }) => {
  return (
    <>
      {items.map((item, index) => (
        <ItemComponent key={index} {...{ [sourceName]: item }} />
      ))}
    </>
  );
};
```

With RegularList, we can easily render lists of authors in different styles by passing in the appropriate item component and data source name. For example:

```typescript
import { authors, RegularList, LargeAuthorListItem, SmallAuthorListItem } from './components';

const App = () => {
  return (
    <div>
      <h1>Authors</h1>
      <h2>Large Cards</h2>
      <RegularList items={authors} sourceName="author" ItemComponent={LargeAuthorListItem} />
      <h2>Small Cards</h2>
      <RegularList items={authors} sourceName="author" ItemComponent={SmallAuthorListItem} />
    </div>
  );
};

export default App;
```

---

By utilizing these components, we can easily create and maintain lists of objects with different styles across our application. This approach promotes code reusability and maintainability, making our React application more efficient and scalable.