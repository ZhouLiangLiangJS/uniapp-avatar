示例说明(可以直接去github下载项目运行, 有问题或讨论方法，请撩924515629)

H5测试

<img src='http://www.snyvic.eu/static/m.png'/>

```
//template部分
    <avatar	
        selWidth="200px" selHeight="400upx" @upload="myUpload" :avatarSrc="url"
        avatarStyle="width: 200upx; height: 200upx; border-radius: 100%;">
    </avatar>

//script部分
    import avatar from "../../components/yq-avatar/yq-avatar.vue";
    export default {
    	data() {
            return {
                url: "../../static/logo.png"
            }
        },      
        methods: {
            myUpload(rsp) {
                this.url = rsp.path; //更新头像方式一
                //rsp.avatar.imgSrc = rsp.path; //更新头像方式二
            }
        }，
        components: {
            avatar
        }
    }
```



用法<br/>
点击头像或自定义触发方式，选择图片进行缩放、旋转、裁剪。既可以直接上传，也可以美化后上传<br/>
单头像建议直接使用avatar，如果多个图片裁剪，建议使用一个，回调函数返回图片路径后自行处理<br/>

<br/>

| 属性        | 必须 | 说明                                                         |
| ----------- | ---- | ------------------------------------------------------------ |
| selWidth    | 是   | 裁剪区域的宽                                                 |
| selHeight   | 是   | 裁剪区域的高                                                 |
| avatarSrc   | 否   | 头像地址                                                     |
| avatarStyle | 否   | 头像样式，默认{width: 150upx; height: 150upx; border-radius: 100%;} |
| expWidth    | f否  | 设置导出宽度，H5平台暂不支持                                 |
| expHeight   | f否  | 设置导出高度，H5平台暂不支持                                 |
| inner       | 否   | 只允许在图片范围内移动，并禁用一切旋转，默认false            |
| quality     | 否   | 生成图片质量，取值范围0~1，默认0.9                           |
| index       | 否   | 索引，回调upload方法，返回该index值，默认undefined           |
| noTab       | 否   | 是否存在tabBar，默认false，主要为了去除报错存信息，不设置也不影响使用 |
| minWidth    | 否   | 缩放允许的最小宽度，数值类型，不需要添加单位后缀，默认单位px |
| minHeight   | 否   | 缩放允许的最小高度，数值类型，不需要添加单位后缀，默认单位px |
| minScale    | 否   | 缩放允许的最小比例，默认0.3                                  |
| maxScale    | 否   | 缩放允许的最大比例，默认4                                    |
| canRotate   | 否   | 是否允许旋转，默认true                                       |
| canScale    | 否   | 是否允许缩放，默认true                                       |
| stretch     | 否   | 图片一边自动铺满裁剪框<br/>x: x轴方向，图片自动铺满<br/>y: y轴方向，图片自动铺满<br/>long:  根据图片长边自动铺满<br/>short:  根据图片短边自动铺满<br/>longSel:  根据裁剪框长边自动铺满<br/>shortSel:  根据裁剪框短边自动铺满 |
| lock        | 否   | 锁定图片移动方向<br/>x:  锁定x轴方向<br/>y:  锁定y轴方向<br/>long: 锁定图片长边方向<br/>short:  锁定图片短边方向<br/>longSel:  锁定裁剪框长边方向<br/>shortSel:  锁定裁剪框短边方向 |

<br/>

| 事件   | 必须 | 说明                                                         |
| ------ | ---- | :----------------------------------------------------------- |
| upload | 是   | 返回格式 {avatar: xx, path: xx, index: xx, data: xx}<br/>avatar: 对象类型，可以通过更新imgSrc值，更新头像<br/>path: 临时头像地址<br/><br/>index: 索引<br/>data: 通过fChooseImg函数设置的额外数据，默认undefined |
<br/>

| ref可调用方法                   | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| fChooseImg(index, params, data) | 触发图片选择<br/>index: 索引，默认undefined<br/>params, 初始化参数，默认undefined<br/>{<br/>selWidth: "xx",  //裁剪框宽度<br/>selHeight: "xx",  //裁剪框高度<br/>}<br/>data, 回调返回的额外数据，可以是任何类型，默认undefined |

<br/>

## 您的支持是开源的动力，觉得不错就给个好评给颗星，谢谢! ^-

<br/>

| 版本  | 变化                                                         |
| ----- | :----------------------------------------------------------- |
| 3.1.9 | 修复直接关闭不显示tabBar问题                                 |
| 3.1.8 | 修复提示bug                                                  |
| 3.1.7 | fChooseImg增加调用参数params/data，upload返回对象增加data字段<br/>删除minWidth/minHeight属性<br/>增加关闭按钮<br/>修复图片过小时采用inner无法移动问题 |
| 3.1.6 | 修复stretch属性                                              |
| 3.1.5 | 增加新属性 noTab                                             |
| 3.1.4 | 增加旋转按钮                                                 |
| 3.1.3 | 删除属性lockWidth/lockHeight<br/>新增控制属性 inner/stretch/lock<br/>新增自动触发子组件方法 fChooseImg(index) |
| 3.1.2 | 新增控制属性minWidth/minHeight/minScale/maxScale/canRotate/canScale/lockWidth/lockHeight |
| 3.1.1 | 调整回调返回数据内容，修复小程序报错问题                     |
| 3.1.0 | 增加index属性，修改回调返回的数据格式                        |
| 3.0.4 | H5平台适配HX1.9.9                                            |
| 3.0.3 | 增加导出图片质量调整参数                                     |
| 3.0.2 | 加强对H5和Android兼容                                        |
| 3.0.1 | 如果tabBar存在，自动隐藏                                     |
| 3.0.0 | 增加色彩变化，android平台需等待官方修复bug，没有启用；其他平台测试正常 |
| 2.0.1 | 修复小程序预览失败                                           |
| 2.0.0 | 适配HX197、198版本，旧版可以去github下载                     |
| 1.0.5 | 屏幕旋转后不需要重新选择图片                                 |
| 1.0.4 | 修复头像样式解析错误                                         |
| 1.0.3 | 修改样式绑定方式                                             |
| 1.0.2 | 修改按钮栏样式                                               |
| 1.0.1 | 修改按钮栏高度                                               |
| 1.0.0 | 增加H5支持                                                   |

