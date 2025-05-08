### AutoMLテスト用競艇実績データ

このデータは、競艇の公式サイト (https://www.boatrace.jp/) で公開されている実績データを、2024年4月1日から2025年4月31日分をテスト用としてスクレイピングして取得したものです。<br>
選手が欠場、失格となったレースなど一部のデータには欠損の可能性がありますがご了承ください。<br>
データの前処理は最小限にとどめ、基本的には取得したままの形式で使用しています。<br>

本来であれば、競艇において重要な要素である気象情報や水面状況など、当日に取得可能なデータを特徴量として加えることが望ましいと考えられますが、今回は運用の現実性を重視し、レース前日の夜時点で取得可能な情報のみを使用しています。

#### トレーニングデータ (boatrace_training.csv)
2024年4月1日から2025年3月31日までの1年分の約5.5万件のレース情報と実績を記録したCSVファイルです

#### 予測対象データ  (boatrace_predict.csv)
本番想定の予測対象データとして2025年4月1日から2025年4月30日までの1ヶ月分の約4200件のレース情報と実績を記録したCSVファイルです。

### データフォーマット

| col_name            | data_type | comment |
|---------------------|-----------|---------|
| RACEDATE            | date      | レース開催日 |
| PLACE               | string    | 開催場（例：平和島、蒲郡など） |
| RACE                | int       | レース番号（1R〜12R） |
| AGE1                | int       | 1号艇選手の年齢 |
| AGE2                | int       | 2号艇選手の年齢 |
| AGE3                | int       | 3号艇選手の年齢 |
| AGE4                | int       | 4号艇選手の年齢 |
| AGE5                | int       | 5号艇選手の年齢 |
| AGE6                | int       | 6号艇選手の年齢 |
| WEIGHT1             | double    | 1号艇選手の体重（kg） |
| WEIGHT2             | double    | 2号艇選手の体重 |
| WEIGHT3             | double    | 3号艇選手の体重 |
| WEIGHT4             | double    | 4号艇選手の体重 |
| WEIGHT5             | double    | 5号艇選手の体重 |
| WEIGHT6             | double    | 6号艇選手の体重 |
| ST_AVG1             | double    | 1号艇選手の平均スタートタイミング（秒） |
| ST_AVG2             | double    | 2号艇選手の平均スタートタイミング |
| ST_AVG3             | double    | 3号艇選手の平均スタートタイミング |
| ST_AVG4             | double    | 4号艇選手の平均スタートタイミング |
| ST_AVG5             | double    | 5号艇選手の平均スタートタイミング |
| ST_AVG6             | double    | 6号艇選手の平均スタートタイミング |
| CLASS1              | int       | 1号艇選手の級別（A1=4, A2=3, B1=2, B2=1） |
| CLASS2              | int       | 2号艇選手の級別 |
| CLASS3              | int       | 3号艇選手の級別 |
| CLASS4              | int       | 4号艇選手の級別 |
| CLASS5              | int       | 5号艇選手の級別 |
| CLASS6              | int       | 6号艇選手の級別 |
| L1                  | int       | 1号艇のスタート後れ回数 |
| L2                  | int       | 2号艇のスタート後れ回数 |
| L3                  | int       | 3号艇のスタート後れ回数 |
| L4                  | int       | 4号艇のスタート後れ回数 |
| L5                  | int       | 5号艇のスタート後れ回数 |
| L6                  | int       | 6号艇のスタート後れ回数 |
| F1                  | int       | 1号艇のフライング回数 |
| F2                  | int       | 2号艇のフライング回数 |
| F3                  | int       | 3号艇のフライング回数 |
| F4                  | int       | 4号艇のフライング回数 |
| F5                  | int       | 5号艇のフライング回数 |
| F6                  | int       | 6号艇のフライング回数 |
| WIN1RATE1           | double    | 1号艇選手の1着率 (全国）|
| WIN1RATE2           | double    | 2号艇選手の1着率 (全国）|
| WIN1RATE3           | double    | 3号艇選手の1着率 (全国）|
| WIN1RATE4           | double    | 4号艇選手の1着率 (全国）|
| WIN1RATE5           | double    | 5号艇選手の1着率 (全国）|
| WIN1RATE6           | double    | 6号艇選手の1着率 (全国）|
| WIN2RATE1           | double    | 1号艇選手の2連対率（全国)|
| WIN2RATE2           | double    | 2号艇選手の2連対率（全国)|
| WIN2RATE3           | double    | 3号艇選手の2連対率（全国)|
| WIN2RATE4           | double    | 4号艇選手の2連対率（全国)|
| WIN2RATE5           | double    | 5号艇選手の2連対率（全国)|
| WIN2RATE6           | double    | 6号艇選手の2連対率（全国)|
| LOCALWIN1RATE1        | double    | 1号艇選手の1着率（当地） |
| LOCALWIN1RATE2        | double    | 2号艇選手の1着率（当地） |
| LOCALWIN1RATE3        | double    | 3号艇選手の1着率（当地） |
| LOCALWIN1RATE4        | double    | 4号艇選手の1着率（当地） |
| LOCALWIN1RATE5        | double    | 5号艇選手の1着率（当地） |
| LOCALWIN1RATE6        | double    | 6号艇選手の1着率（当地） |
| LOCALWIN2RATE1        | double    | 1号艇選手の2連対率（当地） |
| LOCALWIN2RATE2        | double    | 2号艇選手の2連対率（当地） |
| LOCALWIN2RATE3        | double    | 3号艇選手の2連対率（当地） |
| LOCALWIN2RATE4        | double    | 4号艇選手の2連対率（当地） |
| LOCALWIN2RATE5        | double    | 5号艇選手の2連対率（当地） |
| LOCALWIN2RATE6        | double    | 6号艇選手の2連対率（当地） |
| MOTORWIN2RATE1        | double    | 1号機モーターの2連対率 |
| MOTORWIN2RATE2        | double    | 2号機モーターの2連対率 |
| MOTORWIN2RATE3        | double    | 3号機モーターの2連対率 |
| MOTORWIN2RATE4        | double    | 4号機モーターの2連対率 |
| MOTORWIN2RATE5        | double    | 5号機モーターの2連対率 |
| MOTORWIN2RATE6        | double    | 6号機モーターの2連対率 |
| MOTORWIN3RATE1        | double    | 1号機モーターの3連対率 |
| MOTORWIN3RATE2        | double    | 2号機モーターの3連対率 |
| MOTORWIN3RATE3        | double    | 3号機モーターの3連対率 |
| MOTORWIN3RATE4        | double    | 4号機モーターの3連対率 |
| MOTORWIN3RATE5        | double    | 5号機モーターの3連対率 |
| MOTORWIN3RATE6        | double    | 6号機モーターの3連対率 |
| BOATWIN2RATE1         | double    | 1号艇ボートの2連対率 |
| BOATWIN2RATE2         | double    | 2号艇ボートの2連対率 |
| BOATWIN2RATE3         | double    | 3号艇ボートの2連対率 |
| BOATWIN2RATE4         | double    | 4号艇ボートの2連対率 |
| BOATWIN2RATE5         | double    | 5号艇ボートの2連対率 |
| BOATWIN2RATE6         | double    | 6号艇ボートの2連対率 |
| BOATWIN3RATE1         | double    | 1号艇ボートの3連対率 |
| BOATWIN3RATE2         | double    | 2号艇ボートの3連対率 |
| BOATWIN3RATE3         | double    | 3号艇ボートの3連対率 |
| BOATWIN3RATE4         | double    | 4号艇ボートの3連対率 |
| BOATWIN3RATE5         | double    | 5号艇ボートの3連対率 |
| BOATWIN3RATE6         | double    | 6号艇ボートの3連対率 |
| TAN                   | string    | 単勝的中艇番（例："1"） |
| TANK                  | double    | 単勝払戻金（円） |
| RENTAN2               | string    | 2連単的中艇番（例："1>2"） |
| RENTAN2K              | double    | 2連単払戻金（円） |
| RENTAN3               | string    | 3連単的中艇番（例："1>2>3"） |
| RENTAN3K              | double    | 3連単払戻金（円） |
| split                 | string    | データ分割用フラグ（train/valid/test）※トレーニングデータのみ |
