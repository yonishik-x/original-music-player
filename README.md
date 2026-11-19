# Original Music Player

仕事の集中用BGMプレーヤー。単一ファイル（`index.html`）で動作するWebアプリです。

## 収録曲

- **INTERSECTION AT DAYBREAK** — アップテンポなジャズピアノのインストゥルメンタル（124 BPM、2分52秒）
- Gemini（Lyria）で生成したオリジナル曲

## 音源について

音源ファイルはアプリに内蔵せず、Google Driveから直接ストリーミング再生します。

- 保存先: Google Drive のフォルダ「Focus BGM」内の `Intersection_At_Daybreak.mp3`
- 共有設定: リンクを知っている人が閲覧のみ可
- 再生URL: `https://drive.google.com/uc?export=download&id=1VvekNctFUcscDtusIGKYztYJ-IAWOtye`

Drive側のファイルを差し替えると、アプリ側の変更なしに音源を更新できます。

## 機能

- ループ再生（2つの音声要素による音量クロスフェード、つなぎ目 0 / 2 / 4 / 6 秒）
- 再生・一時停止、シーク、音量、再生速度（0.85〜1.30倍）
- 集中タイマー（集中 15 / 25 / 50分、休憩 5 / 10分、切り替え時の合図音、セッション数と集中時間の集計）

## 使い方

`index.html` をブラウザで開くだけで再生できます。静的ホスティング（GitHub Pages、Vercel等）に置いても動作します。
