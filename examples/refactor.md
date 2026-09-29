# Refactor: Before & After

## Before (AI technical output)

> Extracted `RiskStratificationCalculator` from `services/assessment.py`. Moved 8 helper functions into the new class, injected `PatientRepository` via constructor. Updated all 3 callers (`routes/assessment.py`, `routes/followup.py`, `services/report.py`) to use the new class. No behavior change — all existing tests pass.
>
> Reason: `assessment.py` was 1200 lines, hard to navigate. The stratification logic is now testable in isolation.

## After (biz-speak output)

> **改了什么**
>
> 把「危险分层计算」这块逻辑从评估服务里独立出来，变成单独的模块。
>
> **行为不变**
>
> 用户侧没有任何变化——评估流程、分层结果、报告内容都和之前一样。
>
> **为什么改**
>
> 原来的评估服务代码太多（1200 行），危险分层逻辑混在里面，改一个地方容易影响其他地方。现在独立出来后，后续调整分层规则（比如新增危险因素、修改阈值）会更安全，也更容易测试。
