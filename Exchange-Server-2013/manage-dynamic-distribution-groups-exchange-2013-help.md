﻿---
title: '動的配布グループの管理: Exchange Online Help'
TOCTitle: 動的配布グループの管理
ms:assetid: 8ef85d0a-41df-4b5c-b8e7-ca8d09c048ca
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Bb123722(v=EXCHG.150)
ms:contentKeyID: 48269055
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.CreateDynamicGroupWizardForm.CreateDynamicGroupInformationWizardPage
ms.translationtype: HT
---

# 動的配布グループの管理

 

_**適用先:** Exchange Online, Exchange Server 2013_

動的配布グループとは、Microsoft Exchange 組織内で大量の電子メール メッセージおよびその他の情報を効率よく送信するために作成された、メールが有効な Active Directory グループ オブジェクトです。

定義済みのメンバーのセットを含む通常の配布グループとは異なり、動的配布グループのメンバーシップの一覧は、グループにメッセージが送信されるたびに、指定されたフィルターおよび条件に基づいて計算されます。動的配布グループに送信された電子メール メッセージは、そのグループに対して定義されている条件に一致する組織内のすべての受信者に配信されます。


> [!IMPORTANT]
> 動的配布グループには、Active Directory 内の受信者のうち、属性の値がフィルターに一致するすべての受信者が含まれます。受信者のプロパティがフィルターに一致するように変更された場合、その受信者が誤ってそのグループのメンバーになり、グループに送信されたメッセージを受信し始めることがあります。定義済みの一貫性のあるアカウントの準備プロセスを使用すると、このような問題が発生する可能性は低くなります。



## 始める前に把握しておくべき情報

  - 予想所要時間 : 2 ～ 5 分

  - この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可の一覧については、以下を参照してください。「[受信者のアクセス許可](recipients-permissions-exchange-2013-help.md)」の「動的配布グループ」。

  - このトピックの手順で使用可能なキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md)」を参照してください。


> [!TIP]
> 問題がある場合は、Exchange のフォーラムで質問してください。 次のフォーラムにアクセスしてください。<A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>、 <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>、 または <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>。.



## 必要な作業

## 動的配布グループを作成する

## EAC を使用して動的配布グループを作成する

1.  EAC で、**\[受信者\]** \> **\[グループ\]** \> **\[新規作成\]** \> **\[動的配布グループ\]** に移動します。

2.      
    **\[新しい動的配布グループ\]**ページで、次のボックスに入力します。
    
      - **\* \[表示名\]**   このボックスを使用して、表示名を入力します。この名前は共有アドレス帳、このグループにメールを送信するときの電子メールの宛先行、EAC の \[グループ\] 一覧に表示されます。表示名は必須であり、ユーザーが内容を認識できるようにわかりやすい名前にする必要があります。表示名は、フォレスト内で一意である必要があります。
        

        > [!NOTE]
        > グループの名前付けポリシーは、動的配布グループに適用されません。

    
      - **\* \[エイリアス\]**   このボックスには、グループのエイリアス名を入力します。エイリアスは 64 文字以内で、フォレスト内で一意である必要があります。ユーザーが電子メール メッセージの宛先行にエイリアスを入力すると、グループの表示名に解決されます。
    
      - **\[説明\]**   このボックスを使用してグループを説明することにより、ユーザーはこのグループの目的を認識することができます。この説明は共有アドレス帳に表示されます。
    
      - **\[組織単位\]**   既定 (受信者の範囲) 以外の組織単位 (OU) を選択できます。受信者の範囲がフォレストに設定されている場合は、EAC を実行しているコンピューターを含む Active Directory ドメイン内の Users コンテナーが既定値として設定されます。受信者の範囲が特定のドメインに設定されている場合は、そのドメイン内の Users コンテナーが既定で選択されます。受信者の範囲が特定の OU に設定されている場合は、その OU が既定で選択されます。
        
        別の OU を選択するには、**\[参照\]** をクリックします。このダイアログ ボックスには、指定した範囲内のフォレストにあるすべての OU が表示されます。目的の OU を選択し、**\[OK\]** をクリックします。
    
      - **\[所有者\]**  動的配布グループの所有者は省略可能です。**\[参照\]** をクリックして一覧からユーザーを選択すると、所有者を追加できます。

