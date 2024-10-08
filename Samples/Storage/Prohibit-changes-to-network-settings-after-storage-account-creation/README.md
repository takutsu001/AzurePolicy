# ストレージアカウント作成後のネットワーク設定変更を禁止する

> [!NOTE]
> 本説明はChatGPTを利用して作成しています

### 概要
このAzure Policyは、ストレージアカウントの作成が成功した後に、特定のネットワーク設定が存在する場合、操作を拒否する（Deny）ように設定されています

### 目的
このポリシーの目的は、特定のネットワーク設定が存在するストレージアカウントに対して、意図しない変更やアクセスを防止することです

### ポリシーの適用条件
以下の条件がすべて満たされる場合にポリシーが適用されます
- リソースのタイプが Microsoft.Storage/storageAccounts であること
- プロビジョニングの状態が Succeeded（成功）であること
- ネットワークACLまたはパブリックネットワークアクセスの設定が存在すること

これらの条件を満たすと、指定された操作は拒否されます（Deny）

### 本ポリシーの動作についての補足
- ストレージ作成時は本ポリシーは適用されない（適用されるのは作成後）
- パブリックネットワークアクセス関連の設定はすべて拒否される（パブリックアクセスの設定変更や許可するIPの削除や追加など）
- プライベートエンドポイント接続の設定は可能

----
動作イメージ
![](images/Prohibit-changes-to-network-settings-after-storage-account-creation_Policy_01.png)