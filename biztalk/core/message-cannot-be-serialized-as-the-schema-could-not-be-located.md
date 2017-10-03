---
title: "Message ne peut pas être sérialisé car le schéma n’a pas pu être localisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37897c04-650d-4695-846d-b8ba61365647
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b887d4a07d7a461278d3858289882a9ce441e9e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-cannot-be-serialized-as-the-schema-could-not-be-located"></a><span data-ttu-id="229c7-102">Le message ne peut pas être sérialisé car le schéma n'a pu être localisé.</span><span class="sxs-lookup"><span data-stu-id="229c7-102">Message cannot be serialized as the schema could not be located</span></span>
## <a name="details"></a><span data-ttu-id="229c7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="229c7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="229c7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="229c7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="229c7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="229c7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="229c7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="229c7-106">Event ID</span></span>|-|  
|<span data-ttu-id="229c7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="229c7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="229c7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="229c7-108"> EDI</span></span>|  
|<span data-ttu-id="229c7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="229c7-109">Component</span></span>|<span data-ttu-id="229c7-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="229c7-110">EDI Engine</span></span>|  
|<span data-ttu-id="229c7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="229c7-111">Symbolic Name</span></span>|<span data-ttu-id="229c7-112">MessageSerializationFailureDueToMissingSchema</span><span class="sxs-lookup"><span data-stu-id="229c7-112">MessageSerializationFailureDueToMissingSchema</span></span>|  
|<span data-ttu-id="229c7-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="229c7-113">Message Text</span></span>|<span data-ttu-id="229c7-114">Le message ne peut pas être sérialisé car le schéma {0} n'a pu être localisé.</span><span class="sxs-lookup"><span data-stu-id="229c7-114">Message can not be serialized as the schema {0} could not be located.</span></span> <span data-ttu-id="229c7-115">Soit le schéma n'est pas déployé, soit plusieurs copies sont déployées.</span><span class="sxs-lookup"><span data-stu-id="229c7-115">Either the schema is not deployed or multiple copies are deployed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="229c7-116">Explication</span><span class="sxs-lookup"><span data-stu-id="229c7-116">Explanation</span></span>  
 <span data-ttu-id="229c7-117">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu sérialiser l'échange sortant, car il n'est pas parvenu à déterminer le schéma qu'il devait utiliser pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="229c7-117">This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the pipeline could not determine the schema that it needed to use to serialize the interchange.</span></span> <span data-ttu-id="229c7-118">Le schéma n'était pas déployé ou plusieurs copies du schéma étaient déployées.</span><span class="sxs-lookup"><span data-stu-id="229c7-118">The schema was either not deployed or multiple copies of the schema were deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="229c7-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="229c7-119">User Action</span></span>  
 <span data-ttu-id="229c7-120">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="229c7-120">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="229c7-121">Si le schéma associé à l'échange n'a pas été déployé, ouvrez Visual Studio, ajoutez le schéma à un projet BizTalk, puis créez et déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="229c7-121">If the schema associated with the interchange has not been deployed, open Visual Studio, add the schema to a BizTalk project, and then build and deploy the project.</span></span>  
  
2.  <span data-ttu-id="229c7-122">Si plusieurs copies du schéma ont été déployées, ouvrez Visual Studio et annulez le déploiement de toutes les copies du schéma associé à l'échange, à l'exception d'une.</span><span class="sxs-lookup"><span data-stu-id="229c7-122">If more than one copy of the schema has been deployed, open Visual Studio, and undeploy all but one of the copies of the schema associated with the interchange.</span></span>