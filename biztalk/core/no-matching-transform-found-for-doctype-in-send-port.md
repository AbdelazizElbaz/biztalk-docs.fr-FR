---
title: "Aucune transformation correspondante trouvée pour le type de document dans le Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23f62ac7-3849-49fe-a765-2be72880a4c9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bc45ac0edf425bc19ab526fac6b2690f3a6b6d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="no-matching-transform-found-for-doctype-in-send-port"></a><span data-ttu-id="3f5a7-102">Aucune transformation correspondante trouvée pour le type de document dans le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-102">No matching transform found for DocType in Send Port</span></span>
## <a name="details"></a><span data-ttu-id="3f5a7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3f5a7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f5a7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3f5a7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3f5a7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3f5a7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3f5a7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3f5a7-106">Event ID</span></span>|-|  
|<span data-ttu-id="3f5a7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3f5a7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3f5a7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="3f5a7-108"> EDI</span></span>|  
|<span data-ttu-id="3f5a7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="3f5a7-109">Component</span></span>|<span data-ttu-id="3f5a7-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="3f5a7-110">EDI Engine</span></span>|  
|<span data-ttu-id="3f5a7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3f5a7-111">Symbolic Name</span></span>|<span data-ttu-id="3f5a7-112">NoMatchingTransformFoundForSendPortAndDocType</span><span class="sxs-lookup"><span data-stu-id="3f5a7-112">NoMatchingTransformFoundForSendPortAndDocType</span></span>|  
|<span data-ttu-id="3f5a7-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3f5a7-113">Message Text</span></span>|<span data-ttu-id="3f5a7-114">Aucune transformation correspondante trouvée pour {0} DocType dans {{1} du Port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-114">No matching transform found for DocType {0} in Send Port {1}.</span></span> <span data-ttu-id="3f5a7-115">Incompatible avec les informations ExplorerOM</span><span class="sxs-lookup"><span data-stu-id="3f5a7-115">Inconsistent with ExplorerOM information</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f5a7-116">Explication</span><span class="sxs-lookup"><span data-stu-id="3f5a7-116">Explanation</span></span>  
 <span data-ttu-id="3f5a7-117">Cette erreur indique qu'aucune transformation correspondante n'a été trouvée pour un type de document ou un port d'envoi donnés.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-117">This error indicates that a matching transform was not found for a given DocType and SendPort.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f5a7-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3f5a7-118">User Action</span></span>  
 <span data-ttu-id="3f5a7-119">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3f5a7-119">To resolve this error, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="3f5a7-120">Ouvrez la console Administration de BizTalk, repérez le transport et cliquez avec le bouton droit de la souris sur son nom.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-120">Open the BizTalk Administration console, locate the transport, and right-click the transport name.</span></span>  
  
2.  <span data-ttu-id="3f5a7-121">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-121">Click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3f5a7-122">Dans la liste des types de port, sélectionnez celui qui convient.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-122">In the port Type list, select the correct port.</span></span> <span data-ttu-id="3f5a7-123">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-123">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="3f5a7-124">Dans la boîte de dialogue Propriétés de Port d’envoi [nom du port], cliquez sur **mappages sortants** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-124">In the [port name] Send Port Properties dialog box, click **Outbound Maps** in the left pane.</span></span>  
  
5.  <span data-ttu-id="3f5a7-125">Vérifiez que le mappage est répertorié à cet endroit et qu'il correspond au type de document adéquat.</span><span class="sxs-lookup"><span data-stu-id="3f5a7-125">Verify that the map is listed here and that it corresponds to the correct document type.</span></span>