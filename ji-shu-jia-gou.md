---
icon: network-wired
---

# 技术架构

```mermaid
graph 
A[用户] --> B[OpwenWebUI]
subgraph OpwenWebUI
B --> C[内置向量模型]
B --> D[内置索引数据库]
D--> E[文档]
end
B --> G[Ollama]
G --> H[DeepSeekR1:推理模型]
 
```
