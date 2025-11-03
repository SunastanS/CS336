## 2025-03-27
- 学习了 GPT-2 预分词正则的作用与写法，并将其编译成模块常量以复用。
- 设计了 `process_pretokenize` 的数据结构：在 chunk 内使用哈希表去重预 token，并累计频次与 byte-pair 出现位置。
- 明确了局部 pair 统计与全局合并的接口（`ChunkStat` → `ByteCounter.append`），为后续 BPE 训练循环打下基础。
