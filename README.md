最近在网上看好多人做个人支付系统，其实就是hook微信或支付宝，生成收款码，于是我也想研究研究，也做作 了一套，不过只做了微信，没有做支付宝，不想浪费时间 了，要做的话应该也不用多长时间 ，毕竟都差不多。 

本来想把源码撰在自己手里，毕竟也是花了时间和精力的，想想还是算了，开发出来的东西如果没有人用就没有任何价值，所以决定开源，代码很简陋，毕竟不是商业产品 ，我不想花那么时间再维护下去，想要继续开发的可以找我有偿服务。



### 系统介绍

不需要申请微信公众号，不需要与微信签约，交易没有手续费 
不需要上传指定金额的二维码，系统自动根据金额生成二维码。 
新的二维码调配机制 ，在保证每一张二维码都是唯一的情况下，相同金额的二维码不会重新生成。
使用个人微号收款，资金直接到自己账上，安全放心 。
同一个收款系统或账号可多台手机 、多个微信同时上线，系统将自动调配在线设备 ，可解决微信限制二维码生成数量限制。

### 一、项目测试和源码下载
本项目演示地址： [点此测试](http://espay.jmkeji.net)


本项目源码下载： [点此下载](http://espay.jmkeji.net)
  
### 二、 运行流程

用户向支付服务器发起支付请求，服务器调用支付接口

支付接口查找系统是否有相同金额的二维码，如果有并且未使用，直接返回二维码

如果系统没有相同金额的付款码，则服务器向手机端发出通知 ，告诉手机端生成付款码，手机端生成付款码后将付款码数据发回服务器，服务器将收到的付款码信息后展示到页面。

用户扫描付款码完成支付，微信端此时收到付款通知后，通知服务器用户已经付款，并将金额和付款码的编号发给服务器

服务器收到付款完成的通知后，修改订单状态，将回调支付通知接口


### 三、系统组成

整个系统由三个部分组成： 

1、后台接口服务（用PHP开发），负责支付接口调用请求、连接后台服务端通、付款码的调用逻辑逻辑、和接收付款完成的通知； 

2、安卓APP，主要是生成二维码和接收付款通知




