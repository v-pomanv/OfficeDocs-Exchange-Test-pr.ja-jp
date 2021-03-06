﻿---
title: 'Exchange 2013 記憶域構成オプション: Exchange 2013 Help'
TOCTitle: Exchange 2013 記憶域構成オプション
ms:assetid: 37cdeacf-74f9-4399-9860-4d1dbec12bb1
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ee832792(v=EXCHG.150)
ms:contentKeyID: 49896200
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2013 記憶域構成オプション

 

_**適用先:** Exchange Online, Exchange Server, Exchange Server 2013_

_**トピックの最終更新日:** 2016-12-09_

Microsoft Exchange Server 2013 におけるメールボックス サーバーの役割の記憶域オプションと要件を理解することは、メールボックス サーバー記憶域設計ソリューションにとって重要な部分です。

**目次**

記憶域アーキテクチャ

物理ディスクの種類

サポート対象記憶域の構成に関するベスト プラクティス

## 記憶域アーキテクチャ

次の表では、サポートされている記憶域アーキテクチャを説明し、それぞれの種類の記憶域アーキテクチャに関するベスト プラクティスの指示を適切な場所に提供します。

### サポートされている記憶域アーキテクチャ

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>記憶域アーキテクチャ</th>
<th>説明</th>
<th>ベスト プラクティス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>直接接続型ストレージ (DAS)</p></td>
<td><p>DAS は、間に記憶域ネットワークを介しない、サーバーまたはワークステーションに直接に接続されたデジタル記憶域システムです。たとえば、DAS トランスポートには Serial Attached SCSI (Small Computer System Interface) および Serial Attached Advanced Technology Attachment (ATA) が含まれます。</p></td>
<td><p>注意事項なし。</p></td>
</tr>
<tr class="even">
<td><p>ストレージ エリア ネットワーク (SAN):iSCSI (Internet Small Computer System Interface)</p></td>
<td><p>SAN は、リモート コンピューターの記憶装置 (ディスク アレイおよびテープ ライブラリなど) を、オペレーティング システムにローカルに接続されたデバイスとして表示されるように、サーバーに接続するアーキテクチャです (たとえば、ブロック ストレージ)。iSCSI SAN は SCSI コマンドを IP パッケージに内包して、標準のネットワーク インフラストラクチャをストレージ トランスポートとして使用します (たとえば、イーサネット)。</p></td>
<td><p>Exchange のデータをバックアップする物理ディスクは、他のアプリケーションと共有しないでください。</p>
<p>専用のストレージ ネットワークを使用します。</p>
<p>スタンドアロン構成に対して複数のネットワーク パスを使用します。</p></td>
</tr>
<tr class="odd">
<td><p>SAN:ファイバー チャネル</p></td>
<td><p>ファイバー チャネル SAN は SCSI コマンドをファイバー チャネル パケットに内包して、通常は専用のファイバー チャネル ネットワークをストレージ トランスポートとして利用します。</p></td>
<td><p>Exchange のデータをバックアップする物理ディスクは、他のアプリケーションと共有しないでください。</p>
<p>スタンドアロン構成に対して複数のファイバー チャネル ネットワーク パスを使用します。</p>
<p>ストレージ ベンダーの、ファイバー チャネル ホスト バス アダプター (HBA) をチューニングするためのベスト プラクティスに従ってください。たとえば、キューの深さおよびキューの対象などです。</p></td>
</tr>
</tbody>
</table>


NAS (ネットワーク接続ストレージ) ユニットは、ネットワークに接続された自己完結型コンピューターで、ネットワークの他のデバイスに対してファイル ベースのデータ ストレージ サービスを提供することだけを目的としています。NAS ユニット上のオペレーティング システムおよび他のソフトウェアは、データ記憶域、ファイル システム、およびファイルへのアクセスの機能ならびに、それらの機能の管理を提供します (たとえば、ファイル ストレージ)。

Exchange データの格納用に Exchange が使用する記憶域はすべてブロックレベルの記憶域であることが必要です。これは、トピック「[Exchange 2013 仮想化](exchange-2013-virtualization-exchange-2013-help.md)」で説明されている SMB 3.0 シナリオ以外では、Exchange 2013 が NAS ボリュームの使用をサポートしないためです。また、仮想化環境では、ハイパーバイザーでブロックレベルのストレージとしてゲストに示される NAS ストレージはサポートされません。

記憶域層の使用は、システムのパフォーマンスに悪影響を与えるためお勧めしません。このため、記憶域コントローラーが「より高速な」記憶域に最もアクセスの多いファイルを自動的に移動できないようにしてください。

記憶域アーキテクチャ

## 物理ディスクの種類

次の表では、サポートされている物理ディスクの種類の一覧と、それぞれの物理ディスクの種類に対してベスト プラクティスの指示を適切な場所に提供します。

