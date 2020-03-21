# Centering elements

## With flexbox

```css
.parent {
    display: flex;
    flex-direction: column;
    justify-content: center;
}
```

## Without flexbox

```css
.parent { 
    position: relative;
}

.child {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```