## ユースケース
このドキュメントは、共有カスタマイズイメージを解除する方法を説明します。ユーザーはほかのユーザーと共有されているイメージの共有状態をいつでも終了でき、ほかのユーザーと共有しないことを決定できます。この操作はほかのユーザーがこの共有イメージを利用して作成したインスタンスに影響しませんが、他のユーザーがこのイメージを確認したり、このイメージを利用して新しいインスタンスを作成したりすることができません。

## 操作手順
### コンソールを利用して共有を解除する
 1. [CVMコンソール](https://console.cloud.tencent.com/cvm/)にログインします。
 2. 左側ナビゲーションバーで、【イメージ】をクリックします。
 3.【カスタマイズイメージ】タブを選択して、カスタマイズイメージ管理画面に入ります。
 4. カスタマイズイメージリストから、共有を解除するカスタマイズイメージを選択して、【その他】>【共有を解除する】をクリックします。
 5. 新しい画面で、解除する対向側アカウントの唯一IDを選択して、【共有を解除する】をクリックします。
 6. 表示されたプロンプトボックスで、【OK】をクリックして、イメージ共有の解除を完了します。

### APIを利用して共有を解除する
ModifyImageSharePermission インターフェースを利用して、共有イメージを解除できます。詳細については、 [イメージ共有情報の修正](https://cloud.tencent.com/document/product/213/15710)をご参照ください。
