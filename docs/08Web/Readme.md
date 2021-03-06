# Web浏览器模型

## 浏览器线程

```
   // 线程类
   ThreadPoolForegroundWorker
   ThreadPoolBackgroundWorker
   Chrome_ChildIOThread
   GpuMemoryThread
   NetworkConfigWatcher
   Compositor                                         // 多个
   CompositorTileWorker                               // 多个
   ThreadPoolSingleThreadSharedForegroundBlocking     // 多个


   // Helper进程中的线程
   主线程
   js引擎线程
   epoll事件线程
   web-worker线程

   // 进程
   Chrome主进程，浏览器主进程，负责GL操作和调用GPU操作
   GPU进程，GPU硬件加速被打开时创建，负责3D绘制
   Renderer进程，负责生成页面渲染对象
   Helper进程，负责下载文件资源，网络io相关的操作，JS执行器

```

## 浏览器加载渲染流程

<ol>
<li><p>用户输入URL地址</p></li>
<li><p>浏览器解析URL解析出主机名</p></li>
<li><p>浏览器将主机名转换成服务器ip地址（浏览器先查找本地DNS缓存列表 没有的话 再向浏览器默认的DNS服务器发送查询请求 同时缓存）</p></li>
<li><p>浏览器将端口号从URL中解析出来</p></li>
<li><p>浏览器建立一条与目标Web服务器的TCP连接（三次握手）</p></li>
<li><p>浏览器向服务器发送一条HTTP请求报文</p></li>
<li><p>服务器向浏览器返回一条HTTP响应报文</p></li>
<li><p>关闭连接 浏览器解析文档</p></li>
<li><p>如果文档中有资源 重复6 7 8 动作 直至资源全部加载完毕</p></li>
</ol>

```
  // DOMContentLoaded事件触发时，仅当DOM加载完成，不包括样式表，图片等
  // load事件触发时，页面上所有的DOM，样式表，脚本，图片都已加载完成
```

## 浏览器资源加载

    Disk Cache
    ResourceLoader
    CachedResourceLoader

```
    // 优化方式
    1. 优化图片，webp格式，8位png，img标签加上height和width
    2. 合并压缩css，js
    3. 减少http请求
    4. 使用CDN托管
    5. 使用离线缓存
```

## 浏览器渲染优化

angular使用Renderer来管理用户对dom的属性操作，在下一次requestAnimationFrame统一执行更新
react的setState()用于收集属性变化，在下一次requestAnimationFrame统一执行更新
