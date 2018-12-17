# Project california

California 是一个full stack用于股票策略研究的package.可用于股票交易信号的测试，预期收益率预测，投资组合优化,回测以及绩效归因等功能.

- **data**
    - panel： panel类型数据结构的holder
    - time_series: 时间序列类型数据的结构holder
    - rtns: 用于基于panel数据进行各类收益率的计算

- **signal**
   - analyzer: 通过PanelData的数据格式，对信号分析的流程进行整体调用
   - performance: 计算常用信号衡量指标(ic, sorted portfolio, long-short portfolio 等)
   - operator: 对信号进行变形的方法,此处的逻辑在于以变量形式呈现数据，以operator代表运算符加总数据或调整分布.
   - plotting: 基于matplotlib以及seaborn的信号表现绘图

- **combine**
    - start from heuristic and robust risk parity!
    - then working on regression, machine learning and so on and so forth

- **backtest** (未开始)
    - fast: 简单快速的向量化回测
    - slow: 可进行path dependent的for loop或event driven类型的回测

- **optimizer** (暂停)
    - quadratic: 简单二次优化
    - conic: 锥优化
    - 其他: 其他优化方法，如两次进行优化等trick，以及stochastic optimization的相关

- **attribute** (未开始)
    - rtn_based: 基于收益时间序列的归因
    - holding_based: 基于持仓的归因(brison, barra类等).又包括收益以及风险的attribution

## 功能实现
1. data
data 模块应当包含所有常用数据的基本处理和对齐 (当前仅有PanelData)

- **PanelData**
    - 数据整合对齐
    - 数据格式的转变(如由multi-index到2d dataframe)
    - 股票池的筛选 

- **rtns**
    - 无需复权数据的基于preclose进行调整的各类收益(close2close, open2open, vwap2vwap)
    - 其他收益率方式(连续收益等)

2. signal
此模块应当包含所有单因子测试，单因子处理的方式, 此模块应以2d dataframe的数据格式，统一接收信号，股票池，行业分组，收益等相关信息

- **analyzer**
    - 暂无

- **performance**
    - 应当包含所有必要信号表现衡量的函数与方法(除简单回测以外)
    - ic相关的标准
    - 分组组合的标准

3. backtest
此模块包括回测功能

- **fast**
    - 基于向量化的快速的回测

