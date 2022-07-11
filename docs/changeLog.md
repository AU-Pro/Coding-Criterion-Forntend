 # 改动记录

> 每次改动页面时，都要记录相应的信息，方便后续人员追溯

## 文件头示例

```js
/**
 * @Owner: author
 * @CreatedAt: 2020-03-05 19:15:57
 * @LastModifiedBy: author
 * @LastModifiedTime: 2020-03-05 19:54:37
 * @ChangeLog
 *   v1.0.0 http://doc.path 首页3.1 author
 *   v1.1.0 http://doc.path 首页tab栏调整 author
 *   v1.1.1 http://doc.path 解决 tab 切换卡顿的问题 author
 *   v2.0.0 http://doc.path 首页4.0+频道页 author
 */
```
### 关键词解析

#### Owner

此页面的主要维护者，创建时应该是创建者自己，后续根据业务需要会调整每个模块的 Owner

#### CreatedAt

新建的文件应该是对应的创建时间，如果是现在已经存在的文件，就是初始化注释的时间

#### LastModifiedBy

最近修改人，虽然 git 上也可以追溯，但是不直观，利用插件，也不需要开发者手动维护，插件会自动更新，能够便于查阅

#### LastModifiedTime

最近修改时间，插件会自动更新

#### ChangeLog

这是 <span style="color: red;">最重要</span> 的部分，能够便于大家追溯这个页面的改动历史。

格式示例：`语义化版本 需求链接 需求标题or改动简述 改动人员`

这里由以下几个部分组成

🔽🔽🔽

##### 版本信息

严格遵循[语义化版本](https://semver.org/lang/zh-CN/)
- 主版本：破坏性改动，例如：大规模的调整、页面重构、对原有逻辑无法兼容
- 次版本：新增功能或功能迭代，不会影响主体的逻辑
- 修订号：bug 修复性改动

##### 需求链接

一般情况下都是需求的文档地址。

如果是内部优化或者问题修复，那么改动的依据是参考哪个需求的就填写对应需求的链接。

如果是内部发起的任务应该有技术方案，则填写对应的技术方案。

##### 需求标题or改动简述

如果是一个功能上线，那么可以考虑填写需求标题，如果不是需求则简单描述改动内容，例如本次修改是修复某个问题，则描述修改的问题

##### 改动人员

你的签名

## 辅助插件

推荐使用 [vscode-fileheader](https://marketplace.visualstudio.com/items?itemName=mikey.vscode-fileheader)  
然后在 vscode 的配置文件中加入如下配置
```
"fileheader.Author": "your name",
"fileheader.LastModifiedBy": "your name",
"fileheader.tpl": "/**\n * @Owner: {author}\n * @CreatedAt: {createTime}\n * @LastModifiedBy: {lastModifiedBy}\n * @LastModifiedTime: {updateTime}\n * @ChangeLog\n *   v1.0.0 https://www.baidu.com 改动简述 {author}\n */\n"
```
记得改成自己的名字，为了方便后续人员查阅，统一写自己的名字吧
