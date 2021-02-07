---
description: 詳細については、「デバッグインターフェイス」を参照してください。
title: デバッグのインターフェイス
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 6e6cc07e200b9ecf6bf4039f4fd5fd69e27b6fda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717967"
---
# <a name="debugging-interfaces"></a>デバッグのインターフェイス

ここでは、共通言語ランタイム (CLR: Common Language Runtime) で実行するプログラムのデバッグを処理するアンマネージ インターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [ICLRDataEnumMemoryRegions インターフェイス](iclrdataenummemoryregions-interface.md)\
 呼び出し元が指定したメモリ範囲を列挙するメソッドを提供します。  
  
 [ICLRDataEnumMemoryRegionsCallback インターフェイス](iclrdataenummemoryregionscallback-interface.md)\
 メモリの指定された領域を列挙した結果の `EnumMemoryRegions` をデバッガーにレポートするコールバック メソッドを提供します。  
  
 [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)\
 対象の CLR プロセスと対話するためのメソッドを提供します。  
  
 [ICLRDataTarget2 インターフェイス](iclrdatatarget2-interface.md)\
 データ アクセス サービス層で使用して対象プロセスの仮想メモリ領域を操作する、`ICLRDataTarget` のサブクラスです。  
  
 [ICLRDataTarget3 インターフェイス](iclrdatatarget3-interface.md)\
 例外情報へのアクセスを提供する [ICLRDataTarget2](iclrdatatarget2-interface.md) のサブクラスです。  
  
 [ICLRDebugging インターフェイス](iclrdebugging-interface.md)\
 デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。  
  
 [ICLRDebuggingLibraryProvider インターフェイス](iclrdebugginglibraryprovider-interface.md)\
 には、提供 [ライブラリのメソッド](iclrdebugginglibraryprovider-providelibrary-method.md) メソッドが含まれています。このメソッドは、共通言語ランタイムのバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。  
  
 [ICLRMetadataLocator インターフェイス](iclrmetadatalocator-interface.md)\
 データ アクセス サービス層で使用して、対象プロセス内のアセンブリのメタデータを見つけるためのインターフェイスです。  
  
 [ICorDebug インターフェイス](icordebug-interface.md)\
 開発者が CLR 環境でアプリケーションをデバッグできるようにするメソッドを提供します。  
  
 [の Appdomain インターフェイス](icordebugappdomain-interface.md)\
 アプリケーション ドメインをデバッグするためのメソッドを提供します。  
  
 [ICorDebugAppDomain2 インターフェイス](icordebugappdomain2-interface.md)\
 配列、ポインター、関数ポインター、および ByRef 型を使用するメソッドを提供します。 これは、`ICorDebugAppDomain` インターフェイスの機能を拡張するインターフェイスです。  
  
 [ICorDebugAppDomain3 インターフェイス](icordebugappdomain3-interface.md)\
 アプリケーションドメインの Windows ランタイム型を操作するメソッドを提供します。 このインターフェイスは、`ICorDebugAppDomain` インターフェイスと `ICorDebugAppDomain2` インターフェイスを拡張します。  
  
 [ICorDebugAppDomain4 インターフェイス](icordebugappdomain4-interface.md)\
 コードを論理的に拡張して、COM 呼び出し可能ラッパーからマネージオブジェクトを [取得します](icordebugappdomain-interface.md) 。  
  
 [ICorDebugAppDomainEnum インターフェイス](icordebugappdomainenum-interface.md)\
 列挙体の次の位置から、指定した数の `ICorDebugAppDomain` の値を返すメソッドを提供します。  
  
 [ICorDebugArrayValue インターフェイス](icordebugarrayvalue-interface.md)\
 1 次元または多次元の配列を表す `ICorDebugHeapValue` のサブクラスです。  
  
 [のアセンブリインターフェイス](icordebugassembly-interface.md)\
 アセンブリを表します。  
  
 [ICorDebugAssembly2 インターフェイス](icordebugassembly2-interface.md)\
 アセンブリを表します。 これは、`ICorDebugAssembly` インターフェイスの機能を拡張するインターフェイスです。  
  
 [ICorDebugAssembly3 インターフェイス](icordebugassembly3-interface.md)\
 は、この [アセンブリ](icordebugassembly-interface.md) インターフェイスを論理的に拡張して、コンテナーアセンブリとそれに含まれるアセンブリのサポートを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [いいね。インターフェイス](icordebugassemblyenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugAssembly` 配列を列挙します。  
  
 [ICorDebugBlockingObjectEnum インターフェイス](icordebugblockingobjectenum-interface.md)\
 [CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体のリストの列挙子を提供します。  
  
 [の値のインターフェイス](icordebugboxvalue-interface.md)\
 ボックス化された値クラスのオブジェクトを表す `ICorDebugHeapValue` のサブクラス。  
  
 [ICorDebugBreakpoint インターフェイス](icordebugbreakpoint-interface.md)\
 関数のブレークポイント、または値のウォッチ ポイントを表します。  
  
 [いいね Pointenum インターフェイス](icordebugbreakpointenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugBreakpoint` 配列を列挙します。  
  
 [というチェーンインターフェイス](icordebugchain-interface.md)\
 物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。  
  
 [ICorDebugChainEnum インターフェイス](icordebugchainenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugChain` 配列を列挙します。  
  
 [のクラスインターフェイス](icordebugclass-interface.md)\
 基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。  
  
 [ICorDebugClass2 インターフェイス](icordebugclass2-interface.md)\
 ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。 このインターフェイスは、`ICorDebugClass` の機能を拡張します。  
  
 [のコードインターフェイス](icordebugcode-interface1.md)\
 Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。  
  
 [ICorDebugCode2 インターフェイス](icordebugcode2-interface.md)\
 `ICorDebugCode` の機能を拡張するメソッドを提供します。  
  
 [ICorDebugCode3 インターフェイス](icordebugcode3-interface.md)\
 [コード](icordebugcode-interface1.md)と[ICorDebugCode2](icordebugcode2-interface.md)を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。  
  
 [ICorDebugCode4 インターフェイス](icordebugcode4-interface.md)\
 デバッガーが関数のローカル変数と引数を列挙できるようにするメソッドを提供します。  
  
 [のコードの列挙型インターフェイス](icordebugcodeenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugCode` 配列を列挙します。  
  
 [「いいね! 値インターフェイス」](icordebugcomobjectvalue-interface.md)\
 キャッシュされたインターフェイス オブジェクトを取得するメソッドを提供します。  
  
 [テキストコンテキストインターフェイス](icordebugcontext-interface.md)\
 コンテキストのオブジェクトを表します。 このインターフェイスはまだ実装されていません。  
  
 [のコントロールインターフェイス](icordebugcontroller-interface.md)\
 コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。  
  
 [の場合は、このインターフェイス](icordebugdatatarget-interface.md)\
 特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。  
  
 [ICorDebugDataTarget2 インターフェイス](icordebugdatatarget2-interface.md)\
 によって、"の" を論理的に [拡張します](icordebugdatatarget-interface.md) 。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugDataTarget3 インターフェイス](icordebugdatatarget3-interface.md)\
 提供され [たモジュール](icordebugdatatarget-interface.md) に関する情報を提供するために、によって、参照インターフェイスを論理的に拡張します。 **.NET ネイティブのみで使用できます。**  
  
 [のイベントインターフェイス](icordebugdebugevent-interface.md)\
 すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugEditAndContinueErrorInfo インターフェイス](icordebugeditandcontinueerrorinfo-interface.md)\
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEditAndContinueSnapshot インターフェイス](icordebugeditandcontinuesnapshot-interface.md)\
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEnum インターフェイス](icordebugenum-interface1.md)\
 デバッグ中の列挙子の抽象基底インターフェイスとして機能します。  
  
 [いいね Infoenum インターフェイス](icordebugerrorinfoenum-interface.md)\
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [の場合は、インターフェイス](icordebugeval-interface.md)\
 デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。  
  
 [ICorDebugEval2 インターフェイス](icordebugeval2-interface.md)\
 ジェネリック型をサポートできるように `ICorDebugEval` を拡張します。  
  
 [は、の例外のイベントインターフェイス](icordebugexceptiondebugevent-interface.md)\
 は、例外イベントをサポートするために、の [イベント](icordebugdebugevent-interface.md) インターフェイスを拡張します。 **.NET ネイティブのみで使用できます。**  
  
 [いい Exceptionobjectcallstackenum インターフェイス](icordebugexceptionobjectcallstackenum-interface.md)\
 例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。  
  
 [の値インターフェイス](icordebugexceptionobjectvalue-interface.md)\
 によっ [て、](icordebugobjectvalue-interface.md) のマネージ例外オブジェクトからスタックトレース情報を提供するように、の機能を拡張します。  
  
 [テキストフレームインターフェイス](icordebugframe-interface.md)\
 現在のスタックのフレームを表します。  
  
 [の場合は、インターフェイスの列挙体](icordebugframeenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugFrame` 配列を列挙します。  
  
 [の関数インターフェイス](icordebugfunction-interface1.md)\
 マネージド関数またはマネージド メソッドを表します。  
  
 [ICorDebugFunction2 インターフェイス](icordebugfunction2-interface.md)\
 `ICorDebugFunction` を論理的に拡張して、"マイ コードのみ" ステップ実行によるデバッグをサポートします。  
  
 [ICorDebugFunction3 インターフェイス](icordebugfunction3-interface.md)\
 により、再 Jit 要求からコードへのアクセスを提供するために、の [関数](icordebugfunction-interface1.md) インターフェイスを論理的に拡張します。  
  
 [いいね! ブレークポイントインターフェイス](icordebugfunctionbreakpoint-interface.md)\
 関数内のブレークポイントをサポートするように `ICorDebugBreakpoint` を拡張します。  
  
 ["いいね!" インターフェイスの列挙](icordebuggcreferenceenum-interface.md)\
 ガベージ コレクトされるオブジェクトの列挙子を提供します。  
  
 [の値インターフェイス](icordebuggenericvalue-interface.md)\
 すべての値に適用する `ICorDebugValue` のサブクラスです。 このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。  
  
 [は、"いいね" インターフェイス](icordebugguidtotypeenum-interface.md)\
 GUID およびその対応する `ICorDebugType` オブジェクトをマップするオブジェクトの列挙子を提供します。  
  
 [の値インターフェイス](icordebughandlevalue-interface.md)\
 デバッガーが作成したガベージ コレクションのハンドルへの参照値を表す `ICorDebugReferenceValue` のサブクラスです。  
  
 [このインターフェイスは、このインターフェイスによって](icordebugheapenum-interface.md)\
 マネージド ヒープのオブジェクトの列挙子を提供します。  
  
 [ICorDebugHeapSegmentEnum インターフェイス](icordebugheapsegmentenum-interface.md)\
 マネージド ヒープのメモリ領域の列挙子を提供します。  
  
 ["いいね!" インターフェイス](icordebugheapvalue-interface.md)\
 CLR ガベージ コレクターによって収集されたオブジェクトを表す `ICorDebugValue` のサブクラスです。  
  
 [ICorDebugHeapValue2 インターフェイス](icordebugheapvalue2-interface1.md)\
 ランタイム ハンドルのサポートを提供する `ICorDebugHeapValue` の拡張機能です。  
  
 [ICorDebugHeapValue3 インターフェイス](icordebugheapvalue3-interface.md)\
 オブジェクトのモニター ロック プロパティを公開します。  
  
 [のコードインターフェイス](icordebugilcode-interface.md)\
 中間言語 (IL) コードのセグメントを表します。  
  
 [ICorDebugILCode2 インターフェイス](icordebugilcode2-interface.md)\
 では、この [コード](icordebugilcode-interface.md) インターフェイスを論理的に拡張して、関数のローカル変数シグネチャのトークンを返すメソッドを提供し、プロファイラーのインストルメント化された中間言語 (il) オフセットを元のメソッドの il オフセットにマップします。  
  
 [いいね! のインターフェイス](icordebugilframe-interface.md)\
 MSIL コードのスタック フレームを表します。  
  
 [ICorDebugILFrame2 インターフェイス](icordebugilframe2-interface.md)\
 `ICorDebugILFrame` の論理拡張機能です。  
  
 [ICorDebugILFrame3 インターフェイス](icordebugilframe3-interface.md)\
 関数の戻り値をカプセル化するメソッドを提供します。  
  
 [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)\
 ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。 パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。  
  
 [のコードインターフェイス](icordebuginstancefieldsymbol-interface.md)\
 インスタンス フィールドのデバッグ シンボル情報を表します。 **.NET ネイティブのみで使用できます。**  
  
 [のテキストフレームインターフェイス](icordebuginternalframe-interface.md)\
 デバッガーのフレーム種類を識別します。  
  
 [ICorDebugInternalFrame2 インターフェイス](icordebuginternalframe2-interface.md)\
 スタックアドレスや、 [テキストフレーム](icordebugframe-interface.md) オブジェクトに対する位置など、内部フレームに関する情報を提供します。  
  
 [ICorDebugLoadedModule インターフェイス](icordebugloadedmodule-interface.md)\
 読み込まれたモジュールについての情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [の Managedmanagedcallback インターフェイス](icordebugmanagedcallback-interface.md)\
 デバッガーのコールバックを処理するメソッドを提供します。  
  
 [ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)\
 デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。 `ICorDebugManagedCallback2` は、`ICorDebugManagedCallback` の論理拡張機能です。  
  
 [ICorDebugManagedCallback3 インターフェイス](icordebugmanagedcallback3-interface.md)\
 有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。  
  
 [は、のインターフェイス](icordebugmda-interface.md)\
 マネージド デバッグ アシスタント (MDA) メッセージを表します。  
  
 [のの Memorybuffer インターフェイス](icordebugmemorybuffer-interface.md)\
 メモリ内のバッファーを表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugMergedAssemblyRecord インターフェイス](icordebugmergedassemblyrecord-interface.md)\
 マージされたアセンブリに関する情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugMetaDataLocator インターフェイス](icordebugmetadatalocator-interface.md)\
 デバッガーにメタデータ情報を提供します。  
  
 [のモジュールインターフェイス](icordebugmodule-interface.md)\
 実行可能ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) のいずれかの CLR モジュールを表します。  
  
 [ICorDebugModule2 インターフェイス](icordebugmodule2-interface.md)\
 `ICorDebugModule` の論理的な拡張機能として動作します。  
  
 [ICorDebugModule3 インターフェイス](icordebugmodule3-interface.md)\
 動的モジュールのシンボル リーダーを作成します。  
  
 [のモジュールのブレークポイントインターフェイス](icordebugmodulebreakpoint-interface.md)\
 特定のモジュールにアクセスできるように `ICorDebugBreakpoint` を拡張します。  
  
 [いい Moduledebugevent インターフェイス](icordebugmoduledebugevent-interface.md)\
 モジュールレベルのイベントをサポートするように、のモジュールレベル [のイベントを](icordebugdebugevent-interface.md) 拡張します。 **.NET ネイティブのみで使用できます。**  
  
 [のモジュール列挙型インターフェイス](icordebugmoduleenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugModule` 配列を列挙します。  
  
 [ICorDebugMutableDataTarget インターフェイス](icordebugmutabledatatarget-interface.md)\
 変更可能なデータターゲットをサポートするために、の機能を拡張[します。](icordebugdatatarget-interface.md)  
  
 [テキストフレームインターフェイス](icordebugnativeframe-interface.md)\
 ネイティブ フレームで使用される `ICorDebugFrame` の特化された実装。  
  
 [ICorDebugNativeFrame2 インターフェイス](icordebugnativeframe2-interface.md)\
 子と親のフレームの関係をテストするメソッドを提供します。  
  
 [このインターフェイス](icordebugobjectenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、オブジェクトの配列を相対仮想アドレス (RVA: Relative Virtual Address) で列挙します。  
  
 [の値インターフェイス](icordebugobjectvalue-interface.md)\
 オブジェクトが含まれた値を表す `ICorDebugValue` のサブクラスです。  
  
 [ICorDebugObjectValue2 インターフェイス](icordebugobjectvalue2-interface.md)\
 継承およびオーバーライドをサポートするように `ICorDebugObjectValue` を拡張します。  
  
 [のプロセスインターフェイス](icordebugprocess-interface.md)\
 マネージド コードを実行しているプロセスを表します。  
  
 [ICorDebugProcess2 インターフェイス](icordebugprocess2-interface1.md)\
 `ICorDebugProcess` の論理拡張機能です。  
  
 [ICorDebugProcess3 インターフェイス](icordebugprocess3-interface.md)\
 カスタムのデバッガー通知を制御します。

 [ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)\
 アウトプロセス実行制御のサポートを提供します。
  
 [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)\
 [は、](icordebugprocess-interface.md)マネージヒープへのアクセスをサポートし、マネージオブジェクトのガベージコレクションに関する情報を提供し、デバッガーがアプリケーションのローカルのネイティブイメージキャッシュからイメージを読み込むかどうかを判断するために、コードを拡張します。  
  
 [ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)\
 コードを論理的に [拡張して、ネイティブ](icordebugprocess-interface.md) の例外デバッグイベントと仮想モジュール分割でエンコードされたマネージデバッグイベントをデコードするなどの機能を有効にします。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugProcess7 インターフェイス](icordebugprocess7-interface.md)\
 ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。  
  
 [ICorDebugProcess8 インターフェイス](icordebugprocess8-interface.md)\
 ICorDebugManagedCallback2 [process](icordebugprocess-interface.md)インターフェイスを論理的に拡張して、特定の種類の[](icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。  
  
 [の型の Processenum インターフェイス](icordebugprocessenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugProcess` 配列を列挙します。  
  
 [の値インターフェイス](icordebugreferencevalue-interface.md)\
 参照型をサポートする `ICorDebugValue` のサブクラス。  
  
 [いいです。](icordebugregisterset-interface.md)\
 現在コードを実行しているマシン上で使用できるレジスタ セットを表します。  
  
 [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)\
 64 を超えるレジスタを持つハードウェア プラットフォーム用に `ICorDebugRegisterSet` の機能を拡張します。  
  
 [のリモートインターフェイス](icordebugremote-interface.md)\
 リモート ターゲット プロセスに対してマネージド デバッガーを起動または接続する機能を提供します。  
  
 [の Remotetarget インターフェイス](icordebugremotetarget-interface.md)\
 開発者が CLR 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。  
  
 [ICorDebugRuntimeUnwindableFrame インターフェイス](icordebugruntimeunwindableframe-interface.md)\
 共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。  
  
 [は、このインターフェイス](icordebugstackwalk-interface.md)\
 スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。  
  
 [の場合は、コードインターフェイス](icordebugstaticfieldsymbol-interface.md)\
 静的フィールドのデバッグ シンボル情報を表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugStepper インターフェイス](icordebugstepper-interface.md)\
 デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
 [ICorDebugStepper2 インターフェイス](icordebugstepper2-interface1.md)\
 マイ コードのみ (JMC: Just My Code) デバッグのサポートを提供します。  
  
 [というインターフェイス](icordebugstepperenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugStepper` 配列を列挙します。  
  
 [いいねインターフェイス](icordebugstringvalue-interface.md)\
 文字列値に適用する `ICorDebugHeapValue` のサブクラスです。  
  
 [は、プロバイダーインターフェイス](icordebugsymbolprovider-interface.md)\
 デバッグ シンボル情報を取得するために使用できるメソッドを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugSymbolProvider2 インターフェイス](icordebugsymbolprovider2-interface.md)\
 追加のデバッグシンボル情報を取得するために、この [プロバイダー](icordebugsymbolprovider-interface.md) インターフェイスを論理的に拡張します。 **.NET ネイティブのみで使用できます。**  
  
 [のスレッドインターフェイス](icordebugthread-interface.md)\
 プロセス内のスレッドを表します。 `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
 [ICorDebugThread2 インターフェイス](icordebugthread2-interface.md)\
 `ICorDebugThread` の論理的な拡張機能として動作します。  
  
 [ICorDebugThread3 インターフェイス](icordebugthread3-interface.md)\
 とそれに対応するインターフェイス [へのエントリ](icordebugstackwalk-interface.md) ポイントを提供します。  
  
 [ICorDebugThread4 インターフェイス](icordebugthread4-interface.md)\
 スレッドのブロック情報を提供します。  
  
 [いい Threadenum インターフェイス](icordebugthreadenum-interface1.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugThread` 配列を列挙します。  
  
 [の型のインターフェイス](icordebugtype-interface.md)\
 基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。  
  
 [ICorDebugType2 インターフェイス](icordebugtype2-interface.md)\
 によって、テキスト型または複合型 (ユーザー定義型) の型識別子を取得するため [に、を拡張します](icordebugtype-interface.md) 。  
  
 [の型のインターフェイス](icordebugtypeenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugType` 配列を列挙します。  
  
 [ICorDebugUnmanagedCallback インターフェイス](icordebugunmanagedcallback-interface.md)\
 CLR に直接関連していないネイティブ イベントについて通知します。  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 デバッグ中のプロセス内の読み取り値または書き込み値を表します。  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 `ICorDebugValue` をサポートできるように `ICorDebugType` を拡張します。  
  
 [ICorDebugValue3 インターフェイス](icordebugvalue3-interface.md)\
 "ICorDebugValue" インターフェイスと "ICorDebugValue2" インターフェイスを拡張して、2 GB を超える配列のサポートを提供します。  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 特定の値にアクセスできるように `ICorDebugBreakpoint` を拡張します。  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 `ICorDebugEnum` メソッドを実装し、`ICorDebugValue` 配列を列挙します。  
  
 [ページホームインターフェイス](icordebugvariablehome-interface.md)\
 関数のローカル変数または引数を表します。  
  
 [の型の変数の列挙型インターフェイス](icordebugvariablehomeenum-interface.md)\
 関数のローカル変数および引数に列挙子を提供します。  
  
 [ICorDebugVariableSymbol インターフェイス](icordebugvariablesymbol-interface.md)\
 変数のデバッグ シンボル情報を取得します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugVirtualUnwinder インターフェイス](icordebugvirtualunwinder-interface.md)\
 スタック アンワインドを支援するメソッドを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorPublish インターフェイス](icorpublish-interface.md)\
 発行プロセスの汎用インターフェイスとして機能します。  
  
 [ICorPublishAppDomain インターフェイス](icorpublishappdomain-interface.md)\
 アプリケーション ドメインの情報を表し、提供します。  
  
 [ICorPublishAppDomainEnum インターフェイス](icorpublishappdomainenum-interface.md)\
 現在プロセス内に存在する `ICorPublishAppDomain` オブジェクトのコレクションを走査するメソッドを提供します。  
  
 [ICorPublishEnum インターフェイス](icorpublishenum-interface.md)\
 発行する列挙子の抽象ベースとして機能します。  
  
 [ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)\
 プロセスの情報にアクセスするメソッドを適用します。  
  
 [ICorPublishProcessEnum インターフェイス](icorpublishprocessenum-interface.md)\
 `ICorPublishProcess` オブジェクトのコレクションを走査するメソッドを提供します。  

 [ISOSDacInterface インターフェイス](isosdacinterface-interface.md)\
 からデータにアクセスするためのヘルパーメソッドを提供 `SOS` します。

 [IXCLRDataMethodDefinition インターフェイス](ixclrdatamethoddefinition-interface.md)\
 メソッド定義に関する情報を照会するためのメソッドを提供します。

 [IXCLRDataMethodInstance インターフェイス](ixclrdatamethodinstance-interface.md)\
 メソッドインスタンスに関する情報を照会するためのメソッドを提供します。

 [IXCLRDataModule インターフェイス](ixclrdatamodule-interface.md)\
 読み込まれたモジュールに関する情報を照会するためのメソッドを提供します。

 [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)\
 プロセスに関する情報を照会するためのメソッドを提供します。
  
## <a name="related-sections"></a>関連項目  

 [デバッグコクラス](debugging-coclasses.md)\
 [デバッググローバル静的関数](debugging-global-static-functions.md)\
 [列挙型のデバッグ](debugging-enumerations.md)\
 [デバッグ構造体](debugging-structures.md)\
