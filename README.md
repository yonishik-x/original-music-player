# Original Music Player

仕事の集中用BGMプレーヤー。単一ファイル（`index.html`）で動作するWebアプリです。

公開ページ: https://yonishik-x.github.io/original-music-player/

## ディレクトリ構成

```
index.html          プレーヤー本体（曲データの定義もここ：TRACKS 配列が唯一の正）
audio/<曲ID>/       曲ごとの音源データ
  parts.txt         分割ファイルの一覧
  part-0, part-1…   MP3をBase64テキスト化して約900KBずつ分割したもの
tracks/             曲ごとの生成プロンプト記録（1曲1ファイル＋一覧 README.md）
generation-policy.md  BGM生成方針（ベースプロンプトと日替わりバリエーションのルール）
README.md           このファイル
```

## 収録曲

- **INTERSECTION AT DAYBREAK**（`audio/daybreak/`）— アップテンポなジャズピアノ（124 BPM、2分52秒）
- **Before the Final Bell**（`audio/bell/`）— ラフマニノフ風ピアノ協奏曲（2分59秒）
- **COFFEE AND GOLD**（`audio/coffee/`）— ピアノポップ（120 BPM、2分59秒）
- **STEPS IN THE SUN**（`audio/sun/`）— ジャズピアノポップ（116 BPM、3分0秒）

いずれも Gemini（Lyria）で生成したインストゥルメンタル。各曲のプロンプトと音源リンクは `tracks/` に記録。

## 曲の追加方法

1. MP3をBase64化し、約900KBずつに分割して `audio/<曲ID>/part-0`〜 に置き、一覧を `audio/<曲ID>/parts.txt` に書く
2. `index.html` の `TRACKS` 配列に1エントリ追加する（id／タイトル／説明／チップ表示／長さ／Drive・Geminiリンク）。プレイリストのUIと「このアプリについて」の曲リストはここから自動生成されるので、他の場所の編集は不要
3. `tracks/` にプロンプト記録ファイルを追加し、`tracks/README.md` の一覧に行を足す

## 音源について

音源はリポジトリ内にBase64テキスト分割で保存され、ページを開いた時点でブラウザがMP3へ復元します（オンになっている曲のみ）。再生中の追加通信はありません。

当初は Google Drive の直接リンクからストリーミング再生する方式でしたが、Driveのダウンロード用URLはブラウザが「ファイルのダウンロード」として扱う応答（Content-Disposition: attachment）を返すため、音声プレーヤーで再生できず、この方式に変更しました。

元のMP3は Google Drive のフォルダ「Focus BGM」にも保管されています。

## 機能

- プレイリスト：ドラッグ＆ドロップで再生順の入れ替え（端末に保存）、曲ごとのオン／オフ切り替え（オフの曲は再生から除外）
- プレイリスト再生＋リピート（全曲／1曲／なし）
- ループ再生（2つの音声要素による音量クロスフェード、つなぎ目 0 / 2 / 4 / 6 秒）
- 再生・一時停止、前／次の曲、シーク、音量、再生速度（0.85〜1.30倍）
- 集中タイマー（集中 15 / 25 / 50分、休憩 5 / 10分、切り替え時の合図音、セッション数と集中時間の集計）