### サポートされている物理ディスクの種類

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>物理ディスクの種類</th>
<th>説明</th>
<th>サポートまたはベスト プラクティス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Serial ATA (SATA)</p></td>
<td><p>SATA は、ATA および IDE (Integrated Device Electronics) 用のシリアル インターフェイスです。SATA ディスクは、さまざまなフォーム ファクター、速度、および容量で利用できます。</p>
<p>一般的に、以下の設計要件がある場合には Exchange 2013 メールボックスの記憶域として SATA ディスクを選択します。</p>
<ul>
<li><p>大容量</p></li>
<li><p>中程度のパフォーマンス</p></li>
<li><p>中程度の電源使用率</p></li>
</ul></td>
<td><p>Windows Server 2008 および Windows Server 2008 R2 用の 512 バイト セクターのディスクのみサポートされています。また、以下の条件で Windows Server 2008 R2 では 512e ディスクもサポートされています。</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=982018">Microsoft サポート技術情報の文書番号 982018</a>「Windows 7 および Windows Server 2008 R2 と Advanced Format Disk の互換性を向上させる更新プログラムを入手できます」で説明されている修正プログラム。</p></li>
<li><p>Windows Server 2008 R2 Service Pack 1 (SP1) と Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 以降では、ネイティブの 4 キロバイト (KB) セクター ディスクと 512e ディスクをサポートしています。サポートには、データベースのすべてのコピーが同じ物理ディスク タイプ上にある必要があります。たとえば、あるデータベースの 1 つのコピーが 512 バイト セクターのディスク上にあり、同じデータベースのもう 1 つのコピーが 512e ディスクまたは 4K ディスク上にある場合、その構成はサポートされません。</p>
<p>ベスト プラクティス:熱、振動、および信頼性の点において一般的により良い特性を持つエンタープライズ クラスの SATA ディスクを考慮してください。</p></td>
</tr>
<tr class="even">
<td><p>Serial Attached SCSI</p></td>
<td><p>Serial Attached SCSI は、SCSI ディスク用のシリアル インターフェイスです。Serial Attached SCSI ディスクは、さまざまなフォーム ファクター、速度、および容量で利用できます。</p>
<p>一般的に、以下の設計要件がある場合には Exchange 2013 メールボックスの記憶域として Serial Attached SCSI ディスクを選択します。</p>
<ul>
<li><p>中程度の容量</p></li>
<li><p>高パフォーマンス</p></li>
<li><p>中程度の電源使用率</p></li>
</ul></td>
<td><p>Windows Server 2008 および Windows Server 2008 R2 用の 512 バイト セクターのディスクのみサポートされています。また、以下の条件で Windows Server 2008 R2 では 512e ディスクもサポートされています。</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=982018">Microsoft サポート技術情報の文書番号 982018</a>「Windows 7 および Windows Server 2008 R2 と Advanced Format Disk の互換性を向上させる更新プログラムを入手できます」で説明されている修正プログラム。</p></li>
<li><p>Windows Server 2008 R2 Service Pack 1 (SP1) と Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 以降では、ネイティブの 4 キロバイト (KB) セクター ディスクと 512e ディスクをサポートしています。サポートには、データベースのすべてのコピーが同じ物理ディスク タイプ上にある必要があります。たとえば、あるデータベースの 1 つのコピーが 512 バイト セクターのディスク上にあり、同じデータベースのもう 1 つのコピーが 512e ディスクまたは 4K ディスク上にある場合、その構成はサポートされません。</p>
<p>ベスト プラクティス:UPS なしで使用する場合は、物理的なディスク書き込みキャッシュを無効にする必要があります。</p></td>
</tr>
<tr class="odd">
<td><p>ファイバー チャネル</p></td>
<td><p>ファイバー チャネルは、ディスクをファイバー チャネル ベースの SAN に接続するために使用される電気的インターフェイスです。ファイバー チャネル ディスクは、さまざまな速度と容量で利用できます。</p>
<p>一般的に、以下の設計要件がある場合には Exchange 2013 メールボックスの記憶域としてファイバー チャネル ディスクを選択します。</p>
<ul>
<li><p>中程度の容量</p></li>
<li><p>高パフォーマンス</p></li>
<li><p>SAN 接続</p></li>
</ul></td>
<td><p>Windows Server 2008 および Windows Server 2008 R2 用の 512 バイト セクターのディスクのみサポートされています。また、以下の条件で Windows Server 2008 R2 では 512e ディスクもサポートされています。</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=982018">Microsoft サポート技術情報の文書番号 982018</a>「Windows 7 および Windows Server 2008 R2 と Advanced Format Disk の互換性を向上させる更新プログラムを入手できます」で説明されている修正プログラム。</p></li>
<li><p>Windows Server 2008 R2 Service Pack 1 (SP1) と Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 以降では、ネイティブの 4 キロバイト (KB) セクター ディスクと 512e ディスクをサポートしています。サポートには、データベースのすべてのコピーが同じ物理ディスク タイプ上にある必要があります。たとえば、あるデータベースの 1 つのコピーが 512 バイト セクターのディスク上にあり、同じデータベースのもう 1 つのコピーが 512e ディスクまたは 4K ディスク上にある場合、その構成はサポートされません。</p>
<p>ベスト プラクティス:UPS なしで使用する場合は、物理的なディスク書き込みキャッシュを無効にする必要があります。</p></td>
</tr>
<tr class="even">
<td><p>ソリッド ステート ドライブ (SSD) (フラッシュ ディスク)</p></td>
<td><p>SSD は、永続データを格納するためにソリッド ステート メモリを使用するデータ記憶域デバイスです。SSD はハード ディスク ドライブ インターフェイスをエミュレートします。SSD ディスクは、さまざまな速度 (異なる I/O パフォーマンス機能) と容量で利用できます。</p>
<p>一般的に、以下の設計要件がある場合には Exchange 2013 メールボックスの記憶域として SSD ディスクを選択します。</p>
<ul>
<li><p>低容量</p></li>
<li><p>非常に高いパフォーマンス</p></li>
</ul></td>
<td><p>Windows Server 2008 および Windows Server 2008 R2 用の 512 バイト セクターのディスクのみサポートされています。また、以下の条件で Windows Server 2008 R2 では 512e ディスクもサポートされています。</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=982018">Microsoft サポート技術情報の文書番号 982018</a>「Windows 7 および Windows Server 2008 R2 と Advanced Format Disk の互換性を向上させる更新プログラムを入手できます」で説明されている修正プログラム。</p></li>
<li><p>Windows Server 2008 R2 Service Pack 1 (SP1) と Exchange Server 2010 SP1.</p></li>
</ul>
<p>Exchange 2013 以降では、ネイティブの 4 キロバイト (KB) セクター ディスクと 512e ディスクをサポートしています。サポートには、データベースのすべてのコピーが同じ物理ディスク タイプ上にある必要があります。たとえば、あるデータベースの 1 つのコピーが 512 バイト セクターのディスク上にあり、同じデータベースのもう 1 つのコピーが 512e ディスクまたは 4K ディスク上にある場合、その構成はサポートされません。</p>
<p>ベスト プラクティス:UPS なしで使用する場合は、物理的なディスク書き込みキャッシュを無効にする必要があります。</p>
<p>一般的に、Exchange 2013 メールボックス サーバーは、SSD ストレージのパフォーマンスの特性を必要としません。</p></td>
</tr>
</tbody>
</table>


