---
title: "Cette instance est en dehors de la fenêtre de Service de traitement par lot pour le partenaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e420d75-11fd-4221-9d97-814ca6e48c81
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e93e7e769a8f0e30b3753af690a69c5e6eaa9786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="this-instance-is-outside-the-batching-service-window-for-the-partner"></a><span data-ttu-id="3d8fc-102">Cette instance est en dehors de la fenêtre de service de traitement par lot pour le partenaire</span><span class="sxs-lookup"><span data-stu-id="3d8fc-102">This instance is outside the Batching Service window for the partner</span></span>
## <a name="details"></a><span data-ttu-id="3d8fc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3d8fc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d8fc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3d8fc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3d8fc-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3d8fc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3d8fc-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3d8fc-106">Event ID</span></span>|-|  
|<span data-ttu-id="3d8fc-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3d8fc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3d8fc-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="3d8fc-108"> EDI</span></span>|  
|<span data-ttu-id="3d8fc-109">Composant</span><span class="sxs-lookup"><span data-stu-id="3d8fc-109">Component</span></span>|<span data-ttu-id="3d8fc-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="3d8fc-110">Batching Engine</span></span>|  
|<span data-ttu-id="3d8fc-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3d8fc-111">Symbolic Name</span></span>|<span data-ttu-id="3d8fc-112">OutsideBatchingServiceWindow</span><span class="sxs-lookup"><span data-stu-id="3d8fc-112">OutsideBatchingServiceWindow</span></span>|  
|<span data-ttu-id="3d8fc-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3d8fc-113">Message Text</span></span>|<span data-ttu-id="3d8fc-114">Cette instance est en dehors de la fenêtre de service de traitement par lot pour le partenaire</span><span class="sxs-lookup"><span data-stu-id="3d8fc-114">This instance is outside the Batching Service window for the partner</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3d8fc-115">Explication</span><span class="sxs-lookup"><span data-stu-id="3d8fc-115">Explanation</span></span>  
 <span data-ttu-id="3d8fc-116">Cet événement de type erreur/avertissement/information indique qu'une instance de l'orchestration de traitement par lot n'a pas pu démarrer car l'instance était en dehors des limites d'activation pour le tiers.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-116">This Error/Warning/Information event indicates that an instance of the batching orchestration could not be started because the instance fell outside the activation range for the party.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3d8fc-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3d8fc-117">User Action</span></span>  
 <span data-ttu-id="3d8fc-118">Pour résoudre cette erreur, ouvrez la page Paramètres de création de lots d'échange des propriétés EDI pour le tiers et vérifiez que l'instance d'orchestration est incluse dans les limites d'activation.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-118">To resolve this error, open the Interchange Batch Creations Settings page of the EDI Properties for the party, and make sure that the orchestration instance is within the activation range.</span></span> <span data-ttu-id="3d8fc-119">Dans le cas contraire, modifiez la propriété d’heure de début, puis **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-119">If not, change the Start time property and then click **Start**.</span></span>