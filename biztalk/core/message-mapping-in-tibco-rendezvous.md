---
title: Message de mappage dans TIBCO Rendezvous | Documents Microsoft
description: "Champs de message et mappage des messages au format XML dans l’adaptateur BizTalk pour TIBCO Rendezvous"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62793bec-f076-425c-b25e-c4be5bd93cc8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb80ea4f908aa50dc32755c333aa3ccf2ea4db91
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="message-mapping-in-tibco-rendezvous"></a><span data-ttu-id="1ad42-103">Mappage des messages dans TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="1ad42-103">Message Mapping in TIBCO Rendezvous</span></span>
<span data-ttu-id="1ad42-104">Les messages TIBCO Rendezvous sont constitués d'informations d'en-tête et d'un ensemble de champs de message.</span><span class="sxs-lookup"><span data-stu-id="1ad42-104">TIBCO Rendezvous messages are composed of header information and a set of message fields.</span></span> <span data-ttu-id="1ad42-105">Les informations d'en-tête sont directement mappées aux propriétés de contexte du message.</span><span class="sxs-lookup"><span data-stu-id="1ad42-105">The header information is directly mapped to message context properties.</span></span>  
  
## <a name="message-field-elements"></a><span data-ttu-id="1ad42-106">Éléments des champs de message</span><span class="sxs-lookup"><span data-stu-id="1ad42-106">Message Field Elements</span></span>  
 <span data-ttu-id="1ad42-107">Un champ de message est constitué des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1ad42-107">A message field is composed of the following elements:</span></span>  
  
|<span data-ttu-id="1ad42-108">Élément</span><span class="sxs-lookup"><span data-stu-id="1ad42-108">Element</span></span>|<span data-ttu-id="1ad42-109"> Description</span><span class="sxs-lookup"><span data-stu-id="1ad42-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ad42-110">**Nom**</span><span class="sxs-lookup"><span data-stu-id="1ad42-110">**Name**</span></span>|<span data-ttu-id="1ad42-111">Chaîne de caractères.</span><span class="sxs-lookup"><span data-stu-id="1ad42-111">Character string.</span></span> <span data-ttu-id="1ad42-112">Ne doit pas être nécessairement unique dans un message.</span><span class="sxs-lookup"><span data-stu-id="1ad42-112">Does not have to be unique in a message.</span></span>|  
|<span data-ttu-id="1ad42-113">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="1ad42-113">**Identifier**</span></span>|<span data-ttu-id="1ad42-114">Entier court.</span><span class="sxs-lookup"><span data-stu-id="1ad42-114">Short integer.</span></span> <span data-ttu-id="1ad42-115">Unique dans un message.</span><span class="sxs-lookup"><span data-stu-id="1ad42-115">Unique in a message.</span></span> <span data-ttu-id="1ad42-116">Limite de manière implicite le nombre de champs de message à 65535.</span><span class="sxs-lookup"><span data-stu-id="1ad42-116">Implicitly limits the number of message fields to 65535.</span></span> <span data-ttu-id="1ad42-117">L’étendue de l’identificateur est le message (ou sub).</span><span class="sxs-lookup"><span data-stu-id="1ad42-117">The scope of the identifier is the message (or sub message).</span></span> <span data-ttu-id="1ad42-118">Le même identificateur peut être utilisé dans deux sous-messages, qui font eux-mêmes partie d'un message conteneur.</span><span class="sxs-lookup"><span data-stu-id="1ad42-118">The same identifier can be used in two sub-messages, which are themselves part of a containing message.</span></span>|  
|<span data-ttu-id="1ad42-119">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="1ad42-119">**Value**</span></span>|<span data-ttu-id="1ad42-120">Données du champ de message.</span><span class="sxs-lookup"><span data-stu-id="1ad42-120">The message field data.</span></span>|  
|<span data-ttu-id="1ad42-121">**Count**</span><span class="sxs-lookup"><span data-stu-id="1ad42-121">**Count**</span></span>|<span data-ttu-id="1ad42-122">Nombre d'éléments (dans le cas d'un tableau)</span><span class="sxs-lookup"><span data-stu-id="1ad42-122">Number of items (in the case of an array)</span></span>|  
|<span data-ttu-id="1ad42-123">**Type**</span><span class="sxs-lookup"><span data-stu-id="1ad42-123">**Type**</span></span>|<span data-ttu-id="1ad42-124">Type du champ de message.</span><span class="sxs-lookup"><span data-stu-id="1ad42-124">The type of the message field.</span></span>|  
  
### <a name="mapping-process"></a><span data-ttu-id="1ad42-125">Processus de mappage</span><span class="sxs-lookup"><span data-stu-id="1ad42-125">Mapping Process</span></span>  
 <span data-ttu-id="1ad42-126">Les messages structurés TIBCO Rendezvous sont mappés aux éléments XML comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ad42-126">TIBCO Rendezvous structured messages are mapped to XML elements in the following way:</span></span>  
  
-   <span data-ttu-id="1ad42-127">**Nom** est utilisé comme nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="1ad42-127">**Name** is used as the element name.</span></span> <span data-ttu-id="1ad42-128">Le nom de champ TIBCO Rendezvous peut contenir des caractères dont l'utilisation n'est pas valide dans les noms d'élément XML.</span><span class="sxs-lookup"><span data-stu-id="1ad42-128">The TIBCO Rendezvous field name may contain characters that are not valid for use in XML element names.</span></span> <span data-ttu-id="1ad42-129">L'adaptateur génère des mappages de caractères valides entre les messages structurés XML et TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="1ad42-129">The adapter generates valid character mappings between XML and TIBCO Rendezvous structured messages.</span></span>  
  
-   <span data-ttu-id="1ad42-130">**Identificateur** est placé dans un attribut 'id'.</span><span class="sxs-lookup"><span data-stu-id="1ad42-130">**Identifier** is put into an ‘id’ attribute.</span></span>  
  
-   <span data-ttu-id="1ad42-131">**Valeur** contient une représentation de chaîne qui est le corps de l’élément.</span><span class="sxs-lookup"><span data-stu-id="1ad42-131">**Value** contains a string representation that is the body of the element.</span></span>  
  
-   <span data-ttu-id="1ad42-132">**Nombre de** est ignoré.</span><span class="sxs-lookup"><span data-stu-id="1ad42-132">**Count** is ignored.</span></span>  
  
-   <span data-ttu-id="1ad42-133">**Type** informations sont placées dans un attribut xsi : type pour l’élément généré.</span><span class="sxs-lookup"><span data-stu-id="1ad42-133">**Type** information is put into an xsi:type attribute for the generated element.</span></span>  
  
     <span data-ttu-id="1ad42-134">Pour plus d’informations, consultez [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span><span class="sxs-lookup"><span data-stu-id="1ad42-134">For more information, see [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad42-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ad42-135">See Also</span></span>  
 <span data-ttu-id="1ad42-136">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="1ad42-136">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="1ad42-137">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="1ad42-137">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)