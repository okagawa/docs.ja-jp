---
ms.openlocfilehash: 0237c848d71150aaea1f9de4f4b16a0cbbc4ab3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615668"
---
### <a name="new-64-bit-jit-compiler-in-the-net-framework-46"></a>.NET Framework 4.6 の新しい 64 ビット JIT コンパイラ

#### <a name="details"></a>説明

.NET Framework 4.6 以降では、Just-In-Time コンパイルには新しい 64 ビット JIT コンパイラが使用されます。 場合によっては、予期しない例外がスローされるか、32 ビット コンパイラまたは以前の 64 ビット JIT コンパイラを使用してアプリを実行したときとは動作が異なる可能性があります。 この変更は、32 ビット JIT コンパイラには影響しません。 既知の相違には次のようなものがあります。

- 特定の条件下では、最適化が有効なリリース ビルドの <xref:System.NullReferenceException> がボックス化解除操作でスローされる場合があります。
- 場合によっては、大きなメソッド本文の実働コードの実行時に <xref:System.StackOverflowException> がスローされることがあります。
- 特定の条件下では、メソッドに渡された構造体が、リリース ビルドの値の型ではなく、参照型として扱われます。 この問題の兆候の 1 つは、コレクション内の個々の項目が予期しない順序で表示されることです。
- 特定の条件下では、最適化が有効な場合、高ビットが設定された <xref:System.UInt16> 値が正しく比較されません。
- 特定の条件下では、特に、配列値の初期化中に、<xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 命令でのメモリ初期化により、正しくない値でメモリが初期化される場合があります。 その結果、ハンドルされない例外または正しくない出力が発生する場合があります。
- 特定のまれな条件下では、コンパイラの最適化が有効な場合に、条件付きのビット テストで正しくない <xref:System.Boolean> 値が返されたり、例外がスローされたりすることがあります。
- 特定の条件下では、`if` ステートメントを使用して、`try` ブロックの開始前と `try` ブロックの終了時の条件をテストし、同じ条件を `catch` または `finally` ブロックで評価する場合、新しい 64 ビット JIT コンパイラが、コードの最適化の際に `catch` または `finally` ブロックから `if` 条件を削除します。 その結果、`catch` または `finally` ブロックの `if` ステートメント内のコードは無条件で実行されます。

#### <a name="suggestion"></a>提案される解決策

**既知の問題の軽減策** <br/> 上記の問題が発生する場合は、次のいずれかの方法で解決できます。

- .NET Framework 4.6.2 にアップグレードします。 .NET Framework 4.6.2 に含まれている新しい 64 ビット コンパイラは、これらの既知の問題のそれぞれに対処します。
- Windows Update を実行して、Windows のバージョンが最新のものであることを確認します。 .NET Framework 4.6 および 4.6.1 へのサービス更新により、ボックス化解除操作での <xref:System.NullReferenceException> を除き、これらの問題のそれぞれに対処することができます。
- 古い 64 ビット JIT コンパイラでコンパイルします。 この方法の詳細については、「**その他の問題の軽減策**」を参照してください。
**その他の問題の軽減策** <br/> 古い 64 ビット コンパイラと新しい 64 ビット JIT コンパイラでコンパイルされたコードの動作、またはアプリのデバッグ バージョンとリリース バージョン (両方とも新しい 64 ビット JIT コンパイラでコンパイル) の動作に違いが見られる場合は、次のようにして、古い 64 ビット JIT コンパイラでアプリをコンパイルすることができます。

- アプリケーションごとに、アプリケーションの構成ファイルに [<](~/docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) 要素を追加できます。 次のように新しい 64 ビット JIT コンパイラでのコンパイルを無効にし、代わりに従来の 64 ビット JIT コンパイラを使用します。

    ```xml
    <?xml version ="1.0"?>
    <configuration>
      <runtime>
       <useLegacyJit enabled="1" />
      </runtime>
    </configuration>
    ```

- ユーザーごとに、`useLegacyJit` という `REG_DWORD` 値をレジストリの `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` キーに追加できます。 値を 1 にすると、従来の 64 ビット JIT コンパイラが有効になり、値を 0 にすると、従来の 64 ビット JIT コンパイラが無効になり、新しい 64 ビット JIT コンパイラが有効になります。
- コンピューターごとに、`useLegacyJit` という名前の `REG_DWORD` 値をレジストリの `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` キーに追加できます。 値を `1` にすると、従来の 64 ビット JIT コンパイラが有効になり、値を `0` にすると、従来の 64 ビット JIT コンパイラが無効になり、新しい 64 ビット JIT コンパイラが有効になります。
[Microsoft Connect](https://connect.microsoft.com/VisualStudio) でバグを報告し、問題を弊社に知らせることもできます。

| 名前    | 値       |
|:--------|:------------|
| スコープ   | エッジ        |
| バージョン | 4.6         |
| 種類    | 再ターゲット中 |
