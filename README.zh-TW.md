# SupraDrop

**繁體中文** | [English](README.md)

**自動找出 Word 文件腳注中的《藍皮書》引用格式錯誤** — 幾秒鐘內完成，無需安裝任何軟體。

🔗 **[lawreview.tools/supradrop](https://lawreview.tools/supradrop/)**

---

## 為什麼需要這個工具

法律評論文章的品質很大程度上取決於引用格式是否正確。一個位置錯誤的 *supra* 引用、一個指向多個來源的模糊 *Id.*、一個缺少括號說明的 *Cf.* ——這些都是人工審閱容易遺漏的錯誤，在有數百個腳注的文件中尤其如此。要人工核查每一個簡式引用，必須逐一追溯每個 *supra* 所指向的原始腳注、確認每個 *Id.* 沒有歧義、驗證每個引用信號詞都有對應的括號說明，既費時又容易出錯。

SupraDrop 代勞這一切。上傳您的 Word 文件，不到一分鐘即可取得完整的引用格式問題清單——包含精確的腳注編號、問題描述與對應的《藍皮書》規則。

## 功能說明

SupraDrop 在您的瀏覽器中直接讀取 `.docx` 文件，掃描每一個腳注，並針對六大類別的 **24 條《藍皮書》規則**進行檢查：*supra* 的使用、*Id.* 的使用、引用信號詞括號說明、頁碼引用（pincite）、網址封存，以及 *hereinafter* 的一致性。

每個問題都會標示為**錯誤**（違反《藍皮書》強制要求）或**警告**（違反強烈建議但非強制）。您可以下載附有 Word 批注的文件副本，讓問題一目了然。

無需安裝。無需帳號。無需上傳。文件不會離開您的瀏覽器。

## 24 條檢查規則

### Supra 引用

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `SUPRA_NONEXISTENT` | 🔴 錯誤 | *supra* note N — 但腳注 N 根本不存在於文件中（R. 4.2） |
| `SUPRA_FORWARD` | 🔴 錯誤 | *supra* 指向後方的腳注——*supra* 只能回指更早的腳注（R. 4.2） |
| `SUPRA_TO_SHORT_CITE` | 🔴 錯誤 | *supra* 指向另一個 *supra* 或 *Id.*——*supra* 必須指向完整引用（R. 4.2） |
| `SUPRA_MISMATCH` | 🔴 錯誤 | "supra" 前的作者名或標題未出現在所指腳注中——腳注編號可能有誤 |
| `SUPRA_WRONG_SOURCE_TYPE` | 🔴 錯誤 | *supra* 用於案例、法規或憲法——R. 4.2(a) 明確禁止，應改用簡式引用 |
| `SUPRA_NO_PINCITE` | 🟡 警告 | 引用特定頁面時缺少 `, at [頁碼]`（R. 4.2） |

### Id. 引用

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `ID_NO_PRECEDING` | 🔴 錯誤 | *Id.* 出現時前方沒有可回指的引用（R. 4.1） |
| `ID_AMBIGUOUS` | 🟡 警告 | 前一腳注引用多個來源——*Id.* 指向不明確（R. 4.1） |
| `ID_STALE` | 🟡 警告 | *Id.* 距離原始引用已超過 5 個腳注——建議改用簡式引用（R. 4.1） |

### 引用信號詞括號說明

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `CF_NO_PAREN` | 🔴 錯誤 | *Cf.* 後缺少以現在分詞開頭的括號說明（R. 1.2, R. 1.5） |
| `BUT_CF_NO_PAREN` | 🔴 錯誤 | *But cf.* 後缺少括號說明（R. 1.2, R. 1.5） |
| `COMPARE_WITH_NO_PAREN` | 🔴 錯誤 | *Compare … with …* 每個引用來源都須附括號說明（R. 1.2, R. 1.5） |
| `SEE_GEN_NO_PAREN` | 🟡 警告 | *See generally* 後缺少括號說明——《藍皮書》強烈建議加上（R. 1.2, R. 1.5） |
| `EG_FORMAT` | 🟡 警告 | *See e.g.,* 中 "See" 後缺少逗號——應寫 *See, e.g.,* 而非 *See e.g.,*（R. 1.1） |
| `SEE_ALSO_NO_PAREN` | 🟡 警告 | *See also* 後缺少括號說明——《藍皮書》強烈建議加上（R. 1.2, R. 1.5） |
| `BUT_SEE_NO_PAREN` | 🟡 警告 | *But see* 後缺少括號說明——《藍皮書》強烈建議加上（R. 1.2, R. 1.5） |

### 頁碼引用（Pincite）

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `QUOTE_NO_PINCITE` | 🔴 錯誤 | 直接引用卻缺少 pincite 頁碼（R. 3.2(a), R. 5.2） |
| `PINCITE_HYPHEN` | 🔴 錯誤 | 頁碼範圍用連字號（`-`）而非半形破折號（`–`）（R. 3.2(a)） |
| `PINCITE_UNSHORTENED` | 🟡 警告 | 末頁未縮短：`1124–1129` 應寫為 `1124–29`（R. 3.2(a)） |
| `PINCITE_PP` | 🟡 警告 | 頁碼前出現 `pp.`——《藍皮書》的 pincite 不使用 `pp.`，直接寫頁碼即可（R. 3.2） |

### 格式

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `FOOTNOTE_NO_PERIOD` | 🟡 警告 | 腳注未以句號結尾（R. 1.1） |

### 網路資料來源

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `URL_NOT_ARCHIVED` | 🔴 錯誤 | 引用網路來源但缺少 perma.cc 永久封存連結（R. 18.2.1） |

### Hereinafter（下稱）

| 規則代碼 | 嚴重程度 | 檢查內容 |
|----------|----------|----------|
| `HEREINAFTER_FORMAT` | 🔴 錯誤 | *hereinafter* 未用方括號包覆——應寫 `[hereinafter X]`，而非 `(hereinafter X)` 或裸文字（R. 4.2(b)） |
| `HEREINAFTER_NEVER_USED` | 🟡 警告 | 定義了 `[hereinafter X]` 但後續腳注從未使用（R. 4.2(b)） |

## 功能特色

- **嚴重程度篩選** — 一鍵切換「全部問題 / 僅錯誤 / 僅警告」
- **智慧建議** — `SUPRA_MISMATCH` 會搜尋全文，主動建議您可能想引用的正確腳注編號
- **規則開關** — 可逐一啟用或停用個別規則，因應不同期刊的內部格式要求
- **略過誤判** — 將不適用的問題標記為「已略過」，保持工作區整潔；略過的項目可隨時重新查閱
- **匯出加注 .docx** — 在原始文件的問題腳注處插入 Word 批注，可直接傳給作者修改
- **匯出 CSV** — 結構化的問題清單，包含腳注編號、規則代碼、嚴重程度與說明
- **匯出 TXT** — 純文字報告，便於分享或列印
- **多份文件** — 單次工作階段可同時審查多個 `.docx` 文件
- **完全本地端運算** — 文件不會離開瀏覽器，任何內容都不會上傳至伺服器

## 使用方式

1. 開啟 **[lawreview.tools/supradrop](https://lawreview.tools/supradrop/)**
2. 上傳一或多個 `.docx` 文件——可直接拖曳至上傳區，或點擊選取檔案
3. SupraDrop 立即掃描所有腳注，結果顯示於 **Issues（問題）** 分頁
4. 使用 **All / Errors / Warnings** 篩選按鈕，決定先處理哪類問題
5. 點擊任一問題，查看完整的腳注原文及對應的《藍皮書》規則
6. 標記不適用的誤判為「已略過」
7. 下載**加注 .docx**（附 Word 批注）、**CSV** 或 **TXT** 報告

> **小提示——Rules 分頁：** 每份文件都有獨立的 **Rules（規則）** 分頁，可針對該文件開關個別檢查項目。若您的期刊有自訂格式規範（例如不要求 *see generally* 加括號說明），可在此調整。

## 測試用範例文件

本儲存庫附有 [`SupraDrop_TestFixture.docx`](SupraDrop_TestFixture.docx)，這是一份特意設置了引用格式錯誤的 Word 文件，涵蓋全部 24 條規則的範例。您可以將它上傳至 [lawreview.tools/supradrop](https://lawreview.tools/supradrop/)，立即看到所有檢查功能的運作效果。

## 使用需求

- 現代瀏覽器：Chrome、Firefox、Safari 或 Edge
- `.docx` 格式的 Word 文件（不支援 `.doc` 或 PDF）

## 隱私說明

您的文件完全在瀏覽器記憶體中處理，不會上傳至任何伺服器，無需建立帳號，也不會收集任何使用資料。

## lawreview.tools 工具套件

SupraDrop 是 **[lawreview.tools](https://lawreview.tools)** 免費開源工具套件的一部分，專為法律評論編輯與法學學者設計：

| 工具 | 功能 | 使用時機 |
|------|------|----------|
| **[Zotero Perma Archiver](https://lawreview.tools/zotero)** | 在 Zotero 中儲存文獻時自動封存網址至 perma.cc | 寫作研究階段 |
| **[PermaDrop](https://lawreview.tools/permadrop/)** | 批次封存 `.docx` 中所有網址至 perma.cc | 投稿前 |
| **SupraDrop** | 審查所有腳注的引用格式邏輯 | 投稿前 |

建議工作流程：使用 Zotero Perma Archiver 建立研究資料庫 → 用 PermaDrop 封存剩餘網址 → 用 SupraDrop 找出引用錯誤 → 投稿。

## 授權條款

Copyright (C) 2026 [Kirin Chang](https://kirinchang.com)  
Research Fellow, U.S.-Asia Law Institute, NYU School of Law

本工具採用 [GNU Affero 通用公共授權條款第 3 版（AGPL-3.0）](LICENSE)。  
若您修改本工具並以網路服務形式提供，須以相同授權條款公開修改後的原始碼。

本工具與《藍皮書》或 Zotero 無任何附屬或背書關係。
