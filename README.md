# React Popover Wrapper
This is a simple wrapper that makes react-popover a little easier to use.

### Install
`npm install react-popover-wrapper --save`

This package is not yet compiled with babel so you will need to do that. If you are using webpack, set up your loaders to include this file (often webpack loaders will ignore npm).

```
  rules: [
      {
          test: /\.js$/,
          use: ['babel-loader'],
          exclude: /node_modules/
      },{
          test: /\.js$/,
          use: ['babel-loader'],
          include: [
              path.resolve(__dirname, 'node_modules/react-popover-wrapper'),
          ],
      },
  ```

### Example
```javascript
import Popover from 'react-popover-wrapper';

// Then add it to your react components JSX:

<Popover trigger="hover" preferPlace="above">
  <div>Trigger element</div>
  <div className="popover">
    <a>You can put your content here</a>
    <a>The second element will be treated as the popover content</a>
  </div>
</Popover>

```

Some basic CSS should be added. Something like this is a good place to start:
```CSS
.Popover-body {
  display: inline-flex;
  flex-direction: column;
  background: white;
  z-index: 1;
  margin-top: -1px;
  border: 1px solid rgba(0, 0, 0, 0.2);
}

.Popover-tipShape {
  fill: white;
  stroke-width: 1;
  stroke: rgba(0, 0, 0, 0.15);
}

.Popover {
  z-index: 100;
  transform: translateY(0px) !important;
}
```

### Usage
This component makes changing the trigger action very simple. There are several different attributes which can be used with this component:

---

The prefered location of the popover

Default: 'above'

`preferPlace: PropTypes.oneOf(['above', 'below', 'left', 'right'])`

---

Is the popover open? Often used with trigger === 'none' to control state externally

Default: undefined

`open: PropTypes.bool`

---

The type of event to trigger the popver

Default: 'click'

`trigger: PropTypes.oneOf(['click', 'hover', 'hoverDelay', 'hoverSingleDelay', 'none'])`

---

Toggle delay period. To be used with 'hoverDelay' or 'hoverSingleDelay'.

Default: 200

`toggleDelayTime: PropTypes.number`

---

This will stop the popup closing when the overlay is clicked.

Default: false

`disableClickClose: PropTypes.bool`

---

Size of the arrow.

Default: 6

`tipSize: PropTypes.number`

---


Should the popup content inherit the 'isOpen' prop?

Default: false

`inheritIsOpen: PropTypes.bool`

---

Two children should be passed in - children[0] is the trigger, children[1] is the popup content

`children: PropTypes.node.isRequired`
