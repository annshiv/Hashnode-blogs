---
title: "Creating Reusable Modal Components in React"
datePublished: Wed Feb 28 2024 02:30:24 GMT+0000 (Coordinated Universal Time)
cuid: clt56iwhx000809jq1dohdyl2
slug: creating-reusable-modal-components-in-react
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/tZc3vjPCk-Q/upload/8091999d2b56f3f1b198ccb96e00758b.jpeg
tags: design-patterns, architecture, developer

---

Modal components are pop-up windows that overlay the current page, allowing users to interact with content or controls without leaving the context of the application. They are commonly used for tasks such as displaying alerts, confirming actions, or presenting additional information.

**Creating the Modal Component**

We'll start by creating a new file named `Modal.jsx` inside the src/components directory. This file will contain the logic and styles for our modal component. Here's the code for `Modal.jsx`

```typescript
import { useState } from "react";
import styled from "styled-components";

const ModalBackground = styled.div`
  position: fixed;
  left: 0;
  top: 0;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
`;

const ModalContent = styled.div`
  background-color: white;
  padding: 20px;
  border-radius: 5px;
`;

export const Modal = ({ children }) => {
  const [show, setShow] = useState(false);

  return (
    <>
      <button onClick={() => setShow(true)}>Open Modal</button>
      {show && (
        <ModalBackground onClick={() => setShow(false)}>
          <ModalContent onClick={(e) => e.stopPropagation()}>
            <button onClick={() => setShow(false)}>Close Modal</button>
            {children}
          </ModalContent>
        </ModalBackground>
      )}
    </>
  );
};
```

**Using the Modal Component**

Now that we've created our modal component, let's use it in our main application. Open the App.js file in the src directory and replace its content with the following code:

```typescript
import React from "react";
import { Modal } from "./components/Modal";

function App() {
  return (
    <div className="App">
      <Modal>
        <h2>Hello, Modal!</h2>
        <p>This is a simple modal component created in React.</p>
      </Modal>
    </div>
  );
}

export default App;
```

---

Modals are versatile elements that can enhance the user experience by providing contextually relevant information or actions. You can further customize the modal component by adding animations, additional styling, or functionality to suit your application's needs. Feel free to experiment and expand upon the concepts covered in this tutorial to create unique and engaging modal experiences for your applications.