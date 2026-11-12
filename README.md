# PCB 设计与蓝桥杯信号源实验

硬件方向的作品集，包含 3 套可直接用于打样的 PCB Gerber 文件，以及蓝桥杯嵌入式竞赛板上的两份实验报告/设计方案。

## 内容

| 目录 | 内容 | 说明 |
|------|------|------|
| [`pcb/51-mcu-core-board`](pcb/51-mcu-core-board) | 51 单片机核心板 Gerber | 2 层板，含顶层/底层铜箔、丝印、阻焊、钢网、板框和钻孔文件 |
| [`pcb/stm32-dev-board`](pcb/stm32-dev-board) | STM32 开发板 Gerber | 2 层板，含完整的 Gerber + 飞针测试文件 |
| [`pcb/usb-hub`](pcb/usb-hub) | USB HUB 板 Gerber | 2 层板，含完整 Gerber + 钻孔文件 |
| [`lanqiao-cup/waveform-analyzer.md`](lanqiao-cup/waveform-analyzer.md) | 信号波形参数测试仪 | STM32G431 + ADC + LCD1602，识别正弦/三角/脉冲波并测量 Vpp、频率、占空比 |
| [`lanqiao-cup/dds-signal-source.md`](lanqiao-cup/dds-signal-source.md) | DDS 信号源设计 | STM32G431 + AD9850，1 kHz–40 MHz 正弦/方波、自动扫频、按键 + 串口控制 |

## PCB 文件说明

每套 Gerber 目录包含：

```text
Gerber_TopLayer.GTL              顶层铜箔
Gerber_BottomLayer.GBL           底层铜箔
Gerber_TopSilkscreenLayer.GTO    顶层丝印
Gerber_BottomSilkscreenLayer.GBO 底层丝印
Gerber_TopSolderMaskLayer.GTS    顶层阻焊
Gerber_BottomSolderMaskLayer.GBS 底层阻焊
Gerber_TopPasteMaskLayer.GTP     顶层钢网
Gerber_BottomPasteMaskLayer.GBP  底层钢网
Gerber_BoardOutlineLayer.GKO     板框
Gerber_DocumentLayer.GDL         文档层
Gerber_DrillDrawingLayer.GDD     钻孔图
Drill_PTH_Through.DRL            金属化孔
Drill_PTH_Through_Via.DRL        过孔
Drill_NPTH_Through.DRL           非金属化孔
FlyingProbeTesting.json          飞针测试文件
PCB下单必读.txt                   打样说明
```

这些是 **制造文件**，不是 EDA 源工程（如 Altium/立创EDA 的 `.PcbDoc` / `.epro`）。可以直接打包给 PCB 厂打样；如果需要修改设计，需要原始工程文件。

## 蓝桥杯实验

### 信号波形参数测试仪

- MCU：STM32G431RBTx
- 采样：TIM2 触发 ADC，10 kHz 采样率
- 算法：根据采样点分布识别正弦波、三角波、脉冲波；计算峰峰值、频率、占空比
- 显示：LCD1602
- 关键点：定时器触发 ADC、波形特征判别、频率/占空比计算

完整报告：[`lanqiao-cup/waveform-analyzer.md`](lanqiao-cup/waveform-analyzer.md)

### DDS 信号源

- MCU：STM32G431RBT6，HSE 24 MHz，PLL 170 MHz
- DDS：AD9850 模块（30 MHz 有源晶振，6 倍频到 180 MHz）
- 输出：正弦波 1 kHz–40 MHz，频率步进 1 kHz；方波频率/占空比可调
- 扫频：1 kHz–40 MHz，步进 1 kHz，驻留 100 ms
- 交互：4 个按键 + USART1 远程命令（`SETF:`、`SETT:`、`SETS:`、`ASKS:`）
- 显示：2.4 寸 320×240 TFT（ILI932X，8 位并口）
- 实测：频率误差 < 0.2%，扫频平稳，方波占空比可调

完整方案：[`lanqiao-cup/dds-signal-source.md`](lanqiao-cup/dds-signal-source.md)

> 蓝桥杯部分保留的是设计方案和实验报告；竞赛板的厂商 BSP、原理图和数据手册属于第三方资料，未放入本仓库。

## 说明

- 三套 PCB 均为课程/练习阶段的 2 层板设计，适合作为 Layout 入门案例；未做阻抗控制、EMC 和高速信号完整性设计。
- Gerber 文件可以用 KiCad Gerber Viewer、立创EDA 的 Gerber 查看器或 PCB 厂的在线预览打开。
- 打样前请再次确认板框、钻孔和阻焊开窗；不同厂家的工艺能力不同。

## 相关项目

- [STM32 外设实验合集](https://github.com/3265038185/stm32-peripheral-labs)
- [ESP32 + 华为云 IoT 智能家居](https://github.com/3265038185/esp32-huaweicloud-smart-home)
- [MATLAB 数字图像处理实验](https://github.com/3265038185/matlab-digital-image-processing)
