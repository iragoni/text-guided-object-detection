# 命令行入口

计划中的脚本（随实现逐步补充）。所有脚本应支持 `--config` 并记录运行配置与随机种子。

| 脚本 | 用途 |
| --- | --- |
| `prepare_visdrone.py` | VisDrone 标注转换、类别映射、忽略区域处理与回画核验 |
| `build_pairs.py` | 构建图像—中文指令—目标集合配对数据与划分清单 |
| `train_detector.py` | YOLOv11s 候选检测训练（十类微调），导出候选框 |
| `train_matcher.py` | 区域—文本匹配模块训练（分阶段：冻结编码器 → 解冻末层） |
| `quantize_text.py` | 语言模块训练后量化、校准、敏感层分析与恢复训练 |
| `evaluate.py` | 集合精确率/召回率/F1、拒识指标、消融与效率测量 |
| `export_demo.py` | 导出演示用权重与配置清单 |

```bash
python scripts/prepare_visdrone.py --root data/raw/VisDrone2019-DET --out data/processed
python scripts/build_pairs.py      --index data/index/pairs.jsonl --split data/splits
python scripts/train_detector.py   --config configs/detector.yaml
python scripts/train_matcher.py    --config configs/matcher.yaml
python scripts/quantize_text.py    --config configs/quant.yaml
python scripts/evaluate.py         --config configs/eval.yaml
```
