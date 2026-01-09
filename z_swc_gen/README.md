SWC from Excel
================

This example demonstrates generating AUTOSAR ARXML component documents from an Excel spreadsheet using the `autosar` library.

Spreadsheet format
- The first sheet is used.
- First row must be headers. Required columns (case-insensitive): `Component`, `Port`, `Direction`, `DataType`.
- Optional column: `InitValue`.

Direction values: `provide`/`out` create a provided port; other values create a required port.

Usage
-----
1. Install dependency:

```powershell
pip install openpyxl
```

2. Run the example:

```powershell
python swc_from_excel.py path\to\spec.xlsx [output_dir]
```

Generated ARXML files are written into the `generated` folder by default.

Notes
-----
- The script creates one `SenderReceiverInterface` per port, using a single `VariableDataPrototype` referencing an implementation data type.
- The generated XML is a simple example; you may need to adapt the mapping for more advanced AUTOSAR features (runnables, operations, mode-changes, etc.).


Prompts
-----

我在基于Autosar开发项目，myswcautosar.xlsx 是我的软件组件所需要的输入输出列表，清晰的给出了（SWCName	Direction	PortName	InterfaceName	ElementName	InterfaceType	ElementDataType）， 我期望你帮我开发一个python脚本，放在z_swc_gen文件夹下
1.读取我给你的excel，里边包含了上述接口信息，表格中通常包含多个输入输出。
2.根据接口信息，帮我生成autosar的swc描述文件arxml文件
3.你可以借鉴z_swc_gen\application_component.py 中的代码实现，，在代码里将创建数据类型、创建interface、创建port、创建runnable、access等函数化方便我排查问题
4.最终输出一个myswc_gen_.arxml中
5.你在使用指令时需要在.venv 环境下，import autosar库已经安装好
