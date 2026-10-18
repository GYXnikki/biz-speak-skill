# Plan (not shipped yet): Before & After

## Before (AI technical output)

> 计划实现问卷草稿自动保存。方案：survey1.js 里挂一个定时器，停笔 30 分钟后触发 saveDraft()，调 POST /api/survey/draft；后端 drafts 表加 expires_at 字段，7 天后由清理任务删除。本地已跑通，新增 3 个用例 draft_create / draft_resume / draft_expire。
>
> 上线前待确认：清理任务的执行频率还没定。

## After (biz-speak output)

> **功能**
>
> 老人填健康问卷填到一半关掉页面，已填的内容会自动存成草稿；停笔 **30 分钟**后触发一次保存。
>
> **老人能做什么**
>
> 下次打开同一份问卷，会从上次停下的地方接着填，不用从头再来。
>
> **入口**
>
> 从「我的档案 → 健康问卷」重新进入同一份问卷时，页面直接恢复到上次停下的那道题。草稿保留 **7 天**，超过 7 天后清空，需要重新填写。
>
> **待确认**
>
> 清理任务的执行频率还没定，不影响上面描述的行为。
