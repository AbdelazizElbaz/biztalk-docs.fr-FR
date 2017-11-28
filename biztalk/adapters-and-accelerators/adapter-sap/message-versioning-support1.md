---
title: "Message de contrôle de version Support1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message versioning, support for
ms.assetid: 650b966e-9fa6-4af8-a061-7852a892717a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a2175ba0a3aafd052e6830439800569cf5f005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-versioning-support"></a><span data-ttu-id="95c85-102">Prise en charge du Versioning de message</span><span class="sxs-lookup"><span data-stu-id="95c85-102">Message Versioning Support</span></span>
<span data-ttu-id="95c85-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge le contrôle de version en incluant un composant de chaîne de version dans les actions de message, espaces de noms et les ID de nœud signalées pour les opérations.</span><span class="sxs-lookup"><span data-stu-id="95c85-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations.</span></span> <span data-ttu-id="95c85-104">La version actuelle est http://Microsoft.LobServices.Sap/2007/03.</span><span class="sxs-lookup"><span data-stu-id="95c85-104">The current version is http://Microsoft.LobServices.Sap/2007/03.</span></span> <span data-ttu-id="95c85-105">Cela signifie que, pour une commande RFC nommée « RFC_SAMPLE », l’opération de RFC exposée par l’adaptateur comporte les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="95c85-105">This means that for an RFC named "RFC_SAMPLE", the RFC operation surfaced by the adapter has the following:</span></span>  
  
-   <span data-ttu-id="95c85-106">ID de nœud : http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span><span class="sxs-lookup"><span data-stu-id="95c85-106">Node ID: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span></span>  
  
-   <span data-ttu-id="95c85-107">Action du message : http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span><span class="sxs-lookup"><span data-stu-id="95c85-107">Message action: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE</span></span>  
  
-   <span data-ttu-id="95c85-108">Namespace : http://Microsoft.LobServices.Sap/2007/03/Rfc</span><span class="sxs-lookup"><span data-stu-id="95c85-108">Namespace: http://Microsoft.LobServices.Sap/2007/03/Rfc</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95c85-109">Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.</span><span class="sxs-lookup"><span data-stu-id="95c85-109">This feature does not provide backward compatibility with the earlier versions of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c85-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95c85-110">See Also</span></span>  
 [<span data-ttu-id="95c85-111">Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="95c85-111">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)