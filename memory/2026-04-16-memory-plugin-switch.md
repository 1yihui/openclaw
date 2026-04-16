# 2026-04-16 memory 插件切换记录

## 结论
- 已卸载 `memory-lancedb-pro`
- 已切换 `plugins.slots.memory` 为 `memory-core`
- 已启用 `plugins.entries.memory-core.config.dreaming.enabled = true`
- 已移除 `plugins.load.paths` 中的 `/opt/homebrew/lib/node_modules/memory-lancedb-pro`
- 已清理残留的 `plugins.entries.memory-lancedb-pro` stale config

## 现场依据
- 原活动 memory slot: `memory-lancedb-pro`
- 原外部加载路径: `/opt/homebrew/lib/node_modules/memory-lancedb-pro`
- 原报错本质：当前插件不支持 `dreaming`
- 变更后运行态：`plugins.slots.memory = "memory-core"`

## 验证结果
- `config.get` 显示当前运行态：
  - `plugins.slots.memory = "memory-core"`
  - `plugins.entries.memory-core.enabled = true`
  - `plugins.entries.memory-core.config.dreaming.enabled = true`
  - `plugins.load.paths = []`
- `npm uninstall -g memory-lancedb-pro` 已成功返回：`removed 33 packages in 615ms`

## 风险提示
- 从 `memory-lancedb-pro` 切回 `memory-core` 后，原先依赖 pro 插件的能力（如 hybrid retrieval / smartExtraction 等）不再可用。
- 当前目标是恢复 `dreaming`，该目标已满足。
