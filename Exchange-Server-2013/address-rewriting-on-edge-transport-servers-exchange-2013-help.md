﻿---
title: 'エッジ トランスポート サーバー上でのアドレス書き換え: Exchange 2013 Help'
TOCTitle: エッジ トランスポート サーバー上でのアドレス書き換え
ms:assetid: 23f1eaf6-247a-4671-ad72-aae19d9b511d
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Aa996806(v=EXCHG.150)
ms:contentKeyID: 61060531
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# エッジ トランスポート サーバー上でのアドレス書き換え

 

_**適用先:** Exchange Server 2013_

_**トピックの最終更新日:** 2015-03-09_

アドレス書き換えは、エッジ トランスポート サーバー経由で組織に出入りするメッセージ内の送信者と受信者の電子メール アドレスを変更します。エッジ トランスポート サーバーでは、受信用アドレス書き換えエージェントと送信用アドレス書き換えエージェントという 2 つのトランスポート エージェントが書き換え機能を提供します。送信メッセージのアドレス書き換えの主な目的は、単一の電子メール ドメインを一貫して外部の受信者に提示することです。受信メッセージのアドレス書き換えの主な目的は、正しい受信者にメッセージを配信することです。

作成した*アドレス書き換えエントリ*で内部アドレス (変更する電子メール アドレス) と外部アドレス (最終的に必要な電子メール アドレス) を指定します。受信メッセージと送信メッセージの電子メール アドレスを書き換えるのか、送信メッセージの電子メール アドレスだけを書き換えるのかを指定できます。単一ユーザー (chris@contoso.com から support@contoso.com へ)、単一ドメイン内のすべてのユーザー (contoso.com から fabrikam.com へ)、または例外を含む複数のサブドメイン内のユーザー (\*.fabrikam.com から contoso.com へ、legal.fabrikam.com を除く) に関するアドレス書き込みエントリを作成できます。


> [!IMPORTANT]
> アドレス書き換えの用途に関係なく、生成される電子メール アドレスは組織内で一意であり、重複していないことを確認する必要があります。これは、アドレス書き換えでは書き換える電子メール アドレスの一意性が確認されないためです。



**目次**

アドレス書き換えのシナリオ

アドレス書き換えによって変更されるメッセージ プロパティ

アドレス書き換えで変更されないもの

送信専用アドレス書き換えに関する考慮事項

受信アドレス書き換えと送信アドレス書き換えに関する考慮事項

複数のドメイン内の電子メール アドレスの書き換えに関する考慮事項

アドレス書き換えエントリの優先度

デジタル署名されたメッセージ、暗号化されたメッセージ、および権利で保護されたメッセージ

## アドレス書き換えのシナリオ

