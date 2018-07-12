﻿---
title: 'ローカル コンピューターがグループ メンバーシップを拡張する責任を担う_ServerIsDynamicGroupExpansionServer: Exchange 2013 Help'
TOCTitle: ローカル コンピューターがグループ メンバーシップを拡張する責任を担う_ServerIsDynamicGroupExpansionServer
ms:assetid: f6fdd8e1-fda1-45be-b8a2-0d356dbe7d83
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/ms.exch.setupreadiness.serverisdynamicgroupexpansionserver(v=EXCHG.150)
ms:contentKeyID: 48270252
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# ローカル コンピューターがグループ メンバーシップを拡張する責任を担う\_ServerIsDynamicGroupExpansionServer

 

_**適用先:** Exchange Server_

_**トピックの最終更新日:** 2012-06-05_

グループ メンバーシップを展開する役割を持っているハブ トランスポートの役割をアンインストールする試みが失敗したため、Microsoft® Exchange Server 2007 セットアップ プログラムを続行できません。

Exchange 2007 セットアップ プログラムでハブ トランスポートの役割をアンインストールするには、現在のブリッジヘッド サーバーから配布リストの展開が削除されていることが必要です。

配布リストを展開すると、識別対象の配布リストに属する個々の受信者を識別したり、展開のためにどの配布リストを追加したらよいかを識別したりすることができます。展開された配布リストは、必要な任意の配信状態通知 (DSN) へのパスを返すことができます。DSN は、Microsoft Exchange 管理者または電子メールの送信者に、特定の電子メール メッセージの状態を通知します。さらに、配布リストを展開すると、不在メッセージや自動的に生成された返信を元のメッセージの送信者に送信するかどうかも識別されます。

この問題を解決するには、配布グループの展開を別のサーバーに移動した後、Microsoft Exchange セットアップ プログラムを再実行します。

**配布グループまたは動的な配布グループの展開サーバーを変更するには、次の操作を行います。**

1.  Exchange 管理コンソールを開きます。

2.  コンソール ツリーで、**\[受信者の構成\]** を展開します。

3.  コンソール ツリーで、**\[配布グループ\]** をクリックします。

4.  現在のブリッジヘッド サーバーを展開サーバーとして使用するすべての配布グループおよび動的な配布グループを表示するためのフィルターを作成します。
    
    1.  アクション ペインで、**\[フィルターの作成\]** をクリックします。
    
    2.  プロパティのボックスの一覧で、**\[展開サーバー\]** をクリックします。
    
    3.  演算子のボックスの一覧で、**\[と等しい\]** をクリックします。
    
    4.  値のボックスで、**\[参照\]** をクリックし、現在展開サーバーとして機能しているブリッジヘッド サーバーを選択します。


> [!NOTE]
> 以下の手順は省略可能です。



1.  **\[式の追加\]** をクリックして追加のフィルター条件を指定します。すべてのフィルター条件を満たすメッセージのみが表示されます。

2.  **\[フィルターの適用\]** をクリックします。フィルター条件を満たす結果が表示されます。

<!-- end list -->

1.  結果ペインで、展開サーバーを変更する配布グループをクリックし、アクション ペインの **\[プロパティ\]** をクリックします。

2.  **\[プロパティ\]** で、**\[詳細設定\]** タブをクリックします。

3.  \[展開サーバー\] ボックスの一覧で、一覧から特定のサーバーを選択するか、または **\[組織内の任意のサーバー\]** を選択します。

4.  このブリッジヘッド サーバーを展開サーバーとして使用するすべての配布グループまたは動的な配布グループについて、手順 5. ～ 7. を繰り返します。
