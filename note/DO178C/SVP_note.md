# SVP 【CSM100电机控制器软件验证计划】

## 6.4软件编码和集成阶段

### 1. DO-178C 标准中软件编码和软件集成的目标

&emsp;&emsp;DO-178C（Software Considerations in Airborne Systems and Equipment Certification）是航空软件认证的核心标准，其软件编码（Coding Process）和软件集成（Integration Process）属于软件开发过程（Section 5.3和5.4）。这些过程的目标主要定义在Annex A的Table A-5（Verification of Outputs of Software Coding & Integration Processes）中，共有9个主要目标。

以下是Table A-5的目标列表 **( 软件编码和集成过程输出的验证 )**  ，使用表格呈现以便清晰：

| 目标编号 | 目标描述 | 适用DAL及独立性要求 |
|----------|----------|---------------------|
| A-5-1 | 源代码符合低级需求（Source Code complies with low-level requirements） | A, B, C, D（独立性：A, B, C） |
| A-5-2 | 源代码符合软件架构（Source Code complies with software architecture） | A, B, C, D（独立性：A, B, C） |
| A-5-3 | 源代码是可验证的（Source Code is verifiable） | A, B, C（独立性：A, B） |
| A-5-4 | 源代码符合标准（Source Code conforms to standards） | A, B, C（独立性：A） |
| A-5-5 | 源代码可追溯到低级需求（Source Code is traceable to low-level requirements） | A, B, C（独立性：A） |
| A-5-6 | 源代码准确且一致（Source Code is accurate and consistent） | A, B, C, D（独立性：A, B, C） |
| A-5-7 | 软件集成过程的输出完整且正确（Output of software integration process is complete and correct） | A, B, C, D（独立性：A, B, C） |
| A-5-8 | 参数数据项文件正确且完整（Parameter Data Item File is correct and complete） | A, B, C, D（独立性：A, B, C） |
| A-5-9 | 参数数据项文件符合软件架构（Parameter Data Item File complies with software architecture） | A, B, C, D（独立性：A, B, C） |

参数数据项 (PDI) ：不修改可执行目标代码，但影响软件行为的静态数据。  
参数数据项文件 (PDI File) ：包含一个或多个 PDI 的文件，直接可被目标计算机处理系统使用。
这些数据在目标计算机中加载，与软件并存，作为独立配置项管理。

### 2. 针对每个目标的具体验证方法和工具

- **A-5-1: 源代码符合低级需求**  
  方法：单元测试（验证功能实现）、追溯审查。  
  工具：Simulink Test（模型测试）、VectorCAST（单元测试）、Simulink Code Inspector（比较模型与生成的C代码）。  

- **A-5-2: 源代码符合软件架构**  
  方法：架构审查、代码生成器配置审查（确保其配置（如文件划分、函数接口）符合软件架构文档 (SAD) 中定义的结构）、代码审查。  
  工具：VectorCAST（集成测试）。  

- **A-5-3: 源代码是可验证的**  
  方法：不可达代码和死代码分析（评估可测试性）、圈复杂度分析（避免复杂结构）。  
  工具：simulink Test（模型）Vector CAST（源代码）覆盖率测试；（评估代码复杂度）；Polyspace（验证无未定义行为）。  

- **A-5-4: 源代码符合标准**  
  方法：静态分析（检查编码规则，如MISRA C）；代码审查。  
  工具：simulink 模型顾问（检查模型规范）；Polyspace Bug Finder（MISRA C编码规范检查）。  

- **A-5-5: 源代码可追溯到低级需求**  
  方法：追溯分析（手动/自动化矩阵审查）。  
  工具：Requirements Gateway（MathWorks工具，用于模型-需求-代码追溯）  

- **A-5-6: 源代码准确且一致**  
  方法：静态分析（检测不一致，如死代码）；单元/集成测试。  
  工具：VectorCAST（结构覆盖分析，确保一致执行）；Simulink Code Inspector（验证代码准确性）。  

- **A-5-7: 软件集成过程的输出完整且正确**  
  方法：硬件/软件集成测试；覆盖分析（语句/分支/MC/DC覆盖）。  
  工具：VectorCAST（聚合覆盖报告）。  

- **A-5-8: 参数数据项文件正确且完整**  
  方法：静态分析（检查PDI值和结构）；集成测试（验证加载和执行）。  
  工具：Polyspace Bug Finder（PDI缺陷检测）；Embedded Coder（生成和验证PDI文件）。  

- **A-5-9: 参数数据项文件符合软件架构**  
  方法：审查（检查PDI与架构兼容性）；分析（数据流一致性）。  
  工具：Simulink Code Inspector（模型-PDI-架构比较）

