---
title: "Building Reusable Split Screen Layouts in React"
datePublished: Mon Feb 26 2024 02:30:31 GMT+0000 (Coordinated Universal Time)
cuid: clt2bnctm00060al38wphbd7e
slug: building-reusable-split-screen-layouts-in-react
canonical: https://www.linkedin.com/pulse/building-reusable-split-screen-layouts-react-annamalai-palani-t8g8c%3FtrackingId=cJdfbZ7ee9J%252F8KDgiGLoQg%253D%253D/?trackingId=cJdfbZ7ee9J%2F8KDgiGLoQg%3D%3D
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/aI4RJ--Mw4I/upload/69f5467d6444f11aed62f488d2accaa4.jpeg
tags: software-development, reactjs, typescript

---

Split screen layouts are commonly used in web applications to display content side by side. Whether it's comparing two pieces of information or simply organizing content more efficiently, split screen layouts can improve the user experience.

### Basic Split Screen Component

Let's begin by creating a basic version of the SplitScreen component:

```typescript
import React from 'react';
import styled from 'styled-components';

const Container = styled.div`
  display: flex;
`;

const Panel = styled.div`
  flex: ${props => props.flex};
`;

const SplitScreen = ({ Left, Right }) => {
  return (
    <Container>
      <Panel flex={1}>
        {Left}
      </Panel>
      <Panel flex={1}>
        {Right}
      </Panel>
    </Container>
  );
};

export default SplitScreen;
```

In this component:

* We define a Container styled component to hold our split screen layout.
    
* Two Panel styled components are used to represent the left and right sections of the split screen.
    
* The SplitScreen component takes Left and Right props, which are components to be displayed in the left and right sections respectively.
    

### Enhanced Split Screen Component

Now, let's enhance our SplitScreen component to make it more flexible by allowing custom widths for the left and right sections:

```typescript
import React from 'react';
import styled from 'styled-components';

const Container = styled.div`
  display: flex;
`;

const Panel = styled.div`
  flex: ${props => props.flex};
`;

const SplitScreen = ({ children, leftWidth, rightWidth }) => {
  const [left, right] = children;

  return (
    <Container>
      <Panel flex={leftWidth}>
        {left}
      </Panel>
      <Panel flex={rightWidth}>
        {right}
      </Panel>
    </Container>
  );
};

export default SplitScreen;
```

In this enhanced version:

* We modify the SplitScreen component to accept children, leftWidth, and rightWidth props.
    
* The children prop allows us to pass components directly as children to the SplitScreen component.
    
* leftWidth and rightWidth props determine the widths of the left and right sections respectively.
    

### Example Usage

Now, let's see how we can use our SplitScreen component in a React application:

```typescript
import React from 'react';
import SplitScreen from './SplitScreen';

const LeftComponent = ({ title }) => {
  return <h2>{title}</h2>;
};

const RightComponent = ({ title }) => {
  return <h2>{title}</h2>;
};

function App() {
  return (
    <SplitScreen leftWidth={1} rightWidth={3}>
      <LeftComponent title={"Left"} />
      <RightComponent title={"Right"} />
    </SplitScreen>
  );
}

export default App;
```

In this example:

* We import the SplitScreen component.
    
* We define LeftComponent and RightComponent as functional components to be displayed in the left and right sections respectively.
    
* Inside the App component, we use the SplitScreen component and pass LeftComponent and RightComponent as children. We also specify custom widths for the left and right sections.
    

---

By following this approach, you can easily incorporate split screen layouts into your React applications, making them more structured and user-friendly. Feel free to customize the component further to suit your specific needs and styling preferences. Always expecting your support and suggestions ! Thanks in advance