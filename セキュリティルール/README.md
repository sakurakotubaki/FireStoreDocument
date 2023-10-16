# セキュリティールール
FIrestoreにおいて、ユーザーの認証や認可などのアクセス制御やデータのバリデーションのために、セキュリティールールと呼ばれる機能が利用できます。

これは、アクセス時に、ルールに従ってアクセスを許可するかどうかを判断するものです。セキュリティルールでは、以下のようなことが設定できます。

- 認証済みユーザーのみアクセスを許可する
- 管理者ユーザーしか読み書きできない。
- コレクションのドキュメントのフィールドに文字を200文字までしか書き込めないようにする例。

ルールの見本。
```js
service cloud.firestore {
  match /databases/{database}/documents {
    // 認証済みユーザーのみアクセスを許可する
    match /{document=**} {
      allow read, write: if request.auth.uid != null;
    }
    // 管理者ユーザーしか読み書きできない。
    match /admin/{document=**} {
      allow read, write: if request.auth.token.admin == true;
    }
    // コレクションのドキュメントのフィールドに文字を200文字までしか書き込めないようにする例。
    match /users/{userId} {
      allow read: if request.auth.uid == userId;
      allow write: if request.auth.uid == userId
                   && request.resource.data.name.size() <= 200;
    }
  }
}
```