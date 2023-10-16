# Firestoreとは?
Firebaseのデータベースサービスの一つで、NoSQLのドキュメント指向データベースです。
ドキュメント指向データベースとは、データをドキュメントと呼ばれる単位で管理するデータベースのことです。
ドキュメントはJSON形式でデータを格納することができます

## ドキュメントとコレクション
Firestoreは、ドキュメントとコレクションという構造体を使ってデータを管理します。

コレクションは複数のドキュメントをまとめて格納できます。
コレクションに対してクエリを実行することで、コレクション内のドキュメントを取得したりソートすることができます。

[公式のデータ型について](https://firebase.google.com/docs/firestore/manage-data/data-types)

ドキュメントは、１つのデータのオブジェクトを表、複数の`key-value`ペアをフィールドに格納します。

データ型の種類は以下の通りです。
| データ型 | 説明 |
| --- | --- |
| string | 文字列 |
| number | 数値 |
| boolean | 真偽値 |
| array | 配列 |
| map |  key-valueペア |
| null | null値 |
| timestamp | 日付 |
| geoPoint | 緯度経度 |
| reference | 参照 |

ドキュメントはJSONのような構造体のデータオブジェクトとして表現されます。
```json
{
  "name": "John",
  "age": 30,
  "hobbies": ["reading", "cooking"],
  "address": {
    "prefecture": "Tokyo",
    "city": "Shinjuku"
  }
}
```

## Firestoreのスクリーンショット
こんな感じでデータ型を定義します。

<img src="image/../1.png" alt="1">
<img src="image/../2.png" alt="2">
<img src="image/../3.png" alt="3">

**コレクション**
<img src="image/../4.png" alt="4">

**サブコレクション**
<img src="image/../5.png" alt="5">