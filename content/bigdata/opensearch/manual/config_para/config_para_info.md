---
title: "参数介绍"
description: 本小节主要介绍 OpenSearch 常用配置项。 
keyword: 常用配置项,OpenSearch,搜索引擎,大数据
weight: 10
collapsible: false
draft: false
---



在 AppCenter 集群管理控制台，支持对 OpenSearch 常用配置参数的管理，包括**公共参数**、**OpenSearch 节点（热）**、**OpenSearch 节点（温）**、**OpenSearch 节点（冷）**、**Dashboard 节点**、**Logstash 节点**的配置参数。

本小节主要介绍 AppCenter 中各 OpenSearch 配置参数的含义。

## 公共参数

|<span style="display:inline-block;width:80px">参数</span> |<span style="display:inline-block;width:120px">取值范围</span>|<span style="display:inline-block;width:420px">参数说明</span>|
|:----|:----|:----|
|   opensearch.admin.user    |  -       |   表示 OpenSearch Dashboard 超级管理员（admin）帐号名称。 <li>集群创建后，不支持修改。  |
|   opensearch.admin.password      |  -      |   表示 OpenSearch Dashboard 超级管理员（admin）帐号名称。 <li>集群创建后，不支持修改。  |

## OpenSearch 节点（热）

|<span style="display:inline-block;width:80px">参数</span> |<span style="display:inline-block;width:120px">取值范围</span>|<span style="display:inline-block;width:420px">参数说明</span>|
|:----|:----|:----|
|   prometheus.node.exporter    |  <li>true<li>false      |   表示是否对接 Prometheus 开启 Node Exporter 监控服务。 <li>默认值为 `true`。 开启后监控端口默认为 9100. |
|   thread_pool.write .queue_size    |  200~10240     |   表示 queue_size 允许控制没有线程执行它们的待处理请求队列的大小。 <li>默认值 1024。  |
|   thread_pool.search .queue_size      |  1000~10240   |   表示 queue_size 允许控制没有线程来执行它们的待处理请求队列的初始大小。 <li>默认值 1024。  |
|   action.destructive _requires_name      | <li>true<li>false   |   表示是否允许在删除索引时使用通配符或_all。<li>默认值 `true`，表示允许使删除只限于特定名称指向的数据。<li>取值 `false`，表示允许在删除索引时使用通配符或_all，推荐配置。  |
|   discovery.zen.no_master_block      |  <li>全部<li>写  |   表示控制当节点没有活跃的主节点时哪些操作应该被拒绝。  |
|  gateway.recover_after_time     |  -   |   表示如果未达到期望的节点数，recovery 过程将在配置的时间后开始 recover 操作。<li>默认值 5 分钟。  |
|   http.cors.enabled      |  <li>true<li>false   |   表示是否支持跨区域资源共享，例如另一区域的服务器向 OpenSearch 执行请求。  |
|   http.cors.allow-origin      |  -   |   表示允许跨域资源共享的域。详细配置说明，请参见[Elatsticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/7.10/modules-http.html)。  |
|   indices.fielddata .cache.size      |  -   |   表示 field 缓存数据所能使用的堆内存的最大值。 <li>默认值 90%。  |
|   indices.memory.index _buffer_size      |  -   |   表示总堆用于索引缓存被所有分片共享的内存大小。<li>可配置百分比值或字节值。 <li>默认值 10%，表示总堆内存的10%将被用于索引缓存被所有分片共享。  |
|   indices.queries .cache.size      |  -   |   表示控制 filter 缓存的内存大小。<li>默认值 10%。<li>可配置百分比值或字节值。  |
|   indices.requests .cache.size      |  -   |   表示分片级的请求缓存对每一个分片做本地缓存，这个缓存在节点级进行管理。<li>默认堆内存的 1%。  |
|   node.attr.data（热）      |  hot   |   表示 OpenSearch 节点自定义标签（node.attr.data），可用作热-温-冷架构配置。  |
|   script.allowed_types      |  -   |   表示在 opensearch.yml 文件中指定允许的脚本类型。  |
|   script.allowed_contexts      |   -   |   表示在 opensearch.yml 文件中指定允许的文本类型。   |
|   reindex.remote.whitelist     |  -   |   表示允许 Reindex 的远程集群白名单。  |
|   remote_exe_dict     |  -   |   表示用户自定义字典的可访问 URL，例如 `http://<Logstash_IP>/dicts/mydict.dic`。  |
|   remote_exe_stopwords     |  -   |   表示用户停止词字典的可访问 URL，例如 `http://<Logstash_IP>/dicts/mydict.dic`。 |
|   path.repo      |  -   |   表示共享文件系统仓库的路径。  |
|   repositories.url .allowed_urls      |  -   |   表示只读 URL 仓库的路径。  |
|   os_additional_line1      |   -   |   表示在 opensearch.yml 文件中附加配置。   |
|   os_additional_line2     |   -   |   表示在 opensearch.yml 文件中附加配置。   |
|   os_additional_line3      |   -   |   表示在 opensearch.yml 文件中附加配置。   |
|   logger.action.level     | <li>info<li>trace<li>debug<li>warn<li>error   |   表示日志配置文件 log4j2.properties 中的 logger.action.level 配置项。 <li>默认值 `info`。 |
|   rootLogger.level  | <li>info<li>trace<li>debug<li>warn<li>error   |   表示日志配置文件 log4j2.properties 中的 rootLogger.level 配置项。 <li>默认值 `info`。  |
|   logger.deprecation .level     | <li>info<li>trace<li>debug<li>warn<li>error   |   表示日志配置文件 log4j2.properties 中的 logger.deprecation.level 配置项。  <li>默认值 `warn`。 |
|   logger.index_search _slowlog_rolling.level     | <li>info<li>trace<li>debug<li>warn<li>error   |   表示日志配置文件 log4j2.properties 中的 logger.index_search_slowlog_rolling.level 配置项。  <li>默认值 `trace`。 |
|   logger.index_indexing _slowlog.level     | <li>info<li>trace<li>debug<li>warn<li>error   |   表示日志配置文件 log4j2.properties 中的 logger.index_indexing_slowlog.level 配置项。  <li>默认值 `trace`。 |
|   enable_heap_dump    | <li>true<li>false   |   表示是否允许启用自动 Heap Dump。  <li>默认值 `false`。 |
|   heap_dump_path     | -   |   表示 Heap Dump 文件的存储路径。  <li>默认值 `/data/opensearch/dump`。 |
|   clean_logs_older _than_n_days     | 0～   |   表示 OpenSearch 节点日志保留天数。  <li>默认值 7 天。 |
|   tcp_keepalive_intvl    | 0～   |   表示 TCP keepalive 探活的时间间隔。  <li>默认值 75。 |
|   tcp_keepalive_probes     | 0～   |   表示在通知应用层连接断开之前，允许尝试发送未应答的（unacknowledged）探活请求的数量。  <li>默认值 9。 |
|   tcp_keepalive_time     | 0～   |   表示最后一次发送数据包之后，到发送第一个 keepalive 保活请求之间的时间间隔。  <li>默认值 7200 秒。 |

