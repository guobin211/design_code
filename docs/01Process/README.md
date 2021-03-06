# 进程线程与协程

## 简介

1. 一个程序至少有一个进程和一个线程

2. 父进程退出，子进程称成为孤儿进程，被init（linux）接管

3. 协程比线程更轻量，属于用户级别

## 进程

进程（process）是资源分配的基本单位。所有与该进程有关的资源，都被记录在进程控制块PCB中。

进程通过IPC进行通讯

创建子进程的方式有`fork`, `vfork`, `exec`

## 线程

线程（thread）是操作系统能够进行运算调度的最小单位。它被包含在进程之中，是进程中的实际运作单位。

同一进程中的多条线程将共享该进程中的全部系统资源，如虚拟地址空间，文件描述符和信号处理等等。

## 协程

协程（Coroutines）是一种比线程更加轻量级的存在，正如一个进程可以拥有多个线程一样，一个线程可以拥有多个协程