## ディスクの種類の選択時に考慮する要因

Exchange 2013 ストレージ用のディスクの種類を選択する場合、さまざまなトレードオフがあります。正しいディスクは、パフォーマンス (シーケンシャルおよびランダム) と、容量、信頼性、電源使用率、および資本コストのバランスがとれているものです。次の、サポートされている物理ディスクの種類の表は、それらの要因を考慮に入れる場合に役立つ情報を提供します。

パフォーマンスの観点から、負荷がかかった状態でディスクが 20 ミリ秒以下の読み取りおよび書き込みの平均待ち時間を維持できることを条件として、Exchange の記憶域に大型で低速のディスクを使用しても問題ありません。

### ディスクの種類の選択の要因

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>ディスクの回転速度 (RPM)</th>
<th>ディスクのフォーム ファクター</th>
<th>インターフェイスまたはトランスポート</th>
<th>容量</th>
<th>ランダム I/O パフォーマンス</th>
<th>シーケンシャル I/O パフォーマンス</th>
<th>電源使用率</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5,400</p></td>
<td><p>2.5 インチ</p></td>
<td><p>SATA</p></td>
<td><p>平均</p></td>
<td><p>悪い</p></td>
<td><p>悪い</p></td>
<td><p>優秀</p></td>
</tr>
<tr class="even">
<td><p>5,400</p></td>
<td><p>3.5 インチ</p></td>
<td><p>SATA</p></td>
<td><p>優秀</p></td>
<td><p>悪い</p></td>
<td><p>悪い</p></td>
<td><p>平均以上</p></td>
</tr>
<tr class="odd">
<td><p>7,200</p></td>
<td><p>2.5 インチ</p></td>
<td><p>SATA</p></td>
<td><p>平均</p></td>
<td><p>平均</p></td>
<td><p>平均</p></td>
<td><p>優秀</p></td>
</tr>
<tr class="even">
<td><p>7,200</p></td>
<td><p>2.5 インチ</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>平均</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>優秀</p></td>
</tr>
<tr class="odd">
<td><p>7,200</p></td>
<td><p>3.5 インチ</p></td>
<td><p>SATA</p></td>
<td><p>優秀</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>平均以上</p></td>
</tr>
<tr class="even">
<td><p>7,200</p></td>
<td><p>3.5 インチ</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>優秀</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>平均以上</p></td>
</tr>
<tr class="odd">
<td><p>7,200</p></td>
<td><p>3.5 インチ</p></td>
<td><p>ファイバー チャネル</p></td>
<td><p>優秀</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>平均</p></td>
</tr>
<tr class="even">
<td><p>10,000</p></td>
<td><p>2.5 インチ</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>平均以下</p></td>
<td><p>優秀</p></td>
<td><p>平均以上</p></td>
<td><p>平均以上</p></td>
</tr>
<tr class="odd">
<td><p>10,000</p></td>
<td><p>3.5 インチ</p></td>
<td><p>SATA</p></td>
<td><p>平均</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>平均以上</p></td>
</tr>
<tr class="even">
<td><p>10,000</p></td>
<td><p>3.5 インチ</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>平均以上</p></td>
<td><p>平均以下</p></td>
</tr>
<tr class="odd">
<td><p>10,000</p></td>
<td><p>3.5 インチ</p></td>
<td><p>ファイバー チャネル</p></td>
<td><p>平均</p></td>
<td><p>平均以上</p></td>
<td><p>平均以上</p></td>
<td><p>平均以下</p></td>
</tr>
<tr class="even">
<td><p>15,000</p></td>
<td><p>2.5 インチ</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>悪い</p></td>
<td><p>優秀</p></td>
<td><p>優秀</p></td>
<td><p>平均</p></td>
</tr>
<tr class="odd">
<td><p>15,000</p></td>
<td><p>3.5 インチ</p></td>
<td><p>Serial Attached SCSI</p></td>
<td><p>平均</p></td>
<td><p>優秀</p></td>
<td><p>優秀</p></td>
<td><p>平均以下</p></td>
</tr>
<tr class="even">
<td><p>15,000</p></td>
<td><p>3.5 インチ</p></td>
<td><p>ファイバー チャネル</p></td>
<td><p>平均</p></td>
<td><p>優秀</p></td>
<td><p>優秀</p></td>
<td><p>悪い</p></td>
</tr>
<tr class="odd">
<td><p>SSD:エンタープライズ クラス</p></td>
<td><p>該当なし</p></td>
<td><p>SATA、Serial Attached SCSI、ファイバー チャネル</p></td>
<td><p>悪い</p></td>
<td><p>優秀</p></td>
<td><p>優秀</p></td>
<td><p>優秀</p></td>
</tr>
</tbody>
</table>


