# 数学ラボ

さわって動かせる算数・数学の学習教材を集めた静的サイト。
ビルドもインストールも不要で、HTML と CSS を置いているだけです。

公開先: <https://uu3san.github.io/math-lab/>

## ファイル

| ファイル | 内容 |
| --- | --- |
| `index.html` | トップページ（教材の一覧） |
| `polyhedron.html` | 正多面体ラボ（面・辺・頂点をかぞえる／展開図を組み立てる／回して見る） |
| `template.html` | 新しい教材ページの雛形。コピーして使う |
| `style.css` | サイト共通のスタイル |
| `favicon.svg` | ファビコン |
| `.nojekyll` | GitHub Pages の Jekyll 処理を止める（JS の `{{` などが壊されないように） |

正多面体ラボは外部ライブラリを使わず、Canvas 2D に自前で書いた 3D 描画で動いています。

## 新しい教材ページを追加する手順

1. **`template.html` をコピー**して、`〇〇.html`（半角英字）という名前にする。
2. コピーしたファイルの `<title>` ・ページ上部の帯（`.page-head`）・中身を書きかえる。
   ページ固有の CSS は `<style>` の中に、色は `style.css` の変数を使って書く。
3. **`index.html` にカードを1枚足す**。`<div class="cards">` の中に次を追加する。

   ```html
   <a class="card" href="〇〇.html">
     <svg class="mark" viewBox="0 0 26 26" fill="currentColor" aria-hidden="true">
       <!-- 教材をあらわす簡単な図形 -->
     </svg>
     <div class="body">
       <h3>教材名</h3>
       <p>説明を1〜2文。</p>
       <div class="tags"><span>単元</span><span>対象学年</span></div>
     </div>
   </a>
   ```

4. `index.html` の `<p class="count">01</p>` を教材の数に合わせる。
5. 2つ目の教材を足したら、1つ目のカードから `feature` クラスを外す
   （`class="card feature"` → `class="card"`）。1枚だけのときに大きく見せるための指定です。
6. 動作を確認して commit / push する。数分で公開先に反映されます。

### 色とフォント

`style.css` の `:root` にまとめてあります。

- 背景は方眼ノート（24px の細罫 + 120px の太罫）
- アクセントは緑インク `--accent: #0f7a5a`
- 見出しは Zen Kaku Gothic New、本文は Noto Sans JP、数値とラベルは IBM Plex Mono

## 手元で見るには

```
python -m http.server 8000
```

を実行して <http://localhost:8000/> を開きます。

## 公開

GitHub Pages（`master` ブランチのルート）で公開しています。
