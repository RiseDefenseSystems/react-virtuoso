---
id: virtuoso-message-list-resize-observer-errors
title: Virtuoso Message Resize Observer Errors
sidebar_label: Resize Observer Errors
sidebar_position: 10
slug: /virtuoso-message-list/resize-observer-errors
---

# Resize Observer Errors

The Message List component uses the Resize Observer API to measure the size of its items. The observer report is handled synchronously, which causes Safari, Webpack in dev mode, or error trackers like Sentry
to catch errors like `ResizeObserver loop limit exceeded` or `ResizeObserver loop completed with undelivered notifications`. Those errors are benign and can be safely ignored.

## Ignore Resize Observer Errors in Webpack (dev mode)

To ignore Resize Observer errors in Webpack dev server overlay, you can add the following code to your Webpack configuration. More details can be found in the [Webpack documentation](https://webpack.js.org/configuration/dev-server/#overlay).

```javascript
{
  //...
  devServer: {
    client: {
      overlay: {
        errors: false,
        warnings: false,
        runtimeErrors: (error: Error) => {
          if (error.message.includes("ResizeObserver loop")) {
            return false;
          } else {
            return true;
          }
        },
      },
    },
  },
}
```

## Ignore Resize Observer Errors in Sentry

[The following Sentry blog post](https://sentry.io/answers/react-resizeobserver-loop-completed-with-undelivered-notifications/) explains how to ignore Resize Observer errors in Sentry.
