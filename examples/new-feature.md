# New Feature: Before & After

## Before (AI technical output)

> Added `exportToExcel()` in `routes/reports.py`. Uses `openpyxl` to generate `.xlsx` files from the `Assessment` model. Added a download button in `templates/report_list.html` that calls `/api/reports/<id>/export`. Also added `Content-Disposition` header for proper filename encoding.
>
> Tests: 12 new tests in `test_export.py`, all passing.

## After (biz-speak output)

> **功能**
>
> 评估报告现在可以导出为 Excel 文件。
>
> **用户能做什么**
>
> 在报告列表页，每条报告旁边多了一个「下载 Excel」按钮。点击后自动下载该报告的完整数据（包括老人基本信息、评估结果、危险分层），文件名包含老人姓名和日期。
>
> **入口**
>
> 报告列表页（首页 → 评估报告），每条记录右侧。
