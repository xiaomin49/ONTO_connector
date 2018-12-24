# ONTID产品设计

## 目的

将ONTID协议引入生态合作伙伴钱包内，推广ONTID。

## 背景

当前ONTID的使用的问题
- 1 ONTID保存只有keystore一种方法，用户保存能力有限，容易丢失。
- 2 ONTID局限于ONTO中，用户覆盖范围不足，无法在生态中实现更多功能。
- 3 ONTID附带的认证存在本地，由于意外等原因，用户丢失身份认证的情况经常发生。
- 4 ONTID是一长串字符，难以区分，无法辨识。

为了推广ONT ID，加强ONTID和用户的绑定，方便用户管理自己的身份信息，我们引入ONT ID Layer2， 并对ONT ID在注册，管理，授权，认证这四个方面进行了重新规划设计。

## ONT ID Layer2

ONT ID Layer2 在本体Blockchain 基础上，封装了ONT ID的注册、Verifiable Claim的去中心化存储职能，便于dAPP集成ONT ID和使用ONT ID。

在架构设计上 ONT ID Layer2 连接了去中心化存储，也同时使用了中心化系统的高效机制。 

## 一 注册ONT ID

#### 什么时候触发注册ONT ID? 

和ONTO不同，生态合作伙伴钱包（麦子、Onion等）只有在场景中才触发ONT ID的生成 ，比如用户在Candy Box中需要KYC，所有触发ONT ID注册。 

#### 注册体系设计

一切让生态合作伙伴钱包简单，仅需要一个指令发给Cyano Mobile即可完成注册。

![ontid-register](http://assets.processon.com/chart_image/5c1efaa9e4b05e0d063bf702.png)

* **Cyano Mobile的职责:**  帮助钱包方生成私钥和Keystore；
* **Layer2的职责:**  代付钱包方的ONT ID的上链费用，需要验证钱包方 ONT ID签名

#### ONT ID存储和显示规范

生态合作伙伴钱包使用ONT ID Keystore存储规范存储在客户端；

注册成功后，生态合作伙伴钱包需要显示ONT ID的WIF私钥和 Keystore信息。 


## 二 管理ONT ID

ONT ID 的管理包括：

* **导入**，支持WIF 和 KeyStore两个方式导入，Cyano Mobile 支持这两种方式的库；
* **查询**，用户随时可以查询自己的ONT ID，客户端钱包需要随时显示用户的ONT ID，便于用户查询。
* **导出**，用户可以导出ONT ID Keystore和WIF私钥。 





## ONTID 授权
ONTID授权和Account授权完全相同，此处不赘述。

可以参考[授权流程](https://github.com/xizho10/OEPs/blob/master/OEP-11/OEP-11.mediawiki#invoke-smart-contract)

## ONTID 认证
此前所有provider中只有ONTO提供了身份认证功能，身份认证全部存储在本地，用户要使用自己的身份就被局限在ONTO中，管理难度很大。根据目前的dApp开放策略，结合[ONTPASS](https://developer.ont.io/ontpass/introduction)进行身份管理，所有的身份认证将会加密存储于ONTPASS服务器中，配合上一个身份管理dApp，可以实现以下目标：
- 1 用户只要保护好自己ONTID的私钥，就可以随时管理自己的身份认证。
- 2 不再受到ONTO或者单一设备的限制，一处认证，到处可用。
- 3 降低provider的接入难度，provider无感接入，也没有app内保存用户数据的担忧。

#### dApp内完成身份认证流程

<img src="./img/ontpasssupport.jpg" style="width-max:300px"/>


## 总结
总体来说，就是通过Cynao Mobile组件在生态合作钱包内的植入创造基础条件，dApp激励计划吸引更多带有ONTID的dApp，进而吸引更多用户创建ONTID，同时通过ONTPASS进行身份认证管理，一处认证，到处可用，帮助用户在本体生态内构建起自我掌控的身份体系。
