# 使用vlmcsd激活window和office

## 注意！！！

kms只能激活批量版（也称VOL版），不能激活零售版

免费kms激活服务（学习使用）

`kms.nextyu.com`

## 下载vlmcsd

[下载地址](https://github.com/Wind4/vlmcsd/releases)


## 运行vlmcsd服务端（windows版）

运行 PowerShell

```
cd D:\binaries\binaries\Windows\intel # 进入vlmcsd解压之后的目录

./vlmcsd-Windows-x64.exe # 默认运行在1688端口

./vlmcs-Windows-x64.exe 127.0.0.1:1688 # 测试是否可用
```

## 激活win10专业版

需要下载 win10 business edition [MSDN,我告诉你](https://msdn.itellyou.cn/)

管理员模式运行 PowerShell

```
slmgr.vbs /upk                                      # 清除密钥

slmgr.vbs /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX        # 添加密钥 win10专业版

slmgr.vbs /skms 192.168.66.35:1688     # 设置kms服务器

slmgr.vbs /ato                      # 激活

slmgr.vbs /xpr                      # 查看激活时效
```

## 激活office2019专业增强版

需要下载 office 2019 vl 版本 [如何创建 Office 2019 VL（批量许可）版本的安装 ISO (Windows)](https://sysin.org/blog/office-2019-iso/)

管理员模式运行 PowerShell

```
cd C:\Program Files (x86)\Microsoft Office\Office16 # office 安装位置

cscript ospp.vbs /inpkey:NMMKJ-6RK4F-KMJVX-8D9MJ-6MWKP  # 添加密钥 2019专业增强版

cscript ospp.vbs /sethst:192.168.66.35:1688            # 设置kms服务器

cscript ospp.vbs /act                               # 立即激活
```

## 参考资料

- [window激活密钥](https://learn.microsoft.com/zh-cn/windows-server/get-started/kms-client-activation-keys)
- [office激活密钥](https://learn.microsoft.com/zh-cn/DeployOffice/vlactivation/gvlks)
- [KMS 服务器 vlmcsd 的安装和激活](https://blog.beanbang.cn/2019/01/31/kms-server-vlmcsd/)
- [MSDN,我告诉你](https://msdn.itellyou.cn/)
- [常识：并不存在office2019 vol原版安装光盘](https://www.aihao.cc/thread-12243-1-1.html)
- [如何创建 Office 2019 VL（批量许可）版本的安装 ISO (Windows)](https://sysin.org/blog/office-2019-iso/)
- [如何创建 Office LTSC 2021 VL（批量许可）版本的安装 ISO](https://sysin.org/blog/office-2021-iso/)
- [win10 business edition和consumer edition版本区别](https://www.cnblogs.com/hool/p/13530160.html)