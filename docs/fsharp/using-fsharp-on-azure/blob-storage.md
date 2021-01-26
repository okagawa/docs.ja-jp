---
title: F を使用した Azure Blob Storage の概要#
description: Azure Blob Storage を使用して、非構造化データをクラウドに格納します。
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 58c120c26a1e99481b49ae3a0fb096a2188f359e
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794812"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F を使用した Azure Blob Storage の概要\#

Azure Blob Storage は、非構造化データをオブジェクトまたは blob としてクラウドに格納するサービスです。 Blob Storage は、ドキュメント、メディア ファイル、アプリケーション インストーラーなど、任意の種類のテキスト データやバイナリ データを格納できます。 Blob Storage は、オブジェクト ストレージとも呼ばれます。

この記事では、Blob storage を使用して一般的なタスクを実行する方法について説明します。 サンプルは、.NET 用の Azure Storage クライアントライブラリを使用して F # を使用して記述されています。 説明するタスクには、blob のアップロード、一覧表示、ダウンロード、および削除の方法が含まれます。

Blob storage の概念の概要については、「 [.net ガイド](/azure/storage/blobs/storage-quickstart-blobs-dotnet)」を参照してください。

## <a name="prerequisites"></a>前提条件

このガイドを使用するには、最初に [Azure ストレージアカウントを作成](/azure/storage/common/storage-account-create)する必要があります。 また、このアカウントのストレージアクセスキーも必要です。

## <a name="create-an-f-script-and-start-f-interactive"></a>F # スクリプトを作成して F# インタラクティブを開始する

この記事のサンプルは、F # アプリケーションと F # スクリプトのどちらでも使用できます。 F # スクリプトを作成するには、 `.fsx` `blobs.fsx` f # 開発環境で、などの拡張子を持つファイルを作成します。

