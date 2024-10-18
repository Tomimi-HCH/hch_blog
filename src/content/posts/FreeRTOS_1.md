---
title: 从0开始的FreeRTOS（创建任务_伪造现场）
date: 2024-10-18
summary: 这是一篇 Markdown 文章的示例。展示了 Markdown 的语法和渲染效果。
category: FreeRTOS
tags: [RTOS]
---

&emsp;&emsp;学习了FreeRTos内部如何创建任务、伪造现场：如何定义函数和函数指针类型、如何创建任务和仿造硬件中断的现场。可以实现创建自己的线路和运行程序。其中还介绍了如何分配站和参数,以及如何在不同任务之间仿造现场。最后,视频给出了一个简单的示例,展示了整个过程的实现。

---

// ::bilibili{#BV123411578U}

任务的切换就是栈的切换

### FreeRTOS 的最核心文件只有 2 个：

- FreeRTOS/Source/tasks.c
- FreeRTOS/Source/list.c

其他文件的作用也一起列表如下：
|FreeRTOS/Source/下的文件|作用|
|:-----------------------:|:---:|
|tasks.c|必需，任务操作|
|list.c| 必须，列表|
|queue.c| 基本必需，提供队列操作、信号量(semaphore)操作|
|timer.c |可选，software timer|
|event_groups.c |可选，提供 event group 功能|
|croutine.c |可选，过时了|

```c
#include "task.h"

typedef void (*task_function) (void *param) ; //task_function是一个指向接受一个void指针参数且没有返回值的函数的指针类型

void create_task(task_function f, void *param,  char *stack)
{

}

```
