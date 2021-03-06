﻿---
title: 'チェックリスト: Exchange 2007 UM から Exchange 2013 UM へのアップグレード: Exchange 2013 Help'
TOCTitle: 'チェックリスト: Exchange 2007 UM から Exchange 2013 UM へのアップグレード'
ms:assetid: 99b1a081-4052-4516-b63c-77622cbdf962
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn169229(v=EXCHG.150)
ms:contentKeyID: 54652979
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# チェックリスト: Exchange 2007 UM から Exchange 2013 UM へのアップグレード

 

_**適用先:** Exchange Server 2013, Exchange Server 2016_

_**トピックの最終更新日:** 2016-12-09_

このチェックリストは、Exchange 2007 ユニファイド メッセージング (UM) から Exchange 2013 UM へのアップグレードに役立ちます。Exchange 2007 組織と UM 展開を Exchange 2013 にアップグレードする際に、必ずこの情報を参照してください。Exchange 2013 UM にアップグレードする詳細な手順については、「[Exchange 2007 UM から Exchange 2013 UM へのアップグレード](upgrade-exchange-2007-um-to-exchange-2013-um-exchange-2013-help.md)」を参照してください。

このチェックリストを使用して作業を開始する前に、次のトピックで説明されている概念を理解している必要があります。

  - [ユニファイド メッセージングの計画](planning-for-unified-messaging-exchange-2013-help.md)

  - [電話システムの UM との統合](https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/telephone-system-integration-with-um)

  - [電話ネットワークへのボイス メール システムの接続](https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/connect-voice-mail-system/connect-voice-mail-system)

Exchange 2010 UM から Exchange 2013 UM にアップグレードする方法の詳細な手順については、「[チェックリスト: Exchange 2010 UM から Exchange 2013 UM へのアップグレード](checklist-upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md)」を参照してください。

## Exchange 2007 UM から Exchange 2013 UM へのアップグレード用チェックリスト


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>完了?</th>
<th>タスク</th>
<th>トピック</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>テレフォニー コンポーネントを展開して構成する</p></td>
<td><p><a href="connect-um-to-your-telephone-system-exchange-2013-help.md">UM を電話システムに接続する</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Exchange 2013 をインストールする前に、システム要件を確認する</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 のシステム要件</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>インストールの前提条件を満たしていることを確認する</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Exchange 2013 の前提条件</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>必要なクライアント アクセス サーバーとメールボックス サーバーをインストールする</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">セットアップ ウィザードを使用した Exchange 2013 のインストール</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>インストールを確認し、サーバーのセットアップ ログを確認する</p></td>
<td><p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Exchange 2013 のインストールの確認</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>必要に応じて、UM 言語パックをインストールする</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">UM 言語パックをインストールする</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>ダイヤル プランと自動応答カスタム プロンプトをインポートする</p></td>
<td><p><a href="import-custom-prompts-from-exchange-2007-to-exchange-2013-exchange-2013-help.md">Exchange 2007 のカスタム音声ガイダンスを Exchange 2013 にインポートする</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>証明書のエクスポートとインポートを実行する</p></td>
<td><p><a href="deploying-certificates-for-um-exchange-2013-help.md">UM の証明書の展開</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>すべての Exchange 2013 クライアント アクセス サーバーの UM スタートアップ モードを構成する</p></td>
<td><p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">クライアント アクセス サーバーのスタートアップ モードを構成する</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>すべての Exchange 2013 メールボックス サーバーの UM スタートアップ モードを構成する</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">メールボックス サーバーのスタートアップ モードを構成する</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>UM ダイヤル プランを作成するか、既存の UM ダイヤル プランを構成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan">UM ダイヤル プランを作成する</a></p>
<p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/connect-voice-mail-system/manage-um-dial-plan">UM ダイヤル プランの管理</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>UM IP ゲートウェイを作成するか、既存の UM IP ゲートウェイを構成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway">UM IP ゲートウェイを作成する</a></p>
<p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/connect-voice-mail-system/manage-um-ip-gateway">UM IP ゲートウェイの管理</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>UM ハント グループを作成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-hunt-group">UM ハント グループを作成する</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>UM 自動応答を作成または構成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant">UM 自動応答を作成する</a></p>
<p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/manage-um-auto-attendant">UM 自動応答の管理</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>UM メールボックス ポリシーを作成または構成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy">UM メールボックス ポリシーの作成</a></p>
<p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/set-up-voice-mail/manage-um-mailbox-policy">UM メールボックス ポリシーの管理</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>既存の UM が有効なメールボックスを Exchange 2013 に移動する</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Exchange 2013 でのメールボックスの移動</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>新規ユーザーで UM を有効にするか、既存の UM が有効なユーザーの設定を構成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail">ボイス メール用にユーザーを有効にする</a></p>
<p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/set-up-voice-mail/manage-voice-mail-settings">ユーザーのボイス メール設定の管理</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>すべての着信呼び出しを Exchange 2013 クライアント アクセス サーバーに送信するよう、VoIP ゲートウェイ、IP PBX および SIP 対応 PBX を構成する</p></td>
<td><p><a href="https://docs.microsoft.com/ja-jp/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-voip-gateways">サポートされる VoIP ゲートウェイ、IP Pbx、および PBX の構成に関する注意事項</a></p>
<p><a href="connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md">VoIP ゲートウェイ、IP PBX、またはセッション ボーダー コント ローラーを UM に接続する</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Exchange 2007 UM サーバー上の通話応答を無効にする</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=296353">Exchange 2007 でユニファイド メッセージングを無効にする方法 (無効の場合があります)</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>ダイヤル プランから Exchange 2007 UM サーバーを削除する</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/?linkid=194765">ダイヤル プランからユニファイド メッセージング サーバーを削除する方法</a></p></td>
</tr>
</tbody>
</table>

