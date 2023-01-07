### Mistake 1
**Invoking Component Function Directly**

**WRONG:**
```tsx
return (<>
	<div>
		{CustomComponent()}
	<div>
</>)
```

**Why?**
It messes with the state rendering. If CustomComponent has to re-render, the whole app will render and not just the custom component.

**CORRECT:**
```tsx
return (<>
	<div>
		<CustomComponent />
	<div>
</>)
```

### Mistake 2
**Component in Component**

If a component is only used once in another component, don't just add it to the component using it. Rather just abstract everything out.

This has performance implications, React doesn't always know how to handle it.

### Mistake 3
**Locally Invoked Component Functions**

**WRONG**
```tsx
return (
	<>
		{(
			() => <h1>My App</h1>
		)}
	</>
)
```
Combination of both mistakes.

