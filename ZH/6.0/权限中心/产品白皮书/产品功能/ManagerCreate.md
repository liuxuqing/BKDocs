# 超级管理员创建分级管理员

以有超级管理员身份的账号登录到蓝鲸权限中心，在`右上角`个人信息里切换到`超级管理员`身份，进入到`分级管理员`页面，点击`新建`创建分级管理员。

![image-20201029143648601](ManagerCreate/image-20201029143648601.png)

## 基本信息

- 分级管理员名称：区分不同分级管理员，根据需求场景来命名，可以随时修改。
- 成员列表：分级管理员的成员都具备该分级管理员的相关权限，即具体某个分级管理员的管理成员。
- 描述：描述分级管理员的职能。

## 选择操作和资源实例范围

**操作和资源实例范围**代表该分级管理员能够`授权`的权限范围，可以跨系统选择多个操作。

![image-20201029145638479](ManagerCreate/image-20201029145638479.png)

选择操作后，需要针对每个操作进行对应的实例范围选择，实例选择可以选择具体实例，也可以通过属性条件来实现动态实例的选择。

比如，选择了 A 系统的 a 操作，对应的实例是 i1，i2，i3，则该分级管理员就只能给其他人授予 a 操作的 i1、i2、i3 这几个实例内的权限。

![image-20201209185808659](ManagerCreate/image-20201209185808659.png)

## 选择可授权人员范围

**可授权人员范围**代表该分级管理员能够`授权`的人员范围，反过来，也只有在可授权人员范围内的用户才能看到对应分级管理员所创建的用户组，双向的限制，避免了不必要的权限给用户带来的干扰，也避免敏感权限外泄，人员可以是组织，也可以是具体某个用户。

> 比如，选择了`组织：广东分公司、用户：user`，则该分级管理员只能给这两类人授权，也只有他们才能看到对应分级管理员创建的用户组，去申请加入。

![](ManagerCreate/image-20201029152316625.png)

选择完操作实例和人员范围，点击`提交`即完成分级管理员的创建。 

## 切换分级管理员身份

能够切换分级管理员身份的前提是成为分级管理员的管理成员。

![image-20201117093004886](ManagerCreate/image-20201117093004886.png)

点击右上角**个人信息**，点击**切换身份**，选择需要的身份进行切换。

![image-20201117093220231](ManagerCreate/image-20201117093220231.png)