記憶域アーキテクチャ

## サポート対象記憶域の構成に関するベスト プラクティス

ここでは、サポートされているディスクとアレイ コントローラーの構成についてベスト プラクティスを提供します。

RAID (Redundant Array of Independent Disks) はしばしば、単体のディスク障害に対する保護を提供するためと、単体ディスクのパフォーマンス属性を改善するため (複数のディスクにわたってデータをストライピングする) の両方に使用されます。Exchange 2013 では、高可用性の強化により、RAID は Exchange 2013 の記憶域の設計にとって必要な要素ではありません。しかし、スタンドアロン サーバーの Exchange 2013 記憶域の設計では、記憶域のフォールト トレランスが必要なソリューションと同様に RAID は今も重要な要素です。

**オペレーティング システム、システム、ページファイル ボリューム**

オペレーティング システム、システム、ページファイル ボリュームの推奨構成は、このデータ型を保護するための RAID テクノロジの使用です。推奨 RAID 構成は、RAID-1 または RAID-1/0 ですが、すべての RAID の種類がサポートされます。

**分離したメールボックス データベースとログ ボリューム**

スタンドアロンのメールボックス サーバーの役割のアーキテクチャを展開している場合、メールボックス データベースおよびログ ボリュームには RAID テクノロジが必要です。メールボックス ボリューム用の推奨 RAID 構成は、RAID-1/0 (特に 5.4K または 7.2K ディスクを使用している場合) ですが、すべての RAID の種類がサポートされます。ログ ボリュームには、RAID-1 または RAID-1/0 が推奨 RAID 構成です。

オペレーティング システム、ページファイル、または Exchange データ ボリューム用に RAID-5 または RAID-6 構成を使用している場合は、以下に注意してください。

  - RAID-50 や RAID-51 などの派生を含む RAID-5 構成でのディスク数は、アレイ グループ、および優先度の高いスクラブとサーフェイス スキャンを有効化したアレイ コントローラーごとに 7 ディスクまでとします。

  - RAID-6 構成は、優先度の高いスクラブおよびサーフェイス スキャンを有効化したアレイ コントローラーを備えるものとします。

JBOD は、3 つ以上の高可用性データベースのコピーを有する高可用性アーキテクチャでサポートされますが、ログおよびメールボックス データベースのボリュームが分離されるため、JBOD はお勧めできません。

**メールボックス データベースおよびログ ボリュームのコロケーション**

メールボックス データベースおよびログ ボリュームのコロケーションは、スタンドアロン アーキテクチャではお勧めできません。高可用性アーキテクチャでは、このシナリオには 2 つの可能性があります。

1.  ボリュームごとに単一のデータベース

2.  ボリュームごとに複数のデータベース

**ボリュームごとに単一のデータベース**

Exchange の観点からは、JBOD の使用は、データベースおよびその関連付けられたログの両方が単一のディスクに格納されることを意味します。JBOD に展開するには、少なくとも 3 つの高可用性データベース コピーを展開する必要があります。単一ディスクの使用は、ディスクに障害が発生するとそのディスク上のデータベース コピーが失われるため、単一障害点となります。最低 3 つのデータベース コピーを持つことにより、1 つのコピー (または 1 つのディスク) で障害が発生した場合に他の 2 つのコピーによってフォールト トレランスが実現されます。ただし、3 つの高可用性データベース コピーの配置は、時間差データベース コピーの使用と同様、ストレージの設計に影響します。以下の表は、RAID または JBOD に関する考慮事項のガイドラインを示します。

### RAID または JBOD に関する考慮事項

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>データセンター サーバー</th>
<th>2 つの高可用性コピー (合計)</th>
<th>3 つの高可用性コピー (合計)</th>
<th>データ センターごとに 2 つ以上の高可用性コピー</th>
<th>1 つの時間差コピー</th>
<th>データ センターごとに 2 つ以上の時間差コピー</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>プライマリ データセンター サーバー</p></td>
<td><p>RAID</p></td>
<td><p>RAID または JBOD (2 つのコピー)</p></td>
<td><p>RAID または JBOD</p></td>
<td><p>RAID</p></td>
<td><p>RAID または JBOD</p></td>
</tr>
<tr class="even">
<td><p>セカンダリ データセンター サーバー</p></td>
<td><p>RAID</p></td>
<td><p>RAID (1 つのコピー)</p></td>
<td><p>RAID または JBOD</p></td>
<td><p>RAID</p></td>
<td><p>RAID または JBOD</p></td>
</tr>
</tbody>
</table>


プライマリ データセンター サーバーで JBOD 上に展開するには、DAG 内に 3 つ以上の高可用性データベース コピーが必要です。高可用性データベース コピーをホストしているサーバーと同じサーバー上で時間差コピーを混在させる場合 (たとえば、専用の時間差データベース コピー サーバーを使用しない場合) には、少なくとも 2 つの時間差データベース コピーが必要になります。

