# Warm Blob in NZ · Han Remake

> 复刻新西兰“暖水团（Warm Blob）”分析：从 SODA 温盐数据计算 Brunt–Väisälä 频率、
> 密度异常与显著性，并出图；另含 CMEMS 海平面高度示例数据。

## 状态

**冻结（2024）**：分析已完成，2026-11-25 补文档与 `.gitignore`；数据路径仍需手工改。

## 内容与结论

- 用 SODA 月平均温盐计算绝对盐度、保守温度、sigma0 与浮力频率 N²；
- 对暖水团时段（1984–1987、2001、2017–2018、2021–2022）做月/季平均与异常；
- t 检验标记显著异常，Cartopy 出图（含显著性打点）。

## 快速开始

```bash
python3 -m venv .venv && . .venv/bin/activate
pip install numpy xarray matplotlib scipy gsw cartopy netCDF4 jupyter
jupyter lab
```

三个 notebook 建议按顺序跑：

| Notebook | 作用 |
|---|---|
| `calculate brunt_visala freqv2.ipynb` | 读取 SODA，算盐度/温度/密度/N²，导出中间结果 |
| `figSSTA_MLDv2.ipynb` | 海表温度异常与混合层深度图 |
| `fig_sla.ipynb` | 海平面高度异常（用仓库内 CMEMS `.nc`） |

**先改数据路径**：notebook 里硬编码了本机路径（如 `D:\data\observation\...`），
请改成自己的 SODA 目录。仓库内只附一个 CMEMS SSH 月度文件（82MB），SODA 原始数据需自行获取。

## 目录结构

| 路径 | 说明 |
|---|---|
| `calculate brunt_visala freqv2.ipynb` | 核心物理量计算 |
| `figSSTA_MLDv2.ipynb` / `fig_sla.ipynb` | 出图 |
| `cmems_obs-...P1M-m_...nc` | CMEMS 海平面高度示例数据（82MB） |
| `hanremake/Fig1.png` | 复刻图成品 |

> 82MB 的 `.nc` 与 20MB 的 notebook 输出属历史遗留；新数据请放 `data/`（已被 `.gitignore` 忽略）。

## 数据来源

- SODA：Simple Ocean Data Assimilation 月平均温盐（需自行下载，版本以 notebook 内路径为准）。
- CMEMS：`cmems_obs-sl_glo_phy-ssh_my_allsat-l4-duacs-0.25deg_P1M-m`（哥白尼海洋服务）。

## 许可

未声明开源许可证，默认保留所有权利。
SODA/CMEMS 数据遵循各自发布方的使用条款，不在本仓库授权范围内。
