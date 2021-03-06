﻿---
title: 'World Wide Web 発行サービスが無効または見つからない'
TOCTitle: World Wide Web Publishing Service が無効または見つからない_W3SVCDisabledOrNotInstalled
ms:assetid: 2d26d778-ddf1-4225-b5e2-f6b49d819c94
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/ms.exch.setupreadiness.w3svcdisabledornotinstalled(v=EXCHG.150)
ms:contentKeyID: 48269311
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# World Wide Web Publishing Service が無効または見つからない\_W3SVCDisabledOrNotInstalled

 

_**適用先:** Exchange Server_

_**トピックの最終更新日:** 2012-06-05_

このトピックの内容は、Microsoft Exchange Server 2013 向けに更新されていません。まだ更新されていませんが、そのままで Exchange 2013 にも適用できる可能性があります。ヘルプが必要な場合は、以下のコミュニティ リソースを確認してください。

問題がある場合は、Exchange のフォーラムで質問してください。 次のフォーラムにアクセスしてください。[Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612)、 [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542)、 または [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351)。

メールボックス サーバーの役割またはクライアント アクセスの役割をインストールしようとしたときに、このコンピューターで World Wide Web Publishing サービスが無効になっているかまたはインストールされていないことが検出されたため、Microsoft® Exchange Server 2007 セットアップ プログラムを続行できません。

Exchange 2007 セットアップ プログラムを実行するには、Microsoft Exchange をインストールするコンピューターに World Wide Web Publishing サービスがインストールされ、無効以外の状態に設定されている必要があります。

この問題を解決するには、ローカル コンピューターに World Wide Web Publishing サービスがインストールされ、無効以外の状態になっていることを確認した後、Microsoft Exchange セットアップ プログラムを再実行します。

**World Wide Web Publishing サービスがインストールされ、無効以外の状態になっていることを確認するには、次の操作を行います。**

1.  デスクトップの <strong>マイ コンピューター</strong> を右クリックし、<strong>管理</strong> をクリックします。

2.  <strong>サービスとアプリケーション</strong> ノードを展開し、<strong>サービス</strong> ノードをクリックします。

3.  右側のペインで、<strong>World Wide Web Publishing Service</strong> を見つけます。
    
    インストールされているサービスの一覧に <strong>World Wide Web Publishing Service</strong> が表示されない場合は、以下の手順を実行してインストールします。

4.  <strong>World Wide Web Publishing Service</strong> が表示されても、状態が <strong>開始</strong> になっていない場合は、以下の手順を実行して開始します。

5.  <strong>World Wide Web Publishing Service</strong> を右クリックし、<strong>プロパティ</strong> をクリックします。

6.  <strong>スタートアップの種類</strong> が <strong>自動</strong> に設定され、<strong>サービスの状態</strong> が <strong>開始</strong> に設定されていることを確認します。

7.  <strong>適用</strong> をクリックし、<strong>OK</strong> をクリックします。

**World Wide Web Publishing サービスをインストールするには、次の操作を行います。**

1.  <strong>スタート</strong> ボタンをクリックし、<strong>設定</strong> をポイントします。次に、<strong>コントロール パネル</strong> をポイントし、<strong>プログラムの追加と削除</strong> をクリックします。

2.  <strong>Windows コンポーネントの追加と削除</strong> をクリックします。

3.  <strong>コンポーネント</strong> ボックスの一覧で、<strong>アプリケーション サーバー</strong> チェック ボックスをオンにし、<strong>詳細</strong> をクリックします。

4.  <strong>インターネット インフォメーション サービス マネージャー</strong> を選択し、<strong>詳細</strong> をクリックします。

5.  <strong>WWW (World Wide Web) サービス</strong> を選択し、チェック ボックスをオンにします。

6.  <strong>OK</strong> を 2 回クリックして <strong>コンポーネント</strong> ボックスの一覧に戻り、<strong>次へ</strong> をクリックします。

7.  IIS サービスがインストールされたら、<strong>完了</strong> をクリックします。

