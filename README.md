# 概要
ウォーキングシミュレーターゲームのテンプレートです（Unreal Engine 5プロジェクトファイル）。  

サンプルプログラムはFPS視点で3D空間内の100本の蝋燭を歩いて消す百物語カウンターになっています。  
メインメニューや環境設定、コンテニュー、ポーズメニュー、インタラクト（蝋燭を消す）、ダイアログ（会話機能）、アナログ時計サンプルプログラムなどの共通システムがあらかじめ用意されています。  
このゲームテンプレートはUnreal Engine 5でのウォーキングシミュレーターベースの3Dゲームを作る際のベースとして使うことを想定して作っています（自作のFPS視点3Dホラーゲームのベースとして作りました）。  

Unreal Engineやゲーム制作・プログラミングの初心者という方は、過去に公開したUnreal Engine 5プロジェクトファイルの方がより簡単かと思いますので、練習として先にお試しいただくと良いかもしれません。  
* [Text3DGuesser](https://github.com/codelelou/HyakuTales) （Unreal Engine 5のインストールと配布用ファイルの作成練習用のゲームテンプレート）
* [Findloople](https://github.com/codelelou/Findloople) （プログラミング不要で8番ライクゲームも作れるゲームテンプレート）

なお共通システム・共通プログラムはこのゲームテンプレート『HyakuTalesSimTemplate』が最新のものとなっており、過去のゲームテンプレートとは互換性はありません。  
もし新規でオリジナルゲームを開発する際のベースとしてこれらのテンプレートを使用される場合は、『HyakuTalesSimTemplate』の使用がベストかと思います。  

どのテンプレートも共通して環境設定で画質やマウス感度などを設定できるようになっており、初心者でも比較的短期間でゲームの公開までを体験できるかと思います。  

またUnreal Engine 5のライセンス料はゲームの売上が100万ドル（1ドル150円換算で1.5億円）を超えた分に対して5％のため、大半のゲームにおいてライセンス料は発生しない（無料で使用できる）と思われます。  
仮に売上100万ドルを超えてしまったとしても、売上からライセンス料を賄えるでしょう。  

# デモ
このゲームテンプレートでデモとして『[百物語シム](https://codelelou.booth.pm/items/6949715)』を作成しました。  
どのような機能が用意されているのかを把握するのに便利かと思います。  

なおゲーム開発に興味が無くても、百物語配信などでお使いいただけます（配信許可に関してはデモのリンク先に記載しています）。  
百物語配信向けにオリジナル百物語カウンターの作成にご利用いただくことも大歓迎です（Unreal Engineはゲームエンジンですが、映画やアニメ、自動車メーカーなどゲーム以外でも多くの使用実績があります）。  

ただし年間収益100万ドルを超えるスタジオなどが映像作品などのゲーム以外にUnreal Engineを使用する場合は、年間2000ドル弱のライセンス料が発生するようです。  
もし年間収益100万ドルを超える配信者や事務所などが自作のオリジナル百物語カウンターを使って百物語配信を行う場合は、事前にUnreal Engineのライセンスに関して問い合わせた方が良いかもしれません。  
ただ、デモの百物語カウンターや第三者が公開している百物語カウンターを百物語配信に使用するのであればゲーム実況と同じ扱いになりライセンス料は必要ないと推測されます（※個人の感想に過ぎず問い合わせ推奨）。年間収益100万ドルを超える配信者がUnreal Engineで作られたゲームのゲーム実況するとライセンス料を請求されるという話は聞きません。  

---

# 目次
- [導入（開発環境構築）](#導入開発環境構築)
- [オリジナル百物語カウンターの作り方](#オリジナル百物語カウンターの作り方)
  - [蝋燭の編集](#蝋燭の編集)
  - [メイン画面の編集](#メイン画面の編集)
  - [その他](#その他)
- [パッケージ化（配布用exeファイル作成）](#パッケージ化配布用exeファイル作成)
- [フォルダ構成（プログラムなどメインのコンテンツフォルダ）](#フォルダ構成プログラムなどメインのコンテンツフォルダ)
- [ウォーキングシミュレーターゲームテンプレート](#ウォーキングシミュレーターゲームテンプレート)
  - [GameInstance](#gameinstance)
    - [環境設定SaveGame](#環境設定savegame)
    - [MainGame用SaveGame](#maingame用savegame)
    - [コンテニュー機能](#コンテニュー機能)
    - [GameInstance用ブループリントインターフェース](#gameinstance用ブループリントインターフェース)
  - [GameMode](#gamemode)
  - [PlayerController](#playercontroller)
  - [HUD](#hud)
- [共通システム](#共通システム)
  - [インタラクション](#インタラクション)
  - [ダイアログ（ボイス対応会話システム）](#ダイアログボイス対応会話システム)
  - [アイテムビューア](#アイテムビューア)
  - [コントローラー振動](#コントローラー振動)
  - [通知](#通知)
  - [時計](#時計)
- [応用編](#応用編)
  - [国際化（多言語対応）](#国際化多言語対応)
  - [操作方法のキー設定](#操作方法のキー設定)
  - [環境設定画面のカスタマイズ](#環境設定画面のカスタマイズ)
  - [ゲームの画質について](#ゲームの画質について)
  - [サウンドの種類の設定方法](#サウンドの種類の設定方法)
  - [フォント](#フォント)
  - [インタラクティブActorブループリント作成例（回収可能アイテムなど）](#インタラクティブactorブループリント作成例)
  - [プレイヤーキャラクターのカスタマイズ](#プレイヤーキャラクターのカスタマイズ)
  - [別プロジェクトに移行する](#別プロジェクトに移行する)
- [よくある質問](#よくある質問)

---

# 導入（開発環境構築）
Unreal Engine 5プロジェクトファイルを編集するためにUnreal Engine（Unrealエディタ）をインストールする必要があります。  

## Unreal Engineのバージョン
Unreal Engine 5.6  

このバージョン以降のもであれば動作する可能性は高いですが、Unreal Engineのアップデートによっては正常に動作しなくなることはあります。  
このような場合はUnreal Engineのバージョンを下げる必要があります（1つの開発端末に異なる複数のバージョンのUnreal Engineをインストールできます）。  

なお、このゲームテンプレートのアップデート時に対応するUnreal Engineのバージョンが変更になることがあります（バージョンが変更になっても開発中のゲームテンプレートをアップデートしなければ従来通りに開発は継続可能です）。  
ver.01.03.00からUnreal Engine 5.6に変更しています（Unreal Engine 5.6で大きな変化があり公式のアセット・テンプレートの利用や解説などでメリットが大きいと判断しました）。  

## Unreal Engineのインストール
インストールについてはUnreal Engine全般のテーマのため、詳しくは[Unreal Engineダウンロードページ](https://www.unrealengine.com/ja/download)や解説動画などを参考にしてください。  

「Unreal Engine インストール」や「Unreal Engine 入門」などのキーワードで探してみてください。  
このゲームテンプレートを編集する前に、入門者向け・初心者向けの動画などでイメージを掴んでおくのも良いと思います。  

## ゲームテンプレートをダウンロードする
[Releases](https://github.com/codelelou/HyakuTalesSimTemplate/releases)から最新バージョンのゲームテンプレートをダウンロードしてください。  
Assetsの「Souce code (zip)」か「Souce code (tar.gz)」のどちらか一方で構いません。  

ダウンロードが完了したらその圧縮ファイルをわかりやすい場所に展開（解凍）します。  
ゲーム開発ではSSDなどの高速ストレージに展開することを推奨します。  

またディレクトリ構造が深いとゲームエンジンの不具合に繋がることがあるため、浅いディレクトリ階層に展開してください（例えば「D:\UnrealProjects\HyakuTales」など）。  
あわせて親フォルダも含めてフォルダ名は半角英数字のみで構成するようにしてください（Unreal Engineに限らずゲーム開発ではフォルダ名・ファイル名に日本語があると不具合の原因になることがあります）。  

そして展開したUnreal EngineプロジェクトファイルであるHyakuTales.uproject（ファイル名は変更可能ですが、Unreal Engineの仕様により20文字以内推奨）をダブルクリックすれば、対応するUnreal Engineが起動し編集できるようになると思います。  
もし直接開けない場合は、次で説明するUnreal Engineを起動してからプロジェクトファイルを指定して開く方法を試してください。  

## Unreal Engineを起動する
起動するとプロジェクトブラウザが開くと思うので、左上の［最近使用したプロジェクト］を左クリックし、右下の［ブラウズ］ボタンを左クリックしてください（以前からUnreal Engineを使っている場合は自動的に最近開いていたプロジェクトが自動ロードされてしまっている場合があるので、その場合はそれを閉じてプロジェクトブラウザを開いてください）。  

そして先程ダウンロードして展開したゲームテンプレートのアンリアルプロジェクトファイル「HyakuTales.uproject」を開いてください。  
これでこのゲームテンプレートを編集できるようになると思います。  

## 動作確認
エディタ上でゲームをプレイするには、エディタ上部中央左付近の矢印マークが並んだエリアの右端にある点が縦に3つ並んだボタンを左クリックし、	［新規エディタウィンドウ（PIE）］ボタンを左クリックします。  

![エディタプレイ方法の図解](https://github.com/user-attachments/assets/0dd206c2-09c2-4216-88b5-b188111adc87)

なお、このプレイモードではタイトル画面や環境設定画面の表示言語の切替は正常に動作しません。  
またこのモードで言語を切り替えた場合は、エディタの表示言語も切り替わってしまうため注意してください。  

言語の切替も確認したい場合は［スタンドアロンゲーム］モードでプレイしてください（このモードは実行までに多少時間がかかります）。  

---

# オリジナル百物語カウンターの作り方
このゲームテンプレートのサンプルプログラムが百物語カウンターになっており、プログラミング不要で3Dモデルの差替え・追加削除によるオリジナル百物語カウンター作成が可能です。  
3Dモデリングができなくても、アセットストアなどで入手した3Dモデルを使うことができますし、Unreal EngineのRealityCaptureなどスマホのカメラなどから3Dモデルを生成することもできます。  

[デモ用百物語カウンター](https://codelelou.booth.pm/items/6949715)では3Dモデリングは行っておらず、アセットストアで入手した和風環境と蝋燭のアセットを使って作成しました。  
* [和風環境: Japanese Farmhouse](https://www.fab.com/ja/listings/99f75379-1e36-4c6b-bd06-3a9931d48ecf)
* [蝋燭: Candle VFX](https://www.fab.com/ja/listings/98e82577-7a94-4a30-b5b4-b5a2d6073061)

ご自身の百物語配信専用にオリジナル版を作るだけなら、「蝋燭」と「（100本の蝋燭の）メイン画面」の編集だけ良いかと思います（エディタの画面をキャプチャしての配信も可能ですが、エディタは開発用の余分の処理負荷もあるため可能なら[パッケージ化](#パッケージ化配布用exeファイル作成)することを推奨します）。  
第三者に配布・公開する場合は必要に応じて「その他」を参考に編集を行ってください。  

## 蝋燭の編集
蝋燭（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_VefectsCandleVFX.uasset）は1つのプログラムになっており、点灯・消灯で見た目が変化するようになっています。  

デモで使用している[蝋燭アセット: Candle VFX](https://www.fab.com/ja/listings/98e82577-7a94-4a30-b5b4-b5a2d6073061)は個人ライセンス（2025年6月10日現在）なら無料で使用できるため、サンプルの蝋燭では簡単なStaticMesh（3Dモデル）やマテリアル（3Dモデルの表面の画像など）などの設定だけで使用できるようにしています。  
もしこのアセットを使用しない場合は、サンプルとして用意しているシンプルな蝋燭（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_Simple.uasset）を参考にカスタマイズしてください（この蝋燭アセット用の蝋燭サンプルは複雑なつくりをしているため）。  

Unrealエディタの使い方全般の話になるため詳しくは説明しませんが、この蝋燭アセットはWeb上からでもエディタ上でも入手可能です。  
エディタで使えるようにUnrealプロジェクトに追加するには、エディタ上部の［ウィンドウ > （コンテンツを取得） > Fab］を左クリックしてFabプラグインを開き、Fabプラグインの検索機能やMy Libraryなどからこの蝋燭をアセットを開き、［Add to Project］ボタンを左クリックします。ダウンロード・追加が完了すれば、「Lelool」フォルダや「WalkingSimTpl」フォルダと並んで「Vefects」フォルダが作成されていると思います。  
![Fabプラグインを開いてアセット追加完了までの大まかな流れの図解](https://github.com/user-attachments/assets/186881dc-89d0-427f-80ed-4e28a66a0d37)

蝋燭アセットがプロジェクトに追加できたら、先程の蝋燭ActorBlueprint（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_VefectsCandleVFX.uasset）を開きます。  
そしてエディタ上部の［クラスのデフォルト］を左クリックし、「Candle Asset」の各項目に蝋燭アセットを設定していきます。  
- Wax（蝋燭のロウ）
  - WaxStaticMesh = SM_Melted_Candle_02_No_Wick
- Wick（蝋燭の芯）
  - WickStaticMesh = SM_Candle_Wick_01
  - WickLightsOnMaterial（灯火時の先端が光る芯） = MI_Candle_Wick_BP_01
  - WickLightsOutMaterial（消灯時の光っていない芯） = MI_Candle_Wick_Off_01
- Flame（蝋燭灯火時の炎）
  - FlameNiagaraSystemAsset（炎エフェクト） = NS_Candle_Flame_01
  - LightsOutSmokeNiagaraSystemAsset（消灯時の白煙エフェクト） = NS_Candle_Smoke_Mesh_01_Once

蝋燭ActorBlueprintの編集が完了したら、エディタ左上当たりの［コンパイル］ボタンを左クリックします。  
［ビューポート］タブから蝋燭の見た目が変わったことを確認できるかと思います。  

なおデモでは消灯時に効果音を鳴らしているのですが、これは［クラスのデフォルト］の［LightsOutSound］変数にサウンドソースを設定しておくことで鳴らせます。  
デモでは[効果音ラボの『マッチの火を吹き消す』](https://soundeffect-lab.info/sound/various/various3.html)を使用していますが、Unreal EngineはMP3ファイル形式に対応していないため、事前にWavファイル形式などに変換しておく必要があります。また追加した[音ファイルの種類を設定](#サウンドの種類の設定方法)することで環境設定での音量調整（効果音）と連動できます。  

![HT_BP_Actor_Candle_VefectsCandleVFXブループリントの編集の図解](https://github.com/user-attachments/assets/25b2fc97-d0f8-4224-8c82-7c67516b310a)

## メイン画面の編集
100本の蝋燭が表示される百物語カウンターのメイン画面には次の3つの要素が必要です。  
1. 蝋燭×100本
2. HT_BP_Actor_CandleManager(/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_CandleManager.uasset): 蝋燭を管理するプログラム
3. PlayerStart: プレイヤーキャラクターがスポーンされる開始位置

参考までにサンプルのメイン画面（/Content/HyakuTales/Level/HT_Level_CandlesSpace.umap）では次のアクターで構成されています（Unreal Engineではレベル上に配置する3Dモデルやライトなどのあらゆるものをアクターと呼びます）。  
* 蝋燭×100本
* HT_BP_Actor_CandleManager: 蝋燭を管理するプログラム
* PlayerStart: プレイヤーキャラクターがスポーンされる開始位置
* Plane: 床
* DirectionalLight: 全体を照らす照明
* 時計: アナログ時計サンプル（技術デモ用）
* HT_BP_Actor_ItemViewer_Sample: アイテムビューアサンプル（技術デモ用）

サンプルのメイン画面を編集する場合は、お好みで床を削除したり3Dモデルや照明などを配置してください。  

ただアセットストアで入手した環境アセットはあらかじめ建物などが組み立て済みのレベルが用意されていることが多く、そのレベルに先程の必要な3つの要素を配置する方が楽かと思います（PlyarStartアクターは予め配置されてることがあります）。  
デモ用の百物語カウンターでは環境アセットのサンプルレベルを利用しています。床や壁など個別の3Dモデルをあらかじめ組み合わせてくれているので便利です。  

もしこのようなアセットのレベルを使用する場合は、そのレベルのGameModeをHT_BP_GameMode_Candlesブループリント（/Content/HyakuTales/Blueprint/GameMode/HT_BP_GameMode_Candles.uasset）に変更してください。エディタのレベルビューの右上あたりの［設定］ボタンを左クリックし、［ワールドセッティング］を左クリックして表示される［ワールドセッティング］タブの［GameMode > ゲームモードオーバーライド］に「HT_BP_GameMode_Candles」を設定します。  
![メイン画面レベルのGameModeを変更する手順の図解](https://github.com/user-attachments/assets/41cd1f9c-fbdb-4d26-95cc-f86abb3beb9c)

あわせてHT_BP_GameInstanceブループリント（/Content/HyakuTales/Blueprint/GameInstance/HT_BP_GameInstance.uasset）を開き、エディタ上部の［クラスのデフォルト］を左クリックし、右側に表示される［詳細］タブの［デフォルト > MainLevel］に新たに作成したレベル（アセットのレベルを直接したのならそのレベル）を設定してください（デフォルトはサンプルのメイン画面になっています）。  
![HT_BP_GameInstanceブループリントのMainLevelクラス編集変更箇所の図解](https://github.com/user-attachments/assets/c6948b43-e78e-45db-9ce7-570512f5878c)

なおデモのように蝋燭間の距離が近いと、近づいた時に消す対象となる蝋燭の数が多くなり、調整しないと操作性が悪くなる恐れがあります。  
どうしても蝋燭間の距離を近づけたい時は、蝋燭ActorBlueprint（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_VefectsCadleVFX.uasset）を開き、エディタ左側の［コンポーネント］タブ内のInteractionComponentを選択し、エディタ右側に表示される［詳細］タブのパラメーターを調整してください。  
デモでは次のように調整しています。  
* OverrideMaxVisioDistance（インタラクト可能な距離） = 300（初期値500）
* OverridePlayerAngle（インタラクト可能なプレイヤーの視角） = 10（初期値25で、小さいと判定が悪くなり操作性が犠牲になります）
![蝋燭アクターのInteractionComponent設定のオーバーライド箇所の図解](https://github.com/user-attachments/assets/408d034a-f1e6-489f-a798-181434bfa09e)

可能であれば蝋燭の配置を見直し、蝋燭間の距離を広くすることを推奨します。  

## その他

### メインメニューの編集
メインメニューには次の2つの要素が必要です。  
1. HT_BP_LevelHelper_MainMenu（/Content/HyakuTales/Blueprint/LevelHelper/HT_BP_LevelHelper_MainMenu.uasset）: メインメニューのUI表示などを行っているプログラム
2. カメラアクター: メインメニューで使われるカメラ（CineCameraActorなど）

メインメニューは起動時に表示される画面で、終了もこの画面から行います（Alt+F4キーのショートカットでメイン画面からでも終了は可能）。  
ご自身の百物語配信で使用する場合など、メインメニューのカスタマイズが不要なら編集は不要です。  

サンプルのメインメニュー（/Content/HyakuTales/Level/HT_Level_MainMenu.umap）は次のアクターで構成されています。  
* HT_BP_LevelHelper_MainMenu: メインメニューのUI表示などを行っているプログラム
* CineCameraActor: 蝋燭6本を写すカメラ
* Plane: 床
* 蝋燭×6本

メイン画面と同様に、アセットストアで入手したアセットが用意したレベルを使っても良いですし、サンプルのメインメニューレベルを編集しても良いです。  

アセットストアで入手したアセットのレベルを使用する場合は、GameModeをHT_BP_GameMode_MainMenuブループリント（/Content/HyakuTales/Blueprint/GameMode/HT_BP_GameMode_MainMenu.uasset）に設定してください。またメイン画面と同様に、HT_BP_GameInstanceブループリント（/Content/HyakuTales/Blueprint/GameInstance/HT_BP_GameInstance.uasset）を開き、エディタ上部の［クラスのデフォルト］を左クリックし、右側に表示される［詳細］タブの［デフォルト > MainMenuLevel］に新たに作成したレベル（アセットのレベルを直接したのならそのレベル）を設定する必要があります（デフォルトはサンプルのメインメニューになっています）。  
あわせて、レベル上のHT_BP_LevelHelper_MainMenuアクターを選択した状態でエディタ右側の［詳細］タブの［デフォルト > Camera］にレベル上のカメラアクターを設定してください（Camera項目の右側にあるスポイト風アイコンを左クリックした後にレベル上のカメラアクターを左クリックして設定可能）。  
![HT_BP_LevelHelper_MainMenuアクターのCamera変数の場所の図解](https://github.com/user-attachments/assets/6be99770-dfe7-4436-8124-cfd20578599d)

サンプルのメインメニューレベルではHT_BP_LevelHelper_MainMenuが蝋燭6本を参照しているため、これらの蝋燭を削除する場合はその前に、HT_BP_LevelHelper_MainMenuを選択し［デフォルト > Candles］変数の右側にある削除ボタン（ゴミ箱アイコン）を左クリックして参照を解除してください。  
ちなみにこの蝋燭6本の参照は、メインメニュー表示中にメニュー内のボタンのホバー状態に応じて点灯する蝋燭が変化するギミックに使用しているだけです。  

### プロジェクト設定
エディタ上部の［編集 > プロジェクト設定］を左クリックしてプロジェクト設定を開きます。  

プロジェクト設定の［プロジェクト > 説明］を開き、［Unreal Editorについて > プロジェクト名］と［表示 > プロジェクトが表示されたタイトル］にゲームタイトルに入力します（ゲーム起動時のウィンドウ名に使用されます）。  

なお、［Unreal Editorについて > プロジェクト名］はWindowsのタスクマネージャーのアプリの表示で影響があるようです。  
他の項目は特に変更しなくても問題ないかと思いますが、［Unreal Editorについて > プロジェクトバージョン］が未入力だとパッケージ化時にエラーが発生し失敗するようです。  

#### MegaLights
プロジェクト設定の［エンジン > Rendering > 直接ライティング > MegaLight］にチェックを入れると、パフォーマンス（FPS値）の向上が期待できます。  
従来は大量のライトを配置（サンプルの蝋燭は1本ずつにライトがあるため、100個以上のライトを配置していることになります）すると大幅なパフォーマンスの低下の原因となっていましたが、MegaLightsは効率的に大量のライトを処理できるようになります。  

ただしMegaLightsはUnreal Engineの実験的機能で、現時点では製品版での使用は非推奨であり、特にオリジナル百物語カウンターの販売する予定であれば注意してください（禁止されているわけではありません）。  
特にMegaLightsはUnreal Engine 5.5でリリースされた新しい機能のため、より慎重な判断が必要です。  

デモ用百物語カウンターではメインメニューやポーズメニューからMegaLightsのOn/Offの切替ができるようになりますのでお試しください。  

### プロジェクトデータ データテーブル
メインメニューやクレジット表記などに使用するゲームタイトルやバージョン情報、著作権表示などをまとめてプロジェクトデータとしてデータテーブルファイルで管理しています（実際に使用されるデータテーブルは［プロジェクト設定 > プロジェクト > マップ&モード > GameInstance > ゲームインスタンス］で指定されたGameInstanceブループリントのProjectDataTable変数で指定されたデータテーブルになります）。  

サンプルのプロジェクトデータ（/Content/HyakuTales/Blueprint/ProjectData/HT_DataTable_ProjectData.uasset）を開いて、必要な項目を編集してください。  
* Title: メインメニューやUnreal Engineのクレジット表記に使用
* Version: メインメニューの左下部に表示されます（初リリース時は「Ver.01.00.00」などどすると良いでしょう）
* Copyright: メインメニューの右下部に表示されます（「© CodeLelou 2025」のように「著作権マーク 権利者名 リリース年」という書式が一般的なようです）
* RealeaseYear: Unreal Engineのクレジット表記に使用
* UnrealEngineCredit: Unreal Engineのクレジット表記のフォーマットで、特に理由が泣ければ編集しないようにしてください。
* TemplateCredit: このゲームテンプレート「Hyaku Tales Sim Template」のライセンス表記で編集しないでください。
* OtherCredits: Unreal Engineとこのゲームテンプレートの以外のライセンス表記を入力します。

UnrealEngineCredit/TemplateCredit/OtherCreditsに関しては、メインメニューのインフォメーションボタンで表示されるインフォメーションUIのクレジットタブに表示されます。  
ライセンスにもよりますがこのようなライセンス・クレジットの表記は必ずしもゲーム内で表示しなければならないわけでなく、ストアページへの記載やゲームファイルに同梱しても良い場合、ゲームクリア後のエンドロールなどで表記する場合など色々です。  
サンプルでは記載忘れを起こしにくいように、インフォメーションとして表示する機能を実装しました。  

またOtherCreditsに関して、基本的にゲームのアセットストアで入手したものは追加の規約などが無い限りは無料アセットでも特にクレジット表記は不要なことが多いようです。  
例えばデモではアセットストア以外で入手した効果音素材を使用しているため、そのクレジット表記をここに記載しています。  
他にもフリーフォントなどを埋め込む場合もクレジット表記が必要になることが多いかと思います。  

なお無料のものだからといってクレジット表記を蔑ろにしてはいけません。  
もしクレジット表記が使用条件に含まれている場合は、その条件を守っている場合にのみ無料で使用できるのであって、その条件を守っていない場合は無料で使用することはできません。もちろん条件を守らなかったからと言って法外な使用料の請求は法的には認められないでしょうが、割高な使用料の支払いの可能性は否定できません。  

### インフォメーション
メインメニューの［インフォメーション］ボタンで表示される内容は、インフォメーションコンテンツ（/Content/WalkingSimTpl/UI/Info/WST_WBP_Info_Content.uasset）のものになり、ゲームの概要タブとクレジットタブに分かれたUIになっています。  

概要タブに関しては必要に応じて、［デザイナー］の［階層］タブの［SummaryRichTextBlock］を選択し、右側に表示される［詳細］タブの［コンテンツ > Text］を編集してください。  
なおクレジットタブに関しては基本的に編集しないようにしてください（[プロジェクトデータ データテーブル](#プロジェクトデータ データテーブル)の設定内容が表示されるようになっています）。  

---

# パッケージ化（配布用EXEファイル作成）
パッケージ化することで、作ったゲームを他のPCやスマートフォンなどで遊べるようになります。  
Unreal Engine 5はパソコンやスマートフォン以外にも、ゲームコンソール（Switch/PlayStation/Xboxなど）にも対応しています。  
※このテンプレートはWindows向けの動作確認しかしていません。  

どのプラットフォーム向けにパッケージ化するにしても、そのプラットフォーム向けに別途SDKのインストールなど準備が必要です。  
もしすでにUnreal Engineでゲームを開発していてパッケージ化の準備が完了しているのであれば、すぐにパッケージ化できるかと思います。  

ただパッケージ化に関してはこのゲームテンプレート固有のテーマではないため、詳しいパッケージ化の手順などについては公式ドキュメントや動画などを参考にしてください。  

「UE5 パッケージ化」などのキーワードでネットや動画を検索してみてください。  
なおUnreal Engineのバージョンや開発環境がWindowsかMacなどかによって必要なものや手順が異なることがあるため、1つの情報だけでは上手くできない可能性があります。  

もしパッケージ化が失敗する場合、まずはこのゲームテンプレートを編集せずにそのままパッケージ化を試してみても良いかもしれません。  
この時点で失敗する場合はパッケージ化の準備が不十分であると考えられますし、成功する場合はカスタマイズしたゲーム側に問題があると考えられます。  

なおパッケージ化に関しては普通にプログラミングできる人でも苦戦することは珍しくない躓きポイントですので、上手くいかなくてもあまり気にする必要はありません。  
ゲーム開発者でもパッケージ化経験がない人は少なくないでしょうし、そもそもゲームを完成することなく頓挫することも珍しくはありません。  
そのためにパッケージ化に関する情報自体が少ないです。  

## パッケージ化の手順
Windows向けのパッケージ化の準備が完了している場合、次の手順でパッケージ化可能です。  
細かい設定を行うことでパッケージ化したファイルを小さくしたり暗号化したりもできますが、ここでは割愛します。  

![パッケージ化ボタン位置の図解](https://github.com/user-attachments/assets/d977798d-4556-4759-a494-533d7c1c56c0)

エディタ上部中央の［プラットフォーム］ボタンを左クリックしてメニューを開き、［コンテンツ/SDK/デバイス管理 > Windows］を開きます。  
この時、［Windows］の前にビックリマークアイコンが表示されている場合はパッケージ化の準備が完了していないと思われます。  
そして［バイナリ コンフィギュレーション > シッピング］が有効（白い点）になっていなければ、それを左クリックして有効にしてください。  
［シッピング］が有効であれば、［コンテンツ管理 > プロジェクトをパッケージ化］を左クリックしてください。  
保存先のディレクトリを聞かれるので、パッケージ化用にわかりやすいフォルダを作って指定します。  

これでパッケージ化の処理がはじまります。  

パッケージ化時間はゲームの内容や開発端末性能（おそらくCPU性能）で大きく異なります。  
ハイスペックゲーミングPC程度の環境であれば数分ですが、ロースペックPC環境だと数十分以上掛かる可能性があります。  

完了後は成功しても失敗しても音で通知してくれるはずです。  

パッケージ化が成功していれば、指定したフォルダに「Windows」フォルダができていて、その中に配布用ファイル一式がまとめっていると思います。
配布する時はそのWindowsフォルダをZIP化するなどして公開すると良いでしょう（Steamなどのストアで公開する時は、ストアの指示に従ってください）。  

設定などを変更していなければ「HyakuTales.exe」をダブルクリックすればゲームが起動するはずです。  
実は恐ろしい話ですが、エディタ上では問題なく動作していても、パッケージ化すると動作しなくなることは珍しくなく、配布用のファイルでもテストプレイが必要です（ゲームエンジンそのものにもバグはありえます）。  

---

# フォルダ構成（プログラムなどメインのコンテンツフォルダ）
* HyakuTales: 百物語カウンターの本体（ファイル名は原則として「HT_」ではじまるように統一しています）
* Lelool: 共通プログラムファイルで可能な限り編集は避けることを推奨（ファイル名は原則として「Lelool_」ではじまるように統一しています）
* Localization: 国際化ファイルで直接変更非推奨（Unreal Engine標準のローカライゼーションダッシュボードが生成するフォルダ・ファイル）
* WalkingSimTpl: ウォーキングシミュレーターゲームのテンプレート（ファイル名は原則として「WST_」ではじまるように統一しています）

メインのプログラムは極力Leloolフォルダの共通プログラムファイルで行っているため、このゲームテンプレートをアップデートする際はこの共通プログラムファイルがメインになります。  
そのためLeloolフォルダの編集を避けることで、ゲームテンプレートのアップデートを行う際のマージの手間とリスクの抑制が期待できます（特に「Blueprint」「Component」「UI」内のファイルの編集は避けてください）。  

ただし操作の入力キーを変更する場合は、Leloolフォルダ直下のInputフォルダ内にあるInputMappingContextデータアセットを編集することにはなるかと思います（アップデート後に入力キーを再設定してください）。  
もしくはInputMappingContextデータアセットを指定している個所で、独自に作成したInputMappingContextデータアセットを指定します（原則としてサンプルプログラムではInputMappingContextデータアセットをクラス変数化しているはずなので、子クラスなどでオーバーライドできるかと思います）。  

なおサンプルの百物語カウンターではWalkingSimTplフォルダを編集していませんが、これはウォーキングシミュレーターゲームのテンプレートをプレーンな状態のままにするためです。  
オリジナルゲーム制作で使用する場合はWalkingSimTplフォルダをメインの作業フォルダにし、既存ファイルも必要に応じて編集・削除すると良いかと思います（フォルダ名の変更は可能ですが、ファイル参照などに影響がでることもあるのであえて「WalkingSimTpl」のままの方がトラブルは少ないかもしれません）。  

---

# ウォーキングシミュレーターゲームテンプレート  
共通システムであるLeloolフォルダのプログラム（原則ファイル名が「Lelool_」で始まる）をウォーキングシミュレーターゲーム用に組み合わせた構成になっています。  

それらのプログラムは基本的にウォーキングシミュレーター用の子クラス（原則ファイル名が「WST_」で始まる）を作成して使っています。  
カスタマイズする場合はこの子クラス側で上書き（オーバーライド）することで、共通システムのアップデートがあった場合でもLeloolフォルダの更新だけで済ませやすくなり、アップデートの手間やリスクを抑制できます。  

## GameInstance
GameInstanceはゲーム起動時に呼ばれ、そのままゲーム終了時まで使われます（レベルやGameMode、PlayerController、PlayerCharacterなどは、レベルが変わる度に破棄・読込が行われます）。  

デフォルトでは百物語カウンター用GameInstance（/Content/HyakuTales/Blueprint/GameInstance/HT_BP_GameInstance.uasset）になっているため、オリジナルゲーム制作時はウォーキングシミュレーター用GameInstanceに変更しましょう。  
エディタ上部の［編集 > プロジェクト設定］を左クリックしてプロジェクト設定を開き、［プロジェクト > マップ&モード > GameInstance > ゲームインスタンス］にWST_BP_GameInstance（/Content/WalkingSimTpl/Blueprint/GameInstance/WST_BP_GameInstance.uasset）を設定して変更できます。  

そしてWST_BP_GameInstanceブループリントを開き、エディタ上部の［クラスのデフォルト］ボタンを左クリックし、［詳細］タブの各項目を必要に応じて編集してください。  
* MainMenuLevel（メインメニューレベルを設定する）  
* MainLevel（メインレベルを設定する）  
* ProjectDataTable（メインメニューの著作権表記や、インフォメーションのクレジット表記の情報をまとめたデータテーブルを設定する）  

サンプルではMainLevelは1つしか設定できませんが、メインメニューレベルとメインレベルの2つだけでは足りない場合は、このGameInstanceに他のレベルを開く処理（OpenLevel）を実装します（その場合はレベルファイルの変数化は必須ではありません）。  

ただこのゲームテンプレートはあくまでウォーキングシミュレーターゲームのベースとなるテンプレートであり、Unreal Engineでのゲーム制作を広く・深く解説するのを目的としていないため、詳しい解説は行いません。  

### 環境設定SaveGame
WST_BP_GameInstanceブループリントのクラス変数（クラスのデフォルト > 詳細タブ）で環境設定SaveGameの設定が可能です。  
* SettingsSlotName: 環境設定のセーブファイル名として使用されます（Windows OSの場合でOSなどによって仕様が異なる場合があります）。
* SettingsSaveGameClass: 使用する環境設定SaveGame用ブループリントクラスを設定します。
* SoundMix: 音量設定で使用するサウンドクラスミックスを設定します。

もしSettingsSaveGameClassをゲーム公開後に変更する場合はSettingsSlotNameも変更した方が良いかもしれません（公開前の開発中であれば、開発環境のセーブファイルを削除すれば良いです）。  
セーブファイルが既に存在する場合はSettingsSaveGameClassを変更しても、セーブファイルが作成された時点で設定されていたSettingsSaveGameClassが使用されるようです。  
なおSettingsSlotNameを変更すると実質的にそのセーブファイルを削除したのと同じとなるため、アップデート情報などに環境設定がリセットされる旨の通知を検討してください。  

ロードしたセーブデータが旧SaveGameClassであれば新SaveGameClassにマージすることも可能ですが、実装の手間が多くバグの原因になる恐れもあり、可能な限りゲームリリース後のSaveGameClassの変更は避けて、そのSaveGameClassへの項目追加で対応しましょう（そもそもゲームリリース後にSaveGameClassを変更することは極めて稀なケースかと思います）。  

### MainGame用SaveGame
WST_BP_GameInstanceブループリントのクラス変数（クラスのデフォルト > 詳細タブ）でMainGame用SaveGameの設定が可能です。  
* InGameSaveGameSlotName: MainGame用セーブファイル名として使用されます。
* InGameSaveGameClass: 使用するMainGame用SaveGameブループリントクラスを設定します。

サンプル（/Content/HyakuTales/Blueprint/GameInstance/HT_BP_GameInstance.uasset）ではHT_BP_SaveGame_HyakuTalesブループリント（/Content/HyakuTales/Blueprint/SaveGame/HT_BP_SaveGame_HyakuTales.uasset）を設定しており、消した蝋燭の数やカウンターの表示位置などを記録できるようにしています。  

また環境設定SaveGameと同様に、ゲームを公開後にInGameSaveGameClassを変更する場合はInGameSaveGameSlotNameも変更する必要があります。  
ただ管理するデータによってはクリア情報などもリセットされてしまうため、可能であればInGameSaveGameClassを変更せず、設定しているSaveGameブループリントに項目を追加して対応することを推奨します。  

### コンテニュー機能
コンテニューの有無をWST_BP_GameInstanceブループリント（/Content/WalkingSimTpl/Blueprint/GameInstance/WST_BP_GameInstance.uasset）のIsContinue関数（WST_BPI_GameInstance_MainGameブループリントインターフェース）で管理しています。  
デフォルトでは何もチェックしていないため、常にFalse（コンテニュー無し）となっています。  

作るゲームによってコンテニュー可能な場合は、この関数内でコンテニューの有無をチェックして、コンテニューがある時はTrueを返します。  
サンプルとして百物語カウンター用のHT_BP_GameInstanceブループリント（/Content/HyakuTales/Blueprint/GameInstance/HT_BP_GameInstance.uasset）のIsContainue関数では、MainGameSaveGameブループリント内のNumber値（消した蝋燭の数）をチェックし、1～99本の場合はコンテニュー有としています。  

コンテニュー機能はリストア処理（取得済みのアイテムが未取得扱いや解錠したはずのドアが施錠されたままなど）が不具合リスクになるのですが、逆にスタックやUIバグなどにより進行不能になった時の救済処置にもなるので分岐が無いゲームでもコンテニュー対応にはメリットもあります。  
しかしゲーム開発初心者の内は技術的な負担も大きいでしょうから、プレイ時間が数時間程度のゲーム内容であれば、スタックやUIバグなどを重点的に行ってコンテニュー未対応でも悪くないと思います（結果的にバグの抑制になるメリットがある）。  

#### メインメニューのコンテニューボタン
メインメニューWidget（/Content/WalkingSimTpl/UI/MainMenu/WST_WBP_MainMenu.uasset）のコンテニューボタン（/Content/WalkingSimTpl/UI/MainGame/WST_WBP_Button_Start_Continue.uasset）は、ボタン側の処理でGameInstanceのIsContainue関数をチェックしてコンテニューが無い時は無効化しています。  
ゲームとしてコンテニューに対応しない場合は、メインメニューWidget内のコンテニューボタンを非表示（Visibility=Collapsed）にしてください（メニュー内でコンテニューボタンへの参照があるため、削除する場合は手間が増えます）。  

なお新規プレイボタン・コンテニューボタンのどちらが押された場合でも、GameInstanceのOpenMainLevelイベント（WST_BPI_GameInstance_MainGameブループリントインターフェース）が呼ばれます。  
NewGame引数がTrueの時は、MainGameSaveGameの初期化処理（ResetMainGameSaveGameイベント）を実行してからメインレベルを開きます。  
そのため、メインレベルではGameInstanceのIsContainue関数がTrueの時はリストア処理の実装が必要です。もし進行状況によってレベルが異なる場合は、進行状況に応じてあらかじめ開くレベルを変更すると良いでしょう。  

### GameInstance用ブループリントインターフェース
GameInstance用ブループリントインターフェースがあります。  
* Lelool_BPI_GameInstance_Settings（/Content/Lelool/Blueprint/GameInstance/Lelool_BPI_GameInstance_Settings.uasset）
* WST_BPI_GameInstance_MainGameブループリントインターフェース（/Content/WalkingSimTpl/Blueprint/GameInstance/WST_BPI_GameInstance_MainGame.uasset）

これらのインターフェースにより、ActorブループリントやWidgetブループリントなどｄGameInstanceを取得できるGetGameInstanceノードの返り値をキャスト（Cast to HT_BP_GameInstance）することなく、環境設定SaveGameを取得したりメインメニューを開いたりすることができます（インターフェースの使い方がわからないならキャストしても良いです）。  

Lelool_BPI_GameInstance_Settingsブループリントインターフェースでは、環境設定SaveGameの取得・セーブ・リセットなどが可能です。  
WST_BPI_GameInstance_MainGameブループリントインターフェースでは、メインメニューを開いたりMainGame用SaveGameの取得・セーブ・リセットなどが可能です。  

## GameMode
Unreal Engineではレベル毎に何かしらのGameModeブループリントを設定することになり、レベル毎に使用するPlayerControllerやPlayerCharacterなどのクラスを設定します。  
UI専用レベルであればプレイヤーキャラクターは不要なため、プレイヤーキャラクタークラスを設定していないGameModeを使うのがベターです。  

ウォーキングシミュレーター用にGameModeは大まかにUI用GameMode（/Content/WalkingSimTpl/Blueprint/GameMode/WST_BP_GameMode_Menu.uasset）とキャラクターが歩く用GameMode（/Content/WalkingSimTpl/Blueprint/GameMode/WST_BP_GameMode_Character.uasset）を作っており、UI用が親クラス（ベース）でキャラクターが歩く用が子クラスとなっています。  
なお百物語カウンターで使っているGameModeはそれぞれの子クラスであり、UI用GameMode（/Content/HyakuTales/Blueprint/GameMode/HT_BP_GameMode_MainMenu.uasset）とキャラクターが歩く用GameMode（/Content/HyakuTales/Blueprint/GameMode/HT_BP_GameMode_Candles.uasset）となっています。  

ゲームの仕様によって異なりますが、  
* メインメニューレベル（起動画面）: UI用GameMode  
* ステージ1レベル: キャラクターが歩く用GameMode  
* ステージ2レベル: キャラクターが歩く用GameMode  
* ステージ3レベル: キャラクターが歩く用GameMode  
* ステージ4レベル: キャラクターが歩く用GameMode  
* ステージ5レベル: キャラクターが歩く用GameMode  
* エンドロールレベル: UI用GameMode  
のような感じになるかなと思われます（ムービーシーン専用レベルを作る場合はUI用GameModeを使うかもしれません）。  

全てキャラクターが歩く用GameModeにして、UI用レベルの時はカメラを固定にし、プレイヤーキャラクターの入力を無効化（DisableInput）するといったこともできます。  

## PlayerController  
PlayerControllerはUI用（メインメニューレベルで使用）と、その子クラスであるキャラクター操作用の2種類があり、GameModeでそれぞれ指定しています。  
* UI用: WST_BP_PlayerController_Menu（\Content\WalkingSimTpl\Blueprint\Controller\WST_BP_PlayerController_Menu.uasset）
* キャラクター操作用: WST_BP_PlayerController_Character（\Content\WalkingSimTpl\Blueprint\Controller\WST_BP_PlayerController_Character.uasset）

違いは、InputModeがUIOnly（UI用）かGameOnly（キャラクター操作用）の違いと、キャラクター操作用では環境設定の視角や設定の反映や一時停止の切替処理を行っています。  

主な使い方としては、UnrealEngine標準のGetPlayerController関数の返り値に対して、WST_BPI_PlayerControllerブループリントインターフェース（\Content\WalkingSimTpl\Blueprint\Controller\WST_BPI_PlayerController.uasset）経由で以下の機能を呼べます。  
* ForceFeedback（コントローラー振動）
* Dialogue（ボイス対応会話システム）
* ItemViewer（3Dモデルを画面中央に表示して回転・拡大できる機能）

## HUD
HUDはUI用（メインメニューレベルで使用）と、その子クラスであるキャラクター操作用の2種類があり、GameModeでそれぞれ指定しています。  
* UI用: WST_BP_HUD_Menu（\Content\WalkingSimTpl\Blueprint\HUD\WST_BP_HUD_Menu.uasset）
* キャラクター操作用: WST_BP_HUD_Character（\Content\WalkingSimTpl\Blueprint\HUD\WST_BP_HUD_Character.uasset）

違いはキャラクター操作用HUDではレティクル（画面中心点）も管理している点です。  

主な使い方としては、UnrealEngine標準のGetHUD関数（UnrealEngine標準のGetPlayerController関数の返り値に対して実行）の返り値に対して、WST_BPI_HUDブループリントインターフェース（\Content\WalkingSimTpl\Blueprint\HUD\WST_BPI_HUD.uasset）経由で以下の機能を呼べます。  
* Notice（画面左上に表示するメッセージ）  

---

# 共通システム

## インタラクション
インタラクションはアイテムを拾ったりドアの開閉などに使うもので、サンプルの百物語カウンターでは蝋燭を消すアクションがこれにあたります。  
アイテムビューアのサンプルActorBlueprint（\Content\HyakuTales\Blueprint\Actor\ItemViewer\HT_BP_Actor_ItemViewer_Sample.uasset）がシンプルなサンプルになるかと思います。  

このインタラクション機能はFPS視点向けのため、TPS視点や固定カメラには非推奨です。  
TPS視点や固定カメラの場合は、単純に配置したコリジョン（トリガー）のオーバーラップイベントでドアの開閉などを行うと良いかと思います。  

インタラクション可能ActorBlueprintのベース（/Content/WalkingSimTpl/Blueprint/Actor/WST_BP_Actor_Interaction_Base.uasset）を作成済みですので、このActorBlueprintを複製するか子クラスとして、拾うことができるアイテムなどのActorBlueprintを作ると便利です。  
もしアセットストアで入手したActorBlueprintにインタラクション機能を追加したい時は、そのActorBlueprintの親クラスが「Actor」であれば、その親クラスを「WST_BP_Actor_Interaction_Base」すれば使えるようになるはずです（親クラスの変更は［クラス設定 > クラスオプション > 親クラス］から行えます）。  

参考までにインタラクション可能なActorBlueprintを作る共通となる手順を紹介します。  
* ActorComponentとしてWST_BP_InteractionComponent_Actor（/Content/WalkingSimTpl/Component/Interaction/WST_BP_InteractionComponent_Actor.uasset）を追加する。  
* インタラクション用OverlapCollisionを追加する（大き目のサイズにし、プレイヤーキャラクターがオーバーラップしている時にインタラクションの判定処理が行われる）。  
* Lelool_BPI_InteractionActorブループリントインターフェース（/Content/Lelool/Component/Interaction/Actor/Lelool_BPI_InteractionActor.uasset）を実装する。  
* ［オプション］インタラクション用ArrowComponentを追加（プレイヤーキャラクターの視界にActorBlueprintが入っているかの基準として使われる）し、Lelool_BPI_InteractionActorブループリントインターフェースのGetInteractionActorVisioTargets関数がインタラクション用ArrowComponentを返すようにする。  

これらの手順は共通して必要なもので、ActorBlueprint別に「蝋燭を消す」や「アイテムを拾う」や「ドアを開ける」といった個別のアクションに対応する必要があります。  
オプションのインタラクション用ArrowComponentは、インタラクト対象となるアクター側がプレイヤーキャラクターを見ているかどうかの判定に使用されます。通常は360度全方向からインタラクト可能なのですが、これにより例えば柱に掛かった鍵などを柱の裏側からインタラクトできなくすることが可能になります（画面上に映っていないアクターにインタラクトできてしまう事故防止などに便利）。  

まずはインタラクトが可能になった時に画面下部のインタラクションUIにメニューを表示する方法です。  
これはLelool_BPI_InteractionActorブループリントインターフェースのGetInteractionActorActions関数を使います。  
サンプルのHT_BP_Actor_Candle_Base（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_Base.uasset）では、蝋燭点灯時にLightsOutAction（消灯アクション）として消灯用GameplayTagを返すようになっています。  
もしこれがドアであれば、ドアが閉じていることをプログラムでチェックした上でドアを開ける用GameplayTagを返したり、施錠用GameplayTagも一緒に返すことだってできます。  

次はプレイヤーがインタラクションメニューからアクションを実行した場合の処理になります。  
これにはLelool_BPI_InteractionActorブループリントインターフェースのCallInteractionActorActionイベントを使います。  
サンプルのHT_BP_Actor_Candle_Base（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_Base.uasset）では、GameplayTag引数が消灯用GameplayTagと同じかチェックして、同じであれば消灯処理を実行しています。  
もしこれがドアであれば、ドアを開ける用GameplayTagと同じならドアを開ける処理を、施錠用GameplayTagと同じであれば施錠処理を実行します。  

なおインタラクト可能なActorBlueprintは可能な限り距離を離して配置することを推奨します。  

デモでは参考としてあえて100本の蝋燭を近づけて配置する方法を実現していますが、個々の蝋燭の判定処理を小さくするなどの調整が必要となるため、ゲームによっては判定の悪さからゲーム体験を損なう恐れがあります。  
判定の調整はWST_BP_InteractionComponent_Actorを選択し、エディタ右側に表示される［詳細］タブのパラメーターで可能です。  
デモでは次のように調整しています。  
* OverrideMaxVisioDistance（インタラクト可能な距離） = 初期値500
* OverrideObjectAngle（インタラクション用ArrowComponentの視角） = 初期値360（ドアスコープや鍵穴などを覗くアクションの場合に片側からしか覗けないようにするなどの使い方が可能）
* OverridePlayerAngle（インタラクト可能なプレイヤーの視角） = 初期値25（小さいと判定が悪くなり、逆に大きすぎると背後のアイテム入手やドアの開閉が可能になってしまいます）

他にもインタラクション用ArrowComponentの位置や角度を変更することでも調節できる場合があります。
またプレイヤーキャラクターの身長やActorBlueprintとの位置関係によっても判定に影響が出ることがあります。  

## ダイアログ（ボイス対応会話システム）
デモの新規プレイ時のメイン画面の冒頭で、百物語などの説明をダイアログ（Dialogue）システムで行っています。  
サンプルでは行っていませんが、サンプルのメイン画面（HT_Level_CandlesSpace）のHT_BP_Actor_CandleManagerを選択し、［詳細］タブの［ダイアログ > DialogueDataTable］に「HT_DataTable_HowTo」を設定するとデモの説明を表示することができます（サンプルにボイスはありません）。  

ダイアログシステムの使い方のサンプルが蝋燭マネージャー（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_CandleManager.uasset）になっています。  
GetPlayerControllerノードからGetDialogue関数（WST_BPI_PlayerControllerブループリントインターフェース）を呼び、ReturnValueピンからShowDialogue関数（Lelool_BPI_Dialogueブループリントインターフェース）に表示したいダイアログのDataTableを引数として渡して呼びます。  

またGetDialogue関数からOnChangedイベントディスパッチャー（表示するDataTableの行が変わった時に呼ばれる）やOnClosedイベントディスパッチャー（ダイアログが閉じた時に呼ばれる）をバインドでき、会話中にイベントを起こしたり会話終了時にイベントを起こすことも可能です。  
このダイアログシステムは選択肢の表示には対応していませんが、OnClosedイベントディスパッチャーなどで特定のダイアログを閉じた際に選択肢UIを表示するなどで対応可能です。  

サンプルのダイアログの書式はWST_Struct_Dialogue構造体（/Content/WalkingSimTpl/Dialogue/WST_Struct_Dialogue.uasset）とデータテーブルになっており、HT_DataTable_HowToデータテーブル（/Content/HyakuTales/Dialogue/HT_DataTable_HowTo.uasset）を参考・複製して作ってください。  
話し手（Speaker）の国際化（多言語）対応にはWST_WBP_Dialogueウィジットブループリント（/Content/WalkingSimTpl/UI/Dialogue/WST_WBP_Dialogue.uasset）に話し手名のマッピングとローカリゼーションダッシュボードの作業が必要です。  

なおダイアログのデータべテーブルはWST_Struct_Dialogue構造体でなくても自作の構造体でも可能ですが、WST_WBP_Dialogueウィジットブループリントを自作構造体用に変更する必要があります。  

### ダイアログの自動再生
ShowDialogue関数（Lelool_BPI_Dialogueブループリントインターフェース）の［Auto］引数にチェックを入れると、自動再生となりプレイヤーキャラクターは動ける状態のままでセリフが表示されます。  

ただしセリフ中にトリガーを踏んだりインタラクションしたりしてイベントが発生すると不具合の原因になる恐れがあるため、自動再生する場合は注意しましょう（デフォルトではダイアログ表示中はインタラクト不可にしてはいます）。  
基本的には一言二言程度のセリフに向いています。例えば、建物や部屋に初めて入った時に「汚いなぁ」とか「臭いなぁ」とか、演出の物音を再生させた時に「どっかで物音がしたような？」のように聞き逃してしまったプレイヤーにもゲーム内の変化を少しでも伝わるようにするような使い方になるかと思います。  

### ダイアログの戻る機能
複数ページのテキストの時に表示した前ページに戻れるかどうかの設定は、WST_BP_DialogueComponentブループリント（/Content/WalkingSimTpl/Component/Dialogue/WST_BP_DialogueComponent.uasset）の［デフォルト > EnableBack］で切替可能です。  
誤操作で次のページに進んでしまって読み逃すこともあるので、特に理由が無ければ戻る機能は有効のままで良いかと思います。  

### ダイアログのタイプライター演出
テキストを表示する時に1文字ずつ表示（タイプライター演出）するか一度にまとめて表示するかの設定は、WST_BP_DialogueComponentブループリント（/Content/WalkingSimTpl/Component/Dialogue/WST_BP_DialogueComponent.uasset）の［Typewriter > EnableTypewriter］で切替可能です。  

なおタイプライター演出中にコントローラーのBボタンもしくはキーボードのスペースキーを押すと、タイプライター演出をスキップして残りのテキストがまとめて表示されます。  
このキー設定はLelool_IMC_Dialogue（/Content/Lelool/Input/Dialogue/Lelool_IMC_Dialogue.uasset）の「Lelool_IA_Dialogue_SkipTypewriter」で行っています。  

### ダイアログUIの設定
ダイアログで使用するUI（UserWidget）はWST_BP_DialogueComponentブループリント（/Content/WalkingSimTpl/Component/Dialogue/WST_BP_DialogueComponent.uasset）の［ウィジェット > UserWidgetClass］で設定できます。  

デフォルト設定のサンプルのWST_WBP_Dialogueウィジェット（/Content/WalkingSimTpl/UI/Dialogue/WST_WBP_Dialogue.uasset）を参考に、見た目を変えたり、ダイアログ用データテーブルの書式（構造体）の変更に対応させたり可能です。  
ダイアログUIを自作する場合はWST_WBP_Dialogueウィジェットを直接編集するか複製して編集するのが便利かと思います。  
新規で作成する場合はWST_WBP_Dialogue_Baseウィジェット（/Content/WalkingSimTpl/UI/Dialogue/WST_WBP_Dialogue_Base.uasset）かLelool_WBP_Dialogue_Baseウィジェット（/Content/Lelool/Component/Dialogue/Lelool_WBP_Dialogue_Base.uasset）の子クラスとして作成してください（タイプライター演出など色々な共通処理を実装済みのため）。  

### アイテムビューア
画面の中央に表示した3Dモデルを回転やズームで調べることができる機能です。  
テーブルの上のメモを読む時に使ったり、裏や底に謎解きのヒントなどを隠しておくといった使い方ができます。  

アイテムビューアに表示させたいActorブループリントにWST_BP_ItemViewerComponent_Actorブループリント（/Content/WalkingSimTpl/Component/ItemViewer/Actor/WST_BP_ItemViewerComponent_Actor.uasset）を追加し、表示する際にそのブループリントのShow関数を呼ぶだけです。  
アイテムビューアActorブループリントの雛型（/Content/HyakuTales/Blueprint/Actor/ItemViewer/HT_BP_Actor_ItemViewer_Base.uasset）やサンプル（/Content/HyakuTales/Blueprint/Actor/ItemViewer/HT_BP_Actor_ItemViewer_Sample.uasset）を用意しています。  

Actorブループリントに追加したWST_BP_ItemViewerComponent_Actorブループリントを選択した状態で、エディタ右側の［詳細］タブから表示の調整や名称の設定が可能です。  
* Offset: 表示時の位置・角度・大きさを調整できます。
* Name: アイテムビューアUIに表示するアイテム名
* Description: アイテムビューアUIに表示するアイテムの説明

## コントローラー振動
Unreal Engineには標準でコントローラー振動機能（ForceFeedback）がありますが、その処理を管理する共通システムを用意しています。  

標準機能で振動させている時にゲームを一時停止すると、一時停止を解除するまで振動しっぱなしになってしまう場合があります。これを解消するために、コントローラー振動処理を一括で管理し、一時停止時に振動機能も一時停止させることが可能になります。  
またコントローラー振動の無効化や相対的な強弱設定なども管理可能で、サンプルの環境設定から設定可能です。振動機能が苦手なプレイヤーもいますし、ムービーシーンなどでコントローラーをテーブルに置いていた場合に振動音が気になるなど、振動機能の無効化機能を求められるケースはあります。  
これらの点を特に気にしないのであればUE5標準のコントローラー振動機能を直接実行しても問題ありません。  

サンプルとして蝋燭（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_Candle_Base.uasset）の消灯時にわずかですがコントローラー振動を行っています（手で仰ぐ・息を吹きかけるアクションをイメージ）。  
GetPlayerControllerノードからGetForceFeedback関数（WST_BPI_PlayerControllerブループリントインターフェース）を呼び、そのReturnValueピンからPlayForceFeedbackノードにForceFeedbackComponentを渡して呼ぶだけです（標準のForcefeedBackノードの使い方と似ています）。  

ゲームを主にキーボード&マウスでプレイしていると実感がないかもしれませんが、例えばモンスターハンターの太刀であれば見切りの際のコントローラー振動が爽快感などに繋がりますし、ホラーゲームであればドアを叩かれる演出などの補強になるかと思います。  
ただゲーム開発初心者の内は開発の負担を少しでも減らすために、割り切ってコントローラー振動を実装しないという判断も有りかとは思います。特にPCゲームであればキーボード&マウスでプレイするプレイヤーは少なくなく、ゲーム体験への影響は限定的と考えることができます。  

UE5標準のコントローラー振動機能を直接実行する場合やコントローラー振動自体行わない場合は、環境設定のコントローラー振動の項目を非表示にすると良いでしょう（特にUE5標準機能を直接使う場合は振動機能の無効化が反映されないため）。  

## 通知
サンプルで蝋燭を消した際に残りの蝋燭の数を画面右上からスライドで表示する通知システムです。  
ゲーム進行上必要な情報やヒントを通知したり、インタラクトキーを連打しながらプレイするプレイヤーのためにアイテム入手時などに通知したりするのに使えます。  

蝋燭マネージャーActorBlueprint（/Content/HyakuTales/Blueprint/Actor/Candle/HT_BP_Actor_CandleManager.uasset）で火の点いた蝋燭の残数を通知するサンプルを実装しています。  
GetPlayerControllerノードからGetHUDノードを呼び、そこからGetNotice関数（WST_BPI_HUDブループリントインターフェース）を呼び、そのReturnValueピンからAddNoticeItemノード（Lelool_BPI_Noticeブループリントインターフェース）にメッセージ文字列や表示秒数などを渡すことで通知を表示できます。  

## 時計
ホラーゲームの演出用の小物としてアナログ時計のサンプルプログラムを用意しています（デジタル時計にも使えますが、アナログ時計のように各針の角度などの計算が不要なため独自に作成しても良いかと思います）。  

時間を指定することも、プレイヤーの端末のローカル時間に連動することも、高速回転・逆回転・高速逆回転・進まない故障演出（秒針の痙攣）などが簡単にできます。  
デモ用百物語カウンターではメインメニューやポーズメニューから時計の状態を変更できるオプションを用意しているので、どのような機能なのかお試しください。試すとわかるかと思いますが、高速回転演出を行うのであれば秒針が無い時計の方が良いと思いますし、逆回転や進まない故障演出（4時44分44秒）では秒針が無いとわかりにくいかなと思います。  

サンプルの時計はゲームに使用するにはチープすぎると思うので、時計のベース用ActorBlueprint（/Content/HyakuTales/Blueprint/Actor/Clock/HT_BP_Actor_Clock_Base.uasset）の子クラスを作って、時計の本体・短針・長針・秒針（必要なら）の3Dモデルを追加すると良いでしょう。  
時計の針をそれぞれ所定のSceneComponentに配置すると、自動的に時間に合わせて回転します（サンプルも参考にしてください）。
* HourHandScene（短針/時）
* MinuteHandScene（長針/分）
* SecondHandScene（秒針/秒）
使用する3Dモデルによって向きが異なるため、実際にエディタ上でゲームをプレイして確認しながら調整してください。  

時計の開始時刻は時計ActorBlueprintのTime変数で指定できます（4時44分44秒なら「+00000000.04:44:44.000000000」とします）。  
また秒針がある時計ではお好みでIsMinuteUnitHand変数にチェックを入れると良いと思います（長針が毎秒動くか00秒の時に動くかどうか）。  

時計の電源や故障の設定は、時計ActorBlueprintを開いてエディタ左側の［コンポーネント］タブの［ClockComponent］を選択し、右側に表示される［詳細］タブの［デフォルト > Setting］で行います。  
* Realtime（現在時刻を有効にするか）
* Power（時計を動かすかどうか）
* Reverse（逆回転するかどうか）
* Paralysis（進まない痙攣演出するかどうか）
* Speedy（高速回転するかどうか）

優先度の高い順から「Power」「Paralysis」「Reverse/Speedy」「Realtime」「時計ActorBlueprintのTime変数」となります。  

---

# 応用編

## 国際化（多言語対応）
Unreal Engine標準の[ローカリゼーションダッシュボート](https://dev.epicgames.com/documentation/ja-jp/unreal-engine/localization-tools-in-unreal-engine?application_version=5.4)を使ってゲーム内メニューの国際化に対応しています（エディタ上部の［ツール > ローカリゼーションダッシュボート］を左クリックして開けます）。  
ただしローカリゼーションダッシュボートは実験段階の機能のため、不具合が発生しやすかったり、Unreal Engineのアップデートで大幅な仕様変更が行われる可能性もあります。  

国際化対応が難しかったり負担が大きい場合は、割り切って国際化はあきらめても大きな問題はないでしょう。  
国際化対応を行わない場合は、メインメニューと環境設定にある言語設定の項目を非表示にしてください（削除しても良いですが、環境設定だと言語設定を参照しており手間が増えます）。  

なおエディタ上で言語の切替の動作確認を行う場合は「スタンドアローンゲーム」としてプレイする必要があるようです（これ以外のモードでテストしてしまうとエディタの表示言語が変更されてしまう恐れがあります）。  
またパッケージ化した場合に国際化が正常に動作しないこともあるため、パッケージ化後にも正常に動作するかテストした方が良いでしょう。  

## 操作方法のキー設定
キャラクターの操作やメニュー表示などのキーはそれぞれ設定ファイルが分かれています（詳しくは[Unreal EngineのEnhanced Input](https://dev.epicgames.com/documentation/ja-jp/unreal-engine/enhanced-input-in-unreal-engine)などを参照してください）。  

* キャラクター: Lelool_IMC_Character（/Content/Lelool/Input/Character/Lelool_IMC_Character.uasset）
* ダイアログ（会話）: Lelool_IMC_Dialogue（/Content/Lelool/Input/Dialogue/Lelool_IMC_Dialogue.uasset）
* インタラクト（アイテム取得やドアの開閉などのアクションメニュー）: Lelool_IMC_Interaction（/Content/Lelool/Input/Interaction/Lelool_IMC_Interaction.uasset）
* アイテムビューア: Lelool_IMC_ItemViewer（\Content\Lelool\Input\ItemViewer\Lelool_IMC_ItemViewer.uasset）
* 一時停止: Lelool_IMC_Pause（/Content/Lelool/Input/Pause/Lelool_IMC_Pause.uasset）

キーは変更・追加・削除可能で、特定の操作を無効化したい場合はキーを［None］に設定します。  
テンプレートではサンプルとしてメインメニューとポーズメニューに操作方法のボタンを表示しているため、操作方法を変更する様な場合は操作方法ボタンを非表示にしたり操作方法UIを編集してください。  

「ダッシュ」「しゃがみ」「ズーム」に関しては、サンプルとして実装しているだけでゲーム内容によっては無効化しても良いと思います（また使用するキャラクターアセットなどによってはしゃがみなどに対応していない場合もあります）。  
プレイヤーによっては操作方法からメタ読みして攻略を考えることもありゲーム体験を損なわせてしまうことがあるかもしれません。  
「ダッシュ」に関しては移動の遅さのストレスを軽減にも繋がるため、ホラーゲームなどダッシュで雰囲気や恐怖感を損なうなどの理由がなければ有効のままでも良いかと思われます。  

### 操作方法画面のカスタマイズ
操作方法画面はWST_WBP_Control_Contentウィジット（/Content/WalkingSimTpl/UI/Control/WST_WBP_Control_Content.uasset）になります。  

無効にする操作がある場合は、その行の各項目を削除するか、［Visibility］を［Collapsed］に設定し非表示にします。  
必要に応じて他の操作の表示位置を調整したり、GridPanelのフィルルールのFowFill配列を変更してください。  

## 環境設定画面のカスタマイズ
基本的に不要な設定項目は非表示・削除でカスタマイズしてください。  
ただし各設定項目は環境設定ウィジェット（/Content/WalkingSimTpl/UI/Setting/WST_WBP_Setting_Content.uasset）のグラフ内で参照しているため、非表示の方が手間は少ないです（後から表示することになった場合も再表示するだけで楽です）。  

非表示する場合は、非表示したい要素を選択し、エディタ右側の［詳細］タブの［動作 > Visibility］を「Collapsed」に設定します。表示に戻す場合は［Visibility］を元に戻すだけです（大半の要素のデフォルトは「Not Hit-Testable (Self Only)」かと思います）。  
編集を行った後は、エディタ左上の［コンパイル］ボタンを左クリックしてください。  

### 対応解像度（画面モード/解像度）
環境設定で選択できる解像度を変更する場合はWST_BP_Settings_WindowMode_Modelブループリント（/Content/WalkingSimTpl/UI/Setting/WST_BP_Settings_WindowMode_Model.uasset）を開き、エディタ上部の［クラスのデフォルト］をクリックし、エディタ右側の［詳細］タブの［Resolutions］の解像度リストを編集します。編集後はエディタ左上の［コンパイル］ボタンを左クリックします。  

サンプルでは昨今の縦型画面のゲーム実況に対応できるように、縦型解像度・スクエア解像度も設定しています。  
ただしこれらの解像度では左右の表示が欠けるため、作るゲームにって不都合がある場合は削除してください。サンプルでも縦型解像度の時、メインメニューの百物語オプションが中央のボタンに若干被ってしまっています。  

### 音量変更時のプレビュー再生
音量確認用に再生するサウンドソースは、音量設定の要素を選択し、エディタ右側の［詳細］タブの［デフォルト > PreviewSound］で設定します。  

ここで設定するサウンドソースにはサウンドクラスを設定しないでください（[サウンドの種類の設定方法](#サウンドの種類の設定方法)参照）。  
サウンドクラスを設定してしまうとこの環境設定で設定した値がプレビュー時にも影響してしまい、例えば「0」にした後に変更してもサウンドクラスが「0」のため音が鳴らなくなります。  

## ゲームの画質について
初期設定ではUnreal Engineの高画質なグラフィックが有効になっており、処理負荷が高く、低スペックなプレイ環境では快適性が犠牲になってしまいます。  
特に「Lumen」の影響が大きいと思われます。  

LumenはUnreal Engine 5の新機能で、完全に動的なグローバルイルミネーションおよび反射のシステムです。  
これにより自動に光と影がリアルに近い表現となり、初心者でもそれなりに見栄えの良いグラフィックのゲームを作れるようになります。  

Lumenは次世代コンソールやハイエイド環境向けに設計されており、PlyaStation 5やXbox Series Xやそれに匹敵する性能のゲーミングPC向けになっています。  
Unreal Engine 5.5ではLumenで60FPSを出すことは可能になってますが、逆にそれだけ負荷の大きい機能でもあります。  

Lumenを無効化すれば大幅に負荷を軽減できるのですが、グラフィックをかなり犠牲することになります。  
ポストプロセスなどで対応可能のようですが、それには知識・スキルが必要になるようです。  

なおこのゲームテンプレートでは環境設定で5段階の画質から選べるようにし、各種パラメーターを調整して画質とパフォーマンスのバランスを図っています。  

そもそもゲームの最適化は知識・スキルが求められるものですし、特に個人開発では動作確認できる端末が開発用パソコンの1台だけというのも珍しくないので限界もあります。  
画質を諦めてパラメーターを全体的に低めにするか、要求スペックを最低動作環境でも高めに設定するのが現実的かもしれません。  

### 画質のカスタマイズ
特に画質にこだわらない、もしくは画質を妥協してでも要求スペックを下げたい場合、大きく2つの対応方法があります。  

* プロジェクト設定
* ゲーム内画質設定（中・上級者向け）

#### プロジェクト設定
プロジェクト設定はエディタ上部の［編集 > プロジェクト設定］を左クリックで開きます。  
なおプロジェクト設定から色々な変更を行えますが、影響範囲が大きいものもあるためよくわからないで変更しないように注意してください。  

簡単な画質（負荷軽減）に関係する項目を紹介します。  

##### ターゲットハードウェア
プロジェクト設定の［プロジェクト > ターゲットハードウェア］を開きます。  
デフォルトでは「Desktop」「Maximum」と最高設定になっているので必要に応じて下げてみてください（変更後はプロジェクト設定に指示に従ってエディタの再起動が必要になると思います）。  

![プロジェクト設定のターゲットハードウェアの設定個所の図解](https://github.com/user-attachments/assets/993b3a04-3303-4c95-93e2-9c759caa16d0)

##### アンチエイリアス手法
アンチエイリアスは曲線などをボカして綺麗に見せる処理です。  
当然、品質重視にすると負荷は高くなります。  

プロジェクト設定の［エンジン > Rendering］を開き、［Default Settings > アンチエイリアス手法］から設定可能です。  

![アンチエイリアス手法の設定個所の図解](https://github.com/user-attachments/assets/321bdaef-f181-4bf5-ad36-30999d288fa7)

初期設定の「TSR」は負荷が高く「TAA」「FXAA」「None（アンチエイリアス無し）」の順に負荷が下がります（画質も下がる）。  
※「MSAA」はよくわかりませんでした。

#### ゲーム内画質設定（中・上級者向け）
ゲーム内の環境設定で画質を5段階から選択できるようになっていますが、そこで行われる画質設定はWST_BP_GraphicSettingComponentアクターコンポーネント（/Content/WalkingSimTpl/Component/GraphicSetting/WST_BP_GraphicSettingComponent.uasset）で切り替えています。  

このファイルをダブルクリックして開き、エディタの上あたりに表示される［クラスのデフォルト］ボタンを左クリックします。  
そしてクラスのデフォルトの［品質 > Qualities］に配列として5段階の画質設定を設定しています。  

上から順に「最低画質」「低画質」「標準画質」「高画質」「最高画質」となっています。  
ただしこの順番は［品質 > QualityMapping］変数のIndex値と紐づいており、この値を変更すると画質設定にも影響します（変更非推奨）。  

* 1 = 最低画質
* 3 = 低画質
* 5 = 標準画質
* 7 = 高画質
* 9 = 最高画質

そして画質別にUnreal EngineのGameUserSettingsで指定できる画質の値をプリセットとして設定しています。  
なおこれらの値を下げると顕著に画面表示に影響することがあり、中にはゲームプレイに影響しかねないので、画質を下げる変更を行う時はテストプレイで変化を確認するようにしてください。特に明るい所や暗い所、一部のエフェクトでのみ変化が顕著になることがあるので、影響がありそうな箇所は特に注意してください。 

比較的簡単に変更できる項目は「ResolutionScaleNormalized」です。  
数値を下げると動画の解像度を下げた時のように、単純に画面が荒くなります。  

「ShadowQuality」（影）を0（無効化）にすることで負荷の大幅な軽減が期待出来はしますが、影がなくなるだけで顕著に見栄えが悪くなる可能性が高いので注意してください。  
数値を下げると、対象物に近づいた時に遅れて影が描写するため不自然になる恐れがあります。  

また画質ごとに「PostProcessVolume」を設定でき、ここで「Lumen」の無効化ができます。  

##### 初期画質の変更（中・上級者向け）
画質の初期値はWST_BP_SaveGame_Settingsブループリント（/Content/WalkingSimTpl/Blueprint/SaveGame/WST_BP_SaveGame_Settings.uasset）で設定しています。  

［表示 > ImageQuality］変数の値が、WST_BP_GraphicSettingComponentのQualityMapping変数と紐づいています。  
デフォルトでは初期値が「3」（低画質）になっていると思われます（低スペック環境でゲームを起動してしまった場合に重すぎて環境設定画面を開くのが困難になる恐れを考慮し、保険として初期値を低画質にしています）。  

例えばこの値を「5」に変更すると初期画質が「標準画質」になります。  
この値は環境設定で変更されるセーブ・ロード対象の値であり、プレイヤーが変更しておりセーブ・ロードが完了していると、次回以降はプレイヤーが設定した画質で描画されます。  

## サウンドの種類の設定方法
ゲーム内の環境設定からBGM/効果音/ボイスの音量を個別に変更できるようになっています。  
プロジェクトにインポートしたサウンドファイルに種類に応じたサウンドクラスを設定することで、これらの音量設定が反映されるようになります。  

サウンドクラスはインポートしたサウンドファイル（サウンドウェーブ）を開き、［詳細］タブの［サウンド > Class］から変更可能です。  
サウンドの種類によって次のいずれかのサウンドクラスを設定してください。  

* BGM = WST_SoundClass_BGM
* 効果音 = WST_SoundClass_SoundEffect
* ボイス = WST_SoundClass_Voice

![サウンドクラスの設定方法の図解](https://github.com/user-attachments/assets/d576307f-dabb-4d77-be26-a3030926c0ef)

## フォント
Unreal Engine標準のフォントは日本語対応にはなっていますが、日本人からすると不自然に感じるものが一部あります。  
フォントをゲームに組み込むことも可能ですので、余力があれば自作ゲームに組み込んでも良いかもしれません。  

## インタラクティブActorブループリント作成例  
ヒューズや鍵や懐中電灯などのインタラクト可能なActorブループリントの作成方法を解説します。  
[インタラクション](#インタラクション)可能なActorブループリントをベースに、そのアクションに応じてセーブ・通知・ダイアログ・非表示処理を行います。  

サンプル用アイテムビューアActorBueprint（\Content\HyakuTales\Blueprint\Actor\ItemViewer\HT_BP_Actor_ItemViewer_Sample.uasset）が参考になるかと思います。  
インタラクションから呼ばれたCallInteractionActorActionイベントのGameplayTag引数をチェックし、アイテムビューアとして表示するかどうかの処理を行っています。  
![サンプル用アイテムビューアActorBueprintのイベントグラフ](https://github.com/user-attachments/assets/1ccaed5d-7104-4d17-a65c-b6aa7ff094f2)

ようはアイテムビューアの表示処理を、ダイアログ・通知・セーブ・非表示処理などに置き替えたり追加したりして作ります（ただしアイテムビューアとダイアログの同時実行は避けてください）。  

参考としてActorブループリントでのセーブ・ダイアログ・通知・非表示の実装例を紹介します（この実装例のセーブ処理では百物語カウンターで消した蝋燭の数を管理している「Number変数」を流用しています）。  
![回収系アイテムの主な処理の実装例](https://github.com/user-attachments/assets/34020051-8b3b-4a2e-9543-af894c3a3479)

これらのイベントをそのActorブループリントやインタラクションアクションに応じた処理を実行するように実装してください。  

## プレイヤーキャラクターのカスタマイズ
サンプルのプレイヤーキャラクターはWST_BP_Characterブループリント（\Content\WalkingSimTpl\Blueprint\Character\WST_BP_Character.uasset）となっています。  
体を持たない一人称視点のカメラがあるだけのシンプルなキャラクターです。  

このプレイヤーキャラクターはGameModeのWST_BP_GameMode_Character（\Content\WalkingSimTpl\Blueprint\GameMode\WST_BP_GameMode_Character.uasset）の「Default Pawn Class」で指定しています（サンプルでは「WST_BP_Characterブループリント」が設定されています）。  

プレイヤーキャラクターをカスタマイズする場合はサンプルのWST_BP_Characterブループリントを編集するか、別のプレイヤーキャラクターのブループリントをGameModeで指定することになります。  

### ファーストパーソンテンプレートを使用する  
Unreal Engine標準で用意されている一人称視点のファーストパーソンテンプレート（FPS視点・主観視点）を使用する方法を説明します。  
標準のキャラクターをベースにすることで、足音や武器の実装、キャラクターメッシュ（MetaHumanやアセットストアで入手したキャラクター、VRoid Studioで作成したキャラクターなど）の変更方法の解説動画などを参考にカスタマイズしやすくなるかと思います。  

なおUnreal Engine 5.6からこのファーストパーソンテンプレートがアップデートされたため、このゲームテンプレートはこれに合わせて対応バージョンをUnreal Engine 5.6に変更しています。  
そのため解説動画などが旧ファーストパーソンテンプレートをベースにしている場合は注意してください。旧版ではキャラクターの体は腕のみになっていたかと思います（新版で全身あります）。  

このファーストパーソンテンプレートを使用するためには、事前にEpic Games Launcherで使用しているUnreal Engineバージョンのオプションから「テンプレートとおすすめパック」（もしくは「スターター コンテンツ」）をインストールしておく必要があるかと思います。  
![EpicGamesLauncherからスターターコンテンツをインストールする手順の図解](https://github.com/user-attachments/assets/ebf22c1f-7636-4fb1-956f-afb5f5220e58)

エディタ左下の［コンテンツドロワー］ボタンを左クリックしてコンテンツブラウザを開き、コンテンツブラウザ左上の［追加］ボタンを左クリックしてメニューを開き、［機能またはコンテンツパックを追加…］を左クリックします。  
「プロジェクトをコンテンツに追加」ウィンドウが開くので、「ブループリント」の「ファーストパーソン」を左クリックして選択し、そのウィンドウ右下の［プロジェクトに追加］ボタンを左クリックします。  
追加が成功していれば、コンテンツフォルダ直下に「FirstPerson」フォルダが追加されます。  
![ファーストパーソンテンプレートを追加する手順の図解](https://github.com/user-attachments/assets/6274e7e1-5420-460b-b3d0-f49e5b72b4a5)

#### ファーストパーソンキャラクターブループリントを編集する  
ファーストパーソンテンプレートのキャラクターブループリント（\Content\FirstPerson\Blueprints\BP_FirstPersonCharacter.uasset）には入力・動作関連の処理が実装されています（Unreal Engine 5.6の場合で、バージョンによって異なる可能性があります）。  

この解説では、ファーストパーソンテンプレートの入力・動作関連の処理は無効化（削除）し、このゲームテンプレートで用意した入力・動作関連の処理を使うように変更します。  
* BP_FirstPersonCharacterブループリントを開く。  
* ［イベントグラフ］タブ内のノードをすべて選択し削除する。
* ［コンパイル］ボタンを左クリックしてコンパイルする。
* 保存する。
![ファーストパーソンテンプレートから入力・操作関連の処理を削除する手順の図解](https://github.com/user-attachments/assets/0b101d89-2d2b-499a-b338-fc3db5075790)

またカメラの壁貫通や足元を見た時に体の内部が見えてしまうような時は、キャラクターメッシュやカメラの位置を調整してみてください。  
デフォルトの位置が悪いのか、僅かに頭部のメッシュが画面にノイズとして映ることがあるようです。  

なおファーストパーソンテンプレート以外のアセットのキャラクターなどを使う場合で、そのアセットの入力・動作の処理をそのまま使うことも可能です。  
特に武器を使用するようなサンプルにない処理が実装されている場合はその方が便利かと思います。  

#### キャラクターブループリントにキャラクター操作用ActorComponentを追加する  
キャラクターブループリントにキャラクター操作用ActorComponent（\Content\WalkingSimTpl\Component\CharacterControl\WST_BP_CharacterControlComponent.uasset）を追加することで、キャラクターの入力・動作関連の処理を実装できます。  

BP_FirstPersonCharacterブループリントの［コンポーネント］タブの［追加］ボタンから「WST_BP_CharacterControlComponent」を追加してください。  
入力設定のEnhancedInputを変更する場合は、［コンポーネント］タブ内のWST_BP_CharacterControlComponentを選択し、［詳細］タブの［EnhancedInputMappingContexts］のInputMappingContextを編集するか、設定するInputMappingContextを変更します。  
![キャラクターブループリントにキャラクター操作用ActorComponentを追加する手順の図解](https://github.com/user-attachments/assets/a234b21e-3b08-4a5d-aefe-0b85937b43ed)

編集が終わったらコンパイル・保存します。  

なおファーストパーソンテンプレートには「しゃがみ」機能は実装されていないらしく、このキャラクター操作用ActorComponentを追加してもしゃがむことはできません。  
しゃがみ機能が実装されたキャラクターアセットなどを使用するか、自分でしゃがみ機能を実装する必要があります（サンプルのキャラクターは体がないためしゃがみアニメーションが不要で、カメラの高さの変更でしゃがみを実現しています）。  

特にしゃがみが必要ないゲームであれば、そのまましゃがみ機能なしでも良いかと思います。  
プレイヤーによってはしゃがみ機能があることでメタ読みしたり、攻略に必要ないのにしゃがみ機能が実装されていることに不満を感じたり（無駄なことをさせられたと感じる？）することもあるようです。  

もししゃがみ機能などを実装しない場合は、それにあわせて[操作方法画面を編集](#操作方法画面のカスタマイズ)します。  

#### キャラクターブループリントにズーム用ActorComponentを追加する  
キャラクターブループリントにズーム用ActorComponent（\Content\WalkingSimTpl\Component\Zoom\WST_BP_ZoomComponent.uasset）を追加することで、キャラクターにズーム機能を実装できます。  

BP_FirstPersonCharacterブループリントの［コンポーネント］タブの［追加］ボタンから「WST_BP_ZoomComponent」を追加してください。  
![キャラクターブループリントにズーム用ActorComponentを追加する手順の図解](https://github.com/user-attachments/assets/18476ae3-d5cc-450c-98f5-7b79d135e08b)

編集が終わったらコンパイル・保存します。  

なおこのズーム機能は、キャラクターブループリントのカメラコンポーネントのFOVを調整することで実現しています。  
そのためカメラコンポーネントがないなど、キャラクターブループリントによっては動作しない場合があります。  

ズーム機能が動作しない場合やズーム機能自体を実装しない場合は、それにあわせて[操作方法画面を編集](#操作方法画面のカスタマイズ)してください。  

参考として[Advanced Locomotion System V4](https://www.fab.com/ja/listings/ef9651a4-fb55-4866-a2d9-1b38b028f9c7)はキャラクターブループリントにカメラコンポーネントがないようで、このズーム機能は動作しませんでした。  
カメラはPlayerControllerブループリントで設定する「ALS_PlayerCameraManager」で実装しているようで、このALS_PlayerCameraManagerを使わずにキャラクターブループリントにカメラコンポーネントを追加すればズーム機能を動作させることが可能になるかとは思います。もしくはキャラクターブループリントの［コンポーネント］タブのWST_BP_ZoomComponentを選択し、［詳細］タブの［イベント］から「OnFOVChanged」を追加し、イベントノードに追加されたOnFOVChangedイベントのNewFOV引数をキャラクターブループリントのFirstPorsonFOV変数にセットすることでも可能になるかと思います。  
ただしアイテムビューアを使用する際などにカメラの位置の取得方法の関係上、カメラ位置が不自然になるといった注意点があります（アイテムビューア表示時はキャラクターのメッシュを非表示にすることで対処可能ではあるかもしれません）。  

## 別プロジェクトに移行する
このゲームテンプレートを別のUnrealプロジェクトファイルに移行し、移行先で実行する手順を説明します。  

まずは移行先のプロジェクトで次のプラグインが有効になっていない場合は有効にします（設定変更後はエディタの再起動が必要）。  
* Common UI Plugin  

次のディレクトリが移行に必要となります。  
* HyakuTales: 百物語カウンターサンプル（不要なら移行不要です）
* Lelool: 共通システム
* WalkingSimTpl: ウォーキングシミュレーター

ファイルの移行が成功したら［プロジェクト設定 > プロジェクト > マップ&モード］の設定を必要に応じて行ってください（この設定は移行先プロジェクトによって異なるためご自身で理解・判断が必要です）。  

#### Common UI Pluginの設定
このゲームテンプレートのUI（ウィジェット）を使用する場合は、ゲームパッド・キーボード＆マウスのボタン・キー表記やそのショートカットキー操作に対応するための設定が必要です。  
移行先のプロジェクトで既に設定されている場合は調整が必要になるかもしれません。  

［プロジェクト設定 > ゲーム > Common Input Settings］を開きます。  
* ［インプットデータ］にWST_CommonUIInputData（\Content\WalkingSimTpl\UI\WST_CommonUIInputData.uasset）を設定します。
* ［プラットフォーム入力 > Windows > Default］の［デフォルトの入力タイプ］を［Gamepad］に設定し、［デフォルトのゲームパッド名］に［Generic］を設定、コントローラーデータには次の2つを設定します。
  * Lelool_CommonUI_CommonInputBaseControllerData_Gamepad（\Content\Lelool\UI\Lelool_CommonUI_CommonInputBaseControllerData_Gamepad.uasset）
  * Lelool_CommonUI_CommonInputBaseControllerData_MouseAndKeyboard（\Content\Lelool\UI\Lelool_CommonUI_CommonInputBaseControllerData_MouseAndKeyboard.uasset）

［プロジェクト設定 > エンジン > 基本設定 > ゲームのビューポートクライアントクラス］に［CommonGameViewportClient］を設定します（設定を変更した場合はエディタの再起動を求められると思うので、その場合は指示に従って再起動してください）。

---

# よくある質問
このゲームテンプレートはライセンスが非常に緩いMITライセンスで公開しており、ライセンスを守ってライセンス表記さえすれば非常に自由度が高いです（デフォルトでゲーム内にクレジット・ライセンス表記する機能を備えているため、カスタマイズして非表示・無効化・削除していなければこのゲームテンプレートのライセンス表記は行えているはずです）。  

もちろん、他に併用するライブラリなどがある場合はそれらのライセンスの確認は必要です。  

## サンプルゲームをゲーム実況しても良いですか？
問題ありません。  

## このゲームテンプレートで作ったゲームを有料で販売しても良いですか？
問題ありません。  

## このゲームテンプレートで作ったゲームのソースコードは非公開でも良いですか？
問題ありません。  

## このゲームテンプレートの有料教材を作っても良いですか？
問題ありません。  

## このゲームテンプレートを有料の勉強会の教材に使っても良いですか？
問題ありません。  

## このゲームテンプレートで百物語カウンターやウォーキングシミュレーターゲーム以外を作っても良いですか？
問題ありません。  

## このゲームテンプレートの一部を別のゲームに流用しても良いですか？
問題ありません。  

## このゲームテンプレートで有償の開発代行・受注開発を行っても良いですか？
問題ありません。  

## エディタのレイアウトが変になってしまったのですが？
エディタ上部の［ウィンドウ］から［レイアウトをロード > デフォルトのエディタレイアウト］を左クリックすれば、エディタのレイアウトが初期状態に戻ります。  

![デフォルトのエディタレイアウトに戻すための項目の位置の図解](https://github.com/user-attachments/assets/d6cea8ce-18cb-4067-8066-1fbeeb3c8cec)
