---
title: "Les paramètres de lot pour le tiers ont expiré et l’orchestration de traitement par lot est terminée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f272b6-4da2-4736-8d61-ce48359f36dd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d56e06766a980c1ce293b211d2956a86c093726
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-settings-for-party-have-expired-and-the-batching-orchestration-is-being-terminated"></a><span data-ttu-id="ce7e6-102">Les paramètres de traitement par lot pour le tiers ont expiré et l'orchestration de traitement par lots est terminée</span><span class="sxs-lookup"><span data-stu-id="ce7e6-102">The batch settings for party have expired and the batching orchestration is being terminated</span></span>
## <a name="details"></a><span data-ttu-id="ce7e6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ce7e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce7e6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ce7e6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ce7e6-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ce7e6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ce7e6-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ce7e6-106">Event ID</span></span>|-|  
|<span data-ttu-id="ce7e6-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ce7e6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ce7e6-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ce7e6-108"> EDI</span></span>|  
|<span data-ttu-id="ce7e6-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ce7e6-109">Component</span></span>|<span data-ttu-id="ce7e6-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="ce7e6-110">Batching Engine</span></span>|  
|<span data-ttu-id="ce7e6-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ce7e6-111">Symbolic Name</span></span>|<span data-ttu-id="ce7e6-112">BatchSettingsExpired</span><span class="sxs-lookup"><span data-stu-id="ce7e6-112">BatchSettingsExpired</span></span>|  
|<span data-ttu-id="ce7e6-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ce7e6-113">Message Text</span></span>|<span data-ttu-id="ce7e6-114">Les paramètres de traitement par lot pour le tiers {0} ont expiré et l'orchestration de traitement par lots est terminée.</span><span class="sxs-lookup"><span data-stu-id="ce7e6-114">The batch settings for party {0} have expired and the batching orchestration is being terminated.</span></span> <span data-ttu-id="ce7e6-115">Aucun nouveau lot ne sera créé tant que le traitement par lot ne sera pas activé pour ce tiers</span><span class="sxs-lookup"><span data-stu-id="ce7e6-115">Further batches will not be generated till the batching is activated for this party</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce7e6-116">Explication</span><span class="sxs-lookup"><span data-stu-id="ce7e6-116">Explanation</span></span>  
 <span data-ttu-id="ce7e6-117">Cet avertissement indique que l'instance d'orchestration de traitement par lot a été désactivée car la fin des limites de l'activation a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="ce7e6-117">This Warning indicates that the batching orchestration instance has been deactivated because the end of the activation range has been reached.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce7e6-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ce7e6-118">User Action</span></span>  
 <span data-ttu-id="ce7e6-119">Pour résoudre cette erreur, redémarrez le processus de traitement par lot en effectuant l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce7e6-119">To resolve this error, restart the batching process by doing the following:</span></span>  
  
1.  <span data-ttu-id="ce7e6-120">Ouvrez la console Administration de BizTalk Server, puis accédez à la page Paramètres de création de lots d'échange de la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="ce7e6-120">Open the BizTalk Server Administration Console, and move to the Interchange Batch Creation Settings Page of the EDI Properties dialog box.</span></span>  
  
2.  <span data-ttu-id="ce7e6-121">Réinitialiser les critères de fin et redémarrez l’orchestration en cliquant sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce7e6-121">Reset the end criteria, and then restart the orchestration by clicking **Start**.</span></span>  
  
3.  <span data-ttu-id="ce7e6-122">Si la valeur datetime de début est antérieure à l’heure lorsque vous avez cliqué sur **Démarrer**, cliquez sur **Oui** pour mettre à jour la valeur datetime de début à la date/heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="ce7e6-122">If the Start datetime is prior to the time when you clicked **Start**, click **Yes** to update the Start datetime to the current datetime.</span></span>