セカンダリ データセンター サーバーで JBOD を使用するには、セカンダリ データセンターに少なくとも 2 つの高可用性データベース コピーが必要です。セカンダリ データセンターのコピーを失っても、WAN を通じて再シードする必要が生じたり、セカンダリ データセンターをアクティブ化する場合に単一障害点になったりすることはありません。高可用性データベース コピーをホストしているサーバーと同じサーバー上で時間差データベース コピーを混在させる場合 (たとえば、専用の時間差データベース コピー サーバーを使用しない場合) には、少なくとも 2 つの時間差データベース コピーが必要になります。

専用の時間差データベース コピー サーバーでは、JBOD を使用するためにデータセンター内に少なくとも 2 つの時間差データベース コピーが必要です。データベース コピーが足りない場合、ディスクの障害により時間差データベース コピーおよび保護メカニズムが失われます。

**ボリュームごとに複数のデータベース**

ボリュームごとに複数のデータベースとは、新しい JBOD シナリオであり、単一のディスクで混在できるアクティブおよびパッシブのコピー (時間差データベース コピーを含む) を許可する Exchange 2013 で使用可能で、ディスクの使用率向上を実現します。ただし、この手法で時間差データベース コピーを展開するには、自動の時間差データベース コピーのログ ファイルを無視する、を有効にする必要があります。次の表は、ボリュームごとの複数のデータベースの JBOD を検討するためのガイドラインを示します。

### JBOD の考慮事項

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>データセンター サーバー</th>
<th>3 つ以上のコピー (合計)</th>
<th>データ センターごとに 2 つ以上のコピー</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>プライマリ データセンター サーバー</p></td>
<td><p>JBOD</p></td>
<td><p>JBOD</p></td>
</tr>
<tr class="even">
<td><p>セカンダリ データセンター サーバー</p></td>
<td><p>該当なし</p></td>
<td><p>JBOD</p></td>
</tr>
</tbody>
</table>


次の表は、Exchange 2013 用のストレージ アレイ構成に関するガイドを提供します。

### Exchange 2013 のメールボックス サーバーの役割でサポートされている RAID の種類

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>RAID の種類</th>
<th>説明</th>
<th>サポートまたはベスト プラクティス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ディスク アレイの RAID ストライプ サイズ (KB)</p></td>
<td><p>ストライプ サイズは、RAID セット内におけるディスクあたりのデータ分布の単位です。ストライプ サイズは<em>ブロック サイズ</em>とも呼ばれます。</p></td>
<td><p>ベスト プラクティス:256 KB 以上。ストレージ ベンダーのベスト プラクティスに従ってください。</p></td>
</tr>
<tr class="even">
<td><p>ストレージ アレイのキャッシュ設定</p></td>
<td><p>キャッシュ設定は、バッテリでバックアップされたキャッシュ アレイ コント ローラーによって提供されます。</p></td>
<td><p>ベスト プラクティス:RAID または JBOD 構成の DAS ストレージ コントローラーの場合は 100% の書き込みキャッシュ (バッテリーまたはフラッシュ バック付きキャッシュ)。SAN などの他の種類のストレージ ソリューションの場合は 75% の書き込みキャッシュと 25% の読み取りキャッシュ (バッテリーまたはフラッシュ バック付きキャッシュ)。SAN ベンダーが自社のプラットフォーム上のキャッシュ構成に関する別のベスト プラクティスを公開している場合は、SAN ベンダーの指示に従ってください。</p></td>
</tr>
<tr class="odd">
<td><p>物理ディスク書き込みキャッシュ</p></td>
<td><p>キャッシュの設定は、個々のディスクそれぞれです。</p></td>
<td><p>サポート:UPS なしで使用する場合は、物理的なディスク書き込みキャッシュを無効にする必要があります。</p></td>
</tr>
</tbody>
</table>


次の表では、データベースおよびログ ファイルの選択についてのガイドを提供します。

