---
layout: post
title: "使用angular-seed搭建angularjs和bootstrap开发环境"
date: 2014-04-26 17:36:50
comments: true
categories: Javascript
tags: angularjs, bootstrap
---

## Clone angular-seed

	git clone https://github.com/angular/angular-seed.git
	cd angular-seed

## Install Dependencies

	npm install -g bower
	npm install

如果遇到timeout问题，请设置代理：

	npm config set proxy=http://127.0.0.1:8087

## Run the Application

	npm start

访问`http://localhost:8000/app/index.html`，看环境是否搭建ok。

## 安装bootstrap

在`bower.json`中增加`angular-bootstrap`和`bootstrap`：

	{
	  "name": "angular-seed",
	  "description": "A starter project for AngularJS",
	  "version": "0.0.0",
	  "homepage": "https://github.com/angular/angular-seed",
	  "license": "MIT",
	  "private": true,
	  "dependencies": {
	    "angular": "1.2.x",
	    "angular-route": "1.2.x",
	    "angular-loader": "1.2.x",
	    "angular-mocks": "~1.2.15",
	    "angular-bootstrap": "",
	    "bootstrap": ""
	  }
	}

再执行：
	npm install

修改`app.js`：

	'use strict';


	// Declare app level module which depends on filters, and services
	angular.module('myApp', [
	  'ngRoute',
	  'myApp.filters',
	  'myApp.services',
	  'myApp.directives',
	  'myApp.controllers',
	  'ui.bootstrap'
	]).
	config(['$routeProvider', function($routeProvider) {
	  $routeProvider.when('/view1', {templateUrl: 'partials/partial1.html', controller: 'MyCtrl1'});
	  $routeProvider.when('/view2', {templateUrl: 'partials/partial2.html', controller: 'MyCtrl2'});
	  $routeProvider.otherwise({redirectTo: '/view1'});
	}]);

在`index.html`中增加：

	<link rel="stylesheet" href="../bower_components/bootstrap/dist/css/bootstrap.css"/>
和	
	<script src="../bower_components/angular-bootstrap/ui-bootstrap-tpls.js"></script>

同样需要在`index-async.html`中增加：

	<script src="../bower_components/angular-bootstrap/ui-bootstrap-tpls.js"></script>

### Bootstrap测试

使用`http://angular-ui.github.io/bootstrap/`中的测试code，进行测试，即可看到同样的UI效果。
