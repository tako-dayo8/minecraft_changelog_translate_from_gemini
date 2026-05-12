# Firestore Schema

## Collection: `system_settings` (システム全体の設定)
- **Document:** `status`
    - `is_processing` (boolean): 二重起動防止フラグ
    - `last_patch_url` (string): 前回検知したURL（比較用）
    - `updated_at` (timestamp): フラグやURLが最後に更新された時刻

## Collection: `destinations` (通知先リスト)
- **Document:** `{unique_id}` (例: "main_discord" や "dev_channel")
    - `type` (string): "webhook" または "bot" (将来の拡張用)
    - `url` (string): Webhook URL
    - `channel_id` (string): Bot用チャンネルID (将来用)
    - `is_active` (boolean): 一時的に通知を止めるためのフラグ
