# BBDXXX Examples
Software examples for Thorlabs' BBD series benchtop controllers

## BBD30X.py
This example uses the Kinesis C/C++ library and the Python module 'ctypes'´.

## bbd_pythonnet.py
This example uses the Kinesis .NET library and the Python module 'pythonNET'.

## 使用 Python 同时控制两路 BBD302 平移台 (Control two BBD302 channels with Python)
`BBD30X_trigger.py` 已经演示了 BBD302 的两路通道（channel 1 和 channel 2）并列使用，适合双轴平移台：

1. 安装 `pythonnet`：`pip install pythonnet`。保证 `clr.AddReference` 的路径指向本机已安装的
   Kinesis DLL（默认 `C:\Program Files\Thorlabs\Kinesis`）。
2. 将脚本中的 `serial_no` 改为你的 BBD302 序列号。
3. 运行脚本后，它会对两个通道分别 `StartPolling`、`EnableDevice`，依次 `Home`，
   然后按 `new_pos`（通道1）和 `new_pos_ch2`（通道2）设定的位置移动。按需修改这两个位置值即可控制各平移台。
4. 如需并用但不需要触发输出，可保留核心启用/回零/MoveTo 代码，注释掉中间的触发配置段。
5. 没有接硬件时，可取消注释 `SimulationManager.Instance.InitializeSimulations()` 与结尾的
   `UninitializeSimulations()` 行在仿真模式下演练。


## BBD30x_Serial_Command_pySerial.py

This example uses serial commands as documented in the "APT Communications Protocol" and the Python module "pyserial". Please follow the following steps to setup a Virtual Communication Port for Windows OS. 
1. Power up the device and connect the device to the PC using the USB cable
2. Open the device manager by selecting Start/Control Panel/Device Manager/
3. Click ‘USB Serial Bus Controllers’ and select the APT USB Device to be configured, then right click and select ‘Properties’.
4. Select the ‘Advanced’ tab, and check the ‘Load VCP’ box.
5. Click OK, then power cycle the device being configured.
6. In the device manager, click ‘Ports (COM & LPT)’, and note the ‘APT USB Device Serial Port’ COM port number (e.g. COM3). This COM port can then be used for low level protocol messages.
