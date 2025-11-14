# Prevent JSX as JSX prop values (jsx-no-jsx-as-prop)

Prevent JSX that are local to the current method from being used as values of JSX props

## Rule Details

The following patterns are considered warnings:

```jsx
<Item jsx={<SubItem />} />

<Item jsx={this.props.jsx || <SubItem />} />

<Item jsx={this.props.jsx ? this.props.jsx : <SubItem />} />
```

The following patterns are not considered warnings:

```jsx
<Item callback={this.props.jsx} />
```

## Options

### allowComponents

You can disable the rule for specific components by providing their names via `allowComponents`:

```json
{
  "react-perf/jsx-no-jsx-as-prop": [
    "error",
    {
      "allowComponents": ["CustomItem", "Layout.Item"]
    }
  ]
}
```

### nativeAllowList

Use `nativeAllowList` to ignore native elements (those that start in lowercase). For example, this configuration ignores `style` attributes on native elements:

```json
{
  "react-perf/jsx-no-jsx-as-prop": [
    "error",
    {
      "nativeAllowList": ["style"]
    }
  ]
}
```
