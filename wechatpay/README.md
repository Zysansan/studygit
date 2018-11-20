# wechatpay
微信支付sdk

简单demo:<br/>
$p=new \wechatPay\Pay('appid','商户id','商户秘钥');<br/>

调用扫码支付,返回一个图片数据,直接放在img标签里面<br/>
$p->for_NATIVE('订单号','支付回调地址','客户端ip');<br/>

调用公众号支付<br/>

$p->for_jspay(
                '商品描述',<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'订单号',<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;            '商品价格,单位为分',<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;               'openid,自行获取',<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;               '客户端ip',<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;               '支付回调地址'<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;           );


微信js-sdk调用

wx.chooseWXPay({<br/>
timestamp: data.timeStamp, // 支付签名时间戳，注意微信jssdk中的所有使用timestamp字段均为小写。但最新版的支付后台生成签名使用的timeStamp字段名需大写其中的S字符<br/>
nonceStr: data.nonceStr, // 支付签名随机串，不长于 32 位<br/>
package: data.package, // 统一支付接口返回的prepay_id参数值，提交格式如：prepay_id=\*\*\*）<br/>
signType: data.signType, // 签名方式，默认为'SHA1'，使用新版支付需传入'MD5'<br/>
paySign: data.paySign, // 支付签名<br/>
success: function (res) {<br/>
 支付成功后的回调函数<br/>
 if (res.errMsg == "chooseWXPay:ok") {
    
   支付还是以支付回调为主<br/>
 }<br/>


}<br/>
});<br/>

支付回调签名检查，检查成功返回微信服务器数据，包括订单号，订单金额之类<br/>
$re=$pay->check();<br/>
