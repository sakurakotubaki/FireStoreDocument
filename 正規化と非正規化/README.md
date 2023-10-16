# 正規化と非正規化
- 正規化: データベース設計の手法の一つで、データの重複を排除することでデータの整合性を保つことができる
- 非正規化: 正規化されたデータベース設計を、あえて正規化されていない状態に戻すこと

## 正規化
RDBでは複数のテーブルを作成して、データを保存します。１つのテーブルにデータを保存すると冗長なデータが紛れ込む場合があるので、データを分割して保存することでデータの整合性を保つことができます。データの冗長性がなくなるように適切にテーブルを分割することを正規化と呼びます。

## 非正規化
NoSQLは、RDBが重視した生合成の担保よりも、スケーラビリティを優先しているため、データの冗長性を許容しています。データの冗長性を許容することで、データの読み込みを高速化することができます。データの読み込みを高速化するために、データの冗長性を許容することを非正規化と呼びます。

## 最近読んだ本の解説の場合
Firestoreにおける正規化とは、単に「１つのデータを1箇所にしか保存しないこと」と解説。
非正規化とは、「１つのデータを異なる複数の場所にコピーすること」とされていた。

## データの参照
保存した特定のデータを読み込むなら、Reference型を使う。
```dart
final DocumentReference documentReference = Firestore.instance.collection('books').document('abc123');
```

## データの保存
保存するデータをMap型で作成し、setDataメソッドを使う。
```dart
final Map<String, dynamic> data = <String, dynamic>{
  'title': 'title',
  'author': 'author',
  'description': 'description',
  'createdAt': DateTime.now(),
  'updatedAt': DateTime.now(),
};

await documentReference.setData(data);
```