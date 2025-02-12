# Security-Learning-AWS
從零開始學AWS Re：Learning AWS

### AWS 雲端小白必知的資安相關服務 

在 AWS 雲端環境中，資訊安全（Cybersecurity）是不可忽視的議題。AWS 提供多種內建的安全工具，協助使用者保護敏感資料、確保合規性、管理憑證，並提供 API 安全機制。

本文件整理 AWS 資安相關的關鍵服務，適合雲端新手學習與應用。

---

## 📌 1. Amazon Macie：S3 敏感資料防護

### 🔹 **特性**
- 使用 **機器學習** 和 **模式比對** 自動識別 S3 存儲桶中的 **敏感資料**（PII、PHI、憑證）。
- 可設定 **定期掃描**（一次性、每日、每週或每月）確保資料不被未授權公開。
- 內建 **隱私法規合規性**（GDPR、PCI-DSS、HIPAA）。

###  **與資安的關聯**
Amazon Macie 自動發現與標記敏感資料，避免 S3 無意間存放 **API 金鑰、密碼、個資**，降低資料外洩風險。

###  **應用場景**
- **金融業**：偵測 S3 是否存有信用卡號碼（PCI-DSS）。
- **醫療業**：確保醫療紀錄符合 HIPAA 標準。
- **企業內部**：發現 AWS Secret Key 或機密薪資資料。

---

## 📌 2. AWS Artifact：合規報告與審計

### 🔹 **特性**
- 提供 AWS 內部及 **第三方安全合規報告**（SOC 1、SOC 2、ISO 27001、PCI-DSS）。
- 允許企業查閱 AWS 安全控制措施。

###  **與資安的關聯**
企業需確保雲端供應商符合 **產業標準（PCI-DSS、HIPAA）**，AWS Artifact 讓企業獲取 AWS 安全證明文件，確保內部合規與稽核。
![image](https://github.com/user-attachments/assets/9f0c1221-a148-4806-ba2f-d3637f1ce2fc)

可以搜尋到合規報告

![image](https://github.com/user-attachments/assets/dfde9096-d56d-4fdd-a6f4-58cabba36406)

![image](https://github.com/user-attachments/assets/3eac37a4-bf52-489f-a523-250bc274cb48)

也可以確認你的所在地是否有相關的報告提供參考
![image](https://github.com/user-attachments/assets/eeba0ad4-2633-4d7b-81ae-ca78a4559b5c)



###  **應用場景**
- **企業內部 IT 風控**：下載 AWS Artifact 合規文件，確保符合法規。
- **供應鏈合規要求**：取得 AWS 符合特定標準的文件。
- **企業內部政策制定**：參考 AWS 資安標準。

---

## 📌 3. AWS Certificate Manager (ACM)：憑證管理

### 🔹 **特性**
- **自動管理 SSL/TLS 憑證**，無須手動續約或上傳。
- **免費公有 SSL/TLS 憑證**（適用於 AWS CloudFront、ELB、API Gateway）。
- **支援 Private CA（內部 PKI）**，企業可建立內部憑證機制。

###  **與資安的關聯**
SSL/TLS 憑證確保網站與 API 之間的 **傳輸加密**，防止 MITM（中間人攻擊），ACM 可自動化管理憑證，避免憑證過期導致的安全問題。

###  **應用場景**
- **網站 HTTPS 安全**：確保企業網站提供 HTTPS，防止流量被竊聽。
- **API 加密保護**：透過 ACM 為 API Gateway 提供 SSL 加密。
- **企業內部憑證管理**：透過 Private CA 管理內部憑證，確保機密性。

---

## 📌 4. Amazon API Gateway：API 保護與管理

### 🔹 **特性**
- **建立 RESTful API & HTTP API**，提供 API 版控與存取管理。
- 內建 **DDoS 防護機制**。
- **支援身份驗證與授權（IAM、Cognito、Lambda Authorizer）**。
- **API 請求流量管理**，防止濫用。

###  **與資安的關聯**
API Gateway 是應用程式的 **安全入口**，可防止未授權 API 存取，並確保 DDoS 防禦與 API 限流。

###  **應用場景**
- **防止 DDoS 攻擊**：API Gateway 內建 DDoS 防護。
- **強化 API 驗證**：透過 Cognito 或 IAM 限制 API 存取。
- **API 限流防護**：設定 Rate Limiting，避免惡意攻擊。

---

## 📌 5. AWS 使用方式與安全性考量

| 使用方式 | 安全性建議 |
|----------|----------------------------------------|
| **AWS 管理控制台 (GUI)** | 建議開啟 MFA，避免帳戶遭駭客登入。 |
| **AWS CLI（命令列介面）** | 使用 IAM 角色，避免存放明文憑證。 |
| **AWS SDK（開發者 API）** | 避免在 GitHub 泄露 API Key，使用 AWS Secrets Manager。 |
| **AWS CDK（基礎架構即程式碼）** | 透過版本控制管理基礎架構，減少誤操作風險。 |

---

## ✅ 簡單總結

如果你是 AWS 新手，不知道如何開始學習資安，這裡有幾個關鍵的服務可以幫助你：

1. **Amazon Macie**：會幫你檢查 S3 儲存桶裡是否有敏感資料（例如個人資訊、憑證），避免資料外洩。
2. **AWS Artifact**：可以下載 AWS 的合規性報告，確保你的業務符合資安與法規標準。
3. **AWS Certificate Manager (ACM)**：幫助你自動管理 SSL/TLS 憑證，確保網站和 API 連線安全。
4. **Amazon API Gateway**：讓你的 API 更安全，防止未授權存取，並提供 DDoS 防護。
5. **AWS 使用方式安全性**：不管是用管理控制台、CLI、SDK 或 CDK，務必開啟 MFA，避免帳戶被盜。

## 📚 參考文件

以下是一些官方 AWS 文件與資源，可以幫助你進一步了解這些安全服務：

- [Amazon Macie 官方文件](https://docs.aws.amazon.com/macie/latest/userguide/what-is-macie.html)
- [AWS Artifact 官方文件](https://docs.aws.amazon.com/artifact/latest/ug/what-is-artifact.html)
- [AWS Certificate Manager (ACM) 官方文件](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html)
- [Amazon API Gateway 官方文件](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)
- [AWS 安全性最佳實踐](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/security-pillar.html)