### Exchange 2013 メールボックス サーバーの役割の、データベースとログ ファイルの選択

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>データベースとログ ファイルのオプション</th>
<th>説明</th>
<th>スタンドアロン:サポートまたはベスト プラクティス</th>
<th>高可用性:サポートまたはベスト プラクティス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ファイルの配置:ログの独立性あたりのデータベース</p></td>
<td><p>ログの独立性あたりのデータベースは、データベース ファイルとログを同じメールボックス データベースから、異なる物理ディスクからなる異なるボリュームに配置することを意味します。</p></td>
<td><p>ベスト プラクティス:回復性のため、データベース (.edb) ファイルおよびログを同じデータベースから、異なる物理ディスクからなる異なるボリュームに移動します。</p></td>
<td><p>サポート:ログとデータベースの独立性は必要ありません。</p></td>
</tr>
<tr class="even">
<td><p>ファイルの配置:ボリュームあたりのデータベース ファイル</p></td>
<td><p>ボリュームあたりのデータベース ファイルは、ディスク ボリューム内またはディスク ボリュームにまたがってデータベース ファイルを分散させる方法を意味します。</p></td>
<td><p>ベスト プラクティス:バックアップの方法を基にします。</p></td>
<td><p>サポート:JBDO を使用している場合は、データベースとログ ファイル用の別々のディレクトリを含む単一のボリュームを作成します。</p></td>
</tr>
<tr class="odd">
<td><p>ファイルの配置:ボリュームあたりのログ ストリーム</p></td>
<td><p>ボリュームあたりのログ ストリームは、ディスク ボリューム内またはディスク ボリュームにまたがってデータベース ファイルを分散させる方法を意味します。</p></td>
<td><p>ベスト プラクティス:バックアップの方法を基にします。</p></td>
<td><p>サポート:JBDO を使用している場合は、データベースとログ ファイル用の別々のディレクトリを含む単一のボリュームを作成します。</p>
<p>ベスト プラクティス:JBOD を使用している場合は、各ボリュームで複数のデータベースを活用します。</p></td>
</tr>
<tr class="even">
<td><p>データベースのサイズ</p></td>
<td><p>データベースのサイズとは、ディスク データベース (.edb) ファイルのサイズを意味します。</p></td>
<td><p>サポート:約 16 TB。</p>
<p>ベスト プラクティス:</p>
<ul>
<li><p>200 GB (ギガバイト) 以下。</p></li>
<li><p>計算された最大データベース サイズの 120% を準備。</p></li>
</ul></td>
<td><p>サポート:約 16 TB。</p>
<p>ベスト プラクティス:</p>
<ul>
<li><p>2 TB 以下。</p></li>
<li><p>計算された最大データベース サイズの 120% を準備。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>ログの切り詰め方法</p></td>
<td><p>ログの切り詰め方法とは、古いデータベースのログ ファイルの切り詰めと削除のプロセスです。次の 2 つのメカニズムがあります。</p>
<ul>
<li><p>循環ログ。Exchange がログを削除します。</p></li>
<li><p>ログの切り詰め。完全または増分のボリューム シャドウ コピー サービス (VSS) バックアップが正常終了した後に発生します。</p></li>
</ul></td>
<td><p>ベスト プラクティス:</p>
<ul>
<li><p>ログの切り詰めにはバックアップ ログを使用します (たとえば、循環ログが無効)。</p></li>
<li><p>3 日間分のログ生成の容量を準備します。</p></li>
</ul></td>
<td><p>ベスト プラクティス:</p>
<ul>
<li><p>Exchange のネイティブ データ保護機能を使用する展開では、循環ログを有効にします。</p></li>
<li><p>ログ生成容量の再生の時間差を 3 日間超える分を準備します。</p></li>
</ul></td>
</tr>
</tbody>
</table>


次の表では、Windows のディスクの種類に関するガイドを提供します。

### Exchange 2013 メールボックス サーバーの役割用の Windows ディスクの種類

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows ディスクの種類</th>
<th>説明</th>
<th>スタンドアロン:サポートまたはベスト プラクティス</th>
<th>高可用性:サポートまたはベスト プラクティス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ベーシック ディスク</p></td>
<td><p>基本記憶域用に初期化されたディスクをベーシック ディスクと呼びます。ベーシック ディスクには、プライマリ パーティション、拡張パーティション、論理ドライブなどのベーシック ボリュームが含まれます。</p></td>
<td><p>サポートされています。</p>
<p>ベスト プラクティス:ベーシック ディスクを使用します。</p></td>
<td><p>サポートされています。</p>
<p>ベスト プラクティス:ベーシック ディスクを使用します。</p></td>
</tr>
<tr class="even">
<td><p>ダイナミック ディスク</p></td>
<td><p>動的記憶域用に初期化されたディスクをダイナミック ディスクと呼びます。ダイナミック ディスクには、シンプル ボリューム、スパン ボリューム、ストライプ ボリューム、ミラー ボリューム、RAID-5 ボリュームなどのダイナミック ボリュームが含まれます。</p></td>
<td><p>サポートされています。</p></td>
<td><p>サポートされています。</p></td>
</tr>
</tbody>
</table>


次の表では、ボリューム構成のガイドを提供します。

