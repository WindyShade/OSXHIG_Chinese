# 反馈与帮助

## 让用户了解进度

一个应用应该除了要响应用户的指令和动作，还得告知用户一个任务的执行需要多长时间。如果你的应用没有很好的进度反馈，那用户可能会认为你的应用死掉了，没响应了。

![image](images/OSX_HIG_001_023.png)

**即时响应用户的指令和输入。** 用户希望在与应用交互的过程中能够得到持续的反馈，比如 OS X 的按钮就能够在用户点击鼠标的时候给出视觉反馈，鼠标指针也会在进入不同的控件或者区域的时候有不同的样式。同样的，如果一项任务要花比较长的时间来完成，这时候用户需要知道为什么这个任务没法立刻出结果，而且要知道他还可以做什么。对用户的动作反馈得越快，给用户的感觉就越流畅。更多关于反馈的设计原则，请参见[反馈与交流]()一章。

	提示：
	动画可以很好地告知用户他们能做什么，以及他们的动作能带来什么影响。关于动画，请参见[动画]()一章。
	
**不要等到一项耗时较长的任务完成后才展示结果。** 如果在任务完成前一直展示空白，就会让用户感觉你这个应用太慢，太迟钝了。所以，你应该要一边执行任务一边展示已经得到的那部分结果，这样用户可以在任务完成前先获得一部分有用的信息。（译者注：比如实时搜索，搜到的结果先展示，没搜到的继续保持加载状态，等到全部搜完了才出现所有结果。）

**使用指示器来帮助用户估算剩余时间。** 并不是每一项任务都需要给出精确的预估时间，但是多数情况下还是要给出大概的剩余时间的。比如 Finder 的复制功能，就同时使用了进度条和文字说明来告诉用户还需要多长时间来完成复制。

**对于可能产生意外而造成数据丢失的危险操作，一定要发出警告。** 这种警告是必须的，但是不能太频繁，否则用户就会习惯性忽略这种警告了。但是如果用户很明确就要做删除操作的，数据丢失就是用户所期望的，这种时候就不要给出警告。比如 Finder， 在用户删除文件的时候就没有弹出警告，因为用户本来就要删掉这些文件。关于如何在应用中使用警告，请参见[警告]()一章。

	提示：
	如果你的应用有一个前台线程用来展示界面，一个后台线程用来处理各种主要逻辑，你要确保跟用户所有的交互都是由前台界面线程发起的。因为用户可能并不知道后台线程的存在，如果后台线程突然跑出来一个弹框用户就会觉得很迷惑。所以如果一个后台线程必须跟用户交互的时候，应该要启动前台线程，把主窗口激活然后再做下一步界面展示。（译者注：iOS 所有的界面刷新动作都必须在主线程做，否则无效。）
	
## 有些时候，用户需要帮助信息

理想情况下，用户不需要阅读说明书就可以轻松地使用你应用，但是现实是当用户需要使用高级功能或者较为隐蔽的功能的时候，所以我们还是需要一些帮助信息来告知用户这些复杂功能的用法。下面一节主要讲怎么在不妨碍用户操作的同时做好帮助信息。关于帮助的更多信息，请参考[辅助功能]()一章；关于欢迎页的设计，请参考[快速启动]()一章。

**多数时候我们可以用悬浮标签来指示一个控件的用法。** 当鼠标在控件上悬停数秒后，可以弹出悬浮标签，这个标签包含了由一个很小的浮动视图和一个简短的说明组成（如下图字典应用的标签）。当然理想的做法是让控件设计到一眼就能看出是用来干啥的，但是这种悬浮标签既展示了提示，又不影响使用，也不失为一个提供帮助信息的好办法。由于悬浮标签的说明比较简短，同时也是跟一个控件绑定在一起的，所以这种控件就不太适于用来提示更加复杂的操作。

![image](images/OSX_HIG_001_024.png)

**所以更复杂的操作，我们可以提供帮助文档。**当然你也可以在帮助文档里面提供某个控件的具体用法，不过鉴于多数用户都希望从帮助文档里面找到高级任务的指引，你还是从复杂任务的角度来编排这份文档比较好。

**多数情况下，都要避免限制用户的操作。** 除非你做的是一个儿童应用，有个家长监控模式来限制儿童用户，不然还是要尽量避免不必要的限制。