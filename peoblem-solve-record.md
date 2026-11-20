# 问题解决记录
 ## 问题描述
 在使用 Markdown 编写文档时，因为不熟悉 Markdown 语法规则，符号书写错误，花费大量时间调整排版格式。
 ## 问题原因
 1. 符号书写错误：反引号、单引号混用，任务列表 `-[]` 缺少空格；
 2. 不了解 Markdown 渲染规则，出现意外加粗、格式失效等现象。
 ## 解决办法
 1. 严格按照标准语法书写：任务列表写 `- [ ]`，代码块使用反引号 ```；
 2. 写完后切换 Preview 预览，及时查看渲染效果。
 ## 总结
 需要熟记 Markdown 基础语法，规范符号写法，减少格式调试时间。
 
# Git操作问题解决记录
## 问题1：命令缺少git前缀
- 错误输入：`commit -m "git学习笔记"`
- 报错信息：`bash: commit: command not found`
- 问题原因：commit不是独立命令，所有Git子命令都必须以git开头
- 解决办法：修改为 `git commit -m "git学习笔记"`
- 总结收获：Git命令必须带上git前缀

## 问题2：git commit参数缺少空格
- 错误输入：`git commit-m "内容"`
- 问题原因：`-m` 和commit之间缺少空格，Git无法识别参数
- 解决办法：修改为 `git commit -m "内容"`
- 总结收获：Git命令对空格严格，不能随意省略空格

## 问题3：未执行git add直接commit
- 错误操作：没有执行git add，直接执行git commit
- 提示信息：`nothing added to commit but untracked files present`
- 问题原因：新文件属于未追踪文件，没有加入暂存区，无法提交
- 解决办法：先执行 `git add 文件名`，再执行commit
- 总结收获：标准流程：`git add` → `git commit` → `git push`；add作用是把文件放入暂存区

## 问题4：中文文件名编码异常
- 错误操作：`git add git学习笔记.md`
- 现象：add之后文件仍然是untracked状态，文件名显示一串八进制转义字符
- 问题原因：UCRT64/WSL环境下中文文件名编码兼容问题，Git识别失败
- 解决办法：优先使用英文文件名；坚持用中文可执行配置 `git config --global core.quotepath false`
- 总结收获：尽量避免中文文件名，减少编码报错

## 问题5：文件名带空格引发报错
- 错误输入：`git add git learn note.md`
- 报错信息：`fatal: pathspec 'git' did not match any files`
- 问题原因：Git把空格当做多个文件的分隔符，误识别为多个文件
- 解决办法：文件名不用空格，使用横杠连接，例：`git-learn-note.md`；带空格文件名可用英文双引号包裹
- 总结收获：Git文件名推荐英文、横杠连接，不要使用空格

## 问题6：push时需要浏览器授权
- 提示信息：`please complete authentication in your browser`
- 问题原因：推送代码需要GitHub身份验证
- 解决办法：根据提示打开浏览器，登录GitHub完成授权
- 总结收获：第一次push或者授权过期时，需要网页端验证

## 补充知识点
如果`git add`执行成功，只是后面`git commit`写错报错，不需要重新执行git add，暂存区内容保留，直接输入正确commit命令即可；只有git add本身执行失败，才需要重新执行git add。
