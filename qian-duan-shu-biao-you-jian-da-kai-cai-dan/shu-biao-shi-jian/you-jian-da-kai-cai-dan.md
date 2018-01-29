### oncontextmenu事件

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>右键菜单</title>
    <style type="text/css">
        #animal {
            display: flex;
            justify-content: flex-start;
            align-items: flex-start;
        }

        ul,
        li {
            margin: 0;
            padding: 0;
        }

        #animal>li {
            margin: 8px 10px;

            border: 1px solid grey;
            padding: 8px 40px;
            width: 50px;
            list-style-type: none;
        }

        #menu {
            position: fixed;
            left: 0;
            top: 0;
            width: 100px;
            height: 183px;
            box-shadow: 1px 1px 22px grey;
            display: none;
            border: 1px solid grey;
            border-radius: 6px;
            box-sizing: border-box;
        }

        #menu>ul {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
            background: #FFF;
        }

        #menu>ul>li {
            border-bottom: 1px solid rgb(196, 195, 195);
            width: 100%;
            list-style-type: none;
            padding-top: 28px;
            text-align: center;
        }

        #menu>ul>li:nth-last-child(1) {
            border-bottom: 0px solid rgb(196, 195, 195);
        }
    </style>
</head>

<body>
    <ul id="animal">
        <li>
            喜羊羊
        </li>
        <li>
            灰太狼
        </li>
        <li>
            小灰灰
        </li>
        <li>
            红太狼
        </li>
    </ul>
    <div id="menu">
        <ul>
            <li>来抓它</li>
            <li>放了它</li>
            <li>捶死它</li>
        </ul>
    </div>
    <script type="text/javascript">
        var menu = document.getElementById("menu");
        var lis = document.getElementsByTagName("li");

        for (var i = 0; i < lis.length; i++) {//循环让每个div都有效果
            lis[i].oncontextmenu = function (e) {
                var e = e || window.event;
                //鼠标点的坐标
                var oX = e.clientX;
                var oY = e.clientY;
                //菜单出现后的位置
                menu.style.display = "block";
                menu.style.left = oX + "px";
                menu.style.top = oY + "px";
                //阻止浏览器默认事件
                return false;//一般点击右键会出现浏览器默认的右键菜单，写了这句代码就可以阻止该默认事件。
            }
        }
        document.onclick = function (e) {
            var e = e || window.event;
            menu.style.display = "none"
        }
        menu.onclick = function (e) {
            var e = e || window.event;
            e.cancelBubble = true;
        }
    </script>
</body>

</html>
```

![](/WX20180128-214718@2x.png)

![](/WX20180128-214847@2x.png)

