---
id: virtuoso-message-list-hooks
title: Virtuoso Message List Hooks
sidebar_label: Hooks
sidebar_position: 7
slug: /virtuoso-message-list/hooks
---

# Hooks

You can access the message list's internal state and methods by calling hooks inside the inner components. The message list component exposes the following hooks:

* `useVirtuosoMethods` - the equivalent of the `ref` prop, which gives you access to the message list methods. 
* `useVirtuosoLocation` - gives you access to the current `ListScrollLocation`.
* `useCurrentlyRenderedData` - gives you access to the currently rendered data items. Useful if you want to display information for the first or last rendered item.

:::info
The `useVirtuosoMethods` hook exposes several data operations. To make it type-safe, you should pass the type of data and the context you're using in the message list as a type parameters. 

```tsx
// For a message list with items of type { message: string } and context of type { user: string }
const methods = useVirtuosoMethods<{message: string}, {user: string}>()
```
:::

Both hooks are used in the tutorial to implement [the scroll to bottom button](/virtuoso-message-list/tutorial/scroll-to-bottom-button).
