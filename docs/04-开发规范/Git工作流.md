# Git 工作流

---

## 1. 分支策略

```
main           ← 始终可发布版本，受保护
  ↑
develop        ← 集成分支，所有 feature 合入此处
  ↑
feature/xxx    ← 功能开发分支
fix/xxx        ← BUG 修复分支
hotfix/xxx     ← 紧急线上修复（直接合 main 后回流 develop）
```

---

## 2. 分支命名

| 类型 | 命名 | 示例 |
|---|---|---|
| 新功能 | `feature/<模块>-<简述>` | `feature/toss-scoring` |
| 修复 | `fix/<模块>-<简述>` | `fix/physics-jitter` |
| 紧急修复 | `hotfix/<简述>` | `hotfix/ad-crash` |
| 重构 | `refactor/<简述>` | `refactor/event-bus` |
| 文档 | `docs/<简述>` | `docs/update-prd` |

---

## 3. 提交信息规范（Conventional Commits）

```
<type>(<scope>): <subject>

<body>

<footer>
```

### type 类型
- `feat`：新功能
- `fix`：BUG 修复
- `docs`：文档变更
- `style`：代码格式（不影响逻辑）
- `refactor`：重构
- `perf`：性能优化
- `test`：测试相关
- `chore`：构建/工具/杂项
- `phys`：物理参数调整（项目特定）
- `art`：美术资源更新（项目特定）

### 示例
```
feat(toss): 实现 4 枚羊拐落地形态识别

- 新增 ShagaiOrientationDetector
- 集成到抛掷流程

Refs: #12
```

---

## 4. 合并规则

- 所有合入 `main` / `develop` 必须 Pull Request
- 至少一人 Code Review（如果是单人项目可豁免，但仍走 PR 留痕）
- 必须通过 CI（如果有）
- 合并方式：**Squash and Merge**（保持主分支提交干净）

---

## 5. 大文件 / 二进制

- **不在 Git 中存大资源**（贴图 > 1MB、模型、音频）
- 使用 Git LFS 或外部资源仓库
- `.gitignore` 必须包含：`node_modules/`、`build/`、`temp/`、IDE 配置等

---

## 6. 仓库初始化（待 Phase 0 末尾执行）

待技术选型完成后再初始化 Git 仓库，避免初期框架反复重建。
