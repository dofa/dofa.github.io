---
layout: post
title: "Angularjs学习笔记-动态模板"
date: 2014-04-07 16:10:10 -0700
comments: true
categories: Javascript
tags: javascript, Angularjs
---

AngularJS应用使用模型-视图-控制器（MVC）模式解耦代码和分离关注点。

## 视图和模板

在`AngularJS`中，一个视图是模型通过HTML**模板**渲染之后的映射。这意味着，不论模型什么时候发生变化，`AngularJS`会实时更新结合点，随之更新视图。

视图组件被AngularJS用下面这个模板构建出来:

`app/index.html`:

	<html ng-app="phonecatApp">
	<head>
	  ...
	  <script src="../bower_components/angular/angular.js"></script>
	  <script src="js/controllers.js"></script>
	</head>
	<body ng-controller="PhoneListCtrl">
	 
	  <ul>
	    <li ng-repeat="phone in phones">
	      {{phone.name}}
	      <p>{{phone.snippet}}</p>
	    </li>
	  </ul>
	 
	</body>
	</html>

我们刚刚把静态编码的手机列表替换掉了，因为这里我们使用`ngRepeat`指令和两个用花括号包裹起来的`AngularJS`表达式——`{{phone.name}}`和`{{phone.snippet}}`——能达到同样的效果。

在`<li>`标签里面的`ng-repeat="phone in phones"`语句是一个`AngularJS`迭代器。这个迭代器告诉`AngularJS`用第一个`<li>`标签作为模板为列表中的每一部手机创建一个`<li>`元素。
正如我们在第0步时学到的，包裹在`phone.name`和`phone.snippet`周围的花括号标识着数据绑定。和常量计算不同的是，这里的表达式实际上是我们应用的一个数据模型引用，这些我们在`PhoneListCtrl`控制器里面都设置好了。

## 模型和控制器

在`PhoneListCtrl`控制器里面初始化了数据模型（这里只不过是一个包含了数组的函数，数组中存储的对象是手机数据列表）：

`app/js/controller.js:`
 
	var phonecatApp = angular.module('phonecatApp', []);
	 
	phonecatApp.controller('PhoneListCtrl', function ($scope) {
	  $scope.phones = [
	    {'name': 'Nexus S',
	     'snippet': 'Fast just got faster with Nexus S.'},
	    {'name': 'Motorola XOOM™ with Wi-Fi',
	     'snippet': 'The Next, Next Generation tablet.'},
	    {'name': 'MOTOROLA XOOM™',
	     'snippet': 'The Next, Next Generation tablet.'}
	  ];
	});

尽管控制器看起来并没有起到什么控制的作用，但是它在这里起到了至关重要的作用。通过给定我们数据模型的语境，控制器允许我们建立模型和视图之间的数据绑定。我们是这样把表现层，数据和逻辑部件联系在一起的：

* `PhoneListCtrl`——控制器方法的名字（在JS文件`controllers.js`中）和`<body>`标签里面的`ngController`指令的值相匹配。
* 手机的数据此时与注入到我们控制器函数的作用域（`$scope`）相关联。当应用启动之后，会有一个根作用域被创建出来，而控制器的作用域是根作用域的一个典型后继。这个控制器的作用域对所有`<body ng-controller="PhoneListCtrl">`标记内部的数据绑定有效。

`AngularJS`的作用域理论非常重要：一个作用域可以视作模板、模型和控制器协同工作的粘接器。`AngularJS`使用作用域，同时还有模板中的信息，数据模型和控制器。这些可以帮助模型和视图分离，但是他们两者确实是同步的！任何对于模型的更改都会即时反映在视图上；任何在视图上的更改都会被立刻体现在模型中。	

## 测试

“AngularJS方式”让开发时代码测试变得十分简单。让我们来瞅一眼下面这个为控制器新添加的单元测试：

`test/unit/controllersSpec.js:`

	describe('PhoneCat controllers', function() {

	  describe('PhoneListCtrl', function(){

	    it('should create "phones" model with 3 phones', function() {
	      var scope = {},
	      ctrl = new PhoneListCtrl(scope);

	      expect(scope.phones.length).toBe(3);
	    });
	  });
	});

The test instantiates `PhoneListCtrl` and verifies that the phones array property on the scope contains three records. This example demonstrates how easy it is to create a unit test for code in Angular. Since testing is such a critical part of software development, we make it easy to create tests in Angular so that developers are encouraged to write them.

Note: 进入下一步之前要安装`karma`

	npm install -g karma

出现问题试试下面的命令：

	npm install -g karma-cli

	npm install -g zeparser

	npm install npm -g

	npm config set strict-ssl false

另外注意看`debug.log`查看缺失的包，然后安装上去	


## Testing non-Global Controllers

In practice, you will not want to have your controller functions in the global namespace. Instead, you can see that we have registered it via an anonymous constructor function on the `phoneCatApp` module.

In this case Angular provides a service, `$controller`, which will retrieve your controller by name. Here is the same test using `$controller`:

`test/unit/controllersSpec.js:`

	describe('PhoneListCtrl', function(){
	 
	  beforeEach(module('phonecatApp'));
	 
	  it('should create "phones" model with 3 phones', inject(function($controller) {
	    var scope = {},
	        ctrl = $controller('PhoneListCtrl', {$scope:scope});
	 
	    expect(scope.phones.length).toBe(3);
	  }));
	 
	});

* Before each test we tell Angular to load the `phonecatApp` module.
* We ask Angular to inject the `$controller` service into our test function
* We use `$controller` to create an instance of the `PhoneListCtrl`
* With this instance, we verify that the phones array property on the scope contains three records.	

## Writing and Running Tests

Angular developers prefer the syntax of Jasmine's Behavior-driven Development (BDD) framework when writing tests. Although Angular does not require you to use Jasmine, we wrote all of the tests in this tutorial in Jasmine v1.3. You can learn about Jasmine on the Jasmine home page and at the Jasmine docs.

The angular-seed project is pre-configured to run unit tests using Karma but you will need to ensure that Karma and its necessary plugins are installed. You can do this by running npm install.

To run the tests, and then watch the files for changes: npm test.

* Karma will start a new instance of Chrome browser automatically. Just ignore it and let it run in the background. Karma will use this browser for test execution.
* You should see the following or similar output in the terminal:

	info: Karma server started at http://localhost:9876/
	info (launcher): Starting  browser "Chrome"
	info (Chrome 22.0): Connected on socket id tPUm9DXcLHtZTKbAEO-n
	Chrome 22.0: Executed 1 of 1 SUCCESS (0.093 secs / 0.004 secs)

Yay! The test passed! Or not...

* To rerun the tests, just change any of the source or test .js files. Karma will notice the change and will rerun the tests for you. Now isn't that sweet?

## Angularjs动态模板演示

[Angularjs动态模板](/phonecat/step-2/app/)
