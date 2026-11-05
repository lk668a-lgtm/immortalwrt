# Buer-Wrt

基于 ImmortalWrt 25.12（`openwrt-25.12` 分支）的定制固件，目标设备 **CMCC XR30 NAND（cmcc_xr30-nand）**。

## 与上游的差别
- 预装 `luci-app-tkproxy`（多线路分流插件，未预置卡密，客户自行激活）
- 品牌改为 **Buer-Wrt**（banner / 主机名 / 系统描述）
- 默认中文、Asia/Shanghai、Argon 深色主题（主题装上时）
- 新增 `.github/workflows/build-buer-wrt.yml`：推送即编译，产物在 Actions → Artifacts

## 怎么出固件
1. 在 GitHub 仓库 `Actions` 里启用 workflow（fork 仓库首次需要点一次 “I understand my workflows”）
2. 选择 `build-buer-wrt` → `Run workflow` → 分支 `buer-wrt`
3. 约 2–4 小时后，在运行页面底部下载 `buer-wrt-cmcc_xr30-nand`
4. 解压得到 `*sysupgrade.bin`，在 U-Boot 的 FIRMWARE UPDATE 页面上传即可

## 刷机
- 设备进入 U-Boot 网页恢复（192.168.1.1）→ 选择文件 → Upload
- 刷完自动重启，默认后台 http://192.168.1.1 ，root 无密码（首次请立刻设置密码）
- 进「服务 → 多线路分流」输入卡密激活

## 注意
- 本仓库不包含任何卡密、节点、订阅、socks5 凭据
- 只支持 cmcc_xr30-nand；其它机型请改 `.config` 里的 DEVICE 行
