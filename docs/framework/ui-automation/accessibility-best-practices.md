---
title: ユーザー補助のベスト プラクティス
description: .NET でのユーザー補助のベストプラクティスについて説明します。 プログラムによるアクセス、ユーザー設定、ビジュアル UI デザイン、ナビゲーション、およびマルチモーダルインターフェイスについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 30961c83bdacf816856205322ac2b627d0f2594c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235689"
---
# <a name="accessibility-best-practices"></a>ユーザー補助のベストプラクティス

> [!NOTE]
> この記事は、名前空間で定義されているマネージ UI オートメーションクラスを使用する .NET Framework 開発者を対象としてい <xref:System.Windows.Automation> ます。 UI オートメーションの最新情報については、「 [Windows AUTOMATION API: Ui オートメーション](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。  
  
 コントロールまたはアプリケーションに次のベストプラクティスを実装すると、支援技術デバイスを使用するユーザーのアクセシビリティが向上します。 これらのベストプラクティスの多くは、適切なユーザーインターフェイス (UI) 設計に焦点を当てています。 各ベストプラクティスには、Windows Presentation Foundation (WPF) コントロールまたはアプリケーションの実装情報が含まれています。 多くの場合、これらのベストプラクティスを満たすための作業は、WPF コントロールに既に含まれています。  
  
<a name="Programmatic_Access"></a>

## <a name="programmatic-access"></a>プログラムによるアクセス  

 プログラムによるアクセスでは、すべての UI 要素にラベルが付けられ、プロパティ値が公開され、適切なイベントが発生することを確認する必要があります。 標準の WPF コントロールでは、この作業のほとんどは既にによって行われてい <xref:System.Windows.Automation.Peers.AutomationPeer> ます。 カスタム コントロールでは、プログラムによるアクセスが正しく実装されていることを確認する必要があります。  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>

### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>すべての UI 要素とテキストでのプログラムによるアクセスの有効化  

 ユーザーインターフェイス (UI) 要素では、プログラムによるアクセスを有効にする必要があります。 UI が標準の WPF コントロールである場合は、プログラムによるアクセスのサポートがコントロールに含まれます。 コントロールがカスタム コントロール (コモン コントロールのサブクラスに指定されているコントロール、またはコントロールからサブクラスに指定されたコントロール) である場合、変更が必要な領域に対する <xref:System.Windows.Automation.Peers.AutomationPeer> の実装を確認する必要があります。  
  
 このベストプラクティスに従うことで、支援技術ベンダーは、製品の UI の要素を特定および操作できます。  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>

### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>UI オブジェクト、フレーム、およびページにおける、場所の名前、タイトル、説明  

 スクリーン リーダーなどの支援のテクノロジでは、ナビゲーション スキーム内のフレーム、オブジェクト、またはページの場所を理解するためにタイトルを使用します。 そのため、タイトルはわかりやすい名前にする必要があります。 たとえば、「Microsoft Web ページ」といった Web ページのタイトルでは、ユーザーはいくつかの特定の領域に深く入っていった場合に役に立ちません。 わかりやすいタイトルは、スクリーン リーダーに依存する視覚障がい者にとって重要です。 同様に、WPF コントロールで <xref:System.Windows.Automation.AutomationProperties.NameProperty> は、と <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> は支援技術デバイスにとって重要です。  
  
 このベストプラクティスに従うことで、ユーザー補助テクノロジによって、サンプルコントロールとアプリケーションの UI を識別および操作できるようになります。  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>

### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>プログラムによるイベントが、すべての UI 操作によってトリガーされることを確認する  

 このベストプラクティスに従うことで、ユーザーに UI の変更をリッスンし、これらの変更についてユーザーに通知することができます。  
  
<a name="User_Settings"></a>

## <a name="user-settings"></a>ユーザー設定  

 このセクションのベスト プラクティスでは、コントロールやアプリケーションはユーザー設定をオーバーライドしないようにします。  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>

### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>すべてのシステム全体の設定を尊重し、ユーザー補助機能に干渉しない  

 ユーザーは、コントロール パネルを使用して、システム全体のフラグを設定できます。その他のフラグはプログラムで設定できます。 これらの設定は、コントロールやアプリケーションで変更しないでください。 また、アプリケーションは、ホスト オペレーティング システムのユーザー補助の設定をサポートする必要があります。  
  
 このベスト プラクティスに従うことにより、ユーザーはユーザー補助の設定を行えるとともに、これらの設定がアプリケーションによって変更されないことを認識できます。  
  
<a name="Visual_UI_Design"></a>

## <a name="visual-ui-design"></a>UI のビジュアル デザイン  

 このセクションのベストプラクティスでは、コントロールまたはアプリケーションが色とイメージを効果的に使用し、支援技術によって使用できることを確認します。  
  
<a name="Don_t_Hard_Code_Colors"></a>

### <a name="dont-hard-code-colors"></a>色をハードコーディングしない  

 色覚に障がいがあるユーザー、弱視のユーザー、または白黒の画面を使用するユーザーは、ハード コーディングされた色を持つアプリケーションを使用できません。  
  
 このベスト プラクティスに従うことにより、ユーザーは、個人のニーズに基づいて色の組み合わせを調整できるようになります。  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>

### <a name="support-high-contrast-and-all-system-display-attributes"></a>ハイ コントラストとすべてのシステム表示属性をサポートする  

 アプリケーションは、ユーザーが選択したシステム全体のコントラスト設定、色の選択、またはその他のシステム全体のディスプレイの設定と属性を中断または無効にしてはなりません。 ユーザーが採用しているシステム全体の設定は、アプリケーションのユーザー補助機能を強化します。そのため、これをアプリケーションによって無効にしたり、無視したりしないでください。 色は、正しいコントラストを提供するため、正しい前景色と背景色の組み合わせで使用する必要があります。 関連のない色を混在させないでください。色を反転させません。  
  
 黒の背景に白いテキストなど、特定のハイ コントラストの組み合わせが必要なユーザーは多数います。 それらを反転させて、白地に黒のテキストとして描画すると、前景色の上に背景色がにじみ、一部のユーザーには読みづらくなります。  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>

### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>すべての DPI 設定によってすべての UI を正しく拡大/縮小する  

 すべての UI がドット/インチ (dpi) の設定で適切にスケールできることを確認します。 また、UI 要素が 1024 x 768 の画面に収まり、120ドット/インチ (dpi) であることを確認します。  
  
<a name="Navigation"></a>

## <a name="navigation"></a>ナビゲーション  

 このセクションのベスト プラクティスでは、ナビゲーションがコントロールとアプリケーションで対処されていることを確認します。  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>

### <a name="provide-keyboard-interface-for-all-ui-elements"></a>すべての UI 要素にキーボード インターフェイスを指定する  

 タブストップは、特に慎重に計画されている場合、UI 内を移動する別の方法をユーザーに提供します。  
  
 アプリケーションは、次のキーボード インターフェイスを備えている必要があります。  
  
- ボタン、リンク、またはリスト ボックスなど、ユーザーが操作できるすべてのコントロールのタブ ストップ  
  
- 論理的なタブの順序  
  
<a name="Show_the_Keyboard_Focus"></a>

### <a name="show-the-keyboard-focus"></a>キーボード フォーカスの表示  

 ユーザーがキーストロークの効果を予測できるように、ユーザーはどのオブジェクトにキーボード フォーカスがあるかを認識しておく必要があります。 キーボード フォーカスを強調表示するには、色、フォント、または四角形や拡大などのグラフィックスを使用します。 キーボードフォーカスを音声で強調表示するには、音量、ピッチ、または色調の品質を変更します。  
  
 混乱を回避するには、アプリケーションはビジュアル フォーカス インジケーターをすべて非表示にし、非アクティブなウィンドウ (またはペイン) にある選択項目を暗くする必要があります。  
  
 アプリケーションは、キーボード フォーカスで以下を行う必要があります。  
  
- 1 つの項目が常にキーボード フォーカスされている必要がある  
  
- キーボード フォーカスは明確に表示されている必要がある  
  
- 選択項目またはフォーカスされた項目は視覚的に強調表示されている必要がある  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>

### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>ナビゲーションの標準と強力なナビゲーション スキームをサポートする  

 キーボードナビゲーションのさまざまな側面により、ユーザーが UI を操作するためのさまざまな方法が提供されます。  
  
 アプリケーションは、次のキーボード インターフェイスを備えている必要があります。  
  
- すべてのコマンド、メニュー、およびコントロールのショートカットキーと下線付きアクセスキー  
  
- 重要なリンクへのキーボード ショートカット  
  
- すべてのメニュー項目にアクセス キーがあり、すべてのボタンにアクセラレータ キーがあり、すべてのコマンドにアクセラレータ キーがある  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>

### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>マウスの位置がキーボード ナビゲーションと干渉しないようにする  

 マウスの位置は、キーボードのナビゲーションと干渉しないようにしてください。 たとえば、マウスがある場所に位置していて、ユーザーがキーボードを使用して移動している場合、ユーザーによって開始されない限り、マウスをクリックする必要はありません。  
  
<a name="Multimodal_Interface"></a>

## <a name="multimodal-interface"></a>マルチモーダル インターフェイス  

 このセクションのベストプラクティスでは、アプリケーション UI にビジュアル要素の代替手段が含まれていることを確認します。  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>

### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>テキスト以外の要素に相当する、ユーザーが選択可能な項目を提供する  

 テキスト以外の各要素について、テキスト、チャット内容、または音声による説明 (代替テキスト、キャプション、視覚的なフィードバックなど) に相当する、ユーザーが選択可能な項目を提供します。  
  
 テキスト以外の要素は、画像、画像マップ領域、アニメーション、アプレット、フレーム、スクリプト、グラフィカルボタン、サウンド、スタンドアロンオーディオファイル、ビデオなど、さまざまな UI 要素に対応しています。 テキスト以外の要素は、UI の内容を理解するためにユーザーがアクセスする必要がある視覚的な情報、音声、または一般的なオーディオ情報が含まれている場合に重要です。  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>

### <a name="use-color-but-also-provide-alternatives-to-color"></a>色を使用するだけでなく、色の代替手段を提供する  

 色を使用して、他の手段によって示される情報を強化、強調、または再反復処理します。ただし、色単独を使用して情報を伝達しないでください。 色覚に障がいがあるユーザーまたは白黒表示のディスプレイを持つユーザーには、色の代替手段が必要です。  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>

### <a name="use-standard-input-apis-with-device-independent-calls"></a>デバイスに依存しない呼び出しで標準の入力 API を使用する  

 デバイスに依存しない呼び出しでは、キーボードとマウスの機能が等価であると同時に、UI に関する必要な情報を補助テクノロジに提供します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.Peers>
- [テーマと UI オートメーションサポートのサンプルを使用した NumericUpDown カスタムコントロール](/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [キーボード ユーザー インターフェイス設計のガイドライン](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
