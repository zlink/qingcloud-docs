---
title: "场景介绍"
description: 本实践为您介绍如何通过如何通过大数据工作台的 Jar 作业进行 “用户消费 TopN 统计”。
keywords: 大数据工作台,最佳实践,JAR 作业
weight: 5
collapsible: false
draft: false
---

本实践为您介绍如何通过如何通过大数据工作台的 Jar 作业进行 “用户消费 TopN 统计”。

操作流程如下：

<img src="/bigdata/dataomnis/_images/process_practice02.png" alt="实践流程" style="zoom:30%;" />

1. [环境准备](../prepare01)：准备操作过程中需要的数据源环境。
2. [服务准备](../prepare02)：准备操作过程中需要的大数据工作台环境。包括如何创建工作空间、如何创建网络、如何创建计算集群。
3. [准备程序包](../prepare03)：准备实践中需要的 demo 程序包，包括下载 demo、上传程序包。
4. 数据开发（[向 Kafka 写入随机数据](../data_process01)、[消费 Kafka 数据并写入 ClickHouse](../data_process02)）：包括如何创建并开发 Jar 作业、如何配置作业的运行参数、如何配置作业的调度属性。
5. [验证结果](../verify)：验证作业执行结果。