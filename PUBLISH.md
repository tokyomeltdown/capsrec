# 公開手順（GitHub Pages）

このフォルダをそのまま `capsrec` リポジトリとして公開します。
公開後のURLは **https://tokyomeltdown.github.io/capsrec/** になります（LPのOGPに埋め込み済みの値と一致）。

---

## 1. GitHubでリポジトリを作る

1. https://github.com/new を開く
2. **Repository name** に `capsrec`
3. **Public** を選ぶ ← 無料プランのGitHub Pagesは公開リポジトリが必須
4. README/.gitignore/ライセンスの追加は**すべてチェックを外す**（このフォルダに既にあるため）
5. **Create repository**

## 2. ターミナルから push する

Mac のターミナル（`⌘+スペース` → `ターミナル`）で、以下を上から順に実行します。

```bash
cd ~/Documents/Claude/Projects/Plugin/capsREC/lp-site

git init
git add .
git commit -m "caps REC landing page"
git branch -M main
git remote add origin https://github.com/tokyomeltdown/capsrec.git
git push -u origin main
```

`git push` でユーザー名とパスワードを聞かれた場合、パスワードには GitHub のパスワードではなく
**Personal Access Token** を入れます（https://github.com/settings/tokens → Generate new token (classic) → `repo` にチェック）。

## 3. GitHub Pages を有効にする

1. リポジトリの **Settings** → 左メニューの **Pages**
2. **Source** = `Deploy from a branch`
3. **Branch** = `main` / フォルダは **`/docs`** を選択 → **Save**
4. 1〜2分待つと同じ画面の上部に公開URLが出ます

## 4. 確認する

- https://tokyomeltdown.github.io/capsrec/ が開くか
- フッターの「プライバシー」を押して03セクションへ飛ぶか
- OGPの見え方 → https://cards-dev.twitter.com/validator または実際にXで下書きにURLを貼る

---

## 更新するとき

`lp/index.html` を直したら `docs/` にコピーしてから push します。

```bash
cd ~/Documents/Claude/Projects/Plugin/capsREC
cp lp/index.html lp/og-image.png lp-site/docs/
cd lp-site
git add . && git commit -m "update landing page" && git push
```

---

## メモ

- `docs/.nojekyll` は GitHub Pages の Jekyll 処理を無効化する空ファイル。消さないこと
- アプリ本体のソースはこのリポジトリに入れない（非公開のまま）
- 配布用の `.pkg` は Gumroad の商品Contentに置く。GitHub Releases は使わない
