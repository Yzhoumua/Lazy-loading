# JS小dome之懒加载
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box{
            width: 300px;
            height: 300px;
            position: absolute;
            left: 300px;
            top: 1500px;
            background-color: red;
        }
    </style>
</head>
<body>
    <div style="height: 3000px;">
        <div class="box" style="opacity: 0.3;"></div>
    </div>
    <script>
        var div = document.getElementsByClassName('box')[0];
        //获取div元素
        var key = true;
        //给上一个锁防止滑轮滚动一直触发事件
        window.onscroll = function(){
            //滚轮滚动触发事件
            if(div.offsetTop <= window.innerHeight + window.pageYOffset && key === true){
                //当div距页面顶部的距离小于 整个页面的高度加上鼠标滚轮滚动的高度，并且当前的kye是ture的时候执行
             var timer = setInterval(function(){
                 //给加上一个定时器和清除定时器
                 div.style.opacity = parseFloat(div.style.opacity) + 0.001
                 //获取当前div的透明值，让每隔30毫秒给他的opacity值加0.001
                 if(div.style.opacity >= 1){
                     //如果div的opacity值大于1
                     clearInterval(timer);
                     //清除定时器
                     key = false;
                     //让锁给关上
                 }
             },30)
        }
       }

    </script>
</body>
</html>
```