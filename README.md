# Vehicle Museum for LazyCat

本仓库将 [`little-zack-wong/vehicle-museum`](https://github.com/little-zack-wong/vehicle-museum)
打包为懒猫微服 LPK。GitHub Actions 会拉取上游 `main` 分支的最新提交、构建静态站点、
创建带版本号的 GitHub Release 资产，并把经过校验的 LPK 发布到喵喵商店。

## 发布

在 Actions 页面手动运行 **Build and publish LazyCat application**。每次运行会递增补丁版本，
生成 `cloud.lazycat.app.vehicle-museum-v<version>.lpk`，并发布到已配置的喵喵商店。

必需的 GitHub Secrets：

- `APPSTORE_URL`
- `APPSTORE_TOKEN`

可选的 GitHub Secrets：

- `APP_ID`
- `PRIVATE_STORE_GROUP_CODES`

组织级 Secrets 必须授权此仓库。同名 Repository Secret 会覆盖 Organization Secret。

## 本地验证

```bash
./build.sh
lzc-cli project release -o .lazycat-build/vehicle-museum.lpk
lzc-cli lpk info .lazycat-build/vehicle-museum.lpk
```

上游当前未提交依赖锁文件，因此构建使用 `npm install`，解析到的是构建时满足
`package.json` 版本范围的依赖。上游代码与资源保留其原始许可和署名。