次に、[パケット](https://fsprojects.github.io/Paket/)や[NuGet](https://www.nuget.org/)などの[パッケージマネージャー](package-management.md)を使用して `WindowsAzure.Storage` 、 `Microsoft.WindowsAzure.ConfigurationManager` ディレクティブを使用して、パッケージとパッケージをインストールし、スクリプトにおよびを参照 `WindowsAzure.Storage.dll` し `Microsoft.WindowsAzure.Configuration.dll` `#r` ます。

### <a name="add-namespace-declarations"></a>名前空間宣言の追加

次の `open` ステートメントを `blobs.fsx` ファイルの先頭に追加します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得する

このチュートリアルでは、Azure Storage 接続文字列が必要です。 接続文字列の詳細については、「 [ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)」を参照してください。

このチュートリアルでは、次のように、スクリプトに接続文字列を入力します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

ただし、実際のプロジェクトではこの方法は **お勧めできません** 。 ストレージ アカウント キーは、ストレージ アカウントの root パスワードに似ています。 ストレージ アカウント キーは常に慎重に保護してください。 このキーを他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーン テキスト ファイルに保存したりしないでください。 侵害された可能性があると思われる場合は、Azure portal を使用してキーを再生成することができます。

実際のアプリケーションでは、ストレージ接続文字列を維持する最善の方法は構成ファイルにあります。 構成ファイルから接続文字列を取得するには、次の手順を実行します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Configuration Manager の使用はオプションです。 .NET Framework の型などの API を使用することもでき `ConfigurationManager` ます。

### <a name="parse-the-connection-string"></a>接続文字列を解析する

接続文字列を解析するには、次のように指定します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

これにより、が返さ `CloudStorageAccount` れます。

### <a name="create-some-local-dummy-data"></a>いくつかのローカルダミーデータを作成する

開始する前に、スクリプトのディレクトリにダミーのローカルデータを作成します。 後でこのデータをアップロードします。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob service クライアントの作成

型を使用すると、 `CloudBlobClient` blob ストレージに格納されているコンテナーと blob を取得できます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

これで、Blob Storage に対してデータの読み取りと書き込みを実行するコードを記述する準備が整いました。

## <a name="create-a-container"></a>コンテナーを作成する

この例は、コンテナーがない場合に、コンテナーを作成する方法を示しています。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

既定では、新しいコンテナーはプライベートなので、このコンテナーから BLOB をダウンロードするにはストレージ アクセス キーを指定する必要があります。 コンテナー内のファイルをだれでも利用できるようにする場合は、次のコードを使ってコンテナーをパブリックに設定できます。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

パブリック コンテナー内の BLOB は、インターネットに接続しているすべてのユーザーが表示できますが、変更または削除できるのは、適切なアカウント アクセス キーまたは Shared Access Signature を持っているユーザーだけです。

## <a name="upload-a-blob-into-a-container"></a>コンテナーに BLOB をアップロードする

Azure Blob Storage では、ブロック BLOB とページ BLOB がサポートされています。 ほとんどの場合、ブロック blob を使用することをお勧めします。

ファイルをブロック blob にアップロードするには、コンテナーの参照を取得し、それを使用してブロック blob の参照を取得します。 Blob の参照を取得したら、メソッドを呼び出すことによって、データの任意のストリームをアップロードでき `UploadFromFile` ます。 この操作では、blob が既に存在していない場合は作成し、存在する場合は上書きします。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>コンテナー内の BLOB を一覧表示する

コンテナー内の BLOB を一覧表示するには、まず、コンテナーの参照を取得します。 その後、コンテナーのメソッドを使用し `ListBlobs` て、その中の blob やディレクトリを取得できます。 返されるの豊富なプロパティおよびメソッドのセットにアクセスするには `IListBlobItem` 、それを `CloudBlockBlob` 、、 `CloudPageBlob` またはオブジェクトにキャストする必要があり `CloudBlobDirectory` ます。 型がわからない場合は、型チェックを使うとどれにキャストすればよいかがわかります。 次のコードは、 `mydata` コンテナー内の各アイテムの URI を取得して出力する方法を示しています。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Blob には、名前にパス情報を指定することもできます。 これで、従来のファイル システムと同じように、整理およびスキャン可能な仮想ディレクトリ構造が作成されます。 ディレクトリ構造は仮想のみであり、Blob storage で使用できるリソースはコンテナーと blob のみです。 ただし、ストレージクライアントライブラリは、 `CloudBlobDirectory` 仮想ディレクトリを参照するオブジェクトを提供し、この方法で構成されている blob を操作するプロセスを簡略化します。

たとえば、 `photos`という名前のコンテナーに次の一連のブロック BLOB があったとします。

*photo1.jpg*\
*2015/architecture/description.txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/アーキテクチャ/photo5.jpg*\
*2016/アーキテクチャ/photo6.jpg*\
*2016/アーキテクチャ/description.txt*\
*2016/photo7.jpg*\

コンテナーでを呼び出すと `ListBlobs` (上記のサンプルのように)、階層化された一覧が返されます。 `CloudBlobDirectory`コンテナー内のディレクトリと blob をそれぞれ表すオブジェクトとオブジェクトの両方が含まれている場合、 `CloudBlockBlob` 結果の出力は次のようになります。

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

必要に応じて、 `UseFlatBlobListing` メソッドのパラメーター `ListBlobs` をに設定でき `true` ます。 この場合、コンテナー内のすべての blob がオブジェクトとして返され `CloudBlockBlob` ます。 フラットリストを返すためのの呼び出しは次の `ListBlobs` ようになります。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

また、コンテナーの現在の内容によっては、結果は次のようになります。

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>BLOB をダウンロードする

Blob をダウンロードするには、まず blob の参照を取得してから、メソッドを呼び出し `DownloadToStream` ます。 次の例では、メソッドを使用して、 `DownloadToStream` ローカルファイルに永続化できるストリームオブジェクトに blob の内容を転送します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

メソッドを使用し `DownloadToStream` て、blob の内容をテキスト文字列としてダウンロードすることもできます。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>BLOB を削除する

Blob を削除するには、まず blob の参照を取得し、次 `Delete` にそのメソッドを呼び出します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>BLOB をページで非同期に一覧表示する

多数の BLOB を一覧表示する場合や、1 回の一覧表示操作で返される結果の数を制御する場合には、BLOB の一覧を結果のページで表示できます。 この例は、大きな結果のセットを返すために待機している間に実行がブロックされないように、結果をページで非同期に返す方法を示しています。

この例はフラット blob リストを示していますが、 `useFlatBlobListing` メソッドのパラメーターをに設定することによって、階層化された一覧を作成することもでき `ListBlobsSegmentedAsync` `false` ます。

このサンプルでは、ブロックを使用して非同期メソッドを定義し `async` ます。 キーワードは、 ``let!`` リスティングタスクが完了するまで、サンプルメソッドの実行を中断します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

次のように、この非同期ルーチンを使用できるようになりました。 まずダミーデータをアップロードします (このチュートリアルで既に作成したローカルファイルを使用します)。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

ここで、ルーチンを呼び出します。 `Async.RunSynchronously`非同期操作の実行を強制するには、を使用します。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>追加 BLOB への書き込み

追加 BLOB は、ログ記録などの追加操作のために最適化されています。 ブロック blob と同様に、追加 blob はブロックで構成されますが、追加 blob に新しいブロックを追加すると、常に blob の末尾に追加されます。 追加 BLOB の既存のブロックは更新したり、削除することはできません。 追加 BLOB のブロック ID はブロック BLOB 用のため、公開されることはありません。

追加 BLOB 内の各ブロックは、最大 4 MB のサイズにすることができます。また追加 BLOB には最大 50,000 のブロックを含めることができます。 よって追加 BLOB の最大サイズは 195 GB (4 MB X 50,000 ブロック) よりも少し大きくなります。

次の例では、新しい追加 blob を作成し、データを追加して、単純なログ記録操作をシミュレートします。

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

3 つの BLOB タイプにおける違いの詳細については、「 [Understanding Block Blobs, Page Blobs, and Append Blobs (ブロック BLOB、ページ BLOB、追加 BLOB を理解する)](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) 」をご覧ください。

## <a name="concurrent-access"></a>同時アクセス

複数のクライアントまたは複数のプロセス インスタンスからの BLOB への同時アクセスをサポートするには、**ETag** または **占有** を使います。

- **Etag** - BLOB またはコンテナーが別のプロセスによって変更されていることを検出する手段を提供します。

- **リース** -一定期間、blob に対する排他、更新、書き込み、または削除のアクセス権を取得する方法を提供します。

詳細については、「 [Microsoft Azure Storage での同時実行の管理](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)」を参照してください。

## <a name="naming-containers"></a>コンテナーの名前付け

Azure Storage のどの BLOB もコンテナーに格納する必要があります。 コンテナーは、BLOB 名の一部を形成しています。 たとえば、次の BLOB の URI のサンプルでは、 `mydata` がコンテナーの名前です。

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

コンテナー名は有効な DNS 名で、次の名前規則に準拠している必要があります。

1. コンテナー名は英文字または数字で始まり、英文字、数字、ダッシュ (-) 文字のみを含めることができます。
1. すべてのダッシュ (-) 文字は、その直前または直後に文字または数字が使用されている必要があります。連続するダッシュ文字は、コンテナー名では使用できません。
1. コンテナー名の文字はすべて小文字である必要があります。
1. コンテナー名の長さは、3 ～ 63 文字にする必要があります。

コンテナーの名前は、常に小文字である必要があります。 コンテナー名に大文字が含まれている場合や、コンテナーの名前付け規則の他の違反がある場合、400 エラー (無効な要求) が発生することがあります。

## <a name="managing-security-for-blobs"></a>BLOB のセキュリティの管理

既定では、Azure Storage はアカウント所有者へのアクセスを制限することによってデータのセキュリティを維持します。アカウントの所有者は、アカウント アクセス キーを所持している人です。 ストレージ アカウント内の BLOB データを共有する必要がある場合は、アカウント アクセス キーのセキュリティを損なわずに共有することが重要です。 また、ネットワーク経由の送信と Azure Storage でのセキュリティを確保するために、BLOB データを暗号化することもできます。

### <a name="controlling-access-to-blob-data"></a>BLOB データへのアクセスの制御

既定では、ストレージ アカウント内の BLOB データには、ストレージ アカウント所有者だけがアクセスできます。 Blob Storage に対する認証要求には、既定ではアカウント アクセス キーが必要です。 ただし、特定の blob データを他のユーザーが使用できるようにすることもできます。

### <a name="encrypting-blob-data"></a>BLOB データの暗号化

Azure Storage は、クライアントとサーバーの両方で blob データの暗号化をサポートしています。

## <a name="next-steps"></a>次のステップ

これで、Blob Storage の基本を学習できました。さらに詳細な情報が必要な場合は、次のリンク先を参照してください。

### <a name="tools"></a>ツール

- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Blob、テーブル、およびキューの Azure Storage を探索し、その資産に CRUD 操作を簡単に適用するために使用できる F # 型プロバイダー。

- [Fsharp.core](https://github.com/fsprojects/FSharp.Azure.Storage)\
Microsoft Azure Table Storage サービスを使用するための F # API

- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Windows、OS X、Linux で Azure Storage データを視覚的に操作できる Microsoft 製の無料のスタンドアロンアプリです。

### <a name="blob-storage-reference"></a>Blob Storage リファレンス

- [.NET 用 Azure Storage API](/dotnet/api/overview/azure/storage)
- [Azure Storage サービスの REST API リファレンス](/rest/api/storageservices/)

### <a name="related-guides"></a>関連ガイド

- [.NET 用の Azure Blob Storage サンプル](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [AzCopy を使ってみる](/azure/storage/common/storage-use-azcopy-v10)
- [Azure Storage の接続文字列を構成する](/azure/storage/common/storage-configure-connection-string)
- [Azure Storage Team Blog](/archive/blogs/windowsazurestorage/)
- [クイック スタート: .NET を使用してオブジェクト ストレージ内に BLOB を作成する](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
