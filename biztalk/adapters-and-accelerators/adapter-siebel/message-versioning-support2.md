---
title: "Message de contrôle de version Support2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message versioning, support for
ms.assetid: 5b7b9202-9f45-450e-918f-b26a03711aab
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04514a9c55fa29a930b6ba7467177d6a754ff3db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-versioning-support"></a><span data-ttu-id="a2c3c-102">Prise en charge du Versioning de message</span><span class="sxs-lookup"><span data-stu-id="a2c3c-102">Message Versioning Support</span></span>
<span data-ttu-id="a2c3c-103">Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] prend en charge le contrôle de version en incluant un composant de chaîne de version dans les actions de message, espaces de noms et les ID de nœud signalées pour les opérations.</span><span class="sxs-lookup"><span data-stu-id="a2c3c-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations.</span></span> <span data-ttu-id="a2c3c-104">La version actuelle est http://Microsoft.LobServices.Siebel/2007/03.</span><span class="sxs-lookup"><span data-stu-id="a2c3c-104">The current version is http://Microsoft.LobServices.Siebel/2007/03.</span></span> <span data-ttu-id="a2c3c-105">Cela signifie que pour une opération d’insertion sur un objet métier de compte dans le référentiel Siebel, l’opération d’insertion par l’adaptateur dispose des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a2c3c-105">This means that for an Insert operation on an Account business object in the Siebel repository, the Insert operation surfaced by the adapter has the following:</span></span>  
  
-   <span data-ttu-id="a2c3c-106">ID de nœud : http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span><span class="sxs-lookup"><span data-stu-id="a2c3c-106">Node ID: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span></span>  
  
-   <span data-ttu-id="a2c3c-107">Action du message : http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span><span class="sxs-lookup"><span data-stu-id="a2c3c-107">Message action: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert</span></span>  
  
-   <span data-ttu-id="a2c3c-108">Namespace : http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation</span><span class="sxs-lookup"><span data-stu-id="a2c3c-108">Namespace: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c3c-109">Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.</span><span class="sxs-lookup"><span data-stu-id="a2c3c-109">This feature does not provide backward compatibility with the earlier versions of the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c3c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c3c-110">See Also</span></span>  
 [<span data-ttu-id="a2c3c-111">Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="a2c3c-111">Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)