次のシナリオは、アドレス書き換えの使用方法に関する例です。

  - **グループの統合**   一部の組織は、ビジネス要件や技術的な要件に基づいて、内部のビジネスを個別のドメインに分割しています。この構成では、電子メール メッセージが別のグループまたは別の組織から発信されているように見せることができます。
    
    次の例では、Contoso, Ltd. という組織が外部の受信者から内部のサブドメインを隠す方法を示します。
    
      - northamerica.contoso.com、europe.contoso.com、および asia.contoso.com というドメインからの送信メッセージは、単一の contoso.com ドメインから発信されているように書き換えられます。すべてのメッセージは、組織全体とインターネットとの間の SMTP 接続を提供するエッジ トランスポート サーバーを通過するときに書き換えられます。
    
      - Contoso.com 受信者への受信メッセージは、エッジ トランスポート サーバーからメールボックス サーバーに中継されます。メッセージは、受信者のメールボックスに構成されているプロキシ アドレスに基づいて正しい受信者に配信されます。

  - **吸収と合併**   合併された企業は引き続き別の事業体として運営されることもありますが、アドレス書き換えを使用して 2 つの組織を統合された 1 つの組織であるかのように見せることができます。
    
    次の例では、Contoso, Ltd. が新しく合併した企業の Fourth Coffee の電子メール ドメインを隠す方法を示します。
    
      - Contoso, Ltd. は、Fourth Coffee の Exchange 組織からのすべての送信メッセージを Contoso.com から発信されたように見せる必要があります。両方の組織からのすべてのメッセージは Contoso, Ltd. のエッジ トランスポート サーバー経由で送信され、電子メール メッセージは *user*@fourthcoffee.com から *user*@contoso.com に書き換えられます。
    
      - *user*@contoso.com への受信メッセージは書き換えられ、*user*@fourthcoffee.com メールボックスにルーティングされます。*user*@fourthcoffee.com に送信される受信メッセージは Fourth Coffee の電子メール サーバーに直接ルーティングされます。

  - **パートナー**   多くの組織が外部のパートナーを利用して顧客、他の組織、または自分の組織にサービスを提供しています。混乱を避けるために、組織がパートナー組織の電子メール ドメインを独自の電子メール ドメインに置き換える場合があります。
    
    次の例では、Contoso, Ltd. がパートナーの電子メール ドメインを隠す方法を示します。
    
      - Contoso, Ltd. は、より大規模な組織である Wingtip Toys にサポートを提供します。Wingtip Toys は、顧客に統一された電子メール エクスペリエンスを提供したいと考えており、Contoso, Ltd. のサポート担当者からのすべてのメッセージを Wingtip Toys から送信されたように見せることを希望しています。Wingtip Toys に関連したすべての送信メッセージがエッジ トランスポート サーバー経由で送信され、すべての contoso.com 電子メール アドレスが wingtiptoys.com 電子メール アドレスに書き換えられます。
    
      - support@wingtiptoys.com 宛ての受信メッセージは、Wingtip Toy のエッジ トランスポート サーバーで受信され、書き換えられてから、support@contoso.com 電子メール アドレスにルーティングされます。

ページのトップへ

## アドレス書き換えによって変更されるメッセージ プロパティ

標準的な SMTP 電子メール メッセージは、*メッセージ エンベロープ*とメッセージのコンテンツで構成されます。メッセージ エンベロープには、SMTP メール サーバー間でのメッセージの送信と配信に必要な情報が含まれています。メッセージのコンテンツには、総称して "*メッセージ ヘッダー*" と呼ばれるメッセージ ヘッダー フィールドと、メッセージ本文があります。メッセージ エンベロープは RFC 2821 で定義され、メッセージ ヘッダーは RFC 2822 で定義されます。

送信者が電子メール メッセージを作成し、配信のために送信した段階でメッセージに含まれるのは、SMTP 標準に準拠するために必要な基本的な情報 (送信者、受信者、メッセージの作成日時、省略可能な件名、省略可能なメッセージ本文など) です。この情報は、メッセージ自体と、定義上、メッセージ ヘッダー内に含まれます。

送信者のメール サーバーが、メッセージ ヘッダー内の送信者の情報と受信者の情報を使用して、メッセージのメッセージ エンベロープを生成します。それから、メッセージをインターネットに送信して、受信者のメール サーバーに配信します。メッセージ エンベロープはメッセージ送信プロセスによって生成されるもので、実際にはメッセージの一部ではないため、受信者がメッセージ エンベロープを目にすることはありません。

アドレス書き換えでは、メッセージ ヘッダーまたはメッセージ エンベロープ内の特定のフィールドを書き換えることによって、電子メール アドレスが変更されます。また、アドレス書き換えでは、送信メッセージ内の複数のフィールドが変更されますが、受信電子メール メッセージでは 1 つのフィールドのみが変更されます。次の表は、送信メッセージと受信メッセージ内で書き換えられる SMTP ヘッダー フィールドを示しています。

### 送信メッセージと受信メッセージで書き換えられるメッセージ フィールド

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>フィールド名</th>
<th>場所</th>
<th>送信メッセージ</th>
<th>受信メッセージ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>MAIL FROM</strong></p></td>
<td><p>メッセージ エンベロープ</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="even">
<td><p><strong>RCPT TO</strong></p></td>
<td><p>メッセージ エンベロープ</p></td>
<td><p>書き換えられない</p></td>
<td><p>書き換えられる</p></td>
</tr>
<tr class="odd">
<td><p><strong>To</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="even">
<td><p><strong>Cc</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="odd">
<td><p><strong>From</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="even">
<td><p><strong>Sender</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reply-To</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="even">
<td><p><strong>Return-Receipt-To</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="odd">
<td><p><strong>Disposition-Notification-To</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="even">
<td><p><strong>Resent-From</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
<tr class="odd">
<td><p><strong>Resent-Sender</strong></p></td>
<td><p>メッセージ ヘッダー</p></td>
<td><p>書き換えられる</p></td>
<td><p>書き換えられない</p></td>
</tr>
</tbody>
</table>


