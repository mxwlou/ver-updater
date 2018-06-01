# 端点星内容版本控制仓库（TSVC）自动更新脚本
## Terminus Site Version Control Auto Update Script

## 注意事项
* 本品需要和 TSVC 一起使用。默认推送仓库地址为 mxwlou/sitever
* 如果需要客制化仓库地址，请首先克隆或者fork `mxwlou/sitever`, 然后克隆此仓库。
* 然后需要安装 travis加密脚本(`gem install travis`)，并将 `.travis-ci.yml`的最后几行含`secure`的内容删除

并且使用以下命令调用travis加密脚本加密这两个仓库并保存为环境加密变量：
```shell
travis encrypt GHLOC="https://username:password@github.com/user_or_organization/sitever" -r user_or_organization/sitever --add

travis encrypt VERP="https://username:password@github.com/user_or_organization/ver-updater" -r user_or_organization/ver-updater --add

```
填入自己的 `username`, `password`, 以及 `user_or_organization` 设置好。commit即可。

最后在`travis-ci`上为此仓库开通自动构建服务即可（提前开也行，但是请避免自动revert。构建脚本会进行自动revert以避开用户信息泄露的问题）。



## 使用方式：
* 在Github上修改`dev`分支下的`update.json`,按照格式填写更新内容。
* 网上直接Commit即可，无须担心用户信息泄漏问题，会由CI自动去除。
* 等待自动构建。

或者你也可以使用本地构建方式，详见package.json 中的 npm script。

