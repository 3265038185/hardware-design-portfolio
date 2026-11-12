# 蓝桥杯嵌入式竞赛板实验

基于蓝桥杯 CT117E-M4 竞赛板（STM32G431）的两组实验：信号波形参数测试仪、DDS 信号源设计。

## 文档

- [`waveform-analyzer.md`](waveform-analyzer.md)：ADC + 定时器采样 + 波形识别 + LCD1602 显示
- [`dds-signal-source.md`](dds-signal-source.md)：STM32G431 + AD9850 的 1 kHz–40 MHz 信号源、扫频、按键/串口控制

## 硬件平台

- STM32G431RBT6（Cortex-M4，170 MHz）
- CT117E-M4 竞赛板
- AD9850 DDS 模块（DDS 信号源实验）
- 2.4 寸 TFT / LCD1602
- 4 个独立按键、USART1、LED、74HC373

## 说明

- 这里保留的是设计思路、引脚分配、测试数据和实验结论，方便复盘。
- 完整 Keil 工程源码未随报告一起归档；厂商 BSP、原理图和数据手册未放入仓库。
