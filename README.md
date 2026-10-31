# CYUT Research Download

協助搜尋、核對、合法取得並分析學術文獻的 Agent Skill。預設先查看朝陽科技大學電子資料庫入口，再依文獻語言與類型前往 Scopus、出版平台、華藝或國圖等來源。技能會區分「查到書目」與「已取得並驗證 PDF」，不會把搜尋結果當成下載成果。

## 下載並安裝技能

儲存庫根目錄就是技能資料夾，包含 `SKILL.md` 與 Codex 的 `agents/openai.yaml`。資料夾名稱應保持為 `cyut-research-download`。

### Codex

將儲存庫複製到個人技能目錄：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/joseph0351312/cyut-research-download.git ~/.codex/skills/cyut-research-download
```

開始新對話後，可在請求中使用 `$cyut-research-download`。若已安裝舊版，請先確認本機是否有自行修改，再於該技能資料夾更新。

### Claude Code

將儲存庫複製到個人技能目錄：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/joseph0351312/cyut-research-download.git ~/.claude/skills/cyut-research-download
```

若只想讓某個專案使用，則將儲存庫複製到該專案的 `.claude/skills/cyut-research-download`。在 Claude Code 中可用 `/cyut-research-download` 呼叫。

不使用 Git 也可以在 GitHub 儲存庫頁面選擇 **Code → Download ZIP**，解壓後將資料夾重新命名為 `cyut-research-download`，再放入上述對應的 `skills` 目錄。請確認 `SKILL.md` 直接位於 `cyut-research-download` 資料夾內，沒有多包一層。

## 如何使用

請提供研究主題或關鍵字、所需文獻類型、篇數，以及 PDF 的**絕對存放路徑**。例如：

> 使用 `$cyut-research-download` 搜尋「生成式 AI 輔助高等教育學習」的中英文期刊論文。請合法下載 15 篇可取得的 PDF 到 `/Users/你的帳號/Documents/research-papers`，並整理每篇的研究方法、主要發現與限制。

在 Claude Code 中，將開頭改為 `/cyut-research-download` 即可。若尚未指定存放資料夾，技能會先請你提供路徑。未指定篇數時，預設最多取得 10 篇已驗證的 PDF；明確指定更多或更少篇數時，以你指定的篇數為目標與總上限。每批最多處理 10 篇候選，並在同一請求內接續處理；下載嘗試總數最多為目標篇數的兩倍。

## 文獻下載流程

1. 技能先核對書目、出版類型與全文來源。外文先查 Scopus，再到對應出版平台；中文依序查華藝 CEPS、華藝 CETD、國圖博碩士論文網。
2. 需要朝陽校外授權時，由你在官方入口自行登入，並自行完成 CAPTCHA 或其他驗證。請勿將帳號、密碼、驗證碼或 Cookie 提供給助理。
3. 對於你已授權且可合法取得的全文，技能將下載或協助歸檔，檢查 PDF 是否可讀，並回報最終絕對路徑。無授權、無全文或下載失敗的項目會分開列出。
4. 國圖博碩士論文網的檔案由你自行在正式論文頁面操作下載；提供檔案或可存取路徑後，技能才會驗證與歸檔。

技能不繞過付費牆、網站限制或驗證機制。請依資料庫授權條款將取得的文獻用於個人研究。實際可下載篇數可能少於目標，取決於相關文獻、授權狀態與網站可用性。

## 輸出內容

- 已核對的書目資料與正式來源頁面
- 已下載且驗證的 PDF 絕對路徑
- 待你自行下載、無法取得或驗證失敗的項目及原因
- 文獻的研究目的、方法、主要發現、限制，以及與研究問題的關聯

詳細規則請見 [SKILL.md](SKILL.md)。
