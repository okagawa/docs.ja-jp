---
title: Caspol.exe (コード アクセス セキュリティ ポリシー ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- permission sets, modifying security policy
- security policy [.NET Framework], Code Access Security Policy tool
- enterprise security policy
- referencing code groups and permission sets
- user security policy
- Caspol.exe
- Code Access Security Policy tool
- code groups, modifying security policy
- application development [.NET Framework], security
- machine security policy
- security policy [.NET Framework], modifying
- manually editing security configuration files
ms.assetid: d2bf6123-7b0c-4e60-87ad-a39a1c3eb2e0
ms.openlocfilehash: a5a4068d0bf6f6f158ea9b2880785e227f96243d
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645573"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (コード アクセス セキュリティ ポリシー ツール)
ユーザーと管理者は、コード アクセス セキュリティ (CAS) ポリシー ツール (Caspol.exe) を使用して、コンピューター ポリシー レベル、ユーザー ポリシー レベル、およびエンタープライズ ポリシー レベルのセキュリティ ポリシーを変更できます。  
  
> [!IMPORTANT]
> .NET Framework 4 以降では、[\<legacyCasPolicy> 要素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)が `true` に設定されていない限り、Caspol.exe は CAS ポリシーに影響を与えません。 CasPol.exe によって表示または変更された設定は、CAS ポリシーの使用が選択されているアプリケーションにのみ影響します。 詳細については、「[セキュリティの変更点](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)」を参照してください。  
  
> [!NOTE]
> 64 ビット コンピューターには、64 ビット バージョンと 32 ビット バージョンの両方のセキュリティ ポリシーが含まれます。 32 ビット アプリケーションと 64 ビット アプリケーションの両方にポリシーの変更を適用するには、Caspol.exe の 32 ビット バージョンと 64 ビット バージョンの両方を実行します。  
  
 コード アクセス セキュリティ ポリシー ツールは、.NET Framework および Visual Studio と共に自動的にインストールされます。 Caspol.exe は、32 ビット システムでは %windir%\Microsoft.NET\Framework\\*version* に、64 ビット システムでは %windir%\Microsoft.NET\Framework64\\*version* にあります。 (たとえば、場所は、64 ビット システムの .NET Framework 4 では %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe)。コンピューターで複数のバージョンの .NET Framework を side-by-side で実行している場合は、複数のバージョンのツールがインストールされると考えられます。 インストール ディレクトリからツールを実行できます。 ただし、インストール フォルダーに移動する必要のない[コマンド プロンプト](developer-command-prompt-for-vs.md)を使用することをお勧めします。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>パラメーター  
  
|オプション|説明|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-af** *assembly_file*|カスタム セキュリティ オブジェクト (カスタム アクセス許可またはカスタム メンバーシップ条件) を実装するアセンブリを、特定のポリシー レベルの完全信頼アセンブリの一覧に追加します。 引数 *assembly_file* は、追加するアセンブリを指定します。 このファイルは、[厳密な名前](../../standard/assembly/strong-named.md)で署名する必要があります。 アセンブリに厳密な名前で署名するには、[厳密名ツール (Sn.exe)](sn-exe-strong-name-tool.md) を使用します。<br /><br /> カスタム アクセス許可を含むアクセス許可セットをポリシーに追加するたびに、そのカスタム アクセス許可を実装するアセンブリを、該当するポリシー レベルの完全信頼一覧に追加する必要があります。 セキュリティ ポリシー (コンピューター ポリシーなど) の中で使用されるカスタム セキュリティ オブジェクト (カスタム コード グループやメンバーシップ条件など) を実装するすべてのアセンブリを、完全信頼アセンブリの一覧に常に追加する必要があります。 **注意:** カスタム セキュリティ オブジェクトを実装するアセンブリが他のアセンブリを参照している場合は、参照先アセンブリを最初に完全信頼アセンブリの一覧に追加する必要があります。 Visual Basic、C++、および JScript を使用して作成されたカスタム セキュリティ オブジェクトは、それぞれ Microsoft.VisualBasic.dll、Microsoft.VisualC.dll、Microsoft.JScript.dll をこの順で参照します。 これらのアセンブリは、既定では、完全な信頼を持つアセンブリのリストには含まれていません。 カスタム セキュリティ オブジェクトを追加する前に、適切なアセンブリを完全な信頼のリストに追加する必要があります。 これができない場合は、セキュリティ システムが壊れ、すべてのアセンブリの読み込みに失敗します。 この状況では、Caspol.exe **-all -reset** オプションを使用してもセキュリティを修復できません。 セキュリティを修復するには、セキュリティ ファイルを手動で編集し、カスタム セキュリティ オブジェクトを削除する必要があります。|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*flags*]<br /><br /> or<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*flags*]|新しいコード グループをコード グループ階層に追加します。 *parent_label* または *parent_name* を指定できます。 *parent_label* 引数は、追加されているコード グループの親である、コード グループのラベル (1 や 1\.1 など) を指定します。 引数 *parent_name* は、追加するコード グループの親となるコード グループの名前を指定します。 *parent_label* と *parent_name* は交換して使用できるため、Caspol.exe がこの 2 つを区別できる必要があります。 したがって、*parent_name* の先頭を数字にすることはできません。 また、*parent_name* に含めることができるのは、A-Z、0-9、およびアンダースコア文字だけです。<br /><br /> 引数 *mship* は、新しいコード グループのメンバーシップ条件を指定します。 詳細については、このセクションの *mship* 引数の表を参照してください。<br /><br /> 引数 *pset_name* は、新しいコード グループと関連付けられるアクセス許可セットの名前です。 新しいグループに 1 つ以上の *flags* を設定することもできます。 詳細については、このセクションの *flags* 引数の表を参照してください。|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> or<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|新しい名前付きアクセス許可セットをポリシーに追加します。 アクセス許可セットは XML で編集し、.xml ファイルとして格納する必要があります。 XML ファイルにアクセス許可セットの名前が含まれる場合は、そのファイル (*psfile*) だけが指定されます。 XML ファイルにアクセス許可セットの名前が含まれない場合は、XML ファイルの名前 (*psfile*) とアクセス許可セットの名前 (*pset_name*) の両方を指定する必要があります。<br /><br /> アクセス許可セットで使用するすべてのアクセス許可を、グローバル アセンブリ キャッシュ内にあるアセンブリに定義する必要があります。|  
|**-a** **[ll]**|このオプションの後に続くすべてのオプションを、コンピューター、ユーザー、エンタープライズの各ポリシーに適用します。 **-all** オプションは、常に現在ログオンしているユーザーのポリシーを参照します。 現在のユーザー以外のユーザーのポリシーの参照方法については **-customall** オプションを参照してください。|  
|**-chggroup** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flags* `}`<br /><br /> or<br /><br /> **-cg** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flags* `}`|コード グループのメンバーシップ条件、アクセス許可セット、**exclusive**、**levelfinal**、**name**、**description** の各フラグの設定を変更します。 *label* または *name* を指定できます。 *label* 引数は、コード グループのラベル (1 や 1\.1 など) を指定します。 *name* 引数は、変更するコード グループの名前を指定します。 *label* と *name* は交換して使用できるため、Caspol.exe がこの 2 つを区別できる必要があります。 したがって、*name* の先頭を数字にすることはできません。 また、*name* に含めることができるのは、A-Z、0-9、およびアンダースコア文字だけです。<br /><br /> 引数 *pset_name* は、コード グループと関連付けるアクセス許可セットの名前を指定します。 引数 *mship* および *flags* については、このセクションで後述する表を参照してください。|  
|**-chgpset**  *psfile pset_name*<br /><br /> or<br /><br /> **-cp** *psfile pset_name*|名前付きアクセス許可セットを変更します。 引数 *psfile* は、アクセス許可セットの新しい定義を指定します。この定義はシリアル化された XML 形式のアクセス許可セット ファイルです。 引数 *pset_name* は、変更するアクセス許可セットの名前を指定します。|  
|**-customall**  *path*<br /><br /> or<br /><br /> **-ca**  *path*|このオプションの後に続くすべてのオプションを、コンピューター、エンタープライズ、指定したカスタム ユーザーの各ポリシーに適用します。 カスタム ユーザーのセキュリティ構成ファイルの位置を引数 *path* で指定する必要があります。|  
|**-cu** **[stomuser]** *path*|現在実行中の Caspol.exe を実行したユーザーに属さないカスタム ユーザー ポリシーを管理できます。 カスタム ユーザーのセキュリティ構成ファイルの位置を引数 *path* で指定する必要があります。|  
|**-enterprise**<br /><br /> or<br /><br /> **-en**|このオプションの後に続くすべてのオプションを、エンタープライズ レベル ポリシーに適用します。 エンタープライズ管理者ではないユーザーは、エンタープライズ ポリシーを変更するための十分な権限を持ちませんが、参照はできます。 エンタープライズ以外の場合、既定では、このポリシーがコンピューター ポリシーやユーザー ポリシーに干渉することはありません。|  
|**-e** **[xecution]** {**on** &#124; **off**}|コードの実行が開始される前に実行許可を確認する機構のオンとオフを切り替えます。 **注:** このスイッチは、.NET Framework 4 以降のバージョンでは削除されています。 詳細については、「[セキュリティの変更点](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)」を参照してください。|  
|**-f** **[orce]**|ツールの自己破棄テストを行わず、ユーザーに指定されたとおりにポリシーを変更します。 通常、Caspol.exe は、ポリシーを変更した結果 Caspol.exe 自体の適切な動作が妨げられることにならないかどうかをチェックします。妨げられる場合は、Caspol.exe は変更されたポリシーを保存せず、エラー メッセージを表示します。 Caspol.exe の動作を妨げることになっても強制的に Caspol.exe にポリシーを変更する場合は、 **–force** オプションを使用します。|  
|**-h** **[elp]**|Caspol.exe のコマンド構文とオプションを表示します。|  
|**-l** **[ist]**|指定されたコンピューター、ユーザー、エンタープライズ、またはすべてのポリシー レベルにかかわる、コード グループの階層とアクセス許可セットの一覧を表示します。 Caspol.exe は、最初にコード グループのラベルを、次に (null でない場合) 名前を表示します。|  
|**-listdescription**<br /><br /> or<br /><br /> **-ld**|指定されたポリシー レベルのすべてのコード グループの説明を一覧表示します。|  
|**-listfulltrust**<br /><br /> or<br /><br /> **-lf**|指定されたポリシー レベルの完全信頼アセンブリ一覧の内容を一覧表示します。|  
|**-listgroups**<br /><br /> or<br /><br /> **-lg**|指定されたポリシー レベルまたはすべてのポリシー レベルのコード グループを表示します。 Caspol.exe は、最初にコード グループのラベルを、次に (null でない場合) 名前を表示します。|  
|**-listpset** または **-lp**|指定されたポリシー レベルまたはすべてのポリシー レベルのアクセス許可セットを表示します。|  
|**-m** **[achine]**|このオプションの後に続くすべてのオプションをコンピューター レベル ポリシーに適用します。 管理者ではないユーザーは、コンピューター ポリシーを変更するための十分な権限を持ちませんが、参照はできます。 管理者の場合は、 **-machine** が既定値です。|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> or<br /><br /> **-pp** {**on** &#124; **off**}|ポリシーを変更するオプションを使用して、Caspol.exe が実行されるたびに表示されるプロンプトを有効または無効にします。|  
|**-quiet**<br /><br /> or<br /><br /> **-q**|ポリシーを変更するオプションに対して通常表示されるプロンプトを一時的に無効にします。 グローバル変更プロンプトの設定は変更されません。 このオプションは、すべての Caspol.exe コマンドに対してプロンプトを無効にすることを避けるため、単一のコマンドに対してだけ使用してください。|  
|**-r** **[ecover]**|バックアップ ファイルからポリシーを復元します。 ポリシーが変更されるたびに、古いポリシーが Caspol.exe によってバックアップ ファイルの中に格納されます。|  
|**-remfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-rf**  *assembly_file*|ポリシー レベルの完全信頼一覧からアセンブリを削除します。 この操作を実行する必要があるのは、カスタム アクセス許可を含むアクセス許可セットがポリシーによって使用されなくなった場合です。 ただし、カスタム アクセス許可を実装するアセンブリを完全信頼一覧から削除するのは、そのアセンブリが、まだ使用されている他のカスタム アクセス許可を実装していない場合に限ります。 一覧からアセンブリを削除するときは、そのアセンブリが依存している他のすべてのアセンブリも削除する必要があります。|  
|**-remgroup** {*label &#124;name*}<br /><br /> or<br /><br /> **-rg** {l*abel &#124; name*}|ラベルまたは名前で指定したコード グループを削除します。 指定したコード グループが子コード グループを持つ場合は、Caspol.exe によってすべての子コード グループも削除されます。|  
|**-rempset** *pset_name*<br /><br /> or<br /><br /> **-rp** *pset_name*|指定したアクセス許可セットをポリシーから削除します。 引数 *pset_name* は、削除するアクセス許可セットを指定します。 Caspol.exe がアクセス許可セットを削除するのは、そのアクセス許可セットがどのコード グループにも関連付けられていない場合だけです。 既定の (組み込み) アクセス許可セットは削除できません。|  
|**-reset**<br /><br /> or<br /><br /> **-rs**|ポリシーを既定のステータスに戻し、ディスクに永続化します。 このオプションは、変更後のポリシーが修復できそうになく、インストール時点の既定値からやり直す場合に便利です。 特定のセキュリティ構成ファイルに対する変更の開始点として既定のポリシーを使用する場合にも、リセット オプションは便利です。 詳細については、「[手動によるセキュリティ構成ファイルの編集](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1)」を参照してください。|  
|**-resetlockdown**<br /><br /> or<br /><br /> **-rsld**|ポリシーを既定の状態のより制限されたバージョンに戻してディスクに永続化します。前のコンピューター ポリシーのバックアップを作成し、`security.config.bac` というファイルに永続化します。  ロック ダウンされているポリシーは、`Local Intranet`、`Trusted Sites`、および `Internet` の各ゾーンに属し、対応するコード グループに子コード グループがないコードにアクセスを許可しないことを除いて、既定のポリシーと同じです。|  
|**-resolvegroup** *assembly_file*<br /><br /> or<br /><br /> **-rsg**  *assembly_file*|特定のアセンブリ (*assembly_file*) が属するコード グループを表示します。 既定では、このオプションは、アセンブリが属するコンピューター、ユーザー、エンタープライズの各ポリシー レベルを表示します。 1 つのポリシー レベルだけを参照するには、このオプションと共に **-machine**、 **-user**、または **-enterprise** のいずれかのオプションを使用します。|  
|**-resolveperm** *assembly_file*<br /><br /> or<br /><br /> **-rsp** *assembly_file*|アセンブリの実行が許可されていた場合は、指定した (または既定の) レベルのセキュリティ ポリシーによってそのアセンブリに与えられるすべてのアクセス許可を表示します。 引数 *assembly_file* はアセンブリを指定します。 **-all** オプションを指定すると、Caspol.exe は、ユーザー ポリシー、コンピューター ポリシー、およびエンタープライズ ポリシーに基づいて、アセンブリに与えられるアクセス許可を計算します。それ以外の場合は、既定の動作規則が適用されます。|  
|**-s** **[ecurity]** {**on** &#124; **off**}|コード アクセス セキュリティのオンとオフを切り替えます。 **-s off** オプションを指定しても、ロール ベース セキュリティは無効になりません。 **注:** このスイッチは、.NET Framework 4 以降のバージョンでは削除されています。 詳細については、「[セキュリティの変更点](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)」を参照してください。 **注意:** コード アクセス セキュリティを無効にすると、すべてのコード アクセス要求が成功します。 コード アクセス セキュリティを無効にすると、システムは、ウイルスやワームなどの悪意のあるコードの攻撃を受けやすくなります。 セキュリティをオフにすると、パフォーマンスは多少向上しますが、他のセキュリティ対策を講じて、システム セキュリティ全体が損なわれていないことを確認した場合にだけ、オフにしてください。 その他のセキュリティ対策の例としては、公衆ネットワークからの切断、コンピューターの物理的な保護などがあります。|  
|**-u** **[ser]**|このオプションの後に続くすべてのオプションを、Caspol.exe を実行したユーザーにかかわるユーザー レベル ポリシーに適用します。 管理者以外のユーザーの場合は、 **-user** が既定値です。|  
|**-?**|Caspol.exe のコマンド構文とオプションを表示します。|  
  
 コード グループのメンバーシップ条件を指定する引数 *mship* は、 **-addgroup** オプションおよび **-chggroup** オプションと併用できます。 各引数 *mship* は .NET Framework クラスとして実装されます。 *mship* を指定するには、次のいずれかを使用します。  
  
|引数|説明|  
|--------------|-----------------|  
|**-allcode**|すべてのコードを指定します。 このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-appdir**|アプリケーション ディレクトリを指定します。 メンバーシップ条件として **–appdir** を指定する場合は、コードの URL 証拠が、そのコードのアプリケーション ディレクトリ証拠と比較されます。 両方の証拠の値が同じである場合は、このメンバーシップ条件が成立します。 このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-custom**  *xmlfile*|カスタム メンバーシップ条件を追加します。 必須引数の *xmlfile* は、XML シリアル化したカスタム メンバーシップ条件を含む .xml ファイルを指定します。|  
|**-hash** *hashAlg* { **-hex** *hashValue* &#124; **-file** *assembly_file* }|指定されたアセンブリ ハッシュを持つコードを指定します。 コード グループのメンバーシップ条件としてハッシュを使用するには、ハッシュ値またはアセンブリ ファイルを指定する必要があります。 このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-pub** { **-cert** *cert_file_name* &#124;<br /><br /> **-file** *signed_file_name* &#124; **-hex**  *hex_string* }|指定されたソフトウェア発行者を持つコードを、証明書ファイル、ファイル上の署名、または X509 証明書の 16 進表示で指定します。 このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-site** *website*|指定されたサイトがソースであるコードを指定します。 次に例を示します。<br /><br /> `-site** www.proseware.com`<br /><br /> このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-strong -file** *file_name* {*name* &#124; **-noname**} {*version* &#124; **-noversion**}|特定の厳密な名前を持つコードを、ファイル名、文字列としてのアセンブリ名、および *major*.*minor*.*build*.*revision* 形式のアセンブリ バージョンで指定します。 次に例を示します。<br /><br /> **-strong -file** myAssembly.exe myAssembly 1.2.3.4<br /><br /> このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-url** *URL*|指定された URL をソースとするコードを指定します。 URL には、`http://` や `ftp://` などのプロトコルを含める必要があります。 さらに、ワイルドカード文字 (\*) を使用して、特定の URL から複数のアセンブリを指定できます。 **注:** 複数の名前を使用して 1 つの URL を識別できるため、URL をメンバーシップ条件として使用する方法は、コードの識別情報を安全に確認できる方法ではありません。 できるだけ厳密な名前メンバーシップ条件、発行元メンバーシップ条件、またはハッシュ メンバーシップ条件を使用してください。 <br /><br /> このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>」を参照してください。|  
|**-zone** *zonename*|指定されたゾーンがソースであるコードを指定します。 引数 *zonename* として、**MyComputer**、**Intranet**、**Trusted**、**Internet**、または **Untrusted** のいずれかの値を指定できます。 このメンバーシップ条件の詳細については、「<xref:System.Security.Policy.ZoneMembershipCondition> クラス」を参照してください。|  
  
 **–addgroup** オプションまたは **–chggroup** オプションと併用できる引数 *flags* は、次のいずれかの方法で指定します。  
  
|引数|説明|  
|--------------|-----------------|  
|**-description** "*description*"|**–addgroup** オプションと共に使用した場合、追加するコード グループの説明を指定します。 **–chggroup** オプションと共に使用した場合、編集するコード グループの説明を指定します。 引数 *description* を二重引用符で囲む必要があります。|  
|**-exclusive** {**on**&#124;**off**}|**on** に設定すると、コード グループのメンバーシップ条件に適合するコードがある場合、追加または修正しているコード グループと関連付けられたアクセス許可セットだけが考慮されます。 このオプションを **off** に設定すると、ポリシー レベルの中で適合するすべてのコード グループのアクセス許可セットが Caspol.exe で考慮されます。|  
|**-levelfinal** {**on**&#124;**off**}|**on** に設定すると、追加または変更するコード グループが出現するレベルよりも下にあるポリシー レベルは考慮されなくなります。 通常、このオプションはコンピューター ポリシー レベルで使用されます。 たとえば、このフラグをコンピューター レベルでコード グループに設定し、なんらかのコードがこのコード グループのメンバーシップ条件に適合した場合、Caspol.exe はそのコードのユーザー レベル ポリシーの計算または適用を行いません。|  
|**-name** "*name*"|**–addgroup** オプションと共に使用した場合、追加するコード グループのスクリプト名を指定します。 **-chggroup** オプションと共に使用した場合、編集するコード グループのスクリプト名を指定します。 引数 *name* を二重引用符で囲む必要があります。 引数 *name* には A-Z、0-9、およびアンダースコア文字だけを含めることができます。また、先頭には数字を使用できません。 コード グループは、数値のラベルではなくこの *name* によって参照できます。 *name* は、スクリプト目的で使用する場合にも便利です。|  
  
## <a name="remarks"></a>Remarks  
 セキュリティ ポリシーは 3 種類のポリシー レベル、つまりコンピューター ポリシー、ユーザー ポリシー、エンタープライズ ポリシーによって表現されます。 アセンブリが受信するアクセス許可のセットは、これらの 3 種類のポリシー レベルで許可されるアクセス許可セットの積集合によって決定されます。 それぞれのポリシー レベルは、コード グループの階層で表現されます。 すべてのコード グループは、どのコードをそのグループのメンバーとするのかを決定するためのメンバーシップ条件を持ちます。 名前付きアクセス許可セットも、各コード グループと関連付けられます。 このアクセス許可セットは、メンバーシップ条件を満たすコードに対してランタイムから与えられるアクセス許可を指定します。 コード グループの階層、および関連する名前付きアクセス許可セットによって、各レベルのセキュリティ ポリシーの定義と保守が行われます。 **–user**、 **-customuser**、 **–machine**、 **-enterprise** の各オプションを使用して、セキュリティ ポリシーのレベルを設定できます。  
  
 セキュリティ ポリシーの詳細、およびランタイムがコードに与えるアクセス許可を決定する方法については、「[セキュリティ ポリシーの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))」を参照してください。  
  
## <a name="referencing-code-groups-and-permission-sets"></a>コード グループとアクセス許可セットの参照  
 **-list** オプションを使用すると、階層に属するコード グループを簡単に参照できるように、インデントされたコード グループの一覧とその数値ラベル (1、1.1、1.1.1 など) が表示されます。 コード グループを対象とするその他のコマンド ライン操作でも、特定のコード グループを参照するために数値ラベルが使用されます。  
  
 名前付きアクセス許可セットを参照する場合は、名前を使用します。 **–list** オプションでは、最初にコード グループの一覧、次にそのポリシーの中で利用できる名前付きアクセス許可セットの一覧が表示されます。  
  
## <a name="caspolexe-behavior"></a>Caspol.exe の動作  
 **-s** **[ecurity]** {**on** &#124; **off**} を除くすべてのオプションが、Caspol.exe と共にインストールされたバージョンの .NET Framework を使用します。 あるバージョンのランタイムと共にインストールされた Caspol.exe を実行する場合、変更内容はそのバージョンだけに適用されます *。* その他のランタイムが共存する場合、それらのランタイムは影響を受けません。 特定のランタイム バージョンのディレクトリに切り替えずに Caspol.exe をコマンド ラインで実行する場合、Caspol.exe はパスに含まれる最初のランタイム バージョン (通常は最後にインストールされたランタイム バージョン) のディレクトリから実行されます。  
  
 **-s** **[ecurity]** {**on** &#124; **off**} オプションは、コンピューター全体に対する操作です。 コード アクセス セキュリティをオフにすると、すべてのマネージド コードおよびコンピューター上のすべてのユーザーに対するセキュリティ チェックが中止されます。 side-by-side 実行バージョンの .NET Framework がインストールされている場合は、このコマンドによってコンピューターにインストールされているすべてのバージョンのセキュリティがオフになります。 **-list** オプションを使用するとセキュリティがオフになっていることが示されますが、他のユーザーに対してセキュリティがオフになっていることが明確に示されることはありません。  
  
 管理者の権限を持たないユーザーが Caspol.exe を実行する場合、 **–machine** オプションが指定されていない限り、すべてのオプションはユーザー レベル ポリシーを参照します。 管理者が Caspol.exe を実行する場合、 **–user** オプションが指定されていない限り、すべてのオプションはコンピューター ポリシーを参照します。  
  
 Caspol.exe が正しく機能するには、**Everything** アクセス許可セットと等価の許可を与えられている必要があります。 Caspol.exe には防御機構があるため、Caspol.exe が動作するために必要なアクセス許可を得られなくなるような方法でポリシーを変更することはできません。 変更を実行しようとすると、Caspol.exe は、要求されたポリシーの変更で Caspol.exe の実行が中断されること、およびポリシーの変更が拒否されることをユーザーに通知します。 特定のコマンドについてこの防御機構をオフにするには、 **–force** オプションを使用します。  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>
## <a name="manually-editing-the-security-configuration-files"></a>手動によるセキュリティ構成ファイルの編集  
 3 種類のセキュリティ構成ファイルは、Caspol.exe でサポートされる 3 種類のポリシー レベル、つまりコンピューター ポリシー、指定されたユーザーのポリシー、およびエンタープライズ ポリシーと対応します。 これらのファイルがディスク上に作成されるのは、コンピューター ポリシー、ユーザー ポリシー、またはエンタープライズ ポリシーが Caspol.exe によって変更される場合だけです。 必要な場合は、Caspol.exe の **–reset** オプションを使用して、既定のセキュリティ ポリシーをディスクに保存できます。  
  
 ほとんどの場合、手動によるセキュリティ構成ファイルの編集はお勧めしません。 ただし、これらのファイルを変更する必要が生じることもあります。たとえば、管理者が特定のユーザーについてセキュリティ設定を編集する場合などです。  
  
## <a name="examples"></a>使用例  
 **-addfulltrust**  
  
 カスタム アクセス許可を含むアクセス許可セットがコンピューター ポリシーに追加されたものと見なします。 このカスタム アクセス許可は、`MyPerm.exe` と、`MyPerm.exe` の `MyOther.exe` 参照クラスに実装されます。 両方のアセンブリとも、完全信頼アセンブリ一覧に追加する必要があります。 `MyPerm.exe` アセンブリをコンピューター ポリシーの完全信頼一覧に追加するコマンドを次に示します。  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 `MyOther.exe` アセンブリをコンピューター ポリシーの完全信頼一覧に追加するコマンドを次に示します。  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 子コード グループをコンピューター ポリシー コード グループ階層のルートに追加するコマンドを次に示します。 新しいコード グループは **Internet** ゾーンのメンバーであり、**Execution** アクセス許可セットと関連付けられます。  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 共有 \\\netserver\netshare にローカル イントラネット アクセス許可を与える子コード グループを追加するコマンドを次に示します。  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 `Mypset` アクセス許可セットをユーザー ポリシーに追加するコマンドを次に示します。  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 1\.2 というラベルの付いたコード グループのユーザー ポリシーに含まれるアクセス許可セットを、 **Execution** アクセス許可セットに変更するコマンドを、次に示します。  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 1\.2.1 というラベルの付いたコード グループの既定のポリシーに含まれるメンバーシップ条件を変更し、 **exclusive**フラグの設定を変更するコマンドを次に示します。 メンバーシップ条件は、**Internet** ゾーンをソースとするコードとなるように定義され、**exclusive** フラグはオンになります。  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 `Mypset` という名前のアクセス許可セットを `newpset.xml` に含まれるアクセス許可セットに変更するコマンドを次に示します。 現在のリリースでは、コード グループ階層で使用されているアクセス許可の変更はサポートしていません。  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 ユーザー ポリシーのルート コード グループ (ラベル 1) を名前付きアクセス許可セット **Nothing** と関連付けるコマンドを次に示します。 このコマンドにより Caspol.exe は動作できなくなります。  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-recover**  
  
 最後に保存されたコンピューター ポリシーを復元するコマンドを次に示します。  
  
```console  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 1\.1 というラベルの付いたコード グループを削除するコマンドを次に示します。 このコード グループが子コード グループを持つ場合は、子グループも削除されます。  
  
```console  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 ユーザー ポリシーから **Execution** アクセス許可セットを削除するコマンドを次に示します。  
  
```console  
caspol -user -rempset Execution  
```  
  
 `Mypset` をユーザー ポリシー レベルから削除するコマンドを次に示します。  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 `myassembly` が所属するコンピューター ポリシーのすべてのコード グループを表示するコマンドを次に示します。  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 `myassembly` が所属するコンピューター ポリシー、エンタープライズ ポリシー、および指定されたカスタム ユーザー ポリシーのすべてのコード グループを表示するコマンドを次に示します。  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 コンピューター ポリシー レベルとユーザー ポリシー レベルに基づいて `testassembly` のアクセス許可を計算するコマンドを次に示します。  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>関連項目

- [ツール](index.md)
- [Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)
