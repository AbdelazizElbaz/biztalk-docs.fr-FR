---
title: Message de mappage dans TIBCO Rendezvous | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, mapping
- message mapping
- message field elements
ms.assetid: 62793bec-f076-425c-b25e-c4be5bd93cc8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc5b3559067dbb998240a3fc814d890701e2591c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-mapping-in-tibco-rendezvous"></a><span data-ttu-id="6f1b0-102">Mappage des messages dans TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="6f1b0-102">Message Mapping in TIBCO Rendezvous</span></span>
<span data-ttu-id="6f1b0-103">Les messages TIBCO Rendezvous sont constitués d'informations d'en-tête et d'un ensemble de champs de message.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-103">TIBCO Rendezvous messages are composed of header information and a set of message fields.</span></span> <span data-ttu-id="6f1b0-104">Les informations d'en-tête sont directement mappées aux propriétés de contexte du message.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-104">The header information is directly mapped to message context properties.</span></span>  
  
## <a name="message-field-elements"></a><span data-ttu-id="6f1b0-105">Éléments des champs de message</span><span class="sxs-lookup"><span data-stu-id="6f1b0-105">Message Field Elements</span></span>  
 <span data-ttu-id="6f1b0-106">Un champ de message est constitué des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6f1b0-106">A message field is composed of the following elements:</span></span>  
  
|<span data-ttu-id="6f1b0-107">Élément</span><span class="sxs-lookup"><span data-stu-id="6f1b0-107">Element</span></span>|<span data-ttu-id="6f1b0-108"> Description</span><span class="sxs-lookup"><span data-stu-id="6f1b0-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f1b0-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="6f1b0-109">**Name**</span></span>|<span data-ttu-id="6f1b0-110">Chaîne de caractères.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-110">Character string.</span></span> <span data-ttu-id="6f1b0-111">Ne doit pas être nécessairement unique dans un message.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-111">Does not have to be unique in a message.</span></span>|  
|<span data-ttu-id="6f1b0-112">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="6f1b0-112">**Identifier**</span></span>|<span data-ttu-id="6f1b0-113">Entier court.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-113">Short integer.</span></span> <span data-ttu-id="6f1b0-114">Unique dans un message.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-114">Unique in a message.</span></span> <span data-ttu-id="6f1b0-115">Limite de manière implicite le nombre de champs de message à 65535.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-115">Implicitly limits the number of message fields to 65535.</span></span> <span data-ttu-id="6f1b0-116">L’étendue de l’identificateur est le message (ou sub).</span><span class="sxs-lookup"><span data-stu-id="6f1b0-116">The scope of the identifier is the message (or sub message).</span></span> <span data-ttu-id="6f1b0-117">Le même identificateur peut être utilisé dans deux sous-messages, qui font eux-mêmes partie d'un message conteneur.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-117">The same identifier can be used in two sub-messages, which are themselves part of a containing message.</span></span>|  
|<span data-ttu-id="6f1b0-118">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="6f1b0-118">**Value**</span></span>|<span data-ttu-id="6f1b0-119">Données du champ de message.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-119">The message field data.</span></span>|  
|<span data-ttu-id="6f1b0-120">**Count**</span><span class="sxs-lookup"><span data-stu-id="6f1b0-120">**Count**</span></span>|<span data-ttu-id="6f1b0-121">Nombre d'éléments (dans le cas d'un tableau)</span><span class="sxs-lookup"><span data-stu-id="6f1b0-121">Number of items (in the case of an array)</span></span>|  
|<span data-ttu-id="6f1b0-122">**Type**</span><span class="sxs-lookup"><span data-stu-id="6f1b0-122">**Type**</span></span>|<span data-ttu-id="6f1b0-123">Type du champ de message.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-123">The type of the message field.</span></span>|  
  
### <a name="mapping-process"></a><span data-ttu-id="6f1b0-124">Processus de mappage</span><span class="sxs-lookup"><span data-stu-id="6f1b0-124">Mapping Process</span></span>  
 <span data-ttu-id="6f1b0-125">Les messages structurés TIBCO Rendezvous sont mappés aux éléments XML comme suit :</span><span class="sxs-lookup"><span data-stu-id="6f1b0-125">TIBCO Rendezvous structured messages are mapped to XML elements in the following way:</span></span>  
  
-   <span data-ttu-id="6f1b0-126">**Nom** est utilisé comme nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-126">**Name** is used as the element name.</span></span> <span data-ttu-id="6f1b0-127">Le nom de champ TIBCO Rendezvous peut contenir des caractères dont l'utilisation n'est pas valide dans les noms d'élément XML.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-127">The TIBCO Rendezvous field name may contain characters that are not valid for use in XML element names.</span></span> <span data-ttu-id="6f1b0-128">L'adaptateur génère des mappages de caractères valides entre les messages structurés XML et TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-128">The adapter generates valid character mappings between XML and TIBCO Rendezvous structured messages.</span></span>  
  
-   <span data-ttu-id="6f1b0-129">**Identificateur** est placé dans un attribut 'id'.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-129">**Identifier** is put into an ‘id’ attribute.</span></span>  
  
-   <span data-ttu-id="6f1b0-130">**Valeur** contient une représentation de chaîne qui est le corps de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-130">**Value** contains a string representation that is the body of the element.</span></span>  
  
-   <span data-ttu-id="6f1b0-131">**Nombre de** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-131">**Count** is ignored.</span></span>  
  
-   <span data-ttu-id="6f1b0-132">**Type** informations sont placées dans un attribut xsi : type pour l’élément généré.</span><span class="sxs-lookup"><span data-stu-id="6f1b0-132">**Type** information is put into an xsi:type attribute for the generated element.</span></span>  
  
     <span data-ttu-id="6f1b0-133">Pour plus d’informations, consultez [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="6f1b0-133">For more information, see [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1b0-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f1b0-134">See Also</span></span>  
 <span data-ttu-id="6f1b0-135">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="6f1b0-135">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="6f1b0-136">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="6f1b0-136">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)