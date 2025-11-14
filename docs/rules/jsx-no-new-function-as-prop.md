# Prevent `function` as JSX prop values (jsx-no-new-function-as-prop)

Prevent Functions that are local to the current method from being used as values of JSX props

## Rule Details

The following patterns are considered warnings:

```jsx
<Item callback={function() {}} />

<Item callback={() => {}} />

<Item callback={new Function(...)} />

<Item callback={Function(...)} />

<Item callback={this.props.callback || function() {}} />

<Item callback={this.props.callback ? this.props.callback : function() {}} />
```

The following patterns are not considered warnings:

```jsx
<Item callback={this.props.callback} />
```

## Options

### allowComponents

You can disable the rule for specific components by providing their names via `allowComponents`:

```json
{
  "react-perf/jsx-no-new-function-as-prop": [
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
  "react-perf/jsx-no-new-function-as-prop": [
    "error",
    {
      "nativeAllowList": ["style"]
    }
  ]
}
```
