# Prevent `{...}` as JSX prop values (jsx-no-new-object-as-prop)

Prevent Objects that are local to the current method from being used as values of JSX props

## Rule Details

The following patterns are considered warnings:

```jsx
<Item config={{}} />

<Item config={new Object()} />

<Item config={Object()} />

<Item config={this.props.config || {}} />

<Item config={this.props.config ? this.props.config : {}} />

<div style={{display: 'none'}} />
```

The following patterns are not considered warnings:

```jsx
<Item config={staticConfig} />
```

## Options

### allowComponents

You can disable the rule for specific components by providing their names via `allowComponents`:

```json
{
  "react-perf/jsx-no-new-object-as-prop": [
    "error",
    {
      "allowComponents": ["CustomButton", "Layout.Item"]
    }
  ]
}
```

### nativeAllowList

Use `nativeAllowList` to ignore native elements (those that start in lowercase). For example, this configuration ignores `style` attributes on native elements:

```json
{
  "react-perf/jsx-no-new-object-as-prop": [
    "error",
    {
      "nativeAllowList": ["style"]
    }
  ]
}
```
