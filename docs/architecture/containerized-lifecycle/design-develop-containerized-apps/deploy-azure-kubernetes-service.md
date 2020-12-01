---
title: 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
description: Azure Kubernetes Service を使用して、アプリケーションをデプロイする方法について説明します。
ms.date: 08/06/2020
ms.openlocfilehash: ba9887c0a4837c16a60ebeb006416c0fa8c105e0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032204"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) へのデプロイ

Azure コマンドライン インターフェイス (Azure CLI) がインストールされている任意のクライアント オペレーティング システム (Windows、macOS、または Linux) を使用して、AKS と対話することができます。 詳細については、使用可能な環境に関する [Azure CLI ドキュメント](/cli/azure/?view=azure-cli-latest)と[インストール ガイド](/cli/azure/install-azure-cli?view=azure-cli-latest)を参照してください。

## <a name="create-the-aks-environment-in-azure"></a>Azure で AKS 環境を作成する

AKS 環境を作成するにはいくつかの方法があります。 これを行うには、Azure CLI コマンドを使用するか、または Azure portal を使用します。

ここでは、クラスターを作成するための Azure CLI、および結果を確認するための Azure portal を使用して、例をいくつか調べることができます。 また、開発用コンピューターに、Kubectl と Docker も備えている必要があります。

## <a name="create-the-aks-cluster"></a>AKS クラスターを作成する

次のコマンドを使用して、AKS クラスターを作成します (リソース グループが存在している必要があります)。

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> `--node-vm-size` パラメーターと `--node-count` パラメーターの値は、サンプルまたは開発アプリケーションに適しています。

作成ジョブが完了したら、次のことを確認できます。

- 最初のリソース グループに作成された AKS クラスター。
- 次の図に示すような、AKS クラスターに関連するリソースが含まれる関連する新しいリソース グループ。

AKS クラスターが含まれる最初のリソース グループは次のようになります。

![AKS リソース グループのブラウザー ビュー。](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

**図 4-17**.  Azure からの AKS リソース グループ ビュー。

AKS クラスター リソース グループは次のようになります。

![Azure AKS リソース グループのブラウザー ビュー。](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

**図 4-18**. Azure からの AKS ビュー。

> [!IMPORTANT]
> 一般に、AKS クラスター リソース グループ内のリソースを変更する必要はありません。 たとえば、AKS クラスターを削除すると、リソース グループが削除されます。

`Azure CLI` と `Kubectl` を使用して作成したノードを表示することもできます。

最初に、資格情報を取得します。

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上記のコマンドからのコンソール出力:/home/miguel/.kube/config の現在のコンテキストとしてマージされた "explore-docker-aks"。](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

**図 4-19** `aks get-credentials` コマンド結果。

次に、Kubectl からノードを取得します。

```console
kubectl get nodes
```

![上記のコマンドからのコンソール出力:状態、経過時間 (実行時間)、およびバージョンを含むノードの一覧](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

**図 4-20** `kubectl get nodes` コマンド結果。

> [!div class="step-by-step"]
> [前へ](orchestrate-high-scalability-availability.md)
> [次へ](docker-apps-development-environment.md)
