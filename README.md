# 武侠动作 · 雨歇

基于 Godot 4.6.2 的 3D 武侠动作游戏。雨后的山庭、三盏封印灯与一场终局决斗，构成一个围绕走位、弹反、残影和剑意展开的单地图战斗章节。

## 核心玩法

- 三种兵刃：均衡的直剑、擅长打断的重刃，以及能在第三击发射剑气的灵刃。
- 攻防博弈：观察敌人起手动作，利用格挡、适时弹反与闪避寻找破绽。
- 残影回斩：冲刺留下短暂残影，回斩穿过路径上的敌人。
- 推掌与碰撞：将敌人推向墙壁或其他敌人，并反射飞行攻击。
- 剑意爆发：积累剑意后释放范围剑斩，获得短时间强化。
- 关卡成长：解除封印、选择强化，并挑战双阶段首领；提供三档难度。
- 当前单局内支持封印检查点，退出游戏不会保存本局进度。

## 开始运行

安装 **Godot 4.6.2**，将 Godot 可执行文件加入 PATH，或直接使用编辑器导入项目。

```bash
git clone https://github.com/kakssjs/wuxiadongzuo.git
cd wuxiadongzuo
godot --headless --editor --path . --import --quit
godot --path .
```

在编辑器中打开 `project.godot`，按 **F5** 运行。默认场景为 `scenes/rebirth/Stillwater.tscn`，游戏界面为中文。

## 操作说明

| 动作 | 按键 |
| --- | --- |
| 移动 | WASD / 方向键 |
| 攻击、连续攻击 | 鼠标左键 / J，可按住连击 |
| 格挡、适时弹反 | 鼠标右键 / K |
| 冲刺并留下残影 | Shift / 空格 / L |
| 回斩 / 推掌 | Q / E |
| 剑意爆发 | V，剑意满时使用 |
| 饮酒治疗 | R，次数有限 |
| 激活封印 / 破势追击 | F |
| 切换直剑 / 重刃 / 灵刃 | 1 / 2 / 3 |
| 暂停 / 全屏 | Esc / F11 |

## 项目结构

| 路径 | 用途 |
| --- | --- |
| `project.godot` | 引擎设置、输入映射与默认入口 |
| `scenes/rebirth/` | 当前 3D 场景 |
| `scripts/rebirth/Stillwater.gd` | 场景、遭遇、成长与关卡流程 |
| `scripts/rebirth/Duelist.gd` | 移动、战斗状态、体力与架势 |
| `scripts/rebirth/StillwaterUI.gd` | 标题、HUD、设置与结算界面 |
| `scripts/rebirth/CombatPuppet.gd` | 角色动画与外观 |
| `assets/`、`resources/` | 模型、音频、字体及资源配置 |
| `tests/` | 回归测试 |
| `scripts/tools/` | 测试、录制、资源处理与打包工具 |
| `docs/` | 设计、开发与素材文档 |

仓库也包含可独立运行的 2D 场景，其操作与 3D 模式不同。如需查看，可在编辑器中打开 `scenes/interface/TitleScreen.tscn` 并按 F6，默认入口仍为 3D 游戏。

## 开发与验证

建议围绕现有场景和脚本增量修改。战斗改动关注 `scripts/rebirth/`，界面改动关注 `StillwaterUI.gd`，资源处理遵循 `AGENTS.md`。

安装 Python 3 并确保 Godot 位于 PATH 后，从项目根目录执行：

```bash
python scripts/tools/run_tests.py
```

测试结果不能代替实际游玩；修改战斗、输入或渲染后，还需在编辑器中检查相应交互。导出桌面版本需要匹配的 Godot 导出模板，具体流程见 [开发文档](docs/DEVELOPMENT.md)。

代码与素材的许可范围分别见 [LICENSE](LICENSE)、[LICENSE_SCOPE.md](LICENSE_SCOPE.md) 和 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
