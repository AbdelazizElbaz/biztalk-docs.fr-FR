---
title: "Aurait dû contenir l’échange EDIFACT TransactionSetGroup ou FunctionalGroup Xml balises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34318133-211f-422d-acdf-b841ece5d2b0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb93582daf235a7f1f0633231e536f3c5b14ab0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-should-have-contained-transactionsetgroup-or-functionalgroup-xml-tags"></a><span data-ttu-id="f914e-102">L'échange EDIFACT aurait dû contenir les balises Xml TransactionSetGroup ou FunctionalGroup</span><span class="sxs-lookup"><span data-stu-id="f914e-102">Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags</span></span>
## <a name="details"></a><span data-ttu-id="f914e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f914e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f914e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f914e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f914e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f914e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f914e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f914e-106">Event ID</span></span>|-|  
|<span data-ttu-id="f914e-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f914e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f914e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f914e-108"> EDI</span></span>|  
|<span data-ttu-id="f914e-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f914e-109">Component</span></span>|<span data-ttu-id="f914e-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f914e-110">EDI Engine</span></span>|  
|<span data-ttu-id="f914e-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f914e-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="f914e-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f914e-112">Message Text</span></span>|<span data-ttu-id="f914e-113">L'échange EDIFACT aurait dû contenir les balises Xml TransactionSetGroup ou FunctionalGroup</span><span class="sxs-lookup"><span data-stu-id="f914e-113">Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f914e-114">Explication</span><span class="sxs-lookup"><span data-stu-id="f914e-114">Explanation</span></span>  
 <span data-ttu-id="f914e-115">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter un échange reçu par lot EDIFACT qui a été préservé, car les balises TransactionSetGroup ou FunctionalGroup n'étaient pas incluses dans le fichier d'échange XML.</span><span class="sxs-lookup"><span data-stu-id="f914e-115">This Error/Warning/Information event indicates that the send pipeline could not process an EDIFACT batched interchange that was preserved because the TransactionSetGroup or FunctionalGroup tags were not included in the interchange XML file.</span></span>  
  
 <span data-ttu-id="f914e-116">Lorsque BizTalk traite un échange reçu par lot qui est préservé, une balise XML est attribuée à un groupe de documents informatisés ou à un groupe de groupes dans le fichier XML de l'échange.</span><span class="sxs-lookup"><span data-stu-id="f914e-116">When BizTalk processes a batched interchange that is preserved, a group of transaction sets or a group of groups in the interchange's XML file are given an XML tag.</span></span> <span data-ttu-id="f914e-117">La balise TransactionSetGroup est attribuée à un groupe de documents informatiques.</span><span class="sxs-lookup"><span data-stu-id="f914e-117">A group of transaction sets is given the TransactionSetGroup tag.</span></span> <span data-ttu-id="f914e-118">Une balise FunctionalGroup est attribuée au groupe de groupes.</span><span class="sxs-lookup"><span data-stu-id="f914e-118">A group of groups is given the FunctionalGroup tag.</span></span> <span data-ttu-id="f914e-119">Cette condition d'erreur se produit si vous configurez un lot préservé via un pipeline de réception et un pipeline d'envoi de transmission de transfert.</span><span class="sxs-lookup"><span data-stu-id="f914e-119">This error condition occurs if you set up a preserved batch using a receive pipeline and a passthrough transmit send pipeline.</span></span> <span data-ttu-id="f914e-120">Les balises sont définies par le pipeline de réception et sont supprimées par le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f914e-120">The tags are set by the receive pipeline and stripped out by the send pipeline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f914e-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f914e-121">User Action</span></span>  
 <span data-ttu-id="f914e-122">Pour remédier à cette erreur, vérifiez que la structure XML du fichier XML généré pour le lot préservé est bien formée, avec la balise TransactionSetGroup (pour un groupe doté de plusieurs documents informatisés) et/ou la balise FunctionalGroup (pour plusieurs groupes).</span><span class="sxs-lookup"><span data-stu-id="f914e-122">To resolve this error, ensure that the XML file generated for the preserved batch has a well-formed XML structure with the TransactionSetGroup tag (for a group with multiple transaction sets) and/or the FunctionalGroup tag (for multiple groups).</span></span>