# 天气图像分类

使用 PaddlePaddle 和 ResNet50 对五类天气图片进行分类，类别为 `cloudy`、`foggy`、`rainy`、`snowy` 和 `sunny`。项目重点处理数据增强、类别间混淆、Focal Loss、学习率调度和错误样本分析。

## 目录结构

```text
weather-image-classification/
├─ notebooks/weather-classification-v5.ipynb # 推荐阅读和运行版本
├─ experiments/weather-classification-v4.ipynb
├─ data/README.md
├─ results/
└─ requirements.txt
```

## 主要方法

- ResNet50 预训练模型与五分类输出层；
- 训练集随机增强与验证集固定预处理；
- 针对 `sunny`/`cloudy` 混淆加强数据增强；
- 使用 Focal Loss 关注难分类样本；
- Linear Warmup 与学习率调整；
- 分类报告、混淆矩阵和错误样本可视化。

## 运行

建议使用 Python 3.10。PaddlePaddle 的 CPU/GPU 版本应根据机器环境单独安装。

```bash
python -m pip install -r requirements.txt
jupyter lab
```

按照 `data/README.md` 准备数据，然后从仓库根目录打开主 Notebook。公开版已经把原有百度 AI Studio 绝对路径替换为相对路径。

## 历史结果

原始 v5 实验记录的最佳验证准确率约为 **96.29%**，后续训练出现约 95%～94.5% 的回落，表现出过拟合迹象。不同阶段报告过 95.34%、96.11% 等结果，差异来自数据版本、训练轮次和评估阶段。

公开 Notebook 已清除中断异常、设备日志和历史执行输出。上述数字是历史记录，不代表公开版本未经重新运行即可复现。

## 已知限制

- 原始数据集和模型权重未公开；
- 数据增强和类别采样仍可进一步系统化；
- Notebook 含多轮实验代码，后续应拆成训练、评估和预测脚本；
- 团队成员个人 Notebook 与含姓名/学号的报告保留在私有归档，未纳入公开仓库。

## 迭代时间线

| 日期 | 阶段 |
| --- | --- |
| 2026-05-06 前后 | ResNet50 基线、五分类数据读取与 v4 迭代 |
| 2026-05 | Focal Loss、增强策略、错误分析与 v5 |
| 2026-05-31 | 项目材料汇总 |
| 2026-10-12 | 提取主版本、脱敏路径并整理公开仓库 |

日期来自 Notebook 内容和现存文件时间，不等同于 Git 提交历史。

## 使用与授权

本仓库用于个人学习经历与作品集展示，当前未授予复制、修改、再发布或商业使用许可。项目包含团队协作形成的内容；如需引用或复用，请先联系仓库维护者并确认相关贡献者及数据来源的授权。
