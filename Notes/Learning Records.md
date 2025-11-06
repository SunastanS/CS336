## 2025-11-03
- 学习了 GPT-2 预分词正则的作用与写法，并将其编译成模块常量以复用。
- 设计了 `process_pretokenize` 的数据结构：在 chunk 内使用哈希表去重预 token，并累计频次与 byte-pair 出现位置。
- 明确了局部 pair 统计与全局合并的接口（`ChunkStat` → `ByteCounter.append`），为后续 BPE 训练循环打下基础。

## 2025-11-06
- 梳理 `ChunkStat` 结构：将预 token 频次改用 `Counter` 聚合，byte pair occurrence 改用去重 `set`，避免跨 chunk 重映射爆炸。
- 搭建 `ByteCounter` 聚合流水线：新增 `_dirty` 标记和 `append_to_tmp`/`update_from_tmp`，实现 chunk 级累积与一次性全局重建。
- 整理预 token 排序逻辑与 ID 分配策略，准备后续填补 merge 循环与 tokenizer `encode` 逻辑。
