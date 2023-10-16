# クエリ機能について
Firestoreのクエリは、コレクションから１件あるいは複数のドキュメントを取り出す操作です。RDBにおけるSQLのSELECT文のように、条件を指定して、ドキュメントのフィールドのフィールドの値に基づいてフィルタリングしたり、特定のフィールドに基づいてフィルタリングしたり、特定のフィールドをかけてりソートをかけて、取得件数を絞ったりできます。

## クエリの種類
Firestoreのクエリは、以下の種類があります。

- コレクションの全ドキュメントを取得する
- コレクションのドキュメントを条件に基づいて取得する
- コレクションのドキュメントを条件に基づいてソートして取得する

```dart
// コレクションの全ドキュメントを取得する
QuerySnapshot querySnapshot = await Firestore.instance.collection('users').getDocuments();

// コレクションのドキュメントを条件に基づいて取得する
QuerySnapshot querySnapshot = await Firestore.instance.collection('users').where('age', isGreaterThan: 20).getDocuments();

// コレクションのドキュメントを条件に基づいてソートして取得する
QuerySnapshot querySnapshot = await Firestore.instance.collection('users').where('age', isGreaterThan: 20).orderBy('age').getDocuments();
```

英語版のサイトで参考になりそうなサイトのリンクを貼っておきます。
https://firebase.flutter.dev/docs/firestore/usage
