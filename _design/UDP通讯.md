# UDP协议

适用于音频视频数据传输

无连接的传输协议，用户数据报协议。

UDP报头由4个域组成，其中每个域各占用2个字节，具体包括源端口号、目标端口号、数据报长度、校验值

## 特点

1.无连接，可以一对多，性能强

2.面向报文，不拆包不合并包

3.容易丢包
