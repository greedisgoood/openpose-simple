# openpose-simple

このプログラムは、[OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose) の実行を簡単にするバッチプログラムです。

インストール、起動オプション、出力結果等は上記URLをご確認ください。

## 機能概要

以下プログラムで使用するためのOpenposeデータを出力します。

 - [miu200521358/3d-pose-baseline-vmd](https://github.com/miu200521358/3d-pose-baseline-vmd)
 - [miu200521358/3dpose_gan_vmd](https://github.com/miu200521358/3dpose_gan_vmd)
 - [miu200521358/FCRN-DepthPrediction-vmd](https://github.com/miu200521358/FCRN-DepthPrediction-vmd)
 - [miu200521358/VMD-3d-pose-baseline-multi](https://github.com/miu200521358/VMD-3d-pose-baseline-multi)


## 準備

詳細は、[Qiita](https://qiita.com/miu200521358/items/d826e9d70853728abc51)を参照して下さい。

## 実行方法

### 映像の場合

1. `Openpose`の実行ディレクトリ(`bin`とかの一個上) に簡易起動バッチをコピーする
    - PortableDemo版： `LICENSE`のファイルがある階層に、バージョン別のバッチをコピー
      - 1.3 … [PortableDemo/1.3/OpenposeVideo.bat](PortableDemo/1.3/OpenposeVideo.bat) 
      - 1.4 … [PortableDemo/1.4/OpenposeVideo.bat](PortableDemo/1.4/OpenposeVideo.bat) 
      - [OpenposeVideo_en.bat](OpenposeVideo_en.bat) is in English. !! The logs remain in Japanese.
    - 自力ビルド版：`x64`のディレクトリの下に、[self-build/OpenposeVideo.bat](self-build/OpenposeVideo.bat) をコピーする
    - [OpenposeVideo_en.bat](OpenposeVideo_en.bat) is in English. !! The logs remain in Japanese.
1. [OpenposeVideo.bat](OpenposeVideo.bat) を実行する
1. `解析対象映像ファイルパス` が聞かれるので、動画のファイルフルパスを入力する
1. `映像に映っている最大人数` が聞かれるので、映像から読み取りたい最大人数を1始まりで指定する
	- 未指定の場合、デフォルトで1が設定される(１人分の解析)
1. `解析開始フレームNo` が聞かれるので、解析を開始するフレームNoを0始まりで指定する
	- ロゴ等で冒頭に人物が映っていない場合に、人物が映るようになった最初のフレームNoを指定する事で、先頭フレームをスキップできる
	- 未指定の場合、デフォルトで0が設定される(0フレーム目から解析)
1. 処理開始
1. 処理が終了すると、以下に結果が出力される。
    - `解析対象映像ファイルパス/{解析対象映像ファイル名}_{実行日時}/{解析対象映像ファイル名}_json` ディレクトリ
        - → json形式のkeypointsデータ
    - `解析対象映像ファイルパス/{解析対象映像ファイル名}_{実行日時}/{解析対象映像ファイル名}_openpose.avi`
        - → 元映像にOpenposeの解析結果を上乗せしたaviデータ

### 画像の場合

1. `Openpose`の実行ディレクトリ(`bin`とかの一個上) に簡易起動バッチをコピーする
    - PortableDemo版： `LICENSE`のファイルがある階層に、バージョン別のバッチをコピー
      - 1.3 … [PortableDemo/1.3/OpenposeImage.bat](PortableDemo/1.3/OpenposeImage.bat) 
      - 1.4 … [PortableDemo/1.4/OpenposeImage.bat](PortableDemo/1.4/OpenposeImage.bat) 
      - [OpenposeImage_en.bat](OpenposeImage_en.bat) is in English. !! The logs remain in Japanese.
    - 自力ビルド版：`x64`のディレクトリの下に、[self-build/OpenposeImage.bat](self-build/OpenposeImage.bat) をコピーする
    - [OpenposeImage_en.bat](OpenposeImage_en.bat) is in English. !! The logs remain in Japanese.
1. [OpenposeImage.bat](OpenposeImage.bat) を実行する
1. `解析対象画像ディレクトリパス` が聞かれるので、画像が置かれているディレクトリのフルパスを入力する
    - ディレクトリ内には複数枚の画像を置ける
1. `映像に映っている最大人数` が聞かれるので、映像から読み取りたい最大人数を1始まりで指定する
	- 未指定の場合、デフォルトで1が設定される(１人分の解析)
1. 処理開始
1. 処理が終了すると、以下に結果が出力される。
    - `解析対象画像ディレクトリパス/{解析対象画像ディレクトリ名}_{実行日時}/{解析対象画像ディレクトリ名}_json` ディレクトリ/{解析対象画像ファイル名}_keypoints.json.png
        - → json形式のkeypointsデータ
    - `解析対象画像ディレクトリパス/{解析対象画像ディレクトリ名}_{実行日時}/{解析対象画像ディレクトリ名}_openpose/{解析対象画像ファイル名}_rendered.png`
        - → 元画像にOpenposeの解析結果を上乗せしたpngデータ
1. ※画像解析結果は、3d-pose-baseline-vmd 以降には使用できません。

## 注意点

- `JSON出力先ディレクトリパス` に12桁の数字列は使わないで下さい。
    - `short02_000000000000_keypoints.json` のように、`{任意ファイル名}_{フレーム番号}_keypoints.json` というファイル名のうち、12桁の数字をフレーム番号として後ほど抽出するため

## ライセンス
GNU GPLv3


### 以下の行為は自由に行って下さい

- モーションの調整・改変
- ニコニコ動画やTwitter等へのモーション使用動画投稿
- モーションの不特定多数への配布
    - **必ず踊り手様や各権利者様に失礼のない形に調整してください**

### 以下の行為は必ず行って下さい。ご協力よろしくお願いいたします。

- クレジットへの記載を、テキストで検索できる形で記載お願いします。

```
ツール名：MMDモーショントレース自動化キット　/　MMD自動トレース　のいずれか
権利者名：miu200521358
```
- ニコニコ動画の場合、コンテンツツリーへ [トレース自動化マイリスト](https://www.nicovideo.jp/mylist/61943776) の最新版動画を登録してください。
    - コンテンツツリーに登録していただける場合、テキストでのクレジット有無は問いません。

- モーションを配布される場合、以下文言を同梱してください。 (記載場所不問)

```
配布のモーションは、「MMDモーショントレース自動化キット」を元に作成したものです。
ご使用される際には原則として、「MMDモーショントレース自動化キット」もしくは略称の「MMD自動トレース」の使用明記と、
ニコニコ動画等、動画サイトへの投稿の場合、コンテンツツリーもしくはリンクを貼って下さい。
　登録先：MMD自動トレースマイリスト(https://www.nicovideo.jp/mylist/61943776) の最新版動画
Twitter等、SNSの場合は文言のみで構いません。
キット作者が今後の改善の参考にさせていただきます。

キット作者連絡先：
　Twitter：https://twitter.com/miu200521358
　メール：garnet200521358@gmail.com

LICENCE

MMDモーショントレース自動化キット
【Openpose】：CMU　…　https://github.com/CMU-Perceptual-Computing-Lab/openpose
【Openpose起動バッチ】：miu200521358　…　https://github.com/miu200521358/openpose-simple
【深度推定】：Iro Laina, miu200521358　…　https://github.com/miu200521358/FCRN-DepthPrediction-vmd
【Openpose→3D変換】：una-dinosauria, ArashHosseini, miu200521358　…　https://github.com/miu200521358/3d-pose-baseline-vmd
【Openpose→3D変換その2】：Dwango Media Village, miu200521358：MIT　…　https://github.com/miu200521358/3dpose_gan_vmd
【3D→VMD変換】： errno-mmd, miu200521358 　…　https://github.com/miu200521358/VMD-3d-pose-baseline-multi
```

### 以下の行為はご遠慮願います

- 自作発言
- 権利者様のご迷惑になるような行為
- 営利目的の利用
- 他者の誹謗中傷目的の利用（二次元・三次元不問）
- 過度な暴力・猥褻・恋愛・猟奇的・政治的・宗教的表現を含む（R-15相当）作品への利用
- その他、公序良俗に反する作品への利用

## 免責事項

- 自己責任でご利用ください
- ツール使用によって生じたいかなる問題に関して、作者は一切の責任を負いかねます
