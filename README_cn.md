# 中文 | [English](README.md)

# tron1-rl-isaaclab

> 🧭 **TRON1 开源生态的一部分。** TRON1 全部开源仓库和上手路线：[TRON1 开源生态](https://github.com/limxdynamics/tron1-rl-isaacgym/blob/master/README_cn.md#tron1-开源生态)。

基于 [Isaac Lab](https://isaac-sim.github.io/IsaacLab/) 的 LimX **TRON1** 双足机器人强化学习训练栈，使用 PPO 训练 locomotion 策略。本仓库扩展了 Isaac Lab 模板，支持 TRON1 机器人变体的 Sim-to-Real 训练。

## 环境要求

- Isaac Sim + Isaac Lab，且 isaaclab / isaaclab_tasks / isaaclab_rl 可被 import
- Python 3.10
- GPU（推荐 >= 12 GB 显存，用于多环境训练）

## 安装

```bash
# 1. clone 仓库
git clone https://github.com/limxdynamics/tron1-rl-isaaclab.git
cd tron1-rl-isaaclab

# 2. editable install extension 与 vendored rsl_rl
pip install -e exts/bipedal_locomotion
pip install -e rsl_rl
```

> **说明：** 机器人模型资产（USD 文件）已内置在 `exts/bipedal_locomotion/bipedal_locomotion/assets/usd/` 中，覆盖 SF_TRON1A 和 WF_TRON1A 两种变体，无需额外下载模型文件。

## 训练

任务 ID 在 exts/bipedal_locomotion/ 中注册。

```bash
# Solefoot (SF)
python scripts/rsl_rl/train.py --task Isaac-Limx-SF-TRON1A-Blind-Flat-v0 --num_envs 4096 --headless

# Wheelfoot (WF)
python scripts/rsl_rl/train.py --task Isaac-Limx-WF-TRON1A-Blind-Flat-v0 --num_envs 4096 --headless
```

常用选项：
- --checkpoint_path <path> -- 从指定的 .pt checkpoint 恢复训练
- --video -- 启用视频录制
- --max_iterations N -- 覆盖最大迭代次数

日志路径：logs/rsl_rl/<experiment_name>/<timestamp>_<run_name>/

## 机器人形态

| 形态 | 末端 | Task ID 前缀 |
|---|---|---|
| SF_TRON1A | sole foot (ankle pitch) | Isaac-Limx-SF-TRON1A-... |
| WF_TRON1A | wheel | Isaac-Limx-WF-TRON1A-... |

## 相关仓库

| 仓库 | 描述 |
|---|---|
| [tron1-robot-description](https://github.com/limxdynamics/tron1-robot-description) | TRON1 机器人模型文件 |
| [tron1-rl-isaacgym](https://github.com/limxdynamics/tron1-rl-isaacgym) | TRON1 Isaac Gym RL 训练 |
| [tron1-rl-deploy-ros](https://github.com/limxdynamics/tron1-rl-deploy-ros) | TRON1 RL 部署（ROS） |
| [tron1-rl-deploy-python](https://github.com/limxdynamics/tron1-rl-deploy-python) | TRON1 RL 部署（Python） |

## 许可证

[Apache 2.0](LICENCE)。
