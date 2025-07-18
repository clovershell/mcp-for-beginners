<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "1b6c746d9e190deba4d8765267ffb94e",
  "translation_date": "2025-07-16T23:14:29+00:00",
  "source_file": "02-Security/azure-content-safety-implementation.md",
  "language_code": "hk"
}
-->
# 在 MCP 中實現 Azure Content Safety

為了加強 MCP 對提示注入、工具中毒及其他 AI 特有漏洞的防護，強烈建議整合 Azure Content Safety。

## 與 MCP 伺服器的整合

要將 Azure Content Safety 整合到您的 MCP 伺服器中，請在請求處理流程中將內容安全過濾器作為中介軟件加入：

1. 在伺服器啟動時初始化過濾器  
2. 在處理前驗證所有進入的工具請求  
3. 在回傳給客戶端前檢查所有輸出回應  
4. 記錄並警示安全違規事件  
5. 對內容安全檢查失敗實施適當的錯誤處理  

這能有效防禦：  
- 提示注入攻擊  
- 工具中毒嘗試  
- 透過惡意輸入進行的資料外洩  
- 生成有害內容  

## Azure Content Safety 整合的最佳實踐

1. **自訂封鎖清單**：針對 MCP 注入模式建立專屬的自訂封鎖清單  
2. **嚴重性調整**：根據您的具體使用情境和風險承受度調整嚴重性門檻  
3. **全面覆蓋**：對所有輸入和輸出都進行內容安全檢查  
4. **效能優化**：考慮對重複的內容安全檢查實施快取機制  
5. **備援機制**：定義內容安全服務不可用時的明確備援行為  
6. **用戶反饋**：當內容因安全考量被封鎖時，向用戶提供清晰的反饋  
7. **持續改進**：根據新興威脅定期更新封鎖清單和檢測模式

**免責聲明**：  
本文件由 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們致力於確保準確性，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應被視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而引起的任何誤解或誤釋承擔責任。