### Exchange 2013 メールボックス サーバーの役割用のボリューム構成

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>ボリューム構成</th>
<th>説明</th>
<th>スタンドアロン:サポートまたはベスト プラクティス</th>
<th>高可用性:サポートまたはベスト プラクティス</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>GUID パーティション テーブル (GPT)</p></td>
<td><p>GPT は、古いマスター ブート レコード (MBR) のパーティション分割のスキーマを拡張するディスク アーキテクチャです。NTFS でフォーマットされたパーティションの最大サイズは 256 TB です。</p></td>
<td><p>サポートされています。</p>
<p>ベスト プラクティス:GPT パーティションを使用します。</p></td>
<td><p>サポートされています。</p>
<p>ベスト プラクティス:GPT パーティションを使用します。</p></td>
</tr>
<tr class="even">
<td><p>MBR</p></td>
<td><p>MBR (パーティション セクター) は 512 バイトのブート セクターで、ハード ディスクなどのパーティション分割された記憶装置の最初のセクター (LBA Sector 0) です。NTFS でフォーマットされたパーティションの最大サイズは 2 TB です。</p></td>
<td><p>サポートされています。</p></td>
<td><p>サポートされています。</p></td>
</tr>
<tr class="odd">
<td><p>パーティションの配置</p></td>
<td><p>パーティションの配置とは、最適なパフォーマンスのためにセクター境界にパーティションを配置することを意味します。</p></td>
<td><p>サポート:Windows Server 2008 R2 と Windows Server 2012 の既定値は 1 メガバイト (MB) です。</p></td>
<td><p>サポート:Windows Server 2008 R2 と Windows Server 2012 の既定値は 1 MB です。</p></td>
</tr>
<tr class="even">
<td><p>ボリューム パス</p></td>
<td><p>ボリューム パスは、ボリュームのアクセス方法を意味します。</p></td>
<td><p>サポート:ドライブ文字またはマウント ポイント。</p>
<p>ベスト プラクティス:マウント ポイントのホスト ボリュームは RAID が有効になっている必要があります。</p></td>
<td><p>サポート:ドライブ文字またはマウント ポイント。</p>
<p>ベスト プラクティス:マウント ポイントのホスト ボリュームは RAID が有効になっている必要があります。</p></td>
</tr>
<tr class="odd">
<td><p>ファイル システム</p></td>
<td><p>ファイル システムはコンピューターのファイルを格納して整理する方法で、ファイルが格納しているデータの検索とファイルへのアクセスを容易にします。</p></td>
<td><p>サポート:NTFS および ReFS。</p></td>
<td><p>サポート:NTFS および ReFS。</p></td>
</tr>
<tr class="even">
<td><p>NTFS の最適化</p></td>
<td><p>NTFS の最適化は、Windows ファイル システムの断片化の量を減らす処理です。これは、ディスクの内容を物理的に整理して、各ファイルの欠片を近くにまとめて連続的になるように格納することで実現します。</p></td>
<td><p>サポートされています。</p>
<p>ベスト プラクティス:必要ではないし推奨しません。Windows Server 2012 では、自動ディスク最適化およびデフラグ機能を無効にすることもお勧めします。</p></td>
<td><p>サポートされています。</p>
<p>ベスト プラクティス:必要ではないし推奨しません。Windows Server 2012 では、自動ディスク最適化およびデフラグ機能を無効にすることもお勧めします。</p></td>
</tr>
<tr class="odd">
<td><p>NTFS アロケーション ユニット サイズ</p></td>
<td><p>NTFS アロケーション ユニット サイズは、ファイルを保持するために割り当てることができるディスク領域の最小量を表します。</p></td>
<td><p>サポート:すべてのアロケーション ユニット サイズ。</p>
<p>ベスト プラクティス:.edb ファイルとログ ファイル ボリュームの両方に 64 KB。</p></td>
<td><p>サポート:すべてのアロケーション ユニット サイズ。</p>
<p>ベスト プラクティス:.edb ファイルとログ ファイル ボリュームの両方に 64 KB。</p></td>
</tr>
<tr class="even">
<td><p>NTFS 圧縮</p></td>
<td><p>NTFS 圧縮は、ハード ディスクに格納されるファイルの実際のサイズを減らす処理です。</p></td>
<td><p>サポート:Exchange データベースまたはログ ファイルはサポートしていません。</p></td>
<td><p>サポート:Exchange データベースまたはログ ファイルはサポートしていません。</p></td>
</tr>
<tr class="odd">
<td><p>NTFS 暗号化ファイル システム (EFS)</p></td>
<td><p>EFS では、個々のファイル、フォルダー、またはデータ ドライブ全体をユーザーが暗号化できます。EFS は業界標準のアルゴリズムと公開キー暗号を介した強力な暗号化を提供するため、攻撃者がシステム セキュリティをバイパスした場合でも暗号化されたファイルの機密性は維持されます。</p></td>
<td><p>サポート:Exchange データベースまたはログ ファイルはサポートしていません。</p></td>
<td><p>Exchange データベースまたはログ ファイルはサポートしていません。</p></td>
</tr>
<tr class="even">
<td><p>Windows BitLocker (ボリューム暗号化)</p></td>
<td><p>Windows BitLocker は、Windows Server 2008 のデータ保護機能です。BitLocker は、紛失したり盗難にあったコンピューターからデータが盗まれたり漏えいしたりしないように保護し、コンピューターを使用停止するときに、より安全にデータを削除できるようにします。</p></td>
<td><p>サポート:すべての Exchange データベースとログ ファイル。</p></td>
<td><p>サポート:すべての Exchange データベースとログ ファイル。Windows フェールオーバー クラスターには Windows Server 2008 R2 または Windows Server 2008 R2 SP1 および以下の修正プログラムが必要:「<a href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=2446607">コンピューターがフェールオーバー クラスター ノードの場合、Windows Server 2008 R2 のディスク ボリュームで BitLocker を有効にできません</a>」が必要です。以前のバージョンの Windows を実行している Windows フェールオーバー クラスターでは、BitLocker が有効な Exchange ボリュームをサポートしません。</p>
<p>Windows 7 BitLocker 暗号化の詳細については、「<a href="https://go.microsoft.com/fwlink/p/?linkid=220898">Windows 7 の BitLocker ドライブの暗号化:よく寄せられる質問</a>」をご覧ください。</p></td>
</tr>
<tr class="odd">
<td><p>サーバー メッセージ ブロック (SMB) 3.0</p></td>
<td><p>サーバー メッセージ ブロック (SMB) プロトコルは、(TCP/IP や他のネットワーク プロトコル上の) ネットワーク ファイル共有プロトコルであり、コンピューター上のアプリケーションでリモート サーバー上のファイルやリソースにアクセスするためのプロトコルです。またサーバー メッセージ ブロック (SMB) プロトコルにより、SMB クライアント要求を受信する構成にしたサーバー プログラムともアプリケーションで通信できます。Windows Server 2012 では、以下の機能を備えた 3.0 バージョンの新しい SMB プロトコルを導入しました。</p>
<ul>
<li><p>SMB 透過フェールオーバー</p></li>
<li><p>SMB スケールアウト</p></li>
<li><p>SMB マルチチャネル</p></li>
<li><p>SMB ダイレクト</p></li>
<li><p>SMB 暗号化</p></li>
<li><p>SMB ファイル共有のための VSS</p></li>
<li><p>SMB ディレクトリ リース</p></li>
<li><p>SMB PowerShell</p></li>
</ul></td>
<td><p>限定サポート。サポート対象シナリオは、SMB 3.0 共有の VHD でディスクをホストするハードウェア仮想化展開です。これらの VHD を、ホストはハイパーバイザーで認識します。詳細については、「<a href="exchange-2013-virtualization-exchange-2013-help.md">Exchange 2013 仮想化</a>」を参照してください。</p></td>
<td><p>限定サポート。サポート対象シナリオは、SMB 3.0 共有の VHD でディスクをホストするハードウェア仮想化展開です。これらの VHD を、ホストはハイパーバイザーで認識します。詳細については、「<a href="exchange-2013-virtualization-exchange-2013-help.md">Exchange 2013 仮想化</a>」を参照してください。</p></td>
</tr>
<tr class="even">
<td><p>記憶域スペース</p></td>
<td><p>記憶域スペースは、Windows Server 2012 に仮想化機能を提供する新しいストレージ ソリューションです。記憶域スペースにより、物理ディスクをストレージ プールに編成できるほか、ディスクを追加するだけで容易に拡張できます。これらのディスクは USB、SATA、SAS のいずれかを通して接続できます。記憶域スペースは、シン プロビジョニングや基礎となる物理メディアの故障に対する回復性といった強力な機能を備え、物理ディスクと同じように機能する仮想ディスク (スペース) も利用します。詳細については、「<a href="https://technet.microsoft.com/ja-jp/library/hh831739.aspx">記憶域スペースの概要</a>」をご覧ください。</p></td>
<td><p>サポートされています。このトピックに記載されている物理ディスク タイプと同じ制限。</p></td>
<td><p>サポートされています。このトピックに記載されている物理ディスク タイプと同じ制限。</p></td>
</tr>
<tr class="odd">
<td><p>Resilient File System (ReFS)</p></td>
<td><p>ReFS は、NTFS の基礎の上に構築された、Windows Server 2012 用に新しく設計されたファイル システムです。ReFS では NTFS との高度な互換性を維持しながら、強化されたデータの検証および自動修正テクニック、また特に記憶域スペース機能と一緒に使用された場合の破損に対する統合されたエンドツーエンドの回復性を提供します。ReFS の詳細については、「<a href="https://technet.microsoft.com/ja-jp/library/hh831724.aspx">Resilient File System の概要</a>」をご覧ください。</p></td>
<td><p>Exchange データベース ファイル、ログ ファイル、およびコンテンツのインデックス処理ファイルを含むボリュームでサポートされます。Windows Server 2012 に展開する場合は、次の修正プログラムが Windows Server 2012 にインストールされていることを確認します。</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717874">Windows 8 および Windows Server 2012 の更新プログラムのロールアップ (2013 年 4 月)</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717877">仮想ディスク サービスまたは仮想ディスク サービスを使用するアプリケーションが、Windows Server 2012 でクラッシュするかフリーズする。</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717879">参照ボリュームの 'dir' コマンドを実行すると、Windows 8 または Windows Server 2012 ベースのコンピューターがフリーズします</a></p></li>
</ul>
<p>ReFS は OS ボリュームではサポートされません。</p>
<p>ベスト プラクティス: データ整合性機能は、Exchange データベース (.edb) ファイルまたはこれらのファイルをホストするボリュームに対して無効にする必要があります。</p></td>
<td><p>Exchange データベース ファイル、ログ ファイル、およびコンテンツのインデックス処理ファイルを含むボリュームでサポートされます。Windows Server 2012 に展開する場合は、次の修正プログラムが Windows Server 2012 にインストールされていることを確認します。</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717874">Windows 8 および Windows Server 2012 の更新プログラムのロールアップ (2013 年 4 月)</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717877">仮想ディスク サービスまたは仮想ディスク サービスを使用するアプリケーションが、Windows Server 2012 でクラッシュするかフリーズする。</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=717879">参照ボリュームの 'dir' コマンドを実行すると、Windows 8 または Windows Server 2012 ベースのコンピューターがフリーズします</a></p></li>
</ul>
<p>ReFS は OS ボリュームではサポートされません。</p>
<p>ベスト プラクティス: データ整合性機能は、Exchange データベース (.edb) ファイルまたはこれらのファイルをホストするボリュームに対して無効にする必要があります。</p></td>
</tr>
<tr class="even">
<td><p>データ重複除去</p></td>
<td><p>データ重複除去は Windows Server 2012 の記憶域使用を最適化する新しいテクニックです。これはデータの再現性や整合性を損なうことなく重複を発見して除去する方法です。この目的は、ファイルを小さな可変サイズのチャンクに分割して、重複チャンクを特定し、各チャンクの単一コピーを維持することによって、より少ないスペースにより多くのデータを保存することです。チャンクの重複コピーは単一コピーへの参照に置き換えられ、チャンクはコンテナー ファイルにまとめられ、コンテナーはさらにスペースを最適化するために圧縮されます。</p></td>
<td><p>Exchange データベース ファイルに対するサポートなし。メモ:完全にオフラインの Exchange データベース ファイル (バックアップやアーカイブ用) に対して使用できます。</p></td>
<td><p>Exchange データベース ファイルに対するサポートなし。メモ:完全にオフラインの Exchange データベース ファイル (バックアップやアーカイブ用) に対して使用できます。</p></td>
</tr>
</tbody>
</table>


記憶域アーキテクチャ

