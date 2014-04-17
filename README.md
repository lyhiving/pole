Pole：前端开静态化解决方案
==========================
Pole是前端开发集成解决方案的一个组成部分，解决Web应用静态化开发调试的问题，将前后端工作解耦，使前端开发更加的专注在界面工程上。

在产品开发过程中，除纯静态单页Web应用之外，几乎都无法避免由页面动态化（将html转换成jsp或php）带来的一些问题：
* 本机前端开发环境复杂，至少需要部署两个开发环境，除前端环境之外，还额外需要一个动态环境，辅助jsp等动态页面开发调试；
* 对于开发者来说，前后端使用的模版不能通用，必须同时维护两套模版；
* 调试过程繁琐，尤其是在移动端开发，涉及到一些需要调用后端资源的功能，必须依赖后端环境才能完成调试；
* [GUI测试用例](http://baike.baidu.com/view/5131653.htm)难以维护，无法实现自动化GUI测试；

什么是静态化
------------
简单的说就是前端有一个静态开发环境，无需调用后端API获取数据，使用模拟数据开发者可以在静态环境下完成所有前端功能开发，将静态资源引用到动态环境后，动态环境获得与静态环境相同的功能和交互，后续也无需在动态环境下进行bug调试，在静态环境下同样能定位和还原bug。

静态化就是要创建一个这样的环境，解决前端开发和调试的问题。

为什么静态化
------------
推荐大家先阅读两篇檄文，虽然这两篇文章发布的时间比我启动Pole项目的时间稍晚，但文章描述的内容也是我正在思考的。
* [Web研发模式演变](https://github.com/lifesinger/lifesinger.github.com/issues/184)
* [前后端分离的思考与实践（一）](http://ued.taobao.org/blog/2014/04/full-stack-development-with-nodejs/#comment-12055)

对于Web开发来说，前后端一直是交织在一起的，尤其是在View与Controller两层上，无法避免这种开发模式产生的各种业务和沟通问题。
阿里系前端团队探索的是基于NodeJS的一种完全由前端掌控View与Controller的开发模式，技术架构复杂，前端面临的问题领域也从简单的View层扩展到View+Controller甚至Model层，为未来前端向全端的发展道路带了很多技术挑战。

Pole探索的是另一种更简单的开发模式——Web应用静态化，Pole并不希望改变现有的Web开发模式，而是使用静态化技术让Web应用可以在本机开发、调试和运行测试用例。这样做维持了前端开发面对的问题领域，同时也将前后端职责分得比较清晰。

Pole实现静态化
--------------
Pole不是独立存在的一个工具，只有将它融入到一个完整的前端开发集成环境中，才能真正发挥它的作用。Pole只是解决了Web应用静态花的问题，是开发者具备了在本机开发、调试和运行测试用例的能力。

实现Web应用静态化依赖Pole的两个能力：
* 使用[Pole Mock API](https://github.com/polejs/pole-mock)模拟后台数据接口实现纯静态化开发和调试；
* 使用Pole Compiler模块将静态HTML页面编译为后端可运行的JSP或PHP，实现前后端页面模版共享；

基于Pole的Web应用系统结构

![pole-structure](https://raw.github.com/maxzhang/maxzhang.github.com/master/articles/images/pole-structure.png)




