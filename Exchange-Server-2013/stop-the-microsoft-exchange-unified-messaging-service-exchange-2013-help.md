﻿---
title: 'Microsoft Exchange Unified Messaging Service を停止する: Exchange 2013 Help'
TOCTitle: Microsoft Exchange Unified Messaging Service を停止する
ms:assetid: 64fa5535-8150-45c6-82e6-d2346892a031
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Aa998595(v=EXCHG.150)
ms:contentKeyID: 50555799
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Microsoft Exchange Unified Messaging Service を停止する

 

_**適用先:** Exchange Server 2013, Exchange Server 2016_

_**トピックの最終更新日:** 2012-11-16_

Microsoft 管理コンソール (MMC) でサービス スナップインを、またはコマンド プロンプトで cmd.exe を使用すると、メールボックス サーバー上の Microsoft Exchange ユニファイド メッセージング サービスを停止できます。このサービスを停止する必要のある場合もあります。たとえば、メールボックス サーバーをオフラインにする必要のあるときなどです。Microsoft Exchange ユニファイド メッセージング サービスを停止すると、メールボックス サーバーは、着信呼び出しを受け付けて処理することができなくなります。

メールボックス サーバーに関するその他の管理タスクについては、「[UM サービス手順](um-services-procedures-exchange-2013-help.md)」を参照してください。

## 始める前に把握しておくべき情報

  - 予想所要時間: 1 分未満。

  - 以下の手順を実行するには、ローカル Administrators グループのメンバーであるアカウントを使用してメールボックス サーバーにログオンする必要があります。

  - メールボックス サーバーがクライアント アクセス サーバーと同じコンピューターにインストールされているか、または別のコンピューターにインストールされているかを確認します。

  - このトピックの手順で使用可能なキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md)」を参照してください。


> [!TIP]
> 問題がある場合は、Exchange のフォーラムで質問してください。 次のフォーラムにアクセスしてください。<A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>、 <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>、 または <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>。.



## 必要な作業

## MMC サービス スナップインを使用して Microsoft Exchange ユニファイド メッセージング サービスを停止する

1.  <strong>スタート</strong> ボタンをクリックし、<strong>コントロール パネル</strong> をクリックします。

2.  コントロール パネルで、<strong>管理ツール</strong> をダブルクリックします。

3.  <strong>管理ツール</strong> で、<strong>サービス</strong> をダブルクリックします。

4.  <strong>サービス</strong> 詳細ウィンドウで、<strong>Microsoft Exchange ユニファイド メッセージング</strong> を右クリックし、<strong>停止</strong> をクリックします。

## コマンド プロンプトを使用して Microsoft Exchange ユニファイド メッセージング サービスを停止する

1.  <strong>スタート</strong> ボタンをクリックし、<strong>ファイル名を指定して実行</strong> をクリックします。

2.  <strong>名前</strong> ボックスに次のコマンドを入力し、Enter キーを押します。
    
        net stop MSExchangeUM

