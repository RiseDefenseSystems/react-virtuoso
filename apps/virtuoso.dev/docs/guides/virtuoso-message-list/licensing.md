---
id: virtuoso-message-list-licensing
title: Virtuoso Message List Licensing
sidebar_label: Licensing
sidebar_position: 3
slug: /virtuoso-message-list/licensing
---

# Virtuoso Message List Licensing

The `@virtuoso.dev/message-list` package is distributed under a commercial license. You need to obtain a license to use the package in a production environment. Purchasing a license grants you one year of access to the latest versions of the package, including email-based support, bug fixes and new features. Licenses are annual, per-developer.

## License Seats Explained

The number of licenses to **the maximum number of concurrent front-end developers** who contribute to a project that uses the package. This also includes developers who work on the project part-time or as contractors. 

For example, your app uses the `VirtuosoMessageList` component for building an AI Chatbot interface. **Three front-end** and two back-end developers are working on the project.  One developer develops and maintains the message list UI feature, but there are three developers in total who work on the front-end. You must purchase **three licenses** for the project.

Another example: An UI development team in your company creates and maintains an internal UI library which includes the `VirtuosoMessageList`. The teams working on Project X and Project Y are both using the library. Project X has **three developers**, and Project Y has **two**. There are **two front-end developers** in the library team. In this case, you need to purchase 3 + 2 + 2 = **seven licenses**.

Purchasing a license lets you actively use and develop projects with the component for the duration of the license. It also grants you access to the versions of the component released for the duration of the license. 

Production deployments that **include a valid (even expired) license key are working without any restrictions perpetually**, as long as they are not using a version that's released after the key expiration date.

## Trial / Evaluation

In accordance with the [End User License Agreement](/message-list-eula/), you can use the component without a commercial license for 30 days for non-production environments and for evaluation purposes. You can also use it for the development of code not intended for production uses.

## License Key

When you purchase a commercial license, you'll receive a license key by email. Adding the key to the component removes the console warnings and unblocks the component for production use.

The license key is a string that you need to pass as a prop to the `VirtuosoMessageListLicense` component, that should wrap any instance of the `VirtuosoMessageList` component in your application. 
```tsx
<VirtuosoMessageListLicense licenseKey="your-license-key">
  { /* Your application code */ }
  <VirtuosoMessageList  />
  { /* Your application code */ }
</VirtuosoMessageListLicense>
```

### Next.js/SSR

The license component is using a context to pass the license to the `VirtuosoMessageList` component, so you need to ensure that it is not rendered server-side only.

### Why do I need a license key?

By using the license key, you are compliant with the EULA. While each developer needs to be licensed, the license key is set once per project using the component.

## License key security

The license key is validated without any network requests, so you can safely use it in restricted environments. It's expected that the license key will be exposed in a JavaScript bundle; However, you are not encouraged to actively publicize your license key - discovering such keys is a violation of the EULA and will lead to the revocation of the license and any associated support.

## License key validation failures

### No license wrapper component

The `VirtuosMessageListLicense` component will throw an error and render an error unless wrapped with a `VirtuosoMessageListLicense` component. For development/evaluation purposes, you need to wrap one, even with an empty key prop. This will allow you to use the component without a license key for 30 days, keeping an error message in the developer console as a reminder. 

### Missing key

You can use the component without a license key for 30 days for non-production environments and for evaluation purposes - a message in the console will remind you that you have to add the key. If the component is deployed to production without a license key, it will render as an error message in the browser and an error in the console.

### Invalid key

If the key string is invalid, the component will render as an error message in the browser and an error in the console. Check that you have copy-pasted the key from the email correctly.

### Expired key

The error indicates that your annual license has expired. Your production deployments will continue to work without any restrictions perpetually, as long as they are not using a version that's released after the key expiration date. However, you can no longer develop new features or fix bugs with the component using an expired key. 

To solve the issue, you need to renew your license. 

### Expired key in production

The error means that your production deployment is using a version of the package that's published after the key expiration date. You need to downgrade the package to the latest version that was released before the key expiration date. If you wish to use a newer version, you need to renew your license.
