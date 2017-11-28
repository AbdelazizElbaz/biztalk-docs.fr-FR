---
title: "Résolution des problèmes de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, troubleshooting
- troubleshooting, batching
ms.assetid: f47e1a16-47fd-4bd8-8dad-fcdba31a833e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94c8413a8022529e6ace56c50d5e6d75267a72e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-batching"></a><span data-ttu-id="3a7cb-102">Résolution des problèmes de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="3a7cb-102">Troubleshooting Batching</span></span>
<span data-ttu-id="3a7cb-103">Traite des problèmes liés à [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-103">Addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batching.</span></span>  
  
## <a name="error-activating-batch"></a><span data-ttu-id="3a7cb-104">Traitement d’activation erroné</span><span class="sxs-lookup"><span data-stu-id="3a7cb-104">Error activating batch</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="3a7cb-105">Symptôme</span><span class="sxs-lookup"><span data-stu-id="3a7cb-105">Symptom</span></span>  
 <span data-ttu-id="3a7cb-106">Impossible d’activer un lot.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-106">Unable to activate a batch.</span></span> <span data-ttu-id="3a7cb-107">Vous obtenez une erreur réseau générale.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-107">You get a general network error.</span></span>  
  
<span data-ttu-id="3a7cb-108">**Cause possible** : [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] a été redémarré, mais [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] n’était pas dans l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-108">**Possible Cause** : [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was restarted, but [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer was not.</span></span>  
  
<span data-ttu-id="3a7cb-109">**Résolution** : redémarrez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-109">**Resolution** : Restart [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="messages-are-not-batched-when-the-target-namespace-is-not-the-default"></a><span data-ttu-id="3a7cb-110">Les messages ne sont pas traités par lot lorsque l’espace de noms cible n’est pas la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3a7cb-110">Messages are not batched when the target namespace is not the default</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="3a7cb-111">Symptôme</span><span class="sxs-lookup"><span data-stu-id="3a7cb-111">Symptom</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="3a7cb-112">est pas le traitement par lot les messages.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-112"> is not batching messages.</span></span>  
  
<span data-ttu-id="3a7cb-113">**Cause possible** : parties Source et de destination ne sont pas dans le même espace de noms du schéma.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-113">**Possible Cause** : Source and destination parties are not in the same schema namespace.</span></span>  
  
<span data-ttu-id="3a7cb-114">**Résolution** : parties Source et de destination doivent utiliser le même espace de noms du schéma si la validation est requise.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-114">**Resolution** : Source and destination parties must use the same schema namespace if validation is required.</span></span> <span data-ttu-id="3a7cb-115">Assurez-vous que les parties de la source et de destination utilisent le même espace de noms du schéma.</span><span class="sxs-lookup"><span data-stu-id="3a7cb-115">Ensure the source and destination parties are using the same schema namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7cb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a7cb-116">See Also</span></span>  
 [<span data-ttu-id="3a7cb-117">Problèmes connus et dépannage dans HL7</span><span class="sxs-lookup"><span data-stu-id="3a7cb-117">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)