## 
AI OPS Flow 是一个由人工智能驱动的 OPS 流程自动化平台。它采用了 LangChain 和 Ollama Model 等先进的语言模型技术，可以提高 OPS 相关任务的自动化水平。

## 功能需求：

- 支持多种 IaC 框架
- 支持多语言 CICD
- 支持多种 MLOPS 框架
- 支持多种监控、告警、配置变更工具

## 平台架构：

```                    
                      Front(vue3)
                       |
                      API
                       |
                    AI Engine (LangChain / Ollama Model /GO /Python)
                    /        \
                   OPS flows   Data store
                  /       \        
    资源申请 pipeline  测试发布 pipeline   ML pipeline
```

AI Engine 是平台的核心组件，由 LangChain 和 Ollama Model 组成。AI Engine 负责处理 OPS 相关的任务，包括：

- 生成 OPS flows 的脚本或配置文件
- 部署 OPS flows 到目标环境
- 监控 OPS flows 的运行状态
- LangChain 和 Ollama Model 是 AI Engine 的核心组件，负责为 OPS flows 提供人工智能能力。

OPS flows 是平台的核心功能。OPS flows 由一系列步骤组成，用于实现特定的 OPS 功能。例如，资源申请 pipeline 负责申请资源，测试发布 pipeline 负责发布应用，ML pipeline 负责训练和部署模型。

具体说明如下：

- AI Engine：由 LangChain 和 Ollama Model 组成，负责处理 OPS 相关的任务。
- OPS flows：由一系列步骤组成，用于实现特定的 OPS 功能。
- Data store：用于存储 OPS 相关的数据，例如任务配置、资源信息、监控数据等。
- 前端：使用 Vue3 开发，采用 TypeScript 编写。前端提供用户界面，用于管理 OPS flows。
- API 层：使用 Protobuf 编写，用于与前端进行通信。
- 后端服务层：使用 Go 和 Python 开发。后端服务层负责提供 API 服务，以及管理 AI Engine 和 Data store。
- LangChain / Ollama Model 位于 AI Engine 中，负责处理 OPS 相关的任务，包括：


