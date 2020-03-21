# Tips

## Working with styled components

In order to find a styled component in a ```shallow```, import the styled component and pass it as the selector argument to ```find()```. Alternatively, you can use a data test attribute (e.g., ```<div data-test="component-to-select" />```). Because of the way the component tree is rendered in ```shallow```, it is not possible to use a standard ```html``` tag as the selector: ```find()``` will return zero components; however, it is possible to use it with ```mount```.


```js
// Component.jsx

const SomeComponent = styled.div`
`;

export const Label = styled.span` 
`;

const Component = () =>
  <SomeComponent>
    <Label />
    <Label /> 
    <Label />
  </SomeComponent>;

export default Component;

// Component.test.jsx

import Component, { Label } from './Component';

describe('<Component />', () => {
  it('should contain a Label', () => {
    const wrapper = shallow(<Component />);
    const label = wrapper.find(Label);
    expect(label.length).toBe(3);
  });
});
```