ページのトップへ

## アドレス書き換えで変更されないもの

アドレス書き換えでは、SMTP 機能を妨げるメッセージ ヘッダー フィールドは変更されません。たとえば、特定のヘッダー フィールドを変更すると、メッセージ ループの検出に影響したり、署名が無効になったり、権利で保護されたメッセージが判読不能になったりする可能性があります。そのため、次のヘッダー フィールドはアドレス書き換えによって変更されません。

  - **Return-Path**

  - **Received**

  - **Message-ID**

  - **X-MS-TNEF-Correlator**

  - **Content-Type Boundary=string**

  - MIME ボディ内部に配置されたヘッダー フィールド

アドレス書き換えでは、Exchange 組織によって管理されていないドメインが無視されます。つまり、アドレス書き換えでは、Exchange が権限を持っていないドメインを含むヘッダー フィールドが書き換えられません。このようなドメインを書き換えると、メッセージ中継が制御不能になります。

アドレス書き換えでは、別のメッセージに埋め込まれたメッセージのヘッダー フィールドも変更されません。送信者と受信者は、メッセージが送信者と受信者の間で実装されているトランスポート ルールをトリガーする場合以外は、埋め込まれたメッセージがそのまま残され、変更されずに配信されると想定しています。

ページのトップへ

## 送信専用アドレス書き換えに関する考慮事項

エッジ トランスポート サーバーでの送信専用アドレス書き換えでは、メッセージが Exchange 組織から離れるときに送信者の電子メール アドレスが変更されます。送信専用アドレス書き換えは、単一のユーザー (chris@contoso.com から support@contoso.com へ)、または、単一のドメイン内のすべてのユーザー (contoso.com から fabrikam.com へ) に対して構成できます。複数のサブドメイン内のユーザー (\*.fabrikam.com から .contoso.com へ) について送信専用アドレス書き換えを構成する必要があります。

書き換える電子メール アドレスは、影響を受ける受信者のプロキシ アドレスとして構成する必要があります。たとえば、laura@sales.contoso.com を laura@contoso.com に書き換える場合、プロキシ アドレス laura@contoso.com を Laura のメールボックスに構成しなければなりません。このようにすると、返信および受信メッセージを適切に配信できます。

ページのトップへ

## 受信アドレス書き換えと送信アドレス書き換えに関する考慮事項

エッジ トランスポート サーバー上での受信と送信のアドレス書き換え、つまり、*双方向*アドレス書き換えでは、Exchange 組織から離れるメッセージ内の送信者の電子メール アドレスと、Exchange 組織に入るメッセージ内の受信者の電子メール アドレスが変更されます。

送信専用アドレス書き換えは、単一のユーザー (chris@contoso.com から support@contoso.com へ) と単一のドメイン内のすべてのユーザー (contoso.com から fabrikam.com へ) に対して構成できます。複数のサブドメイン内のユーザー (\*.fabrikam.com から contoso.com へ) に対して双方向アドレス書き換えを構成することはできません。

ページのトップへ

## 複数のドメイン内の電子メール アドレスの書き換えに関する考慮事項

複数の内部ドメインまたはサブドメインを単一の外部ドメインに統合する場合は、次の要因を考慮する必要があります。

  - **一意のエイリアスの確認**   すべての電子メール エイリアス (@ 記号の左側の部分) はすべてのサブドメインを通して一意にする必要があります。たとえば、joe@sales.contoso.com が存在する場合は、joe@marketing.contoso.com を存在させることはできません。なぜなら、両方のユーザーの電子メール アドレスを書き換えると joe@contoso.com になるためです。

  - **プロキシ アドレスの追加**   書き換える電子メール アドレスは、影響を受けるドメイン内の影響を受けるすべての送信者のプロキシ アドレスとして構成する必要があります。たとえば、joe@sales.contoso.com を joe@contoso.com に書き換える場合は、プロキシ アドレスの joe@contoso.com を Joe のメールボックスに追加する必要があります。このようにすると、返信および受信メッセージを適切に配信できます。

  - **非 Exchange 組織のメール連絡先**   非 Exchange 電子メール システムからの電子メール アドレスを書き換える場合は、Exchange 内で非 Exchange 電子メール システム内のユーザーを表す電子メール連絡先を作成する必要があります。これらの電子メール連絡先に、元の電子メール アドレスと書き換えた後の電子メール アドレスを含める必要があります。たとえば、joe@unix.contoso.com を joe@contoso.com に書き換える場合は、joe@unix.contoso.com を外部電子メール アドレスとして、joe@contoso.com をプロキシ アドレスとして含むメール連絡先を作成する必要があります。

