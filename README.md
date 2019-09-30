# react-three-gui

A graphical user interface for changing variable states in React.

## Examples

https://codesandbox.io/s/react-three-fiber-gui-62pvp

## Usage

Basic example

```tsx
import { Controls, useControl } from 'react-three-gui';

export const App = () => {
  const rotationX = useControl('Rotation X', { type: 'number' });
  return (
     <>
       <Canvas>
         <mesh rotation-x={rotationX} />
       </Canvas>
       <Controls />
     </>
   );
};
```

Also possible to pass in your own state:
```tsx
const [value, set] = useState(0);

useControl('Adjust value', {
  type: 'number',
  state: [value, set],
});
```

Also you can pass your own control component:
```tsx
const MyControl = ({ control, value }) => (
  <input
    type="number"
    onChange={e => control.set(e.currentTarget.value)}
    value={value}
  />
);

useControl('Test', { value: 2, component: MyControl });
```

### Supported controls
- number
- xypad
- boolean
- button
- color
- select

### Future plans

- [x] Support custom control components
- [ ] Support passing refs and directly manipulate THREE objects
- [ ] Groups
- [x] Draggable Widget
- [ ] Collapsable widget
- [ ] Multi platform?