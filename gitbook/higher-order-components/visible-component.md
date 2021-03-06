# `VisibleComponent` / `isVisibleComponent`

* Wrapped components will be checked against the activeModules array of the state: If the wrapped component (identified by it's name) is included in the state, it will be rendered, if not, it wont.

```
import React from 'react';
import { render } from 'react-dom';
import { Button } from 'antd';
import { isVisibleComponent } from '../../index.js';

// Enhance (any) Component by wrapping it using isVisibleComponent().
const VisibleButton = isVisibleComponent(Button);

// The activeModules is a whitelist of components (identified by it's names) to
// render.
const activeModules = [{
  name: 'visibleButtonName'
}, {
  name: 'anotherVisibleButtonName'
}];

render(
  <div>
    <VisibleButton
      name="visibleButtonName"
      activeModules={activeModules}
      type="primary"
      shape="circle"
      icon="search"
    />
    <VisibleButton
      name="notVisibleButtonName"
      activeModules={activeModules}
      type="primary"
      shape="circle"
      icon="search"
    />
    <VisibleButton
      name="anotherVisibleButtonName"
      activeModules={activeModules}
      type="primary"
      shape="circle"
      icon="poweroff"
    />
  </div>,
  document.getElementById('exampleContainer')
);
```
