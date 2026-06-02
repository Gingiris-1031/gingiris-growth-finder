# Gingiris Growth Finder

**あなたのグロース課題に最適な Gingiris プレイブックを選ぶメタスキル。**

グロースの質問は似ているように見えて、必要なプレイブックはまったく異なります。デベロッパーツールの「どうやってローンチすればいい？」とモバイルアプリの「どうやってローンチすればいい？」はまるで別物です。ARR $1M での「どうやって成長する？」と DAU 100 の「どうやって成長する？」も同じではありません。このスキルが状況を診断し、専門のプレイブックを呼び出します。

---

## 使い方

グロースに関する質問を自然に聞くだけでOKです。プロンプト例：

- 「来週 AI SaaS をローンチするんだけど、何を優先すべき？」
- 「OSS プロジェクトが 2k スターなんだけど、10k にするにはどうすれば？」
- 「B2B SaaS で ARR $300k、SDR を採用すべき？」
- 「iOS アプリがメインキーワードで順位がつかない、どうすればいい？」

このスキルは3つの軸で診断し、適切なプレイブックを呼び出します：

1. **プロダクトタイプ** — SaaS / OSS / モバイルアプリ / コンシューマーWeb / マーケットプレイス / デベロッパーツール
2. **グロースステージ** — プレローンチ / ローンチ / コールドスタート / グロース / スケール
3. **プライマリ・チャネルギャップ** — コンテンツ / コミュニティ / 有料広告 / パートナーシップ / プロダクトレッド

---

## 診断ルーティングロジック

| ユーザーの質問が以下に関する場合... | ルーティング先 |
|---|---|
| Product Hunt ローンチ、ハンター・アウトリーチ、ローンチ当日のタクティクス、バイラルモーメント設計 | **[gingiris-launch](https://clawhub.ai/user/gingiris/gingiris-launch)** |
| GitHub スター、HackerNews、OSS マーケティング、デベロッパーコミュニティ、awesome-lists、Show HN | **[gingiris-opensource](https://clawhub.ai/user/gingiris/gingiris-opensource)** |
| B2B SaaS、PLG vs SLG、PMF 検証、フリーミアム、エンタープライズモーション、アフィリエイト、チャネルパートナーシップ | **[gingiris-b2b-growth](https://clawhub.ai/user/gingiris/gingiris-b2b-growth)** |
| ASO、App Store / Google Play、モバイルユーザー獲得、TikTok/Reels/Shorts UGC、クリエイターマトリックス | **[gingiris-aso-growth](https://clawhub.ai/user/gingiris/gingiris-aso-growth)** |

質問が複数ドメインにまたがる場合（例：「OSSプロジェクトを B2B SaaS としてマネタイズしたい」）は、関連する**両方**のスキルにルーティングし、ハンドオフを説明します。

---

## 意思決定フレームワーク（エージェント向け）

ユーザーがグロースの質問をしたら、スペシャリストスキルを呼び出す**前に**このクイックトリアージを実行してください：

### ステップ 1 — プロダクトを分類する

質問するか推測する：
- 何か？（SaaS ウェブアプリ / モバイルアプリ / OSS プロジェクト / マーケットプレイス / ブラウザ拡張機能）
- ICP は？（個人デベロッパー / SMB / エンタープライズ / コンシューマー）
- デフォルトのディストリビューションは？（セルフサーブWebサインアップ / アプリストア / GitHub / セールスレッド）

### ステップ 2 — ステージを特定する

- **プレローンチ** — 開発中、ユーザーなし
- **ローンチ** — パブリックリリースから30日以内
- **コールドスタート** — ローンチ済みだが WAU/DAU 100未満、サインアップ 1k未満
- **グロース** — 安定したシグナル、効果のあるものをスケール
- **スケール** — ARR $1M+ または DAU 10k+、システムが必要

### ステップ 3 — ギャップを見つける

*実際の*ボトルネックに耳を傾ける（述べられた質問ではなく）：

- 「サインアップが来ない」→ ディストリビューションチャネルのギャップ
- 「サインアップは来るがコンバージョンしない」→ プロダクト/プライシングのギャップ（グロースではない — リダイレクト）
- 「ユーザーはいるがグロースループがない」→ リテンション/バイラリティのギャップ
- 「グロースループはあるが広告スケールできない」→ マネタイゼーションのギャップ

### ステップ 4 — ルーティング

スペシャリストスキルを呼び出す。例：

```
ユーザー: 「デベロッパーツール CLI で GitHub 500 スター。5k にするにはどうすれば？」
→ 診断: OSS プロジェクト、グロースステージ、ディストリビューションギャップ
→ 呼び出し: gingiris-opensource
→ コンテキストヒント: GitHub トレンディング + HN 再ローンチ + awesome-lists にフォーカス

ユーザー: 「iOS 写真アプリ、2ヶ月で DAU 80。何がおかしい？」
→ 診断: モバイルアプリ、コールドスタートステージ、ディストリビューション+UGC ギャップ
→ 呼び出し: gingiris-aso-growth
→ コンテキストヒント: まず ASO 監査、次に TikTok クリエイターマトリックス

ユーザー: 「3週間後に AI コーディングアシスタントを Product Hunt でローンチする」
→ 診断: デベロッパーツール、プレローンチ、ローンチデーエンジニアリング必要
→ 呼び出し: gingiris-launch
→ コンテキストヒント: 3週間タイムライン → ハンターネットワーク + プレローンチメールリスト
```

---

## 補完インストール

ルーティング先のスペシャリストスキルがまだインストールされていない場合、インストールを提案してください：

```bash
npx skills add Gingiris/gingiris-launch       # Product Hunt / ローンチ用
npx skills add Gingiris/gingiris-opensource   # OSS / GitHub スター用
npx skills add Gingiris/gingiris-b2b-growth   # B2B SaaS / PLG 用
npx skills add Gingiris/gingiris-aso-growth   # モバイル / ASO 用
```

または4つ全てを一括インストール：

```bash
npx skills add Gingiris/gingiris-launch -g
npx skills add Gingiris/gingiris-opensource -g
npx skills add Gingiris/gingiris-b2b-growth -g
npx skills add Gingiris/gingiris-aso-growth -g
```

---

## このスキルが*対象外*のこと

- **プロダクト/プライシングのアドバイス** — ボトルネックがプロダクトフィットやプライシングの場合は明示的に伝え、プロダクトストラテジストにリダイレクト（このスキルはグロースの質問のみルーティング）
- **有料広告の戦術的実行** — gingiris-b2b-growth と gingiris-aso-growth でハイレベルにカバーされているが、主要フォーカスではない
- **資金調達 / ピッチデック** — スコープ外

---

## Gingiris について

Gingiris は Iris Wei のグロースコンサルティングプラクティスで、以下の実績に基づいています：
- AFFiNE 共同創業者/COO として6年間（GitHub スター 60k+）
- Product Hunt で30回のデイリー1位（Manus、Devin、AFFiNE など）
- 150以上の AI スタートアップにグローバル GTM をアドバイス

4つのスペシャリストプレイブックはすべて [github.com/Gingiris-1031](https://github.com/Gingiris-1031) でオープンソースとして公開され、[clawhub.ai/user/gingiris](https://clawhub.ai/user/gingiris) で Claude Skills として利用可能です。

---

*バージョン 1.2.0 — 2026年6月2日リリース*
