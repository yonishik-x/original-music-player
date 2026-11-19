# Original Music Player

仕事の集中用BGMプレーヤー。単一ファイル（`index.html`）で動作するWebアプリです。

公開ページ: https://yonishik-x.github.io/original-music-player/

## 収録曲

- **INTERSECTION AT DAYBREAK** — アップテンポなジャズピアノのインストゥルメンタル（124 BPM、2分52秒）
- Gemini（Lyria）で生成したオリジナル曲

## 音源について

音源はこのリポジトリ内の `track-part-0`〜`track-part-6`（MP3をBase64テキスト化して分割したもの、`parts.txt` が一覧）として保存され、ページ読み込み時にブラウザがMP3へ復元して再生します。

当初は Google Drive の直接リンクからストリーミング再生する方式でしたが、Driveのダウンロード用URLはブラウザが「ファイルのダウンロード」として扱う応答（Content-Disposition: attachment）を返すため、音声プレーヤーで再生できず、この方式に変更しました。

元のMP3は Google Drive のフォルダ「Focus BGM」にも保管されています（`Intersection_At_Daybreak.mp3`、リンクを知っている人が閲覧のみ可）。

## 機能

- ループ再生（2つの音声要素による音量クロスフェード、つなぎ目 0 / 2 / 4 / 6 秒）
- 再生・一時停止、シーク、音量、再生速度（0.85〜1.30倍）
- 集中タイマー（集中 15 / 25 / 50分、休憩 5 / 10分、切り替え時の合図音、セッション数と集中時間の集計）

## 使い方

`index.html` をブラウザで開くか、静的ホスティング（GitHub Pages、Vercel等）に置いて使います。`track-part-*` と `parts.txt` は `index.html` と同じ場所に置いてください。
