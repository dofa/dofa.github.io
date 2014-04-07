---
layout: post
title: "Angularjs学习笔记-双向绑定"
date: 2014-04-07 21:11:50 -0700
comments: true
categories: Javascript
tags: javascript, Angularjs
---

动态排序可以这样实现，添加一个新的模型属性，把它和迭代器集成起来，然后让数据绑定完成剩下的事情。

## 模板
`app/index.html:`

	Search: <input ng-model="query">
	Sort by:
	<select ng-model="orderProp">
		<option value="name">Alphabetical</option>
		<option value="age">Newest</option>
	</select>


	<ul class="phones">
		<li ng-repeat="phone in phones | filter:query | orderBy:orderProp">
			{{phone.name}}
			<p>{{phone.snippet}}</p>
		</li>
	</ul>

我们在`index.html`中做了如下更改：

* 首先，我们增加了一个叫做`orderProp`的`<select>`标签，这样我们的用户就可以选择我们提供的两种排序方法。  

* 然后，在`filter`过滤器后面添加一个`orderBy`过滤器用其来处理进入迭代器的数据。`orderBy`过滤器以一个数组作为输入，复制一份副本，然后把副本重排序再输出到迭代器。

`AngularJS`在`select`元素和`orderProp`模型之间创建了一个双向绑定。而后，`orderProp`会被用作`orderBy`过滤器的输入。

正如我们在步骤3中讨论数据绑定和迭代器的时候所说的一样，无论什么时候数据模型发生了改变（比如用户在下拉菜单中选了不同的顺序），AngularJS的数据绑定会让视图自动更新。没有任何笨拙的DOM操作！

## 控制器

`app/js/controllers.js:`

	var phonecatApp = angular.module('phonecatApp', []);
	 
	phonecatApp.controller('PhoneListCtrl', function ($scope) {
	  $scope.phones = [
	    {'name': 'Nexus S',
	     'snippet': 'Fast just got faster with Nexus S.',
	     'age': 1},
	    {'name': 'Motorola XOOM™ with Wi-Fi',
	     'snippet': 'The Next, Next Generation tablet.',
	     'age': 2},
	    {'name': 'MOTOROLA XOOM™',
	     'snippet': 'The Next, Next Generation tablet.',
	     'age': 3}
	  ];
	 
	  $scope.orderProp = 'age';
	});

* 我们修改了`phones`模型—— 手机的数组 ——为每一个手机记录其增加了一个`age`属性。我们会根据`age`属性来对手机进行排序。
* 我们在控制器代码里加了一行让`orderProp`的默认值为`age`。如果我们不设置默认值，这个模型会在我们的用户在下拉菜单选择一个顺序之前一直处于未初始化状态。

现在我们该好好谈谈双向数据绑定了。注意到当应用在浏览器中加载时，“Newest”在下拉菜单中被选中。这是因为我们在控制器中把`orderProp`设置成了‘age’。所以绑定在从我们模型到用户界面的方向上起作用——即数据从模型到视图的绑定。现在当你在下拉菜单中选择“Alphabetically”，数据模型会被同时更新，并且手机列表数组会被重新排序。这个时候数据绑定从另一个方向产生了作用——即数据从视图到模型的绑定。

## Test
The changes we made should be verified with both a unit test and an end-to-end test. Let's look at the unit test first.

`test/unit/controllersSpec.js:`

	describe('PhoneCat controllers', function() {
	 
	  describe('PhoneListCtrl', function(){
	    var scope, ctrl;
	 
	    beforeEach(module('phonecatApp'));
	 
	    beforeEach(inject(function($controller) {
	      scope = {};
	      ctrl = $controller('PhoneListCtrl', {$scope:scope});
	    }));
	 
	    it('should create "phones" model with 3 phones', function() {
	      expect(scope.phones.length).toBe(3);
	    });
	 
	 
	    it('should set the default value of orderProp model', function() {
	      expect(scope.orderProp).toBe('age');
	    });
	  });
	});

The unit test now verifies that the default ordering property is set.

We used Jasmine's API to extract the controller construction into a beforeEach block, which is shared by all tests in the parent describe block.

You should now see the following output in the Karma tab:

	Chrome 22.0: Executed 2 of 2 SUCCESS (0.021 secs / 0.001 secs)

Let's turn our attention to the end-to-end test.

`test/e2e/scenarios.js:`

	...
    it('should be possible to control phone order via the drop down select box', function() {
 
      var phoneNameColumn = element.all(by.repeater('phone in phones').column('{{phone.name}}'));
      var query = element(by.model('query'));
 
      function getNames() {
        return phoneNameColumn.map(function(elm) {
          return elm.getText();
        });
      }
 
      query.sendKeys('tablet'); //let's narrow the dataset to make the test assertions shorter
 
      expect(getNames()).toEqual([
        "Motorola XOOM\u2122 with Wi-Fi",
        "MOTOROLA XOOM\u2122"
      ]);
 
      element(by.model('orderProp')).findElement(by.css('option[value="name"]')).click();
 
      expect(getNames()).toEqual([
        "MOTOROLA XOOM\u2122",
        "Motorola XOOM\u2122 with Wi-Fi"
      ]);
    });...

The end-to-end test verifies that the ordering mechanism of the select box is working correctly.

You can now rerun npm run protractor to see the tests run.

## Angularjs双向绑定演示

[Angularjs双向绑定](/phonecat/step-4/app/)