3.      
    **\[メンバー\]** を使用して、グループの受信者の種類を指定し、メンバーシップを決定するルールを設定します。次のいずれかのボックスを選択します。
    
      - **\[すべての種類の受信者\]**   このグループに対して定義されている条件に一致するメッセージをすべての種類の受信者に送信するには、このオプションを選択します。
    
      - **\[次の受信者の種類のみ\]**   このグループに対して定義されている条件に一致するメッセージが、次の 1 つ以上の種類の受信者に送信されます。
        
          - **\[Exchange メールボックスを持つユーザー\]**   Exchange メールボックスを持つユーザーを含めるには、このチェック ボックスをオンにします。Exchange メールボックスを持つユーザーとは、Exchange 組織でユーザー ドメイン アカウントとメールボックスを持つユーザーのことです。
        
          - **\[外部のメール アドレスを持つユーザー\]**   外部の電子メール アドレスを持つユーザーを含める場合は、このチェック ボックスをオンにします。外部の電子メール アカウントを持つユーザーは、Active Directory のユーザー ドメイン アカウントを持っていますが、組織の外部の電子メール アカウントを使用します。これにより、これらのユーザーはグローバル アドレス一覧 (GAL) に含まれ、配布リストに追加されます。
        
          - **\[リソース メールボックス\]**   Exchange リソース メールボックスを含める場合は、このチェック ボックスをオンにします。リソース メールボックスを使用すると、会議室や社用車などの会社のリソースをメールボックスによって管理できます。
        
          - **\[外部のメール アドレスを持つ連絡先\]**   外部の電子メール アドレスを持つ連絡先を含める場合は、このチェック ボックスをオンにします。外部の電子メール アカウントを持つ連絡先は Active Directory のユーザー ドメイン アカウントを持っていませんが、外部の電子メール アドレスは GAL で使用できます。
        
          - **\[メールが有効なグループ\]**   メールが有効になっているセキュリティ グループや配布グループを含める場合は、このチェック ボックスをオンにします。メールが有効なグループは配布グループと同様です。メールが有効なグループ アカウントに送信された電子メール メッセージは、複数の受信者に配信されます。

4.      
    **\[ルールを追加する\]** をクリックして、このグループのメンバーシップの条件を定義します。

5.  ドロップダウン リストから次のいずれかの受信者の属性を選択し、値を指定します。選択した属性の値が定義した値と一致する場合、受信者はこのグループに送信されたメッセージを受信します。
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>属性</th>
    <th>次の場合にメッセージを受信者に送信します...</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>受信者コンテナー</strong></p></td>
    <td><p>受信者オブジェクトが指定されたドメインまたは OU にある場合。</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>都道府県</strong></p></td>
    <td><p>指定された値が受信者の &quot;都道府県&quot; プロパティと一致する場合。</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Company</strong></p></td>
    <td><p>指定された値が受信者の &quot;会社&quot; プロパティと一致する場合。</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>部署</strong></p></td>
    <td><p>指定された値が受信者の &quot;部署&quot; プロパティと一致する場合。</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>カスタム属性 N</strong> (N は 1 ～ 15 の数値)</p></td>
    <td><p>指定された値が受信者の CustomAttributeN プロパティと一致する場合。</p></td>
    </tr>
    </tbody>
    </table>
    

    > [!IMPORTANT]
    > 選択した属性に入力する値は、受信者のプロパティに表示される値と正確に一致している必要があります。たとえば、<STRONG>[都道府県]</STRONG> に「<STRONG>Washington</STRONG>」と入力しても受信者のプロパティが <STRONG>WA</STRONG> である場合、条件が一致しません。また、指定するテキストベースの値では大文字と小文字を区別しません。たとえば、<STRONG>[会社]</STRONG> 属性に <STRONG>Contoso</STRONG> を指定すると、メッセージはこの値が <STRONG>contoso</STRONG> である場合に受信者に送信されます。



6.  **\[単語または語句の指定\]** ウィンドウのテキスト ボックスに値を入力します。**\[追加\]** をクリックし、**\[OK\]** をクリックします。

