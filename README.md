
<!doctype html> 
<html> 
<head> 
    <meta charset="gb2312">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>万能收款码</title>
    
    <script>
    var setting = {
        // 在以下双引号中粘贴QQ钱包收款链接
        qqUrl: "http://qm.qq.com/cgi-bin/qm/qr?k=Zh64RHVrrxEWyZiFVPkcZy9kd65Tj-76",
",
        
        // 在以下双引号中粘贴微信收款链接
        wechatUrl: "wxp://f2f0a4SwOkTkg-BrkwBHiAny2J0GWn2e6-yO",
",
        
        // 在以下双引号中粘贴支付宝收款链接
        aliUrl: "HTTPS://QR.ALIPAY.COM/FKX03791ID1TPHHZ16ZZ60",
        
        // 用于动态生成二维码的API，不需要修改。
        qrcodeApi: "http://qr.liantu.com/api.php?text="    
        /*
        备用二维码api：
        http://s.jiathis.com/qrcode.php?url=
        http://www.kuaizhan.com/common/encode-png?large=true&data=
        http://b.bshare.cn/barCode?site=weixin&url=
        http://pan.baidu.com/share/qrcode?w=150&h=150&url=
        */
    }
    </script>
    
    <style>
    * {
        margin: 0; padding: 0;
        font-family: Microsoft yahei;
    }
    body {
        background-color: #fff;
    }
    .code-item {
        width: 100%;
        max-width: 400px;
        margin: 0 auto;
        padding-bottom: 1px;
        display: none;
        background-color: #5c92ef;
    }
    .code-title {
        height: 100px;
        background-color: #f2f2f2;
        background-position: center;
        background-repeat: no-repeat;
        background-size: 50%;
    }
    .code-area {
        text-align: center;
    }
    .code-area>img {
        margin: 80px 0;
        width: 60%;
        min-width: 100px;
    }
    .code-footer {
        height: 80px;
        text-align: center;
        background-color: #fff;
        color: #666;
        line-height: 80px;
        font-size: 20px;
        margin: -2px 2px 2px 2px;
    }
    
    #code-all>.code-title {
        background-image: url("https://ww2.sinaimg.cn/large/a15b4afegy1fiw0rt77kwj2092032aa4.jpg");
    }
    
    #code-qq {
        background-color: #54b4ef;
    }
    #code-qq>.code-title {
        background-image: url("https://ww2.sinaimg.cn/large/a15b4afegy1fiw0uxpya8j20b403qaa1.jpg");
    }
    
    #code-wechat {
        background-color: #54bc6e;
    }
    #code-wechat>.code-title { 
        background-image: url("https://ww2.sinaimg.cn/large/a15b4afegy1fiw0w2er9aj2092032t94.jpg");
        
    }
    </style>    

</head>
<body>
    <!-- 万能收款码展示区域 -->
    <div class="code-item" id="code-all">
        <div class="code-title"></div>
        <div class="code-area">
            <img id="page-url" src="data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==">
        </div>
        <div class="code-footer">扫描以上二维码向我付款</div>
    </div>
    
    <!-- QQ钱包二维码展示区域 -->
    <div class="code-item" id="code-qq">
        <div class="code-title"></div>
        <div class="code-area">
            <img id="qq-url" src="data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==">
        </div>
        <div class="code-footer">长按以上二维码向我付款</div>
    </div>
    
    <!-- 微信二维码展示区域 -->
    <div class="code-item" id="code-wechat">
        <div class="code-title"></div>
        <div class="code-area">
            <img id="wechat-url" src="data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==">
        </div>
        <div class="code-footer">长按以上二维码向我付款</div>
    </div>
    
    <script>
    if(navigator.userAgent.match(/Alipay/i)) {
        // 支付宝
        window.location.href = setting.aliUrl; 
    } else if(navigator.userAgent.match(/MicroMessenger\//i)) {
        // 微信
        document.getElementById("wechat-url").src = setting.qrcodeApi + urlEncode(setting.wechatUrl);
        document.getElementById("code-wechat").style.display = "block";
    } else if(navigator.userAgent.match(/QQ\//i)) {
        // QQ
        document.getElementById("qq-url").src = setting.qrcodeApi + urlEncode(setting.qqUrl);
        document.getElementById("code-qq").style.display = "block";
    } else {
        // 其它，显示“万能码”
        document.getElementById("page-url").src = setting.qrcodeApi + urlEncode(window.location.href);
        document.getElementById("code-all").style.display = "block";
    }
    
    /*****************************************
     * url编码函数
     * 输入参数：待编码的字符串
     * 输出参数：编码好的
     ****************************************/
    function urlEncode(String) {
        return encodeURIComponent(String).replace(/'/g,"%27").replace(/"/g,"%22");	
    }
    </script>

</body>
</html>
