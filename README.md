<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>邀请吃饭</title>
    <script>
        var canClosePage = false; // 初始状态下不允许关闭页面

        function showDinnerInvitation() {
            while (true) {
                var userResponse = confirm("一起吃饭呗！");
                if (userResponse) {
                    alert("太好了，我们一起去吃饭吧！");
                    canClosePage = true; // 用户同意后允许关闭页面
                    break;
                } else {
                    alert("就要一起吃饭！");
                }
            }
        }

        window.onload = showDinnerInvitation;

        window.onbeforeunload = function(e) {
            if (!canClosePage) {
                e = e || window.event;
                if (e) {
                    e.returnValue = '您必须先选择 "我同意" 才能离开此页面。';
                }
                return '您必须先选择 "我同意" 才能离开此页面。';
            }
        };

        function closePage() {
            if (canClosePage) {
                window.close(); // 允许关闭页面
            } else {
                alert('您必须先选择 "我同意" 才能关闭页面。');
            }
        }
    </script>
</head>
<body>
    <!-- 空白的body，用户将看不到任何内容，除非他们关闭了所有的弹窗 -->
    <button onclick="closePage()">关闭页面</button>
</body>
</html>

