
# Gemini CLI

一個簡單的命令列工具，用於與 Gemini API 進行互動。

## 功能特點

- 支援自定義 Gemini API 端點
- 簡單易用的命令列介面
- 可配置的環境變數
- 支援多種輸入方式

## 安裝

### 先決條件

- 已安裝 Node.js (建議使用 LTS 版本)
- 有效的 Gemini API 金鑰

### 安裝步驟

1. 參考 https://github.com/google-gemini/gemini-cli
2. 安裝 gemini-cli：
   ```bash
   npm install -g @google/gemini-cli
   ```
3. 設定環境變數（見下方說明）

## 環境變數設定

您可以通過以下方式設定環境變數：

### 1. 使用 `.env` 檔案

在專案根目錄建立 `.env` 檔案，並加入以下內容：

```env
GOOGLE_GEMINI_BASE_URL="http://localhost:8000"
GEMINI_API_KEY="sk-123456"
```

### 2. 在 shell 設定檔中設定

將以下內容加入您的 shell 設定檔（如 `~/.bashrc`、`~/.zshrc` 等）：

```bash
export GOOGLE_GEMINI_BASE_URL="http://localhost:8000"
export GEMINI_API_KEY="sk-123456"
```

然後執行：
```bash
source ~/.bashrc  # 或對應的設定檔
```

## 使用方式

### 基本用法

```bash
# 啟動互動式 CLI
gemini

# 選擇 Gemini API Key 的方式
```

## 環境變數說明

- `GOOGLE_GEMINI_BASE_URL`: Gemini API 的基礎 URL，預設為 `http://localhost:8000`
- `GEMINI_API_KEY`: 您的 Gemini API 金鑰

## 授權

[MIT License](LICENSE)