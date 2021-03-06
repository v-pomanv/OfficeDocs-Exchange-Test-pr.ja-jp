﻿---
title: 'Exchange を実行していないシステムから電子メールを受信するための受信コネクタの作成: Exchange 2013 Help'
TOCTitle: Exchange を実行していないシステムから電子メールを受信するための受信コネクタの作成
ms:assetid: 85f0864a-6502-49db-8804-16755a7292b4
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ657467(v=EXCHG.150)
ms:contentKeyID: 49896343
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange を実行していないシステムから電子メールを受信するための受信コネクタの作成

 

_**適用先:** Exchange Server 2013_

_**トピックの最終更新日:** 2012-10-03_

Exchange を実行していないシステムからメッセージを受信する場合があるかもしれません。 たとえば、ポリシー チェックを実行し、メッセージを Exchange サーバーにルーティングするネットワーク アプライアンスがある場合です。この場合、アプライアンスは SMTP を使用することを前提としています。 そうでない場合、外部コネクタまたは配信エージェント コネクタを使用する必要があります。

この手順を使用しているシナリオに興味はありますか?次のトピックを参照してください。

  - [メール フローおよびクライアント アクセスの構成](configure-mail-flow-and-client-access-exchange-2013-help.md)

## 始める前に把握しておくべき情報

  - 予想所要時間 : 15 分

  - この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可の一覧については、以下を参照してください。「[メール フローのアクセス許可](mail-flow-permissions-exchange-2013-help.md)」の「受信コネクタ」。

  - インストールを開始する際には、「[Exchange 2013 の新規インストールの展開](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md)」を参照してください。インストール後に、このトピックの手順を使用して受信コネクタを作成します。

  - このトピックの手順で使用可能なキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md)」を参照してください。


> [!TIP]
> 問題がある場合は、Exchange のフォーラムで質問してください。 次のフォーラムにアクセスしてください。<A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>、 <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>、 または <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>。



## EAC を使用して受信コネクタを作成し、メッセージング アプライアンスからメッセージを受信する

1.  EAC で、<strong>メール フロー</strong> \> <strong>受信コネクタ</strong> に移動します。<strong>追加</strong>![\[追加\] アイコン](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "[追加] アイコン") をクリックして受信コネクタを作成します。

2.  <strong>新しい受信コネクタ</strong> ページで、受信コネクタの名前を指定し、<strong>役割</strong> で <strong>ハブ トランスポート</strong> を選択します。 この場合、トランスポート サービスを実行しているメールボックス サーバーでアプライアンスからメッセージを受信します。

3.  種類には <strong>カスタム</strong> を選択します。受信コネクタが Microsoft Exchange Server 2013 を実行していないアプライアンスからメールを受信するためです。

4.  <strong>ネットワーク アダプター バインド</strong> では、<strong>IP アドレス</strong> リストに <strong>利用可能なすべての IPv4 アドレス</strong> がリストされていることを確認します。<strong>次へ</strong> をクリックします。

5.  <strong>リモート ネットワーク設定</strong> では、<strong>削除</strong>![\[削除\] アイコン](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "[削除] アイコン") をクリックして、<strong>IP アドレス</strong> リストから **0.0.0.0-255.255.255.255** を削除します。コネクタが特定のアプライアンスからのメールを受け入れることを指定するためです。 <strong>追加</strong>![\[追加\] アイコン](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "[追加] アイコン") をクリックして、新しい IP アドレスを追加し、<strong>IP アドレスの追加</strong> ウィンドウでアプライアンスの IP アドレスを追加します。<strong>保存</strong> をクリックします。

6.  <strong>終了</strong> ボタンをクリックしてユーザーのコネクタを作成します。

受信コネクタの作成が完了すると、受信コネクタ一覧に表示されます。コマンドレットを使用して受信コネクタを作成する手順の例については、「[New-ReceiveConnector](https://technet.microsoft.com/ja-jp/library/bb125139\(v=exchg.150\))」を参照してください。

## 正常な動作を確認する方法

メッセージング アプライアンスからメッセージを受信する受信コネクタが正常に作成されたことを確認するには、アプライアンスからメールを受信できることをテストします。メールを受信することができれば、構成は正常に機能しています。

## 詳細情報

[受信コネクタを作成してインターネットからの電子メールを受信する](create-a-receive-connector-to-receive-email-from-the-internet-exchange-2013-help.md)

