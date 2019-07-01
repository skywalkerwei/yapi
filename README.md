#api-doc

### 使用方法
####1、安装扩展
```
composer require kyle/ycpai
```

####2、配置参数
- 5.0安装好扩展后在 application\extra\ 文件夹下会生成 doc.php 配置文件
- 5.1安装好扩展后在 application\config\ 文件夹下会生成 doc.php 配置文件
- 在controller参数中添加对应的类
```
    'controller' => [
        'app\\api\\controller\\Demo' //这个是控制器的命名空间+控制器名称
    ]
```
####3、在相关接口类中增加注释参数( group 参数将接口分组，可选)
- 方法如下：返回参数支持数组及多维数组
```
<?php
namespace app\index\controller;
use think\Controller;

/**
 * @title 测试demo
 * @description 接口说明
 * @group 接口分组
 * @header name:key require:1 default: desc:秘钥(区别设置)
 * @param name:public type:int require:1 default:1 other: desc:公共参数(区别设置)
 */
class Demo extends Controller
{
    /**
     * @title 测试demo接口
     * @description 接口说明
     * @author 开发者
     * @url /index/demo
     * @method GET
     *
     * @header name:device require:1 default: desc:设备号
     *
     * @param name:id type:int require:1 default:1 other: desc:唯一ID
     *
     * @return name:名称
     * @return mobile:手机号
     * @return list_messages:消息列表@
     * @list_messages message_id:消息ID content:消息内容
     * @return object:对象信息@!
     * @object attribute1:对象属性1 attribute2:对象属性2
     * @return array:数组值#
     * @return list_user:用户列表@
     * @list_user name:名称 mobile:手机号 list_follow:关注列表@
     * @list_follow user_id:用户id name:名称
     */
    public function index()
    {
        //接口代码
        $device = $this->request->header('device');
        echo json_encode(["code"=>200, "message"=>"success", "data"=>['device'=>$device]]);
    }

    /**
     * @title 登录接口
     * @description 接口说明
     * @author 开发者
     * @url /api/demo
     * @method GET
     * @module 用户模块

     * @param name:name type:int require:1 default:1 other: desc:用户名
     * @param name:pass type:int require:1 default:1 other: desc:密码
     *
     * @return name:名称
     * @return mobile:手机号
     *
     */
    public function login(Request $request)
    {
        //接口代码
        $device = $request->header('device');
        echo json_encode(["code"=>200, "message"=>"success", "data"=>['device'=>$device]]);
    }
}
```
####4、在浏览器访问http://你的域名/doc 或者 http://你的域名/index.php/doc 查看接口文档



