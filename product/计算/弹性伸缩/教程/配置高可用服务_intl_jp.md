
## シナリオの説明

伝統的なアクティブ/スタンバイまたはデュアルアクティブHAクラスターの構築は比較的面倒です。ASのヘルス検出機能を使用して高可用性を実現できます。

システムは自動的にアクティブノードのヘルス状況を検出します。アクティブノードのpingが到達できない場合、ASは健康なインスタンスを自動的にコピーして異常な状態のインスタンスを置き換え、ビジネスが健康で安定した運営を確保し、ビジネスを守ります。
次の図は例です。

![Alt text](https://mc.qcloudimg.com/static/img/b4553279b674477afa12c5109e09bf6f/04+%282%29.gif)

## 使用方法

step1：クラスターステートレスCVMのイメージを作成します。

step2：スケーリンググループを作成し、最大スケーリング数と最小スケーリング数は、目標クラスターCVMの上限と下限です。作成後、スケーリンググループのCVMリストで「クラウドCVMの追加」を選択し、手動でクラスター内の既存のCVMを追加します。注：手動でスケーリンググループに追加されたCVMが置き換えられた時、それがスケーリンググループによって終了されず、単にスケーリンググループからCVMを除去します。

step3：通知を作成し、異常なインスタンスを置き換えるスケーリングアクティビティー通知を受け入れることを選択することで、

![Alt text](https://mc.qcloudimg.com/static/img/ebee2c6fbcae2766d12ca046cdc75317/26.png)

構成は完了することができます。

## ASによってもたらされる価値

クラスターにセキュリティを高めます。

## 適用業界
ステートレスCVMを含める限り、ステートレスCVMをスケーリンググループに追加することを強くお勧めします。IT配置の習慣にすることをお勧めします。

