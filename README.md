# Hunter V2 · 开源人形机器人硬件

> 快装快换，随心所造。

**Hunter V2** 是南京因克斯智能科技有限公司与桥介数物联合打造的开源人形机器人。因克斯负责硬件设计与制造，桥介数物负责软件开发，双方共同推进 Hunter 系列机器人的持续迭代。

本仓库 `hunter130_hardware` 提供 Hunter V2（EC H130-V2）的机械模型、电气资料、机器人描述文件和安装手册，供开发者开展结构研究、装配、仿真接入与二次开发。

## 项目亮点

- **第二代关节**：采用因克斯第二代关节模组，支持快速拆装，便于维护与更换。
- **25 个自由度**：覆盖躯干、双臂与双腿，为人形机器人的运动研究与开发提供硬件基础。
- **硬件与软件协作**：因克斯负责硬件，桥介数物负责部署与训练相关软件。
- **持续迭代**：延续 Hunter V1 的开源合作，继续更新 Hunter 系列机器人及配套资源。

## 基本参数

| 项目 | 规格 |
| --- | --- |
| 产品名称 | Hunter V2 |
| 硬件型号 | EC H130-V2 |
| 身高 | 130 cm |
| 整机重量 | 约 32 kg |
| 全身自由度 | 25 |
| 关节模组 | 因克斯第二代关节，支持快速拆装 |
| 硬件设计与制造 | 南京因克斯智能科技有限公司 |
| 软件开发 | 桥介数物 |

## 仓库内容

```text
hunter130_hardware/
├── Mechanical/                       # 机械模型与安装手册
│   ├── EC-H130-V2_装配体.x_t         # Parasolid 格式整机装配模型（Git LFS）
│   └── EC H130-V2 产品安装手册.md
├── Electrical/                       # 电气资料
│   └── Pcb/
│       ├── PMS/                      # PMS 板 PDF 与三维模型
│       ├── 腿部电容板/                # 腿部电容板 PDF 与三维模型
│       └── 髋中心板/                  # 髋中心板 PDF 与三维模型
├── URDF/                             # 机器人描述与网格资源
│   ├── EC-H130-V2_URDF.urdf
│   └── meshes/                       # STL 网格文件
├── LICENSE
└── README.md
```

| 资源 | 入口 | 内容 |
| --- | --- | --- |
| 安装手册 | [EC H130-V2 产品安装手册](Mechanical/EC%20H130-V2%20产品安装手册.md) | 装配注意事项、安装步骤、操作说明与物料清单 |
| 机械模型 | [Mechanical](Mechanical/) | Parasolid 格式的整机装配模型 |
| 电气资料 | [Electrical](Electrical/) | PMS 板、腿部电容板和髋中心板的 PDF 与 STEP 文件 |
| 机器人描述 | [URDF](URDF/) | URDF 文件及其引用的 STL 网格资源 |

## 开始使用

### 下载完整模型

本仓库使用 [Git LFS](https://git-lfs.com/) 管理 STEP/STP、Parasolid（X_T/X_B）和 STL 模型，文件扩展名不区分大小写。请先安装 Git 和 Git LFS，再执行：

```bash
git lfs install
git clone https://github.com/EncosTech/hunter130_hardware.git
cd hunter130_hardware
git lfs pull
```

已有本地仓库时，在仓库目录执行 `git lfs install`、`git pull` 和 `git lfs pull`。使用 `git lfs ls-files` 可以查看由 LFS 管理的文件。

如果模型文件只有几行文本，并以 `version https://git-lfs.github.com/spec/v1` 开头，说明下载到的是 LFS 指针；请执行 `git lfs pull` 获取完整模型。GitHub 的 **Download ZIP** 是否包含模型原文件取决于仓库设置，建议使用上面的克隆方式。

### 使用资料

1. **了解结构与装配要求**：先阅读[安装手册](Mechanical/EC%20H130-V2%20产品安装手册.md)，了解装配流程、所需物料与安全操作要求。
2. **查看机械模型**：使用支持 STEP 或 Parasolid 的 CAD 工具打开 [Mechanical](Mechanical/) 中的模型。
3. **查看电气资料**：按板卡类别查阅 [Electrical/Pcb](Electrical/Pcb/) 下的 PDF 与三维模型。
4. **接入仿真或可视化工具**：加载 [EC-H130-V2_URDF.urdf](URDF/EC-H130-V2_URDF.urdf)，并保留其与 `meshes/` 文件夹的相对位置。接入具体平台时，请按平台要求配置资源路径与控制接口。

## 软件与后续计划

本仓库聚焦硬件资料。部署程序与训练程序由桥介数物负责，作为配套软件开源内容持续更新；相关仓库链接将在公布后补充到此处。

后续计划兼容桥介 **RoboCraft AI** 平台，该项为规划内容。硬件资料与软件资源将随 Hunter 系列迭代持续完善。

## 反馈与贡献

欢迎通过 Issues 反馈资料问题、装配经验与改进建议，也欢迎提交 Pull Request 完善文档和设计资料。反馈时请注明硬件版本、相关文件路径，以及便于复现问题的说明或图片。

提交模型前，请在本地仓库执行 `git lfs install`。根目录的 `.gitattributes` 会自动将上述模型格式交给 LFS；按平常的 `git add`、`git commit`、`git push` 流程提交即可，推送时会同时上传 LFS 文件。新增其他大文件格式时，请先使用 `git lfs track` 配置追踪，并将更新后的 `.gitattributes` 一起提交。配置说明见 [GitHub 官方文档](https://docs.github.com/en/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage)。

## 许可证

除另有说明的第三方材料外，本仓库由项目权利人提供的硬件设计文件、机器人描述文件及配套文档采用 **CERN Open Hardware Licence Version 2 – Strongly Reciprocal（CERN-OHL-S-2.0）** 授权。完整条款见 [LICENSE](LICENSE)。

SPDX-License-Identifier: CERN-OHL-S-2.0

允许依照许可证使用、复制、修改、制造和销售。对外分发相关设计或产品时，须履行许可证规定的完整源文件提供、声明保留和修改标注等义务；适用例外以许可证原文为准。

第三方材料遵循各自的许可证。本项目文档中的安全提示、产品使用说明和合规说明不构成对 CERN-OHL-S-2.0 授予权利的附加限制，也不赋予任何一方单方面更改该许可证的权利。
