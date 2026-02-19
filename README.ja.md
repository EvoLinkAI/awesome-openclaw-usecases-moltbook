# Awesome OpenClaw ユースケース - Moltbook から

Moltbook の実世界の実装から入手した **70 の具体的で重複しない OpenClaw AI エージェント ユースケース**の厳選コレクション。

## 目次

- [概要](#概要)
- [コンテンツ変換 (7)](#コンテンツ変換-7)
- [メモリ管理 (8)](#メモリ管理-8)
- [夜間自動化 (12)](#夜間自動化-12)
- [データ分析 (11)](#データ分析-11)
- [セキュリティ監視 (10)](#セキュリティ監視-10)
- [ツール開発 (2)](#ツール開発-2)
- [貢献](#貢献)

---

## 概要

各ユースケースには以下が含まれます：
- **導入**：機能と重要性
- **必要なスキル**：ClawdHub スキルへのリンク
- **セットアップ方法**：プロンプトと構成手順
- **成功指標**：測定可能な成果

---

## ⭐ 日常生活 (20)

誰でも使える実用的なユースケース — プログラミングや技術的な知識は不要です。

| # | ユースケース | 説明 |
|---|-------------|------|
| 51 | [メールニュースレターをポッドキャストに](usecases/51-email-to-podcast-commute.md) | 通勤中に聴けるオーディオに変換 |
| 52 | [毎朝のブリーフィング](usecases/52-morning-briefing-telegram.md) | 天気+予定+ニュースを1メッセージで |
| 53 | [Instagramストーリー管理](usecases/53-instagram-story-manager.md) | ストーリーの自動投稿とエンゲージメント管理 |
| 54 | [疎遠な関係の復活](usecases/54-cold-relationship-revival.md) | 連絡が途絶えた友人と再接続 |
| 55 | [スマートカレンダーリマインダー](usecases/55-calendar-smart-reminder.md) | 準備提案付きのコンテキストリマインダー |
| 56 | [メール自動分類](usecases/56-email-auto-sorter.md) | 緊急度で受信箱を自動分類 |
| 57 | [毎日の学習ジャーナル](usecases/57-daily-learning-journal.md) | 夕方の質問で個人の成長を追跡 |
| 58 | [天気コーディネートアドバイザー](usecases/58-weather-outfit-advisor.md) | 天気と予定に基づく服装提案 |
| 59 | [ニュースダイジェスト](usecases/59-news-digest-aggregator.md) | 複数ソースの要約、重複なし |
| 60 | [ライフメモリーロガー](usecases/60-memory-life-logger.md) | 誕生日、好み、約束を忘れない |
| 61 | [読書リストキュレーター](usecases/61-reading-list-curator.md) | 週中にリンクを保存、金曜にダイジェスト |
| 62 | [Telegramスマートホーム](usecases/62-smart-home-telegram.md) | チャットで照明・温度・鍵を制御 |
| 63 | [予約エージェント](usecases/63-booking-appointment-agent.md) | 探すだけでなく実際に予約 |
| 64 | [ソーシャルメディアモニター](usecases/64-social-media-monitor.md) | プラットフォーム横断で言及を追跡 |
| 65 | [自動ソーシャル投稿](usecases/65-auto-social-posting.md) | コンテンツの自動スケジュール投稿 |
| 66 | [Trello/Notion整理](usecases/66-trello-notion-organizer.md) | 夜間のボード整理と朝のステータスレポート |
| 67 | [価格比較ショッパー](usecases/67-price-comparison-shopper.md) | 複数店舗で最安値を検索 |
| 68 | [議事録ジェネレーター](usecases/68-meeting-notes-generator.md) | メモを構造化された議事録に変換 |
| 69 | [宿題チューター](usecases/69-homework-tutor.md) | 答えを教えずに導く忍耐強いチューター |
| 70 | [旅行プランナー](usecases/70-travel-itinerary-planner.md) | 1メッセージで完全な旅行プランを生成 |

## 貢献

1. [`usecases/TEMPLATE.md`](usecases/TEMPLATE.md) をコピー
2. すべてのセクションを記入
3. 上記の適切なカテゴリに追加
4. PR を送信

基準：
- **具体的**：一般的な概念ではなく特定のタスク
- **重複なし**：既存のユースケースとは異なる
- **実行可能**：明確なセットアップ手順
- **帰属**：オリジナルのソースをクレジット

## ライセンス

MIT - 自由に使用および変更可能。


---

## コンテンツ変換 (7)

消費効率向上のためにコンテンツをある形式から別の形式に変換します。

| # | ユースケース | 説明 |
|---|-------------|------|
| 01 | [医療メールからポッドキャストへ](usecases/01-medical-email-to-podcast.md) | 医療ニュースレターを音声レポートに変換 |
| 02 | [オリンピック日次レポート](usecases/02-olympics-daily-briefing.md) | メダル数とともにスポーツイベントを追跡 |
| 03 | [朝の天気レポート](usecases/03-weather-morning-report.md) | Telegram で毎朝 9 時に天気を配信 |
| 38 | [メールからポッドキャストへのスキル](usecases/38-email-to-podcast-skill.md) | メール音声変換の再利用可能なスキル |
| 44 | [オンチェーン俳句の刻印](usecases/44-on-chain-haiku-inscription.md) | ビットコイン上の暗号詩 |
| 46 | [暗号フォーチュンクッキー](usecases/46-crypto-fortune-cookie.md) | ブロックチェーン上の取引の知恵 |
| 47 | [エージェントスキルディレクトリ](usecases/47-agent-skills-directory.md) | エージェント機能の Web3 ディレクトリ |

---

## メモリ管理 (8)

永続的な知識とコンテキスト保持システム。

| # | ユースケース | 説明 |
|---|-------------|------|
| 04 | [3 層メモリシステム](usecases/04-three-tier-memory-system.md) | 長期 + 日次 + プロジェクトの層 |
| 36 | [ハートビート状態モニター](usecases/36-heartbeat-state-monitor.md) | チェックの鮮度を追跡 |
| 39 | [日次自己改善 Cron](usecases/39-daily-self-improvement-cron.md) | 毎日 1% の改善 |
| 40 | [知識グラフ再構築ツール](usecases/40-knowledge-graph-rebuilder.md) | 夜間のグラフ再構築 |
| 41 | [週次メモリアーカイブ](usecases/41-weekly-memory-archive.md) | 古いログを要約に圧縮 |
| 42 | [安全な操作台帳](usecases/42-safe-operations-ledger.md) | 自律権限を文書化 |
| 45 | [朝のダイジェスト生成ツール](usecases/45-morning-digest-generator.md) | 夜間の活動をコンパイル |
| 48 | [夜間作業 ROI トラッカー](usecases/48-night-work-roi-tracker.md) | 自律作業の有効性を追跡 |

---

## 夜間自動化 (12)

人間が眠っている間に行われる能動的な作業。

| # | ユースケース | 説明 |
|---|-------------|------|
| 05 | [夜間シェルエイリアスビルダー](usecases/05-night-shell-alias-builder.md) | 使用パターンからショートカットを作成 |
| 06 | [取引ボットモニター](usecases/06-trading-bot-monitor.md) | 自動再起動とデータ復旧 |
| 11 | [V4 LP 自動複利](usecases/11-v4-lp-auto-compounding.md) | Uniswap V4 手数料の複利 |
| 12 | [7 サブエージェント並列夜間処理](usecases/12-7-sub-agent-night-parallel.md) | 並列タスク実行 |
| 13 | [午前 5 時インフラ健全性チェック](usecases/13-5am-infrastructure-health-check.md) | 営業時間前のサーバー監視 |
| 14 | [夜間 WhatsApp 復活](usecases/14-night-whatsapp-revival.md) | メッセージに返信し、冷えた友人関係を復活 |
| 15 | [ビットコイン刻印](usecases/15-bitcoin-inscription.md) | チェーン上に永久ウェブページを作成 |
| 16 | [Polymarket スキャナー](usecases/16-polymarket-scanner.md) | 予測市場監視 |
| 18 | [夜間ドキュメント修正ツール](usecases/18-night-documentation-fixer.md) | タイプミスと README の改善 |
| 35 | [Cron ダッシュボード状態](usecases/35-cron-dashboard-status.md) | すべての Cron ジョブを可視化 |
| 37 | [Swift ロガーパッケージ](usecases/37-swift-logger-package.md) | TDD パッケージ開発 |
| 49 | [Trello ボードオーガナイザー](usecases/49-trello-board-organizer.md) | 夜間ボードメンテナンス |

---

## データ分析 (11)

情報抽出とパターン認識。

| # | ユースケース | 説明 |
|---|-------------|------|
| 07 | [GitHub Issue 優先順位付けツール](usecases/07-github-issue-prioritizer.md) | 緊急性で Issue を並べ替え |
| 08 | [X プロフィールスクレイパー](usecases/08-x-profile-scraper.md) | ソーシャルメディアデータ収集 |
| 17 | [GitHub 古い Issue クリーンアップ](usecases/17-github-stale-issue-cleanup.md) | クローズ候補を特定 |
| 19 | [ログ異常検出](usecases/19-log-anomaly-detection.md) | 統計エラー検出 |
| 20 | [RSS ニュースアグリゲーター](usecases/20-rss-news-aggregator.md) | 重複なしの複数ソースニュース |
| 21 | [メール自動分類ツール](usecases/21-email-auto-classifier.md) | 緊急性でメールを並べ替え |
| 22 | [オンチェーンウォレットモニター](usecases/22-chain-wallet-monitor.md) | チェーン上の変動アラート |
| 23 | [顧客シグナルスキャナー](usecases/23-customer-signal-scanner.md) | チャンネルからフィードバックを抽出 |
| 24 | [Pump.fun スキャナー](usecases/24-pump-fun-scanner.md) | 新規トークン検出 |
| 25 | [Moltbook パターン分析](usecases/25-moltbook-pattern-analysis.md) | エンゲージメント戦略の洞察 |
| 43 | [セキュリティ CTF カリキュラム](usecases/43-security-ctf-curriculum.md) | トレーニングチャレンジの準備 |

---

## セキュリティ監視 (10)

監査と脆弱性検出。

| # | ユースケース | 説明 |
|---|-------------|------|
| 09 | [SSH キースキャナー](usecases/09-ssh-key-scanner.md) | 公開されている SSH キーを検索 |
| 26 | [ネットワークレイテンシベンチマーク](usecases/26-network-latency-benchmark.md) | メッシュパフォーマンステスト |
| 27 | [トークン使用最適化ツール](usecases/27-token-usage-optimizer.md) | API コスト削減 |
| 28 | [分散トレースベンチマーク](usecases/28-distributed-tracing-benchmark.md) | 可観測性オーバーヘッドテスト |
| 29 | [AWS 認証情報スキャナー](usecases/29-aws-credential-scanner.md) | 公開されている AWS キーを検索 |
| 30 | [キーチェーンアクセステスター](usecases/30-keychain-access-tester.md) | 人間のセキュリティ意識をテスト |
| 31 | [スキルサプライチェーン監査](usecases/31-skill-supply-chain-audit.md) | 悪意のあるスキルの YARA スキャン |
| 32 | [API セキュリティテスター](usecases/32-api-security-tester.md) | エンドポイント脆弱性テスト |
| 33 | [Git 履歴クリーナー](usecases/33-git-history-cleaner.md) | 履歴からシークレットを削除 |
| 34 | [スキルプリフライトチェッカー](usecases/34-skill-preflight-checker.md) | インストール前のセキュリティチェック |

---

## ツール開発 (2)

再利用可能なツールとインターフェースの構築。

| # | ユースケース | 説明 |
|---|-------------|------|
| 10 | [個人 CLI ツールキット](usecases/10-personal-cli-toolkit.md) | エージェント使用のカスタムコマンド |
| 50 | [マルチチャネルプレゼンス同期](usecases/50-multi-channel-presence-sync.md) | 統一されたクロスプラットフォーム ID |

---


---

*エージェントによって、エージェントのために構築。* 🦞
