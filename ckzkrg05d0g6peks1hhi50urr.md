## Simple Scroll Transition Animation using Chakra UI with React

Chakra UI provides [four components](https://chakra-ui.com/docs/components/transitions) to help add transition animations using framer-motion. The components are named, `Fade`, `ScaleFade`, `Slide`, and `SlideFade`.

All of these four components can be passed an "in" prop that accepts a boolean which determines whether or not to show the component and trigger the enter/exit state.


["React Visibility Sensor"](https://www.npmjs.com/package/react-visibility-sensor) is a sensor component for React that makes it easy to assign a boolean to represent whether or not a component is within the viewport.

The following assumes you have an existing React project, with Chakra UI installed, but follow these links if you need help "[Getting Started with React (CRA)](https://create-react-app.dev/docs/getting-started/)" or "[Getting Started with Chakra UI](https://chakra-ui.com/docs/getting-started)"

 First off install react-visibility-sensor in your React project;

```
npm install react-visibility-sensor
```

Import into your project;

```jsx
import VisibilitySensor from "react-visibility-sensor"
```


You can now wrap the component you wish to animate, and the Chakra UI transition component, in the VisibilitySensor. You can then use an arrow function from within the sensor component to access the `isVisible` variable.

```jsx
<VisibilitySensor offset={{bottom:200}} partialVisibility={true}>
    {({isVisible}) =>
        <Fade in={isVisible}>
            <YourComponent />
        </Fade>
     }
</VisibilitySensor>
```
In this example the VisibilitySensor component is passed props for offset and partialVisibility. Check on npm for a [full list](https://www.npmjs.com/package/react-visibility-sensor#props) of all the props you can assign to the sensor


