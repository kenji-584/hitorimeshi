# 一人飯.com / HITORIMESHI.COM

> 一人で入りにくい、あの店に入れる。  
> A guide for solo diners.

ひとり飯好きのための、食の情報プラットフォーム。焼肉、鮨、しゃぶしゃぶ、カウンターの小料理屋── "一人で入っていいのかな" を、実際に行った人の声で解消する。

---

## 📦 このフォルダの中身

### HTMLページ（全11ページ）

| ファイル | 役割 |
|---|---|
| `index.html` | トップページ（LP） |
| `find.html` | お店検索・地図 |
| `shop.html` | 店舗詳細（サンプル） |
| `match.html` | 食事会・同じ店の常連 |
| `report.html` | 入店レポート投稿 |
| `for-shops.html` | お店向け（掲載無料の案内） |
| `safety.html` | 安全の仕組み |
| `terms.html` | 利用規約 |
| `report-abuse.html` | 違反通報フォーム |
| `welcome.html` | メール登録完了ページ |
| `404.html` | エラーページ |

### アセット

| ファイル | 役割 |
|---|---|
| `ogp.jpg` | SNSシェア時に表示される画像（1200×630） |
| `favicon.ico` / `favicon-32.png` / `favicon-180.png` / `favicon-512.png` | ファビコン |
| `sitemap.xml` | SEO用サイトマップ |
| `robots.txt` | クローラー制御 |

---

## 🚀 公開方法（一番ラクな順）

### ① Netlify Drop（ドラッグ&ドロップで最速 — おすすめ）

1. ブラウザで [app.netlify.com/drop](https://app.netlify.com/drop) を開く
2. この `hitorimeshi` フォルダを、そのままブラウザにドラッグ
3. 10秒〜30秒で `random-name-12345.netlify.app` のURLが発行される
4. すぐに世界中から見られる状態に

**独自ドメインを使いたい時:**
- Netlifyダッシュボード → Site settings → Domain management → Add custom domain
- `hitorimeshi.com` を追加 → 表示されるDNS設定をドメイン管理画面で入れる

### ② Vercel CLI（コマンドで公開）

ターミナルで以下:
```bash
cd ~/Downloads/hitorimeshi
npx vercel
```
初回はログインを求められる → ブラウザで承認 → 数十秒で公開URLが発行される

### ③ Cloudflare Pages（高速・無料）

1. [pages.cloudflare.com](https://pages.cloudflare.com) でアカウント作成
2. 「Create a project」→「Direct upload」
3. プロジェクト名入力、フォルダをアップロード

---

## 🌐 ドメイン取得

### おすすめ

| サービス | 料金（.com） | 備考 |
|---|---|---|
| **Cloudflare Registrar** | 約¥1,500/年 | 原価販売、DNSセットも無料。一番安くて使いやすい |
| **お名前.com** | 初年¥1円〜（更新は高め） | 日本最大、UIやや煩雑 |
| **Namecheap** | 約¥1,800/年 | 海外、英語UI |

### 候補ドメイン

- `hitorimeshi.com` ← 推奨（英字で覚えやすい、海外展開も視野）
- `一人飯.com`（日本語ドメイン、ブラウザで表示が `xn--...` に変わる場合あり）

**購入の流れ（Cloudflareの場合）:**
1. Cloudflareでアカウント作成
2. Registrar → Transfer or Register
3. `hitorimeshi.com` を検索・購入
4. DNSを公開先（Netlify/Vercel）に合わせて設定

---

## ✅ 公開前チェックリスト

### 必須
- [ ] ホスティング（Netlify/Vercel/Cloudflare Pages）にアップロード
- [ ] `index.html` が公開URLで表示されることを確認
- [ ] 全ページのリンクが動くかチェック（ナビゲーションから全ページ回ってみる）
- [ ] スマホで表示してみる（PCのブラウザで F12 → デバイス表示でもOK）
- [ ] OGP画像が正しく出るか [opengraph.xyz](https://www.opengraph.xyz/) で確認

### 推奨
- [ ] 独自ドメインの取得と設定
- [ ] Google Search Console に登録（サイトマップ `sitemap.xml` を提出）
- [ ] アクセス解析設置（Google Analytics or Plausible）
- [ ] 連絡先メアド設定（`hello@` / `safety@` / `shops@` など）
  - ドメインの転送機能で無料で使える
  - 本格運用するなら Google Workspace（月¥816/user）
- [ ] 利用規約の弁護士レビュー（将来の法的リスク予防、5-10万円目安）

### β版リリース時
- [ ] メール収集バックエンド（ConvertKit / Mailchimp / Substack 等）と接続
- [ ] フォームの `onsubmit` を本番の登録処理に差し替え
- [ ] SNSアカウント開設（X、Instagram）

---

## 🎨 デザインシステム

**配色:**
- `--paper` #f0e7d3（メインの紙色）
- `--ink` #15110c（主文字）
- `--wine` #7a1e2a（アクセント）
- `--cream` #d4b896（温かい強調）
- `--pine` #1f3d2c（成功・承認）

**フォント:**
- 和文: Shippori Mincho B1 + Noto Sans JP
- 欧文: EB Garamond (italic) + Playfair Display

**トーン:** 雑誌エディトリアル風、深夜の居酒屋カウンター、落ち着いた大人向け

---

## 🛠 今後の実装（バックエンド）

現在はフロントエンドのみ。β版機能（ユーザー登録、食事会、1対1のお食事お誘い等）を実装する際の推奨スタック:

### 1人運営想定のスタック
- **Next.js** — 既存HTMLをReactコンポーネント化
- **Supabase** — DB・認証・ストレージを一括
- **Vercel** — ホスティング
- **Resend** — メール送信
- **Twilio** — SMS認証
- **Stripe** — 決済

### 最小限のDBテーブル設計
```
users            (id, email, phone, is_verified, created_at)
shops            (id, name, genre, address, lat, lng, approved)
reports          (id, user_id, shop_id, verdict, text, tags)
gatherings       (id, host_id, shop_id, starts_at, max_seats)
attendees        (gathering_id, user_id, checked_in)
abuse_reports    (id, reporter_id, target_id, type, description, status)
```

---

## 📞 連絡先（公開時に設定）

- `hello@hitorimeshi.com` — 一般問い合わせ
- `safety@hitorimeshi.com` — 安全・通報
- `shops@hitorimeshi.com` — お店関係

---

Built with 🍚 by HITORIMESHI.COM  
© 2026
