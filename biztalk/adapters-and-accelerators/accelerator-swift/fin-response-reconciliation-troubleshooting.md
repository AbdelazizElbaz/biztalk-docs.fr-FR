---
title: "Réponse FIN rapprochement dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, troubleshooting
- troubleshooting, FIN Response Reconciliation
ms.assetid: f62326aa-9a4e-4941-a9bb-20bde980f99e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a92812086f191d5777b387d9861b32a3147c1e96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation-troubleshooting"></a><span data-ttu-id="f7c9f-102">Réponse de la FIN la résolution des problèmes de rapprochement</span><span class="sxs-lookup"><span data-stu-id="f7c9f-102">FIN Response Reconciliation Troubleshooting</span></span>
## <a name="the-frr-bam-view-does-not-show-the-message-type-of-a-message"></a><span data-ttu-id="f7c9f-103">La vue FRR BAM n’affiche pas le type de message d’un message</span><span class="sxs-lookup"><span data-stu-id="f7c9f-103">The FRR BAM view does not show the message type of a message</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="f7c9f-104">Symptôme</span><span class="sxs-lookup"><span data-stu-id="f7c9f-104">Symptom</span></span>  
 <span data-ttu-id="f7c9f-105">La vue FRR BAM dans le site MRSR n’affiche pas le type de message pour un ou plusieurs messages.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-105">The FRR BAM view in MRSR site does not show the message type for one or more messages.</span></span> <span data-ttu-id="f7c9f-106">Toutes les autres données pour l’ou les messages sont indiquées, et le type de message s’affiche pour les instances de tous les autres types de message.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-106">All other data for the message or messages is shown, and the message type is shown for instances of all other message types.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="f7c9f-107">Cause possible</span><span class="sxs-lookup"><span data-stu-id="f7c9f-107">Possible Cause</span></span>  
 <span data-ttu-id="f7c9f-108">L’activité FRRMessageOut n’enregistre pas le type de message pour les messages F21 (accusés de réception/NAKs).</span><span class="sxs-lookup"><span data-stu-id="f7c9f-108">The FRRMessageOut activity does not record the message type for F21 messages (ACKs/NAKs).</span></span>  
  
### <a name="solution"></a><span data-ttu-id="f7c9f-109">Solution</span><span class="sxs-lookup"><span data-stu-id="f7c9f-109">Solution</span></span>  
 <span data-ttu-id="f7c9f-110">Si vous rencontrez ce problème, interpréter les messages qui ne sont pas un type de message répertorié dans la vue FRR BAM dans le site MRSR sous forme de message F21.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-110">If you encounter this problem, interpret any message that does not have a message type listed in the FRR BAM view in MRSR site as an F21 message.</span></span>  
  
## <a name="deploying-system-level-schemas-in-a-project-generates-an-error"></a><span data-ttu-id="f7c9f-111">Déploiement de schémas au niveau du système dans un projet génère une erreur</span><span class="sxs-lookup"><span data-stu-id="f7c9f-111">Deploying system-level schemas in a project generates an error</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="f7c9f-112">Symptôme</span><span class="sxs-lookup"><span data-stu-id="f7c9f-112">Symptom</span></span>  
 <span data-ttu-id="f7c9f-113">Lorsque vous tentez de déployer les schémas au niveau du système dans FrrSchemas.dll dans un projet, vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-113">When you attempt to deploy the system-level schemas in FrrSchemas.dll in a project, you receive an error.</span></span> <span data-ttu-id="f7c9f-114">Pour obtenir la liste de ces schémas, consultez [les Types de réponse de FIN](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7c9f-114">For a list of these schemas, see [FIN Response Types](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md).</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="f7c9f-115">Cause possible</span><span class="sxs-lookup"><span data-stu-id="f7c9f-115">Possible Cause</span></span>  
 <span data-ttu-id="f7c9f-116">Les schémas au niveau du système dans FrrSchemas.dll sont déjà déployés dans FrrSchemas.dll.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-116">The system-level schemas in FrrSchemas.dll are already deployed in FrrSchemas.dll.</span></span> <span data-ttu-id="f7c9f-117">Essayez de les déployer à nouveau entraîne une erreur.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-117">Trying to deploy them again results in an error.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="f7c9f-118">Solution</span><span class="sxs-lookup"><span data-stu-id="f7c9f-118">Solution</span></span>  
 <span data-ttu-id="f7c9f-119">Il n’est pas nécessaire de déployer les schémas dans FrrSchemas.dll au niveau du système.</span><span class="sxs-lookup"><span data-stu-id="f7c9f-119">There is no need to deploy the system-level schemas in FrrSchemas.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c9f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7c9f-120">See Also</span></span>  
 [<span data-ttu-id="f7c9f-121">Résolution des problèmes : Problèmes et résolutions</span><span class="sxs-lookup"><span data-stu-id="f7c9f-121">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)