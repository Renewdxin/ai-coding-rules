# AI Coding Rules Collection

[![GitHub](https://img.shields.io/badge/GitHub-ai--coding--rules-blue?logo=github)](https://github.com/Renewdxin/ai-coding-rules)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

这是一套专为Claude和Cursor等AI编程工具设计的开发规则集合，涵盖不同开发场景的规范和工作流程。

## 🚀 快速开始

### 克隆仓库
```bash
git clone git@github.com:Renewdxin/ai-coding-rules.git
cd ai-coding-rules
```

### 在项目中使用
```bash
# 复制规则到你的项目
cp -r ai-coding-rules/* your-project/
```

## 📋 规则文件说明

### 核心规则
- `GENERAL_RULES.md` - 通用开发规则，包含核心目标和五个关键步骤
- `WORKFLOW.md` - 标准开发工作流程和最佳实践
- `CODE_QUALITY_RULES.md` - 代码质量标准和技术债务管理
- `ARCHITECTURE_RULES.md` - 架构设计原则和设计模式应用
- `GIT_RULES.md` - Git提交规范和分支管理策略

### 场景特定规则
- `FRONTEND_RULES.md` - 前端开发专用规则
- `BACKEND_RULES.md` - 后端开发专用规则
- `TESTING_RULES.md` - 测试相关规范
- `WORKPLACE_RULES.md` - 工作环境和团队协作规则
- `SECURITY_RULES.md` - 安全开发规范和OWASP防护

### AI辅助开发
- `AI_CODING_RULES.md` - AI辅助编程专用规则和最佳实践
- `UTILITY_RULES.md` - 常用工具函数和设计模式模板

### 配置文件
- `.gitignore` - 标准忽略文件模板

## 🎯 使用方法

### 在Claude中使用
1. 将相关规则文件内容复制到对话中
2. 告知Claude遵循这些规则进行开发
3. 根据项目类型选择对应的规则文件

### 在Cursor中使用
1. 将规则文件放在项目根目录
2. 在Cursor设置中引用这些规则文件
3. 或在代码注释中引用具体规则

### 示例使用
```markdown
请遵循以下规则进行开发：
- 参考 GENERAL_RULES.md 中的五个关键步骤
- 按照 GIT_RULES.md 进行版本控制
- 遵循 FRONTEND_RULES.md 的前端开发规范
```

## 🎯 核心目标

这套规则适用于所有编程任务，要求工程师以高级工程师的视角，严格按照流程执行任务，确保代码改动精准、高效，且不会引入问题或不必要的复杂性。

## 🔄 五个关键步骤

1. **明确任务范围** - 分析任务，制定清晰计划
2. **精准定位代码修改点** - 确定具体修改位置，避免无关改动
3. **最小化、隔离化的代码改动** - 只编写任务所需代码
4. **严格检查代码** - 检查正确性和副作用
5. **清晰交付成果** - 总结改动内容和原因

## 💡 核心编程原则

### 基本原则
- **DRY (Don't Repeat Yourself)** - 避免代码重复
- **KISS (Keep It Simple, Stupid)** - 保持简单设计
- **YAGNI (You Ain't Gonna Need It)** - 只构建必需功能
- **SOC (Separation of Concerns)** - 关注点分离
- **SRP (Single Responsibility Principle)** - 单一职责原则

### 设计原则
- **SOLID原则** - 面向对象设计的五大原则
- **组合优于继承** - 优先使用组合构建行为
- **减少可变状态** - 优先不可变对象
- **Unix哲学** - 模块化、清晰性、简单性

## ⚡ 规则要点

1. **语言规范**: 代码注释英文，用户交互中文
2. **内容控制**: 严格按需求执行，不私自扩展
3. **变更管理**: 先分析现有代码，确认方案后执行
4. **测试规范**: 适量测试，文件加入.gitignore
5. **前端开发**: 禁止私自mock数据
6. **代码优化**: 不改变原有功能
7. **架构设计**: 遵循SOLID原则和设计模式
8. **安全规范**: 实施OWASP防护和安全最佳实践
9. **AI辅助**: 多步规划，文件保持简短，描述性命名
10. **实用工具**: 复用常见模式，维护工具库

## 🔧 Git规则特色

### 强制要求
- **Git Add前确认**: 必须询问用户确认暂存文件
- **一句话提交**: 所有提交必须使用单行格式
- **用户配置检查**: 首次提交前验证username和email
- **分支命名**: 必须使用 `**/**` 格式（如 `feature/user-auth`）

## 🚀 工作流程

参考 `WORKFLOW.md` 中的标准流程：
- 任务分析 → 代码实现 → 代码审查 → 部署准备
- Git工作流和提交规范
- 项目设置和故障排除流程

## 🤖 AI辅助开发特色

- **多步规划策略**: 生成计划→分阶段实施→每步检查测试
- **AI优化的代码组织**: 文件<500行，描述性命名，清晰结构
- **提示工程指南**: 有效的AI交互模式和上下文管理
- **常用模式库**: 验证规则、错误处理、设计模式模板

## 🤝 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/new-rule`)
3. 提交更改 (`git commit -m 'feat(rules): add new coding rule'`)
4. 推送到分支 (`git push origin feature/new-rule`)
5. 创建 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 🔗 相关链接

- [GitHub仓库](https://github.com/Renewdxin/ai-coding-rules)
- [问题反馈](https://github.com/Renewdxin/ai-coding-rules/issues)
- [贡献指南](https://github.com/Renewdxin/ai-coding-rules/blob/main/CONTRIBUTING.md)

## 📞 联系方式

如有问题或建议，请通过以下方式联系：
- 创建 [GitHub Issue](https://github.com/Renewdxin/ai-coding-rules/issues)
- 提交 Pull Request

---

⭐ 如果这个项目对你有帮助，请给个星标支持！
