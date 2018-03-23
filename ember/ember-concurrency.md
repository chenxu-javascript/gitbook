# ember-concurrency

标签（空格分隔）： 并发  yield

---

ember-concurrency是一个可以轻松编写简洁，健壮且美观的异步代码的ember插件。

它为您提供了强大的任务原语（Task primitive），它具有以下优点：

- 与promise不同，task支持取消。

- task会暴露其基础状态（无论它们是正在运行还是空闲），这使得构建加载指示器时无需手动跟踪/变更状态变得微不足道。

- task修饰符使得阻止同一任务的两次执行同​​时运行变得微不足道，例如，您可以使用.drop（）修饰符防止双表单提交，也可以将任务配置为.restartable（），以便在单击“重新启动”按钮时重新开始。在没有任务的情况下实现这个逻辑需要大量的样板代码和防御性编程。

- 生活在组件上的任务在组件未被降级时会自动取消;没有更多，如果（this.isdestroyed）检查，以防止定时器或ajax响应导致“设置销毁对象”错误。

- and so on 


# Introduction to ember-concurrency

引入并发性为了演示ember-concurrency旨在解决的问题类型，我们将首先实现一个仅使用core ember apis在组件中加载数据的基本示例。那么我们将引入ember-concurrency任务作为重构的一部分。本教程（以及ember-concurrency本身）假设您已经熟悉了ember的核心API，特别是周围的组件，模板，操作和承诺。对于我们的用例，我们将实现一个获取并显示附近零售商店的组件。这涉及两步异步过程：