---
layout: page
title: React 18
permalink: /
---

# Welcome to React 18.2.0

![assets/img/react_logo.png](assets/img/react_logo.png "React blog")
- Automatic Batching 같은 즉시 사용 가능한 개선사항
- startTransition 같은 New API, Concurrent 기능 추가
- Suspense를 지원하는 스트리밍 서버 사이드 렌더링(Suspense와 React.lazy 지원)
- ReactDOM.render()가 Deprecated, ReactDOM.createRoot() API 대체

> React 18의 많은 기능은 새로운 Concurrent 렌더러를 기반으로 한다.
 Concurruent React는 옵트인이고  Concurrent 기능을 사용할 때만 활성화되지만  애플리케이션을 빌드하는 방식에는 큰 영향을 미칠 것이다.


## Features

Technically, concurrent rendering is a breaking change. Because concurrent rendering is interruptible, components behave slightly differently when it is enabled.

In our testing, we’ve upgraded thousands of components to React 18. What we’ve found is that nearly all existing components “just work” with concurrent rendering, without any changes. However, some of them may require some additional migration effort. Although the changes are usually small, you’ll still have the ability to make them at your own pace. The new rendering behavior in React 18 is *only enabled in the parts of your app that use new features.*

The overall upgrade strategy is to get your application running on React 18 without breaking existing code. Then you can gradually start adding concurrent features at your own pace. You can use <StrictMode> to help surface concurrency-related bugs during development. Strict Mode doesn’t affect production behavior, but during development it will log extra warnings and double-invoke functions that are expected to be idempotent. It won’t catch everything, but it’s effective at preventing the most common types of mistakes.

After you upgrade to React 18, you’ll be able to start using concurrent features immediately. For example, you can use startTransition to navigate between screens without blocking user input. Or useDeferredValue to throttle expensive re-renders.

However, long term, we expect the main way you’ll add concurrency to your app is by using a concurrent-enabled library or framework. In most cases, you won’t interact with concurrent APIs directly. For example, instead of developers calling startTransition whenever they navigate to a new screen, router libraries will automatically wrap navigations in startTransition.

It may take some time for libraries to upgrade to be concurrent compatible. We’ve provided new APIs to make it easier for libraries to take advantage of concurrent features. In the meantime, please be patient with maintainers as we work to gradually migrate the React ecosystem.

For features, getting started with development, see the {% include doc.html name="Getting Started" path="getting-started" %} page. Would you like to request a feature or contribute?
[Open an issue]({{ site.repo }}/issues)