## 一意のエイリアスを確認する

複数のサブドメイン内の電子メール アドレスを書き換える場合は、すべての電子メール エイリアスがすべてのサブドメインを通して一意であることを確認する必要があります。たとえば、次の構成について考えてみます。

次のユーザーは、サブドメインの sales.contoso.com、marketing.contoso.com、および research.contoso.com に属しています。

  - maria@sales.contoso.com

  - chris@sales.contoso.com

  - david@marketing.contoso.com

  - brian@marketing.contoso.com

  - chris@research.contoso.com

  - adam@research.contoso.com

サブドメインの sales.contoso.com、marketing.contoso.com、および research.contoso.com を単一ドメインの domain contoso.com に書き換えるとします。

各サブドメイン内の電子メール アドレスを書き換えると、chris@sales.contoso.com と chris@research.contoso.com の間で競合が発生します。なぜなら、どちらの電子メール アドレスも chris@contoso.com に書き換えられるためです。この状況を解決するには、影響を受ける受信者のどちらかの電子メール アドレスを変更する必要があります。たとえば、chris@research.contoso.com を christopher@research.contoso.com に変更すれば、この電子メール アドレスは christopher@contoso.com に書き換えられます。

ページのトップへ

## アドレス書き換えエントリの優先度

ユーザーの電子メール アドレスが複数のアドレス書き換えエントリと一致する場合、その電子メール アドレスは、最もよく一致するエントリに基づいて一度だけ書き換えられます。以下に、アドレス書き換えエントリを優先度の高いものから順に示します。

1.  **個別の電子メール アドレス**   アドレス書き換えエントリは、電子メール アドレスを john@contoso.com から support@contoso.com に書き換えるように構成されます。

2.  **ドメインまたはサブドメイン マッピング**   アドレス書き換えエントリは、すべての contoso.com 電子メール アドレスを northwindtraders.com に、または、すべての sales.contoso.com 電子メール アドレスを contoso.com に書き換えるように構成されます。

3.  **ドメイン統合**   アドレス書き換えエントリは、\*.contoso.com 電子メール アドレスを contoso.com に書き換えるように構成されます。

たとえば、送信アドレス書き換えエントリが次のように構成されているエッジ トランスポート サーバーを考えます。

  - \*.contoso.com 電子メール アドレスが contoso.com に書き換えられる

  - japan.sales.contoso.com 電子メール アドレスが contoso.jp に書き換えられる

masato@japan.sales.contoso.com から電子メール メッセージが送信された場合、そのアドレスは masato@contoso.jp に書き換えられます。これは、このエントリが送信者の電子メール アドレスに最もよく一致しているためです。

ページのトップへ

## デジタル署名されたメッセージ、暗号化されたメッセージ、および権利で保護されたメッセージ

署名、暗号化、または権利の保護が行われているほとんどのメッセージは、アドレス書き換えによって影響を受けることはありません。アドレス書き換えによりメッセージが無効になるか、そうでない場合は何らかの方法でこの種のメッセージのセキュリティ ステータスが変更される場合は、アドレス書き換えが適用されません。

次の値は、情報がメッセージの署名の一部でなく、暗号化または権利による保護もされていないため、書き換えることができます。

  - メッセージ エンベロープ内のフィールド

  - 最上位のメッセージ本文ヘッダー

次の値は、情報がメッセージの署名の一部であるか、暗号化または権利による保護をされているため、書き換えられません。

  - 署名されている可能性がある MIME ボディ内部に配置されたヘッダー フィールド

  - MIME コンテンツの種類の境界文字列パラメーター

ページのトップへ