7.  別のルールを追加してメンバーシップの条件を定義するには、前に作成したルールの下にある **\[ルールを追加する\]** をクリックします。
    

    > [!IMPORTANT]
    > 複数のルールを追加してメンバーシップを定義する場合、受信者はグループに送信されたメッセージを受信するために各ルールの条件に一致している必要があります。つまり、各ルールはブール演算子 <STRONG>AND</STRONG> につながっています。



8.  完了したら、**\[保存\]** をクリックして動的配布グループを作成します。


> [!NOTE]
> EAC で使用できる属性以外の属性に対してルールを指定する場合は、シェルを使用して動的配布グループを作成する必要があります。カスタムの受信者フィルターを使用した動的配布グループのフィルターおよび条件の設定は、シェルでしか管理できないことに注意してください。カスタム クエリで動的配布グループを作成する方法の例については、シェルを使用した動的配布グループの作成に関する次のセクションを参照してください。



## シェルを使用して動的配布グループを作成する

この例では、メールボックス ユーザーのみで構成される動的配布グループ "Mailbox Users DDG" を作成します。

    New-DynamicDistributionGroup -IncludedRecipients MailboxUsers -Name "Mailbox Users DDG" -OrganizationalUnit Users

この例では、カスタムの受信者フィルターを使用して動的配布グループを作成します。この動的配布グループには、Server1 という名前のサーバー上のすべてのメールボックス ユーザーが含まれます。

    New-DynamicDistributionGroup -Name "Mailbox Users on Server1" -OrganizationalUnit Users -RecipientFilter {((RecipientTypeDetails -eq 'UserMailbox' -and ServerName -eq 'Server1'))}

この例では、カスタムの受信者フィルターを使用して動的配布グループを作成します。動的配布グループには、**CustomAttribute10** プロパティの値が "FullTimeEmployee" であるすべてのメールボックス ユーザーが含まれます。

    New-DynamicDistributionGroup -Name "Full Time Employees" -RecipientFilter {(RecipientTypeDetails -eq 'UserMailbox') -and (CustomAttribute10 -eq 'FullTimeEmployee')}

