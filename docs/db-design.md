
AI Engine 数据源设计的细节信息：

1. 监控日志链路事件等信息写入 Clickhouse

监控日志链路事件等信息是 OPS 流程自动化的重要数据源。这些数据可以帮助 OPS 流程自动化工具实时监控 OPS 流程的运行状态，并进行异常报警。

这些数据可以写入 Clickhouse 中，以便 OPS 流程自动化工具可以通过 SQL 语句进行查询和分析。

具体实现

监控日志链路事件等信息可以通过以下方式写入 Clickhouse：

# 写入日志数据
INSERT INTO logs (timestamp, level, message, ...) VALUES (...);

# 写入链路数据
INSERT INTO links (source, target, ...) VALUES (...);

# 写入事件数据
INSERT INTO events (timestamp, event_type, ...) VALUES (...);
优化建议

数据分区
可以根据数据的类型和访问频率对数据进行分区，以提高数据查询效率。

数据压缩
可以对数据进行压缩，以节省存储空间。

数据安全
需要采取措施保护数据安全，例如数据加密、访问控制等。

示例

以下是一个示例，用于将监控日志数据写入 Clickhouse：

SQL
# 创建日志表
CREATE TABLE logs (
  timestamp TIMESTAMP,
  level INT,
  message STRING,
  ...
) ENGINE = MergeTree(timestamp, (level, message), 8192);

# 插入日志数据
INSERT INTO logs (timestamp, level, message)
VALUES ('2023-07-20 12:00:00', 2, 'This is a log message.');
请谨慎使用代码。了解详情
监控服务

监控服务可以通过 Clickhouse 提供的 API 接口来查询监控数据。例如，监控服务可以使用以下 API 接口来查询过去 1 小时内发生的所有异常事件：

SQL
SELECT *
FROM events
WHERE timestamp > NOW() - INTERVAL 1 HOUR
AND event_type = 'exception';
请谨慎使用代码。了解详情
2. 云资源账号 K8S 集群内部依赖拓扑信息写入 Neo4j

云资源账号、K8S 集群内部依赖拓扑信息是 OPS 流程自动化的重要数据源。这些数据可以帮助 OPS 流程自动化工具了解 OPS 流程的资源依赖关系，并进行资源优化。

这些数据可以写入 Neo4j 中，以便 OPS 流程自动化工具可以通过图形查询进行查询和分析。

具体实现

云资源账号、K8S 集群内部依赖拓扑信息可以通过以下方式写入 Neo4j：

# 创建节点
CREATE (node:Node {name: "node_name", value: "node_value"})

# 创建关系
CREATE (node1)-[relation:RELATION_TYPE]->(node2)
优化建议

数据分区
可以根据数据的类型和访问频率对数据进行分区，以提高数据查询效率。

数据压缩
可以对数据进行压缩，以节省存储空间。

数据安全
需要采取措施保护数据安全，例如数据加密、访问控制等。

示例

以下是一个示例，用于将云资源账号数据写入 Neo4j：

SQL
# 创建节点
CREATE (node:Account {
  name: 'account_name',
  id: 'account_id',
  region: 'region',
  ...
});
请谨慎使用代码。了解详情
AI Engine agent

AI Engine agent 可以通过 Neo4j 提供的 API 接口来查询云资源账号数据。例如，AI Engine agent 可以使用以下 API 接口来查询所有位于某个区域的云资源账号：

SQL
MATCH (node:Account {region: 'region'})
RETURN node;


长期记忆、SOP、资源清单、运维事件处理信息 也被添加到 VectorDB 中。

长期记忆 数据是指 OPS 流程的历史运行数据，这些数据可以帮助 AI Engine 了解 OPS 流程的运行规律，并进行优化和改进。

SOP 数据是指 OPS 流程的标准操作流程，这些数据可以帮助 AI Engine 生成 OPS 流程的自动化脚本。

资源清单 数据是指 OPS 流程所使用的资源信息，这些数据可以帮助 AI Engine 了解 OPS 流程的资源依赖关系，并进行资源优化。

运维事件处理信息 数据是指 OPS 流程运行过程中发生的事件信息，这些数据可以帮助 AI Engine 了解 OPS 流程的运行情况，并进行异常报警。
