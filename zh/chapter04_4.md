# 数据绑定data-binding

上一节我们介绍了如何将ng-controller的数据显示在HTML当中，但是我们如何在html中修改这些数据呢？这一步操作也很简单。

我们先直接看看代码吧！

```html
<!DOCTYPE html>
<html lang="zh" ng-app="App">
<head>
    <meta charset="UTF-8">
    <!-- 网页的标题，我们在这里使用了AngularJS的基本表达式 -->
    <title>{{"学习AngularJS 1.x"}}</title>
</head>
<body>
    <!-- 将FirstCtrl绑定到这个div标签上，这个标签中的内容将可以使用FirstCtrl中的数据-->
    <div ng-controller="FirstCtrl">
        <h1>{{data.message + " World!"}}</h1>
        <!-- 这里增加了一个input输入框，并使用ng-model绑定了data.message-->
        <input type="text" ng-model="data.message">
    </div>

    <script type="text/javascript" src="components/angular/angular.js"></script>
    <script type="text/javascript" src="js/app.js"></script>
</body>
</html>
```

运行结果

![图4-3 ng-controller运行结果](./pic/0403_ng-model.png)

如果您实际运行代码，会发现，您每输入/删除一个文字，改动会马上在上方显示出来。这就是数据绑定的魅力！

## 功能的绑定
界面操作里面还有一个重要的功能，就是界面上按钮的与控制器中的函数进行绑定。这个也很容易实现：

```javascript
App.controller("FirstCtrl", function($scope){
    $scope.data = {
      message : "Hello"
    };

    //在$scope上绑定一个函数
    $scope.onClick = function(){
        alert($scope.data.message);
    }
});
```

```html
<div ng-controller="FirstCtrl">
    <h1>{{data.message + " World!"}}</h1>
    <input type="text" ng-model="data.message">
    <!-- 这里我们放置一个按钮，并使用ng-click绑定了$scope.onClick事件-->
    <input type="button" value="按钮" ng-click="onClick()">
</div>
```
点击按钮，我们即可看到数据通过弹出框显示了出来（onClick函数中的逻辑）。

![图4-3 ng-click运行结果](./pic/0404_ng-click.png)