# macOS arm64 微信 4.1 数据库解密

## 须知

1. 只在最新的微信 4.1.2.241 测试过，其他版本可能没用，其中 4.0 以下版本铁定没用
2. 这个方法并不稳定，说不定下个版本就封了，还有暴力内存检索 `x'...'` 的方法，一些开源项目也在用，供参考

## 使用步骤

1. 安装 lldb 和 python3
2. 禁用 macOS 系统完整性保护 (SIP) `csrutil disable`
3. 退出微信登录，然后退出微信，然后打开微信到扫码登录界面
4. PYTHONPATH=$(lldb -P) python3 find_key.py
5. 微信扫码登录
6. 保持微信运行，按日常操作看看联系人、消息啥的，看看 find_key.py 输出的日志，如果有捕获到新 key 就说明成功了

## 原理分析

[微信数据库解密](./微信数据库解密.md)。

## Thanks

直接在内存中匹配搜索数据库密钥 <https://github.com/ylytdeng/wechat-decrypt>，但只有 windows 版本 T_T
