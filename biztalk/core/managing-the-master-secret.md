---
title: Gestion du Secret | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, managing
- managing [Master Secret server]
- SSO, Master Secret server
ms.assetid: f79e8f3f-c740-4ea1-9589-b42552fcd52d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2505fa6f5ec1abc04ded45e7701fd4e5212f889
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-master-secret"></a><span data-ttu-id="6e688-102">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="6e688-102">Managing the Master Secret</span></span>
<span data-ttu-id="6e688-103">Le secret principal est la clé utilisée pour chiffrer les informations stockées dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="6e688-103">The master secret is the key used to encrypt all the information stored in the SSO database.</span></span> <span data-ttu-id="6e688-104">Si le serveur de secret principal échoue et que vous perdez le secret, vous ne pourrez pas récupérer les informations stockées dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="6e688-104">If the master secret server fails and you lose the secret, you will not be able to retrieve the information stored in the SSO database.</span></span> <span data-ttu-id="6e688-105">Aussi, est-il très important de sauvegarder le secret principal dès que celui-ci est généré.</span><span class="sxs-lookup"><span data-stu-id="6e688-105">Therefore, it is very important to back up the master secret as soon as you generate it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e688-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6e688-106">In This Section</span></span>  
  
-   [<span data-ttu-id="6e688-107">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="6e688-107">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="6e688-108">Comment sauvegarder le Secret principal</span><span class="sxs-lookup"><span data-stu-id="6e688-108">How to Back Up the Master Secret</span></span>](../core/how-to-back-up-the-master-secret.md)  
  
-   [<span data-ttu-id="6e688-109">Comment restaurer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="6e688-109">How to Restore the Master Secret</span></span>](../core/how-to-restore-the-master-secret.md)  
  
-   [<span data-ttu-id="6e688-110">Comment déplacer le serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="6e688-110">How to Move the Master Secret Server</span></span>](../core/how-to-move-the-master-secret-server.md)