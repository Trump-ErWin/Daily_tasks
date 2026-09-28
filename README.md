# Daily_tasks

AI 自动化任务的缓存与归档仓库：由根目录下的 5 个提示词模板（`.txt`）驱动，自动更新、汇总、整理，并在整合完成后删除缓存文件，全程同步到 GitHub。

## 目录结构

- `cache/` 缓存区（由任务自动增删）
  - `cache/daily/` 每日简报 `今日简报-YYYY-MM-DD.md` ← 周报整合后删除
  - `cache/weekly/` 周报 `第W周YYYY-MM-DD至YYYY-MM-DD.md` ← 月报整合后删除
  - `cache/movie/` 电影推荐 `第W周电影介绍详情.md` ← 被下一周替换
- `archive/monthly/` 月报 `YYYY年M月.md`（长期保留）
- `records/` 长期记录（只增不删）
  - `电影推荐历史记录.md`（去重用）
  - `美食推荐.md`（追加 + 压缩整理）

## 缓存闭环

1. 每日：`01每日新闻.txt` → 生成日报缓存
2. 每周：`02每周新闻.txt` → 汇总日报为周报，删除已整合日报
3. 每月：`03每月新闻.txt` → 汇总周报为月报归档，删除已整合周报
4. 每周：`每周电影推荐.txt` → 替换旧电影缓存，追加历史记录
5. 按需：`美食推荐.txt` → 追加更新长期美食记录

## 提示词模板

| 模板 | 周期 | 产物 |
| --- | --- | --- |
| 01每日新闻.txt | 每日 | cache/daily/今日简报-YYYY-MM-DD.md |
| 02每周新闻.txt | 每周 | cache/weekly/第W周*.md |
| 03每月新闻.txt | 每月 | archive/monthly/YYYY年M月.md |
| 每周电影推荐.txt | 每周 | cache/movie/第W周电影介绍详情.md |
| 美食推荐.txt | 按需 | records/美食推荐.md |

> 注意：`cache/` 下的文件会被任务自动删除，请勿存放需要长期保留的内容。