構文およびパラメーターの詳細については、「[New-DynamicDistributionGroup](https://technet.microsoft.com/ja-jp/library/bb125127\(v=exchg.150\))」を参照してください。

## 正常な動作を確認する方法

動的配布グループが正常に作成されたことを確認するには、次のいずれかを実行します。

  - EAC で、**\[受信者\]** \> **\[グループ\]** に移動します。新しい動的配布グループがグループ リストに表示されます。**\[グループの種類\]** の種類は **\[動的配布グループ\]** です。

  - シェルで次のコマンドを実行して、新しい動的配布グループに関する情報を表示します。
    
        Get-DynamicDistributionGroup | FL Name,RecipientTypeDetails,RecipientFilter,PrimarySmtpAddress

## 動的配布グループのプロパティを変更する

## EAC を使用して動的配布グループのプロパティを変更する

1.  EAC で、**\[受信者\]** \> **\[グループ\]** に移動します。

2.  グループ リストで、表示または変更する動的配布グループをクリックし、**\[編集\]**![編集アイコン](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "編集アイコン") をクリックします。

3.  プロパティを表示または変更するには、グループのプロパティのページで以下のセクションをクリックします。
    
      - 全般
    
      - 所有権
    
      - メンバーシップ
    
      - 配信管理
    
      - メッセージの承認
    
      - メール オプション
    
      - メール ヒント
    
      - グループの委任

## 全般

このセクションを使用して、グループに関する基本情報を表示または変更します。

  - **\* \[表示名\]**   この名前は共有アドレス帳、このグループにメールを送信するときの電子メールの宛先行、\[グループ\] 一覧に表示されます。表示名は必須であり、ユーザーが内容を認識できるようにわかりやすい名前にする必要があります。また、表示名は、ドメイン内で一意である必要があります。

  - **\* \[エイリアス\]**   これは、電子メール アドレスの @ 記号の左に表示される名前の部分です。エイリアスを変更すると、グループのプライマリ SMTP アドレスも変更され、新しいエイリアスが含まれます。また、以前のエイリアスが含まれている電子メール アドレスは、グループのプロキシ アドレスとして保持されます。

  - **\[説明\]**   このボックスを使用してグループを説明することにより、ユーザーはこのグループの目的を認識することができます。この説明は、アドレス帳と EAC の \[詳細\] ウィンドウに表示されます。

  - **\[このグループをアドレス一覧に表示しない\]**   このグループがアドレス帳に表示されないようにする場合は、このチェック ボックスをオンにします。電子メールをこのグループに送信するには、送信者は宛先行または CC 行にグループのエイリアスまたは電子メール アドレスを入力する必要があります。

  - **\[組織単位\]**   この読み取り専用のボックスには、動的配布グループが含まれている組織単位 (OU) が表示されます。\[Active Directory ユーザーとコンピューター\] を使用し、別の OU にグループを移動する必要があります。

## 所有権

このセクションを使用して、グループの所有者を割り当てます。動的配布グループに割り当てることができる所有者は 1 人だけです。グループの所有者は \[Active Directory ユーザーとコンピューター\] のオブジェクトの **\[管理者\]** タブに表示されます。

**\[参照\]** をクリックして一覧から所有者を選択すると、所有者を追加できます。所有者を削除するには、**\[クリア\]** をクリックしてから**\[保存\]**![\[削除\] アイコン](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "[削除] アイコン") をクリックします。

## メンバーシップ

このセクションを使用して、グループのメンバーシップの決定に使用する条件を変更します。既存のメンバーシップのルールを削除または変更したり、新しいルールを追加したりすることができます。この作業の手順については、EAC を使用して新しい動的配布グループを作成するときにメンバーシップを構成する手順のEAC を使用して動的配布グループを作成する を参照してください。

## 配信管理

このセクションを使用して、このグループに電子メールを送信できる送信者を管理します。

  - **\[組織内の送信者のみ\]**   組織内の送信者のみがこのグループにメッセージを送信できるようにする場合は、このオプションを選択します。選択すると、組織外のユーザーがこのグループに電子メール メッセージを送信した場合、そのメッセージは拒否されます。これは既定の設定です。

  - **\[組織内および組織外の送信者\]**   グループへのメッセージ送信をすべての人に許可する場合は、このオプションを選択します。
    
    グループにメッセージを送信できるユーザーを制限するには、特定の送信者に対してのみこのグループへのメッセージ送信を許可します。**\[追加\]**![\[追加\] アイコン](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "[追加] アイコン") をクリックして、1 人以上の受信者を選択します。この一覧に送信者を追加すると、グループにメールを送信できるのはその送信者だけになります。一覧にないユーザーから送信されたメールはすべて拒否されます。
    
    一覧からユーザーまたはグループを削除するには、そのユーザーまたはグループを一覧から選択し、**\[削除\]**![\[削除\] アイコン](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "[削除] アイコン") をクリックします。
    

    > [!IMPORTANT]
    > 組織内の送信者のみがグループにメッセージを送信できるようにグループを構成した場合は、メール連絡先をこの一覧に追加しても、その連絡先から送信された電子メールは拒否されます。



## メッセージの承認

このセクションを使用して、グループをモデレートするためのオプションを設定します。モデレーターは、グループに送信されたメッセージがグループ メンバーに配信される前に、そのメッセージを承認または拒否します。

  - **\[このグループに送信されるメッセージにはモデレーターの承認を必要とする\]**   このチェック ボックスは、既定ではオンになっていません。このチェック ボックスをオンにすると、受信メッセージは配信される前にグループ モデレーターによって確認されます。グループ モデレーターは受信メッセージを承認または拒否できます。

  - **\[グループ モデレーター\]**   グループ モデレーターを追加するには、**\[追加\]**![\[追加\] アイコン](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "[追加] アイコン") をクリックします。モデレーターを削除するには、そのモデレーターを選択し、**\[削除\]**![\[削除\] アイコン](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "[削除] アイコン") をクリックします。\[このグループに送信されるメッセージにはモデレーターの承認を必要とする\] チェック ボックスをオンにして、モデレーターを選択していない場合、グループへのメッセージは承認のためにグループ所有者に送信されます。

  - **\[メッセージの承認が不要な送信者\]**    このグループのモデレートを省略できるユーザーまたはグループを追加するには、**\[追加\]**![\[追加\] アイコン](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "[追加] アイコン") をクリックします。ユーザーまたはグループを削除するには、そのユーザーまたはグループを選択して、**\[削除\]**![\[削除\] アイコン](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "[削除] アイコン") をクリックします。

  - **\[モデレート通知の選択\]   **このセクションを使用して、メッセージ承認についてユーザーに通知する方法を設定します。
    
      - **\[メッセージが承認されない場合にすべての送信者に通知する\]**   これは既定の設定です。メッセージが承認されない場合、組織内外を問わずすべての送信者に通知します。
    
      - **\[自分のメッセージが承認されていない場合だけ組織内の送信者に通知する\]**   このオプションを選択すると、グループ宛てに送信したメッセージがモデレーターによって承認されなかった場合、組織内の送信者またはグループにのみ通知が行われます。
    
      - **\[メッセージが承認されない場合、どの送信者にも通知しない\]**   このオプションを選択すると、メッセージがグループ モデレーターに承認されなかった場合、メッセージの送信者に通知は送信されません。

## メール オプション

このセクションを使用して、グループに関連付けられている電子メール アドレスを表示または変更します。これには、グループのプライマリ SMTP アドレスと関連付けられたすべてのプロキシ アドレスが含まれます。プライマリ SMTP アドレス (*返信アドレス*とも呼ばれます) は、アドレス一覧に太字で表示され、**\[種類\]** 列に大文字の **SMTP** 値が表示されます。

  - **\[追加\]**   **\[追加\]**![\[追加\] アイコン](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "[追加] アイコン") をクリックして、このメールボックスの新しい電子メール アドレスを追加します。次のいずれかのアドレスの種類を選択します。
    
      - **\[SMTP\]**   これは既定のアドレスの種類です。このボタンをクリックして、**\* \[電子メール アドレス\]** ボックスに新しい SMTP アドレスを入力します。
        

        > [!NOTE]
        > 新しいアドレスをグループのプライマリ SMTP アドレスにするには、<STRONG>[このアドレスを返信アドレスに設定する]</STRONG> チェック ボックスをオンにします。

    
      - **\[カスタム アドレスの種類\]**   このボタンをクリックして、**\* \[電子メール アドレス\]** ボックスにサポートされている SMTP 以外の電子メール アドレスの種類の 1 つを入力します。
        

        > [!NOTE]
        > X.400 アドレスを除き、Exchange は、カスタム アドレスが適切な形式かどうかを検証しません。指定するカスタム アドレスが、そのアドレスの種類の書式要件に従っていることを確認する必要があります。



  - **\[編集\]**   グループに関連した電子メール アドレスを変更するには、そのアドレスを一覧から選択し、**\[編集\]**![編集アイコン](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "編集アイコン") をクリックします。
    

    > [!NOTE]
    > 既存のアドレスをグループのプライマリ SMTP アドレスにするには、<STRONG>[このアドレスを返信アドレスに設定する]</STRONG> チェック ボックスをオンにします。



  - **\[削除\]**   グループに関連した電子メール アドレスを削除するには、そのアドレスを一覧から選択し、**\[削除\]**![\[削除\] アイコン](images/Dd362328.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "[削除] アイコン") をクリックします。

  - **\[この受信者に適用されるメール アドレス ポリシーに基づいてメール アドレスを自動更新する\]**   組織の電子メール アドレス ポリシーに加えられた変更に基づいて受信者の電子メール アドレスを自動的に更新するには、このチェック ボックスをオンにします。このチェック ボックスは既定でオンになっています。

## メール ヒント

このセクションでは、このグループにメッセージを送信する前に問題が発生する可能性があるユーザーに警告するためのメール ヒントを追加します。メール ヒントは、このグループが新しい電子メール メッセージの \[宛先\]、\[CC\]、または \[BCC\] 行に追加されたときに情報バーに表示されるテキストです。たとえば、大規模なグループにメール ヒントを追加して、メッセージを送信しようとしているユーザーに対して、多数のユーザーにメッセージが送信されることを警告することもできます。


> [!NOTE]
> メール ヒントに HTML タグを入れることはできますが、スクリプトは許可されません。カスタム メール ヒントの長さは 175 文字 を超えることはできません。これは表示文字数で、HTML タグは含まれません。



## グループの委任

このセクションを使用して、アクセス許可をユーザー (*代理人*と呼ばれる) に割り当てて、そのユーザーがグループとしてメッセージを送信したり、グループに代わってメッセージを送信したりできるようにします。次のアクセス許可を割り当てることができます。

  - **\[差出人を指定して送信する\]**   このアクセス許可によって、代理人はグループとしてメッセージを送信できるようになります。このアクセス許可が割り当てられると、代理人はグループを **\[差出人\]** 行に追加し、メッセージがグループによって送信されたことを示すことができます。

  - **\[代理人として送信する\]**   このアクセス許可によって、代理人はグループに代わってメッセージを送信できるようになります。このアクセス許可が割り当てられると、代理人はグループを **\[差出人\]** 行に追加することができるようになります。メッセージは、グループによって送信されたように見えますが、グループに代わって代理人が送信したことがわかるようになっています。

代理人にアクセス許可を割り当てるには、該当するアクセス許可の下にある **\[追加\]** をクリックして **\[受信者の選択\]** ページを表示します。このページに、アクセス許可を割り当てることができる Exchange 組織内のすべての受信者の一覧が表示されます。目的の受信者を選択し、一覧に追加して、**\[OK\]** をクリックします。また、\[検索\] ボックスに受信者の名前を入力し、**\[検索\]** をクリックすることによって、特定の受信者を検索することもできます。

## シェルを使用して動的配布グループのプロパティを変更する

**Get-DynamicDistributionGroup** コマンドレットと **Set-DynamicDistributionGroup** コマンドレットを使用して、動的配布グループのプロパティを表示および変更します。シェルを使用する場合の利点は、EAC で使用できないプロパティを変更できることと複数のグループのプロパティを変更できることです。配布グループのプロパティに対応するパラメーターの詳細については、以下のトピックを参照してください。

  - [Get-DynamicDistributionGroup](https://technet.microsoft.com/ja-jp/library/bb124762\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/ja-jp/library/bb123796\(v=exchg.150\))

ここでは、シェルを使用して動的配布グループのプロパティを変更する例をいくつか示します。

この例では、組織内のすべての動的配布グループの次のパラメーターを変更します。

  - すべての動的配布グループがアドレス帳に表示されないようにする

  - グループに送信できる最大メッセージ サイズを 5MB に設定する

  - モデレートを有効にする

  - 管理者をグループのモデレーターとして割り当てる

<!-- end list -->

    Get-DynamicDistributionGroup -ResultSize unlimited | Set-DynamicDistributionGroup -HiddenFromAddressListsEnabled $true -MaxReceiveSize 5MB -ModerationEnabled $true -ModeratedBy administrator

この例では、プロキシ SMTP 電子メール アドレス Seattle.Employees@contoso.com を All Employees グループに追加します。

    Set-DynamicDistributionGroup -Identity "All Employees" -EmailAddresses SMTP:All.Employees@contoso.com, smtp:Seattle.Employees@contoso.com

## 正常な動作を確認する方法

動的配布グループのプロパティが正常に変更されたことを確認するには、次のいずれかを実行します。

  - EAC でグループを選択して **\[編集\]**![編集アイコン](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "編集アイコン") をクリックし、変更したプロパティまたは機能を表示します。変更したプロパティによっては、選択したグループの \[詳細\] ウィンドウに表示される場合があります。

  - シェルで **Get-DynamicDistributionGroup** コマンドレットを使用して、変更を確認します。シェルを使用する場合の利点の 1 つは、複数のグループの複数のプロパティを表示できることです。最初の例では、次のコマンドを実行して新しい値を確認します。
    
        Get-DynamicDistributionGroup -ResultSize unlimited | fl Name,HiddenFromAddressListsEnabled,MaxReceiveSize,ModerationEnabled,ModeratedBy
    
    メッセージ制限が変更された上記の例では、このコマンドを実行します。
    
        Get-Mailbox -OrganizationalUnit "Marketing" | fl Name,IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults
