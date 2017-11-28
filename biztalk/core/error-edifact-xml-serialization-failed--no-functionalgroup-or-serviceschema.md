---
title: "Échec de la sérialisation Xml de l’échange EDIFACT en raison d’une structure non valide, aucun FunctionalGroup ou ServiceSchema | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 530faadd-e301-4743-b4b3-b04ba7578f1d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f79d64a9ec19e62f13220be056335bf2d249519a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-functionalgroup-or-serviceschema"></a><span data-ttu-id="24147-102">Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide, absence de FunctionalGroup ou ServiceSchema.</span><span class="sxs-lookup"><span data-stu-id="24147-102">Edifact interchange Xml serialization failed due to invalid structure, no FunctionalGroup or ServiceSchema</span></span>
## <a name="details"></a><span data-ttu-id="24147-103">Détails</span><span class="sxs-lookup"><span data-stu-id="24147-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24147-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="24147-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="24147-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="24147-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="24147-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="24147-106">Event ID</span></span>|-|  
|<span data-ttu-id="24147-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="24147-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="24147-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="24147-108"> EDI</span></span>|  
|<span data-ttu-id="24147-109">Composant</span><span class="sxs-lookup"><span data-stu-id="24147-109">Component</span></span>|<span data-ttu-id="24147-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="24147-110">EDI Engine</span></span>|  
|<span data-ttu-id="24147-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="24147-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="24147-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="24147-112">Message Text</span></span>|<span data-ttu-id="24147-113">Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide.</span><span class="sxs-lookup"><span data-stu-id="24147-113">Edifact interchange Xml serialization failed due to invalid structure.</span></span> <span data-ttu-id="24147-114">Recherche de FunctionalGroup ou de ServiceSchema pour UNZ, mais aucun n'a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="24147-114">Looking for FunctionalGroup or ServiceSchema for UNZ, but none found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="24147-115">Explication</span><span class="sxs-lookup"><span data-stu-id="24147-115">Explanation</span></span>  
 <span data-ttu-id="24147-116">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter un échange reçu par lot EDIFACT qui a été préservé, car les balises TransactionSetGroup ou FunctionalGroup n'étaient pas incluses dans le fichier d'échange XML.</span><span class="sxs-lookup"><span data-stu-id="24147-116">This Error/Warning/Information event indicates that the send pipeline could not process an EDIFACT batched interchange that was preserved because the TransactionSetGroup or FunctionalGroup tags were not included in the interchange XML file.</span></span>  
  
 <span data-ttu-id="24147-117">Lorsque BizTalk traite un échange reçu par lot qui est préservé, une balise XML est attribuée à un groupe de documents informatisés ou à un groupe de groupes dans le fichier XML de l'échange.</span><span class="sxs-lookup"><span data-stu-id="24147-117">When BizTalk processes a batched interchange that is preserved, a group of transaction sets or a group of groups in the interchange's XML file are given an XML tag.</span></span> <span data-ttu-id="24147-118">Une balise FunctionalGroup est attribuée au groupe de groupes.</span><span class="sxs-lookup"><span data-stu-id="24147-118">A group of groups is given the FunctionalGroup tag.</span></span> <span data-ttu-id="24147-119">La balise ServiceSchema indique le schéma de contrôle utilisé pour l'échange reçu par lot préservé.</span><span class="sxs-lookup"><span data-stu-id="24147-119">The ServiceSchema flag indicates the control schema used for the preserved-batch interchange.</span></span> <span data-ttu-id="24147-120">Cette condition d'erreur se produit si vous configurez un lot préservé via un pipeline de réception et un pipeline d'envoi de transmission de transfert.</span><span class="sxs-lookup"><span data-stu-id="24147-120">This error condition occurs if you set up a preserved batch using a receive pipeline and a passthrough transmit send pipeline.</span></span> <span data-ttu-id="24147-121">Les balises sont définies par le pipeline de réception et sont supprimées par le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="24147-121">The tags are set by the receive pipeline and stripped out by the send pipeline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="24147-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="24147-122">User Action</span></span>  
 <span data-ttu-id="24147-123">Pour remédier à cette erreur, vérifiez que la structure XML du fichier XML généré pour le lot préservé est bien formée, avec la balise FunctionalGroup (pour plusieurs groupes) et/ou la balise ServiceSchema (pour le schéma de contrôle utilisé pour l'échange reçu par lot préservé).</span><span class="sxs-lookup"><span data-stu-id="24147-123">To resolve this error, ensure that the XML file generated for the preserved batch has a well-formed XML structure with the FunctionalGroup tag (for multiple groups) and/or the ServiceSchema tag (for the control schema used for the preserved-batch interchange).</span></span>