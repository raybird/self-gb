
# Claude Code Router

一個輕量級的路由器，用於將 Claude API 請求導向不同的模型提供者，特別目前是 Gemini-balance。

## 🚀 快速開始

### 1. 安裝必要套件

```bash
# 安裝 Claude Code
npm install -g @anthropic-ai/claude-code

# 安裝 Claude Code Router
npm install -g @musistudio/claude-code-router
```

### 2. 建立最小配置

建立設定檔 `~/.claude-code-router/config.json`：

```bash
mkdir -p ~/.claude-code-router
cat > ~/.claude-code-router/config.json << 'EOL'
{
  "LOG": true,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini-balance",
      "api_base_url": "http://localhost:8000/v1beta/models/",
      "api_key": "sk-123456",
      "models": ["gemini-2.5-pro", "gemini-2.5-flash"],
      "transformer": {"use": ["gemini"]}
    }
  ],
  "Router": {
    "default": "gemini-balance,gemini-2.5-pro"
  }
}
EOL
```

### 3. 啟動服務

```bash
ccr code
```

## ⚙️ 進階配置

### 完整配置選項

```json
{
  "LOG": true,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini-balance",
      "api_base_url": "http://localhost:8000/v1beta/models/",
      "api_key": "sk-123456",
      "models": ["gemini-2.5-pro", "gemini-2.5-flash"],
      "transformer": {"use": ["gemini"]}
    }
  ],
  "Router": {
    "default": "gemini-balance,gemini-2.5-pro",
    "background": "gemini-balance,gemini-2.5-pro",
    "think": "gemini-balance,gemini-2.5-pro",
    "longContext": "gemini-balance,gemini-2.5-pro",
    "longContextThreshold": 60000,
    "webSearch": "gemini,gemini-2.5-flash"
  }
}
```

### 配置說明

| 參數 | 說明 | 範例 |
|------|------|------|
| `LOG` | 啟用日誌記錄 | `true` |
| `API_TIMEOUT_MS` | 請求超時時間（毫秒） | `600000` |

#### 路由規則

- `default` - 預設模型
- `background` - 背景任務
- `think` - 思考任務
- `longContext` - 長文本處理
- `webSearch` - 網路搜尋

## 🔄 常用指令

```bash
# 啟動服務
ccr code

# 重新啟動服務（修改配置後）
ccr restart

# 查看日誌
tail -f ~/.claude-code-router.log
```

## 📝 注意事項

1. **效能**
   - 長時間運行的請求請設定適當的 `API_TIMEOUT_MS`
   - 監控日誌檔案大小 `~/.claude-code-router.log`

2. **除錯**
   - 啟用 `"LOG": true` 記錄詳細日誌
   - 日誌位置：`~/.claude-code-router.log`

## 📚 參考資源

- [官方文件](https://github.com/musistudio/claude-code-router)
- [Claude Code 文件](https://docs.anthropic.com/en/docs/claude-code/quickstart)