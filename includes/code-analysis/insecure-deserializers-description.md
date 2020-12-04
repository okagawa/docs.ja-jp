---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2020
ms.locfileid: "96591101"
---
安全でないデシリアライザーは、信頼できないデータを逆シリアル化するときに脆弱です。 攻撃者は、悪意のある副作用を持つオブジェクトを挿入するために、シリアル化されたデータを変更し、予期しない型を含めることができます。 セキュリティで保護されていないデシリアライザーに対する攻撃は、たとえば、基になるオペレーティングシステムでコマンドを実行したり、ネットワークを介して通信したり、ファイルを削除したりすることができます。
