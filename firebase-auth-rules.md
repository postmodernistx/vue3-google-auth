# Firebase Read/Write rules

Limit read/write to certain Google users

https://console.firebase.google.com/project/PROJECT-NAME-HERE/firestore/rules

```
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth.uid == "google-user-id-goes-here";
      allow read, write: if request.auth.uid == "another-user-id-here";
    }
  }
}
```
