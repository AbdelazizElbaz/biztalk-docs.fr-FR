---
title: "Type de message n’est pas reconnu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad4094bf-af00-4d5c-9661-7c8abcb1b722
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd58907b61e68140ccf68d8256882b81e46bd863
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognised-message-type"></a><span data-ttu-id="72542-102">Type de message non reconnu</span><span class="sxs-lookup"><span data-stu-id="72542-102">Unrecognised message type</span></span>
## <a name="details"></a><span data-ttu-id="72542-103">Détails</span><span class="sxs-lookup"><span data-stu-id="72542-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72542-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="72542-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="72542-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="72542-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="72542-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="72542-106">Event ID</span></span>|-|  
|<span data-ttu-id="72542-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="72542-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="72542-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="72542-108"> EDI</span></span>|  
|<span data-ttu-id="72542-109">Composant</span><span class="sxs-lookup"><span data-stu-id="72542-109">Component</span></span>|<span data-ttu-id="72542-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="72542-110">EDI Engine</span></span>|  
|<span data-ttu-id="72542-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="72542-111">Symbolic Name</span></span>|<span data-ttu-id="72542-112">UnRecognizedMessageType</span><span class="sxs-lookup"><span data-stu-id="72542-112">UnRecognizedMessageType</span></span>|  
|<span data-ttu-id="72542-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="72542-113">Message Text</span></span>|<span data-ttu-id="72542-114">Type de message non reconnu.</span><span class="sxs-lookup"><span data-stu-id="72542-114">Unrecognised message type.</span></span> <span data-ttu-id="72542-115">Impossible de poursuivre.</span><span class="sxs-lookup"><span data-stu-id="72542-115">Cannot proceed further.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="72542-116">Explication</span><span class="sxs-lookup"><span data-stu-id="72542-116">Explanation</span></span>  
 <span data-ttu-id="72542-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car aucun schéma de document n'a été déployé pour le type de document d'un document informatisé dans cet échange, ou BizTalk Server ne peut pas déterminer le type de document à partir du code identificateur, de la version et de l'espace de noms du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="72542-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because no document schema has been deployed for the document type of a transaction set in that interchange, or BizTalk Server cannot determine the document type from the transaction set identifier code, version, and namespace.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="72542-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="72542-118">User Action</span></span>  
 <span data-ttu-id="72542-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="72542-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="72542-120">Déployez un schéma de document pour le type de document d'un document informatisé dans l'échange, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="72542-120">Deploy a document schema for the document type of a transaction set in the interchange, and then resend the interchange.</span></span>  
  
-   <span data-ttu-id="72542-121">Vérifiez que les valeurs suivantes définissent un schéma valide : X12, l’espace de noms cible, version/publication et au document, tapez ; pour EDIFACT, l’espace de noms cible, le numéro de version de message, le numéro de version du message et le message type.</span><span class="sxs-lookup"><span data-stu-id="72542-121">Verify that the following values define a valid schema: for X12, the target namespace, version/release, and document type; for EDIFACT, the target namespace, message version number, message release number, and message type.</span></span> <span data-ttu-id="72542-122">Pour plus d'informations, consultez la section « Détection du schéma » de la rubrique « Résolution de tiers, détection du schéma et autorisation des messages EDI reçus » de l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72542-122">For more information, see the "Schema Discovery" section in the "Party Resolution, Schema Discovery, and Authorization for Received EDI Messages" topic in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>