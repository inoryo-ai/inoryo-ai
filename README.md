# 猪野 凌（Ryo Ino）

千葉在住、Centaurus のソロ開発者。**本番稼働中のマルチテナント SaaS** と、**決定論的で監査可能な知識応答エンジン**を作っています。どちらも動くコードを公開しています。

## 取り組んでいること

- **課金顧客のいる本番 SaaS** — LINE ベースの飲食店ロイヤルティ基盤（稼働中・月額課金）と、継続報酬型アフィリエイト基盤（稼働中・月額保守契約）。
- **AI 受託開発** — 建築図面からの構造スクリーニング、クライアント保有ナレッジに対する問い合わせ応答システム。要件定義から納品・運用まで一貫して個人で担当。
- **決定論的な知識応答エンジン（NOUS）** — Brain + Book アーキテクチャ。バージョン管理された JSON ナレッジベース上で、出典が辿れる回答を返す。実行時の LLM 依存はゼロ。

## 主な公開リポジトリ

| リポジトリ | 概要 |
|---|---|
| [repitol-clean](https://github.com/inoryo-ai/repitol-clean) | LINE ベースの飲食店ロイヤルティ基盤。スタンプカード・クーポン・自動配信。Next.js 16 + Supabase + LINE Messaging API。本番稼働中マルチテナント SaaS の公開ミラー。 |
| [nous-core](https://github.com/inoryo-ai/nous-core) | 決定論的・LLM 非依存の知識応答エンジン。バージョン管理された JSON ナレッジベース上で追跡可能な回答を返す。実行時依存ゼロ。本番システム1件で稼働中。 |
| [shift-tool-public](https://github.com/inoryo-ai/shift-tool-public) | 飲食店シフト管理。Excel ⇔ JSON 変換 + OR-Tools CP-SAT による自動生成、Streamlit UI。3店舗で運用中。 |
| [public-tender-pipeline](https://github.com/inoryo-ai/public-tender-pipeline) | 入札案件情報システムの技術検証。クローラのサイレント故障検知・案件の名寄せ・LLM コスト設計。CI（ruff・mypy・pytest）と、要件からコードまでのトレーサビリティ検査つき。 |
| [zero-to-web-engineer](https://github.com/inoryo-ai/zero-to-web-engineer) | 未経験から Web エンジニアへ：低レイヤーから作って理解する全27章の Ruby/Rails 教材（非公式・CC BY 4.0）。 |
| [centaurus-oss](https://github.com/inoryo-ai/centaurus-oss) | プロジェクト横断の Python ユーティリティ。外部サービスアダプタ基盤、TTL 応答キャッシュ、FastAPI セキュリティ補助。 |
| [logos](https://github.com/inoryo-ai/logos) | マルチテナント業務ワークフロー基盤。トレースファースト、フェイルソフト検証、アノテーションキャッシュ。Next.js 15 + Supabase RLS + Langfuse。**設計・実装進行中。** |

## 技術選定の考え方

技術は「何ができるか」ではなく、**その案件で最も重い失敗が何かを先に決めて、それを構造的に潰せるか**で選んでいます。実際の判断基準は次の4つです。

| 基準 | 具体的な適用例 |
|---|---|
| **失敗を構造で潰す（規約や注意力に頼らない）** | マルチテナントで最も重い失敗は「テナント間のデータ混在」。認可をアプリ層に置くと実装漏れが漏洩に直結するため、Supabase RLS でデータベース層に寄せている（[repitol-clean](https://github.com/inoryo-ai/repitol-clean)・[logos](https://github.com/inoryo-ai/logos)） |
| **説明可能性を性能より優先する** | 規制ドメインや業務判断では「なぜこの答えなのか」を説明できないと採用されない。だから LLM ではなく決定論的マッチング（[nous-core](https://github.com/inoryo-ai/nous-core)）、ヒューリスティクスではなく制約充足ソルバ（[shift-tool-public](https://github.com/inoryo-ai/shift-tool-public)）を選ぶ |
| **1人で保守できる構成量に抑える** | すべて個人で運用・保守するため、デプロイ対象とインフラ運用対象の数そのものを設計変数として扱う。Temporal ではなく Vercel Workflow DevKit、専用ベクトル DB ではなく pgvector を選ぶのはこの理由 |
| **顧客の既存運用を変えない** | 導入が止まる最大の要因は技術ではなく運用変更。Excel 運用には書式付き XLSX で戻し（openpyxl）、LINE で完結している顧客にはアプリではなく LIFF を出す |

各リポジトリの README に、そのプロジェクト固有の「技術選定」表を記載しています。

## 非公開の案件

規模の大きい受託案件は NDA のため GitHub には置いていません。

- **建築事務所向け耐震診断 AI** — 平面図からの構造検出、建築基準法・国土交通省告示に準拠したスコアリング、建築士による監修。Web 版と完全オフラインのローカル版の両方を納品。
- **教育企業向け問い合わせ応答システム** — `nous-core` が知識マッチングを担当し、小規模 LLM は最終的な文面整形にのみ使用。確信度が閾値を下回る回答は推測せず、人へエスカレーションする設計。

設計判断と技術的なトレードオフについては、対話の中で喜んで説明します。

## 探索的な取り組み

以下は探索の記録であり、確証的な結果ではありません。

- [cognitive-research-papers](https://github.com/inoryo-ai/cognitive-research-papers) — LLM による認知機能のモデル化と、記憶を持たないエージェントにおける感情パラメータに関するノート。**小標本（N=3〜1,131）、自己申告ラベル — 探索的であり確証的ではありません。**
- [cognitive-dictionary](https://github.com/inoryo-ai/cognitive-dictionary) — 0/1 基盤から導出した認知操作のボトムアップ「辞典」。ARC-AGI タスクに対して検証。

## 技術スタック

**フロントエンド** Next.js (App Router) / React / TypeScript / Tailwind
**バックエンド** Python (FastAPI) / Node.js / Supabase Postgres / pgvector
**AI / ML** Anthropic / OpenAI / NOUS（自社製） / YOLO / OR-Tools CP-SAT
**インフラ** Vercel / Docker / GitHub Actions / Langfuse

## 連絡先

- メール — GitHub プロフィールを参照
- 千葉在住 — フルリモートの案件に対応可能
