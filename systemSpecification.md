# Minecraft Changelog を翻訳しDiscordに通知

## 目的
基本的に英語で配信されているMinecraftのChangelogを"自動的"にGemini APIを使用して翻訳しDicordにwebhookを通じて送信する
また、将来的に自動的にサイトを作成する仕組みを検討する  
※ Discordのwebhookには送信文字数制限があるため

## 考慮
過去に私が作成した`MinecraftChangelogGenerator`が利用できそうなため利用する

## 技術スタック
| 項目          | 技術                        | 
| ------------- | --------------------------- | 
| **Platform**  | Google Cloud Platform (GCP) | 
| **Computing** | Cloud Run (GCP)             | 
| **Messaging** | Cloud Pub/Sub               | 
| **Database**  | Firestore                   | 
| **AI**        | Gemini                      | 
| **Interface** | Discord webhook             |

## ワークフロー
**SystemWorkflow.xlsx**参照

## エラーハンドリング
- Cloud Run B の例外発生時、`finally`句にてFirestoreフラグを強制リセット。
- GCP Monitoringによるエラーログ検知・通知。
