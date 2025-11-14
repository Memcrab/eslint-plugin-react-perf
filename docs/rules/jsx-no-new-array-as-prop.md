# Prevent `[...]` as JSX prop values (jsx-no-new-array-as-prop)

Prevent Arrays that are local to the current method from being used as values of JSX props

## Rule Details

The following patterns are considered warnings:

```jsx
<Item list={[]} />

<Item list={new Array()} />

<Item list={Array()} />

<Item list={this.props.list || []} />

<Item list={this.props.list ? this.props.list : []} />
```

The following patterns are not considered warnings:

```jsx
<Item list={this.props.list} />
```

## Options

### allowComponents

You can disable the rule for specific components by providing their names via `allowComponents`:

```json
{
  "react-perf/jsx-no-new-array-as-prop": [
    "error",
    {
      "allowComponents": ["CustomList", "Layout.Item"]
    }
  ]
}
```

### nativeAllowList

Use `nativeAllowList` to ignore native elements (those that start in lowercase). For example, this configuration ignores `style` attributes on native elements:

```json
{
  "react-perf/jsx-no-new-array-as-prop": [
    "error",
    {
      "nativeAllowList": ["style"]
    }
  ]
}
```
