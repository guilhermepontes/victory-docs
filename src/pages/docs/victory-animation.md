---
id: 3
title: VictoryAnimation
category: core
scope: null
---
# VictoryAnimation

`VictoryAnimation` animates prop changes for any React component. Just use a child function inside `VictoryAnimation` that accepts an object of tweened values and other animation information and returns a component to render.

```jsx
<VictoryAnimation {...animationProps} data={myComponentProps}>
  {(tweenedProps, animationInfo) => {
    if (animationInfo.animating && animationInfo.progress < 1) {
      return <MyComponent {...tweenedProps}/>
    }
  }}
</VictoryAnimation>
```

## Props

### children

`VictoryAnimation` takes a single child, which should be given as a function of a tweened props object and an animation information object. The child function should return a component to render.

### data

The `data` prop specifies a set of values to tween between. When this prop changes, `VictoryAnimation` will begin animating between the current and next values. This prop should be given as an array or an object. `VictoryAnimation` uses [d3-interpolate] to tween between values, with some [slight modifications].

*examples:* `data={this.props}`

### duration

The `duration` prop determines the number of milliseconds the animation should take to complete. This prop should be given as a number.

*default:* `duration={1000}`

### delay

The `delay` prop specifies a delay in milliseconds before the start of an animation, or between each animation in the queue. This prop should be given as a number.

*default:* `delay={0}`

### easing

The `easing` prop specifies the type of easing to use for an animation. The supported types of easing are: *"back", "backIn", "backOut", "backInOut", "bounce", "bounceIn", "bounceOut", "bounceInOut", "circle", "circleIn", "circleOut", "circleInOut", "linear", "linearIn", "linearOut", "linearInOut", "cubic", "cubicIn", "cubicOut", "cubicInOut", "elastic", "elasticIn", "elasticOut", "elasticInOut", "exp", "expIn", "expOut", "expInOut", "poly", "polyIn", "polyOut", "polyInOut", "quad", "quadIn", "quadOut", "quadInOut", "sin", "sinIn", "sinOut", "sinInOut"*.

*default:* `easing="quadInOut"`

### onEnd

The `onEnd` prop specifies a function that will be called when the animation ends. If there are multiple animations in the queue, the `onEnd` function will be called after the last animation in the queue completes.

[d3-interpolate]: https://github.com/d3/d3-interpolate
[slight modifications]: https://github.com/FormidableLabs/victory-core/blob/master/src/victory-animation/util.js