# PR 与 CI 合并规则

默认分支要求 PR、固定 GitHub Actions `CI`、同步主分支及解决审查讨论；失败、取消、意外跳过均不能通过。禁止强推、删除或管理员绕过。

默认主分支为 `master`。
| 阶段 | 范围 |
| --- | --- |
| PR / master push | Go 1.27.1 的 Linux amd64、Windows amd64、macOS arm64 原生单元/编译器 E2E/可执行示例与 race；另三种架构编译冒烟 |
| 发布 / 手动 full | Go 1.25.8 / 1.26.8 / 1.27.1 六种原生平台及五种 race 平台；Windows arm64 不运行 race |
| Release artifacts | 同一提交完整源码门禁；构建一次六个平台归档，再进行十八种原生执行及不可变提交的公共 Go 代理安装 |

普通 PR 的所有原生核心 E2E 与断言继续执行，编译冒烟只声明构建覆盖。完整模式不重复编译冒烟，因为相同架构已由原生矩阵覆盖；汇总门禁仅在该模式允许它预期跳过。

`v*` 仅由 `release-artifacts.yml` 编排完整源码与制品，避免同一标签同时启动另一套源码全矩阵。`examples/rules/v*` 仍单独验证完整规则源码；手动 full 可提前验证兼容范围。没有定时任务、专用 Runner、外部测试 Secret 或受保护 Environment。

固定 `Release CI` 要求源码、包和远程安装都成功；只保存 Actions 制品，公开发行由维护者另行操作。详见 [测试入口](testing_CN.md) 与 [脚本指南](../scripts/README_CN.md)。慢平台保留真实编译器与显式超时，不把超时记为通过。
