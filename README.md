
ZenML 徽标
皮皮 皮皮 皮皮 贡献者 执照

构建可移植、生产就绪的 MLOps 管道。
加入我们的Slack 社区并成为 ZenML 家族的一员。 松弛

功能 · 路线图 · 报告错误 · 投票新功能 · 阅读博客 · 为开源做出贡献 · 与团队见面

🎉 版本 0.54.1 已发布。请在此处查看发行说明 。

🏁 目录

🤖 简介
🤹 ZenML 是一个可扩展的开源 MLOps 框架，用于创建可移植的、可用于生产的机器学习管道。通过将基础架构与代码解耦，ZenML 使整个组织的开发人员能够在开发到生产时更有效地协作。

💼 ZenML 使数据科学家能够自由地完全专注于建模和实验，同时编写从一开始就可以投入生产的代码。

👨‍💻 ZenML 使 ML 工程师能够端到端地掌控整个 ML 生命周期。采用 ZenML 意味着更少的切换点以及对组织中正在发生的事情的更多可见性。

🛫 ZenML 使 MLOps 基础设施专家能够定义、部署和管理易于同事使用的复杂生产环境。

从实验到生产的漫长旅程。

ZenML 提供专为 ML 工作流程设计的用户友好语法，与任何云或工具兼容。它支持集中式管道管理，使开发人员只需编写一次代码即可轻松将其部署到各种基础设施。


🤸 快速入门
通过 PyPI安装 ZenML。需要 Python 3.8 - 3.11：

pip install "zenml[server]"
通过运行以下命令来浏览引导式快速入门：

zenml go
🖼️ 创建您自己的 MLOps 平台
ZenML 允许您使用一流的开源和基于云的技术创建和管理自己的 MLOps 平台。以下是如何为您的团队进行设置的示例：

🔋 1.部署ZenML
为了获得完整的功能，ZenML 应部署在云上，以启用协作功能作为团队的中央 MLOps 界面。

ZenML 架构图。

目前，部署 ZenML 有两个主要选项：

ZenML Cloud：通过ZenML Cloud，您可以利用控制平面来创建 ZenML 服务器（也称为租户）。这些租户由ZenML的专门团队管理和维护，减轻您端服务器管理的负担。

自托管部署：或者，您可以灵活地在自己的自托管环境中部署 ZenML。这可以通过多种方法来实现，包括使用我们的 CLI、Docker、Helm 或 HuggingFace Spaces。

👨‍🍳 2. 部署堆栈组件
ZenML 拥有大量与流行 MLOps 工具的集成。ZenML Stack 概念确保这些工具能够很好地协同工作，从而将结构和标准化引入 MLOps 工作流程。

使用 ZenML 进行部署和配置非常简单。对于AWS，这可能看起来有点像这样

# Deploy and register an orchestrator and an artifact store
zenml orchestrator deploy kubernetes_orchestrator --flavor kubernetes --cloud aws
zenml artifact-store deploy s3_artifact_store --flavor s3

# Register this combination of components as a stack
zenml stack register production_stack --orchestrator kubernetes_orchestrator --artifact-store s3_artifact_store --set # Register your production environment
当您使用此堆栈集运行管道时，它将在您部署的 Kubernetes 集群上运行。

您还可以手动部署自己的工具。

🏇 3. 创建管道
以下是代码中的 hello world ZenML 管道示例：

# run.py
from zenml import pipeline, step


@step
def step_1() -> str:
    """Returns the `world` substring."""
    return "world"


@step
def step_2(input_one: str, input_two: str) -> None:
    """Combines the two strings at its input and prints them."""
    combined_str = input_one + ' ' + input_two
    print(combined_str)


@pipeline
def my_pipeline():
    output_step_one = step_1()
    step_2(input_one="hello", input_two=output_step_one)


if __name__ == "__main__":
    my_pipeline()
python run.py
👭 4.启动仪表板
使用此命令打开 ZenML 仪表板。

zenml show
🗺 路线图
ZenML 正在公开构建。该路线图是 ZenML 社区定期更新的事实来源，以了解产品的短期、中期和长期发展方向。

ZenML 由核心开发人员团队管理，负责制定关键决策并纳入社区的反馈。团队通过各种渠道监督反馈，您可以直接影响路线图，如下所示：

在我们的讨论板上投票选出您最想要的功能。
在我们的Slack 频道中启动一个线程。
在我们的 GitHub 存储库上创建问题。
🙌 贡献和社区
我们很乐意与我们的社区一起开发 ZenML！最好的开始方法是从good-first-issue 标签中选择任何问题 并打开拉取请求！如果您想做出贡献，请查看我们的贡献指南以获取所有相关详细信息。

🆘 寻求帮助
第一个呼叫点应该是我们的 Slack 小组。询问有关错误或特定用例的问题，核心团队的人员会做出回应。或者，如果您愿意，可以在我们的 GitHub 存储库上提出问题。

📜 许可证
ZenML 根据 Apache 许可证版本 2.0 的条款进行分发。该存储库的LICENSE文件中提供了完整版本的许可证。对此项目所做的任何贡献都将根据 Apache 许可证版本 2.0 获得许可。
