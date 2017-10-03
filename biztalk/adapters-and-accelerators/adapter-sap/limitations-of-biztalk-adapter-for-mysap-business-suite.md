---
title: "Limitations de l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, limitations of
- IDOC, sending an IDOC to an SAP system
ms.assetid: 1ca1e0cf-7ae7-4a8b-8363-e5f3746e8e26
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d392178cd49918151f0ad86c73a5fcba712d6b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="7c8d6-102">Limitations de l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="7c8d6-102">Limitations of BizTalk Adapter for mySAP Business Suite</span></span>

## <a name="limitations-list"></a><span data-ttu-id="7c8d6-103">Liste des limitations</span><span class="sxs-lookup"><span data-stu-id="7c8d6-103">Limitations list</span></span>
<span data-ttu-id="7c8d6-104">Les éléments suivants sont connus des limitations de la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7c8d6-104">The following are known limitations of the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]:</span></span>  
  
-   <span data-ttu-id="7c8d6-105">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] n’est pas compatible avec l’adaptateur Microsoft BizTalk pour mySAP Business Suite, la version précédente de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-105">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is not compatible with Microsoft BizTalk Adapter for mySAP Business Suite, the previous release of the adapter.</span></span> <span data-ttu-id="7c8d6-106">Cette version de l’adaptateur ne prend pas en charge les envoyer et recevoir des messages ayant des schémas générés à l’aide de la version antérieure de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-106">This release of the adapter does not support sending and receiving messages having schemas generated using the earlier version of the adapter.</span></span>  
  
-   <span data-ttu-id="7c8d6-107">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge les normes RFC avec les types de paramètre complexe, y compris les types de table (hiérarchiques) ITAB II.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-107">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs with complex parameter types, including ITAB II (hierarchical) table types.</span></span>  
  
-   <span data-ttu-id="7c8d6-108">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge les RFC ayant des types ABAP personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support RFCs having custom ABAP types.</span></span>  
  
-   <span data-ttu-id="7c8d6-109">En raison de problèmes de délai d’attente un traitement par la bibliothèque cliente sous-jacente, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-109">Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support command and connection timeout.</span></span>  
  
-   <span data-ttu-id="7c8d6-110">Si vous modifiez l’heure système de l’ordinateur qui exécute l’hôte BizTalk Server, l’heure n’est pas automatiquement actualisé dans l’hôte BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-110">If you change the system time of the computer running the BizTalk Server host, the time is not updated automatically in the BizTalk Server host.</span></span> <span data-ttu-id="7c8d6-111">Cela peut entraîner un comportement incorrect des opérations entrantes qui utilisent le port de réception de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-111">This could lead to incorrect behavior of the inbound operations that use the receive port of BizTalk Server.</span></span> <span data-ttu-id="7c8d6-112">Pour résoudre ce problème, vous devez redémarrer l’instance d’hôte qui possède un port de réception après avoir modifié l’heure système de l’ordinateur exécutant.</span><span class="sxs-lookup"><span data-stu-id="7c8d6-112">As a workaround, you must restart the host instance that has a receive port, after you have changed the system time of the computer running it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8d6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c8d6-113">See Also</span></span>  
 [<span data-ttu-id="7c8d6-114">Comprendre l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="7c8d6-114">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)