## Transition Animation on Scroll with Chakra UI and React

Chakra UI provides [four components](https://chakra-ui.com/docs/components/transitions) to help add transition animations. The components are named, `Fade`, `ScaleFade`, `Slide`, and `SlideFade`.

These components can be passed an "in" prop that accepts a boolean which determines whether or not to show the component and trigger the enter/exit state.

["react-visibility-sensor"](https://www.npmjs.com/package/react-visibility-sensor) is a component for React that makes it easy to assign a boolean to represent whether or not a DOM element is within the viewport.

[react-intersection-observer](https://www.npmjs.com/package/react-intersection-observer) provides similar functionality in this use case, and is a newer and actively maintained project with some additional features. Since this package utilizes a [built in browser API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API), it requires no additional dependencies. More on browser compatibility can be found at [caniuse.com](https://caniuse.com/intersectionobserver).

The following assumes you have an existing React project, with Chakra UI setup, but follow these links if you need help "[Getting Started with React (CRA)](https://create-react-app.dev/docs/getting-started/)" or "[Getting Started with Chakra UI](https://chakra-ui.com/docs/getting-started)"

## react-visibility-sensor

 First off, install react-visibility-sensor in your project;

```
npm install react-visibility-sensor
```

Import into your project;

```jsx
import VisibilitySensor from "react-visibility-sensor"
```

You can now wrap the element you wish to animate, and the Chakra UI transition component, in the VisibilitySensor component. You can then use an arrow function from within the VisibilitySensor component to access the `isVisible` variable.

```jsx
<VisibilitySensor offset={{bottom:200}} partialVisibility={true}>
    {({isVisible}) =>
        <Fade in={isVisible}>
            <YourElement />
        </Fade>
     }
</VisibilitySensor>
```
In this example the VisibilitySensor component is passed props for `offset` and `partialVisibility`. Check on npm for a [full list](https://www.npmjs.com/package/react-visibility-sensor#props) of all the options you can assign.

## react-intersection-observer

First off, install react-intersection-observer in your project;

```
npm install react-intersection-observer
```
Import into your project;

```jsx
import InView from "react-intersection-observer"
```
You can now wrap the element you wish to animate, and the Chakra UI transition component, in the InView component. You can then use an arrow function from within the InView component to access the `inView` variable. You must also include a `ref` prop on the element you will be observing.

```jsx
<InView rootMargin="-200px" triggerOnce={true}>
    {({inView, ref}) =>
        <Fade in={inView} >
            <YourElement ref={ref} />
        </Fade>
     }
</InView >
```
In this example the InView component is passed props for `rootMargin` and `triggerOnce`. Check on npm for a [full list](https://www.npmjs.com/package/react-intersection-observer#options) of all the options you can assign.

And there you have two methods of triggering transition animations using the built-in Chakra UI components.



