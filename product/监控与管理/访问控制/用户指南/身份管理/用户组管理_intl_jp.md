## 概要
同じ機能を持つユーザーを同じユーザーグループに追加し、そのユーザーグループに適切なポリシーを関連付けて、さまざまな権限を割り当てて、作業効率を向上させます。
ポリシーがユーザーグループに関連付けられると、そのユーザーグループ内のユーザーにポリシーの説明権限が付与されます。これは、一括認証シナリオに非常に適しています。

## 操作ガイド
### ユーザーグループの新規作成

1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。
2. 【ユーザーグループの新規作成】をクリックして、ユーザーグループ名とコメントを入力します。この記事では例としてグループを新規作成して、【次へ】をクリックします。
![](https://main.qcloudimg.com/raw/3d0df07232ad5255564915341ca56bd2.png)
>ユーザーグループリストで、ユーザーグループ名またはコメントを検索し、多くのユーザーグループの中から対応するユーザーグループを素早く正確に見つけることができます。

3. （オプション）関連ポリシーを選択します。選択しなくても、ユーザーグループの新規作成操作を完了できます。【次へ】をクリックしてレビュー手順に入ります。
![](https://main.qcloudimg.com/raw/28a7fe34644cfd986f0fc3fe29331a04.png)
4. レビュー中に、ユーザーグループの関連設定を確認し、エラーがある場合はそれを変更できます。確認後、【完了】をクリックしてユーザーグループの新規作成操作を完了します。
![](https://main.qcloudimg.com/raw/7dac4da14cb82e38355200b2a878b1b1.png)

### ユーザーグループにユーザーを追加
#### 単一のユーザーグループにユーザーを追加
1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。ユーザーグループリストで、ユーザーを追加したいユーザーグループを見つけて、右側の【ユーザーの追加】をクリックします。
![](https://main.qcloudimg.com/raw/8d46923017c61ec74dcf901e3e97109e.png)
2. 追加するユーザーを選択して【OK】をクリックすると、そのユーザーグループに対するユーザーの追加を完了します。
![](https://main.qcloudimg.com/raw/7824db271abb280599476a4709a91ed3.png)

#### 複数のユーザーグループにユーザーを追加
1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。ユーザーグループリストで、ユーザーを追加したいユーザーグループを見つけて、【ユーザーの追加】をクリックします。
![](https://main.qcloudimg.com/raw/34b96460336cc44e22fba290d9f0b8a7.png)

2. 追加するユーザーを選択して【OK】をクリックすると、そのユーザーグループに対するユーザーの追加を完了します。
![](https://main.qcloudimg.com/raw/7824db271abb280599476a4709a91ed3.png)

### ユーザーグループのユーザーを削除
#### ユーザーグループから単一のユーザーを削除
1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。ユーザーグループ名をクリックして、ユーザーグループの詳細ページに入ります。
![](https://main.qcloudimg.com/raw/6cdce4885bb299c758130fa480af0f92.png)

2. 【追加されたユーザー】をクリックし、ユーザーリストから削除するユーザーを1人ずつ探し、右側の【このグループから除去】をクリックして個々のユーザーを削除します。
![](https://main.qcloudimg.com/raw/e7ab8520de2aa75deef2b307e45dcdc9.png)

3. 【ユーザーの除去】をクリックして、ユーザーグループに対するユーザーの削除を完了します。

#### ユーザーグループから複数のユーザーを削除
1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。ユーザーグループ名をクリックして、ユーザーグループの詳細ページに入ります。
![](https://main.qcloudimg.com/raw/6cdce4885bb299c758130fa480af0f92.png)

2. 【追加されたユーザー】をクリックし、削除するユーザーを複数選択して、左上の【ユーザーの除去】をクリックします。
![](https://main.qcloudimg.com/raw/9106a51eb41ea9d949ebd47fb8c66c23.png)

3. 【除去の確認】をクリックして、ユーザーグループに対するユーザーの削除を完了します。

### ユーザーグループにポリシーを追加

1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。ユーザーグループ名をクリックして、ユーザーグループの詳細ページに入ります。
![](https://main.qcloudimg.com/raw/750507c3c3bff9e82746366d0b4f9961.png)
2. 【関連付けられているポリシー】>【関連ポリシー】をクリックします。
 ![](https://main.qcloudimg.com/raw/752a908e7a8f69b31e3b4257a5d506fc.png)
3. ポップアップボックスで追加するポリシーを選択して【OK】をクリックすると、そのユーザーグループに対するポリシーの追加を完了します。
![](https://main.qcloudimg.com/raw/0ae6e0b78f0ed7e6147a0c0bc2dba2eb.png)

### ユーザーグループのポリシーを削除

1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。ユーザーグループ名をクリックして、ユーザーグループの詳細ページに入ります。

 ![](https://main.qcloudimg.com/raw/750507c3c3bff9e82746366d0b4f9961.png)

2. リストから削除するポリシーを見つけて、図のように、右側の【解除】をクリックします。

 ![](https://main.qcloudimg.com/raw/ac114903444a8b9d5a81e9cd560fe143.png)

3. エラーがないことを確認してから、【解除の確認】をクリックし、ユーザーグループに対するポリシーの削除を完了します。

### ユーザーグループの削除

1. [CAMコンソール](https://console.cloud.tencent.com/cam/overview )にログインし、左側のナビゲーションをクリックして【ユーザーグループ管理】に入ります。削除したいユーザーグループを選択し、図のように【削除】をクリックします。

 ![](https://main.qcloudimg.com/raw/a4a3cfa9b48052ba6656bba59d26a9df.png)

2. エラーがないことを確認してから、【削除の確認】をクリックして、ユーザーグループの削除を完了します。
