---
layout: post
title: "Angularjs学习笔记-迭代器过滤"
date: 2014-04-07 20:56:50 -0700
comments: true
categories: Javascript
tags: javascript, Angularjs
---

使用AngularJS的迭代器过滤功能可以方便的对数据进行过滤。

## 控制器

我们对控制器不做任何修改。

## 模板

`app/index.html`:

  <div class="container-fluid">
    <div class="row-fluid">
      <div class="span2">
        <!--Sidebar content-->
 
        Search: <input ng-model="query">
 
      </div>
      <div class="span10">
        <!--Body content-->
 
        <ul class="phones">
          <li ng-repeat="phone in phones | filter:query">
            {{phone.name}}
            <p>{{phone.snippet}}</p>
          </li>
        </ul>
 
      </div>
    </div>
  </div>



我们现在添加了一个`<input>`标签，并且使用`AngularJS`的`$filter`函数来处理`ngRepeat`指令的输入。

这样允许用户输入一个搜索条件，立刻就能看到对电话列表的搜索结果。我们来解释一下新的代码：

* 数据绑定： 这是`AngularJS`的一个核心特性。当页面加载的时候，`AngularJS`会根据输入框的属性值名字，将其与数据模型中相同名字的变量绑定在一起，以确保两者的同步性。

* 在这段代码中，用户在输入框中输入的数据名字称作`query`，会立刻作为列表迭代器（`phone in phones | filter:query`）其过滤器的输入。当数据模型引起迭代器输入变化的时候，迭代器可以高效得更新DOM将数据模型最新的状态反映出来。

* 使用`filter`过滤器：`filter`函数使用`query`的值来创建一个只包含匹配`query`记录的新数组。

* `ngRepeat`会根据`filter`过滤器生成的手机记录数据数组来自动更新视图。整个过程对于开发者来说都是透明的。

	

## 测试

在步骤2，我们学习了编写和运行一个测试的方法。单元测试用来测试我们用js编写的控制器和其他组件都非常方便，但是不能方便的对DOM操作和应用集成进行测试。对于这些来说，端到端测试是一个更好的选择。

搜索特性是完全通过模板和数据绑定实现的，所以我们的第一个端到端测试就来验证这些特性是否符合我们的预期。

`test/e2e/scenarios.js:`

	describe('PhoneCat App', function() {
	 
	  describe('Phone list view', function() {
	 
	    beforeEach(function() {
	      browser.get('app/index.html');
	    });
	 
	 
	    it('should filter the phone list as user types into the search box', function() {
	 
	      var phoneList = element.all(by.repeater('phone in phones'));
	      var query = element(by.model('query'));
	 
	      expect(phoneList.count()).toBe(3);
	 
	      query.sendKeys('nexus');
	      expect(phoneList.count()).toBe(1);
	 
	      query.clear();
	      query.sendKeys('motorola');
	      expect(phoneList.count()).toBe(2);
	    });
	  });
	});

This test verifies that the search box and the repeater are correctly wired together. Notice how easy it is to write end-to-end tests in Angular. Although this example is for a simple test, it really is that easy to set up any functional, readable, end-to-end test.


## Running End to End Tests with Protractor

Even though the syntax of this test looks very much like our controller unit test written with `Jasmine`, the end-to-end test uses APIs of Protractor. Read about the Protractor APIs at `https://github.com/angular/protractor/blob/master/docs/api.md`.

Much like `Karma` is the test runner for unit tests, we use Protractor to run end-to-end tests. Try it with npm run protractor. End-to-end tests are slow, so unlike with unit tests, Protractor will exit after the test run and will not automatically rerun the test suite on every file change. To rerun the test suite, execute npm run protractor again.

	Note: You must ensure you've installed the protractor and updated webdriver prior to running the npm run protractor. You can do this by issuing npm install and npm run update-webdriver into your terminal.

## Angularjs迭代器过滤演示

[Angularjs迭代器过滤](/phonecat/step-3/app/)