## OpenSearch 节点（温）

|<span style="display:inline-block;width:80px">参数</span> |<span style="display:inline-block;width:120px">取值范围</span>|<span style="display:inline-block;width:420px">参数说明</span>|
|:----|:----|:----|
|   node.attr.data（温）      |  warm   |   表示 OpenSearch 节点自定义标签（node.attr.data），可用作热-温-冷架构配置。  |

## OpenSearch 节点（冷）

|<span style="display:inline-block;width:80px">参数</span> |<span style="display:inline-block;width:120px">取值范围</span>|<span style="display:inline-block;width:420px">参数说明</span>|
|:----|:----|:----|
|   node.attr.data（冷）      |  cold  |   表示 OpenSearch 节点自定义标签（node.attr.data），可用作热-温-冷架构配置。  |

## Dashboard 节点

|<span style="display:inline-block;width:80px">参数</span> |<span style="display:inline-block;width:120px">取值范围</span>|<span style="display:inline-block;width:420px">参数说明</span>|
|:----|:----|:----|
｜  enable_cerebro     |  <li>true<li>false |   表示是否开启 Cerebro  第三方管理工具。<li>默认值为 `true`，表示开启 Cerebro。 |
|   OS 代理负载均衡策略     |  <li>轮询<li>static-rr<li>最少连接<li>first<li>源地址 |   表示 Dashboard 节点代理负载均衡策略类型。详细策略类型说明，请参见 [HAProxy Configuration](https://cbonte.github.io/haproxy-dconv/1.8/configuration.html#4-balance) 。 |
|   OS 代理连接超时时间      |  - |   表示 HAProxy 连接后端 OpenSearch 服务的超时时间。<li>单位可设置 ms（毫秒）、s（秒）、m（分）或者 h（小时）。<li>默认值 5秒。 |
|   OS 代理超时时间      |   - |   表示 HAProxy 等待后端 OpenSearch 服务返回响应的超时时间。<li>单位可设置 ms（毫秒）、s（秒）、m（分）或者 h（小时）。<li>默认值 60秒。 |
|  OS 代理最大连接数      |  0~65535 |   表示 Dashboard 节点代理最大并发连接数，超出的客户端连接请求将排队等待。详细连接数说明，请参见 [HAProxy Configuration](https://cbonte.github.io/haproxy-dconv/1.8/configuration.html#4-maxconn) 。<li>默认值 2000。 |
|   OS 代理最大请求体      |  - |   表示 OpenSearch 代理的客户端请求体的最大允许值。<li>默认值 20 MB。 <li>单位为 MB，设置以 m表示。|

## Logstash 节点

|<span style="display:inline-block;width:80px">参数</span> |<span style="display:inline-block;width:120px">取值范围</span>|<span style="display:inline-block;width:420px">参数说明</span>|
|:----|:----|:----|
|   config.reload.automatic     |  <li>true<li>false |   表示是否定期检查配置文件并自动加载更改过的 pipeline 配置。 |
|   config.reload.interval      |  - |   表示定期检查配置文件的频率。<li>单位为秒。<li>默认值 3 秒。 |
|   input_conf_content      |   - |   表示执行 Logstash 时，用 -f 指定配置文件，配置文件的 input 段的内容将由此设置项决定。<li>不支持换行，请把所有注释行（以 # 开头的行）去掉，以防止引起语法错误。 |
|  filter_conf_content      |   - |   表示执行 Logstash 时，用 -f 指定配置文件，配置文件的 filter 段的内容将由此设置项决定。<li>不支持换行，请把所有注释行（以 # 开头的行）去掉，以防止引起语法错误。 |
|  output_conf_content     |  - |     表示执行 Logstash 时，用 -f 指定配置文件，配置文件的 output 段的内容将由此设置项决定。<li>不支持换行，请把所有注释行（以 # 开头的行）去掉，以防止引起语法错误。 |
|  output_os_content      |   - |   表示执行 Logstash 时，用 -f 指定配置文件，配置文件的 output 段中的 elasticsearch 段的内容将由此设置项决定。<li>不支持换行，请把所有注释行（以 # 开头的行）去掉，以防止引起语法错误。 |
|  gemfile_append_content     |  - |     表示 Logstash 的 Gemfile 文件增加内容。 |
