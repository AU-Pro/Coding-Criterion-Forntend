# Git
  
## 分支模型

- master：生产分支
- ~~develop：开发分支~~
- hotfix：紧急发布分支，从 master 切出来的分支
- release：版本发布分支，从 master 切出来的分支
- test：需求提测分支（release 是当天已经具备发布条件的分支），从 master 切出来的分支
- feature：功能开发分支，从 master 切出来的分支

> 一句话概括：所有其他分支都是以 master 为准，所有的更改都是相对于线上代码

#### 遵循以下三条基本规则

##### 1. 开始工作前，从 master 创建 feature 分支。

从代表最新已发布版本的 master 分支上创建一个通常以 feature/前缀命名的特性分支，然后在这个分支上提交代码修改。也就是说，每个工作项（可以是一个人完成，或是多个人协作完成）对应一个特性分支，所有的修改都不允许直接提交到 master 分支。

##### 2. 具备提测条件的 feature 分支，合并到当日的测试分支

这个分支可能存在多个需求的代码，<span style="color: red;">切记不要反向 merge</span>，在你的功能测试完备之后再合并到 release

##### 3. 当日的发布分支

从 master 分支上拉出一条新分支，将所有本次要集成或发布的 feature 分支依次合并过去，从而得到 release 分支。release 分支通常以 release/前缀命名。

##### 4. 发布到线上正式环境后，合并相应的 release 分支到 master 分支，在 master 分支上添加 tag，同时删除该 release 分支关联的 feature 分支。

为了避免在代码仓库里堆积大量历史上的 feature 分支，还应该清理掉已经上线部分 feature 分支。如果要回溯历史版本，只需在 master 分支上找到相应的版本的 tag 即可。

> 以上来自[开发分支管理模型之阿里 AoneFlow](https://segmentfault.com/a/1190000016373314)，<span style="color: red;">请认真阅读</span>

### 分支规范

功能分支：feature/{姓名简写}-{日期}-{主要功能} 例如：feature/zc-20190601-pay

提测分支：test/{日期}-test test/20190601-test

版本发布分支：release/{日期}-release 例如：release/20190601-release

紧急发布分支：hotfix/{日期}-hotfix 例如：hotfix/20190601-hotfix

### 代码提交

遵循以下原则：

1. 可读性好，清晰，不必深入看代码即可了解当前commit的作用
2. 少量多次，一次提交一个功能或改动点
3. commit 的格式

   ```
   <type>(<scope>): <subject>
   // 空一行
   <body>
   // 空一行
   <footer>
   ```

   - type  
   
    用于说明 commit 的类别，只允许使用下面 7 个标识(type)

    feat：新功能（feature）

    fix：修补bug

    docs：文档（documentation）

    style： 格式（不影响代码运行的变动）

    refactor：重构（即不是新增功能，也不是修改bug的代码变动）

    test：增加测试

    chore：构建过程或辅助工具的变动

   - scope  
   
    scope用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

  - subject

    subject是 commit 目的的简短描述，不超过50个字符。

    示例：
    ```
    feat(文章详情页): 改变互动区的展示逻辑

    1. 风险评测：现在代理人视角也会展示这个模块
    2. 聊天窗口：滚动到互动区域之后会弹出聊天窗口
    ```

  > 更多的信息可以参考[这里](https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)
