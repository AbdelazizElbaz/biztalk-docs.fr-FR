---
title: "Composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], about XML Disassembler
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component]
ms.assetid: ef39b695-6ae7-401d-be1e-b066048c34e9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3346cdbfeed14e933039d7866e174c833f17212e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-disassembler-pipeline-component"></a><span data-ttu-id="f1da1-102">Composant de pipeline Désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="f1da1-102">XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="f1da1-103">Le composant de pipeline Désassembleur XML associe le désassemblage et l’analyse XML dans un seul composant.</span><span class="sxs-lookup"><span data-stu-id="f1da1-103">The XML Disassembler pipeline component combines XML parsing and disassembling into one component.</span></span> <span data-ttu-id="f1da1-104">Ses principales fonctions consistent à :</span><span class="sxs-lookup"><span data-stu-id="f1da1-104">Its primary functions are:</span></span>  
  
-   <span data-ttu-id="f1da1-105">supprimer des enveloppes ;</span><span class="sxs-lookup"><span data-stu-id="f1da1-105">Removing envelopes.</span></span>  
  
-   <span data-ttu-id="f1da1-106">désassembler l'échange ;</span><span class="sxs-lookup"><span data-stu-id="f1da1-106">Disassembling the interchange.</span></span>  
  
-   <span data-ttu-id="f1da1-107">promouvoir les propriétés de contenu du niveau des documents individuels et de l'échange au contexte du message.</span><span class="sxs-lookup"><span data-stu-id="f1da1-107">Promoting the content properties from interchange and individual document levels on to the message context.</span></span>  
  
 <span data-ttu-id="f1da1-108">Les actions suivantes se produisent dans le composant Désassembleur XML après la réception d’une enveloppe :</span><span class="sxs-lookup"><span data-stu-id="f1da1-108">The following actions occur in the XML Disassembler component after receiving an envelope:</span></span>  
  
1.  <span data-ttu-id="f1da1-109">Le désassembleur analyse l’enveloppe à l'aide des schémas d'enveloppe associés statiquement au composant au moment de la conception ou dynamiquement en déterminant les schémas d'enveloppe à partir du type de message au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f1da1-109">The disassembler parses the envelope by using the envelope schemas statically associated with the component at design time or dynamically by determining envelope schemas from the message type at run time.</span></span> <span data-ttu-id="f1da1-110">Le schéma permet de vérifier la structure de l’enveloppe pendant son analyse.</span><span class="sxs-lookup"><span data-stu-id="f1da1-110">The schema is used to verify the structure of the envelope during envelope parsing.</span></span> <span data-ttu-id="f1da1-111">Si la structure d’enveloppe n’est pas définie, elle est déterminée de manière récursive à l’aide de l’espace de noms du nœud racine et du nom de base pour consulter les schémas.</span><span class="sxs-lookup"><span data-stu-id="f1da1-111">If envelope structure is not defined, it is found recursively by using the root node's namespace and base name to look up the schemas.</span></span>  
  
2.  <span data-ttu-id="f1da1-112">Le composant désassembleur analyse chaque document de l’enveloppe.</span><span class="sxs-lookup"><span data-stu-id="f1da1-112">The disassembler component parses each document within the envelope.</span></span> <span data-ttu-id="f1da1-113">Pour chaque document, l’objet de message BizTalk est créé avec son propre contexte dans lequel toutes les propriétés promues de l'enveloppe et du document lui-même sont copiées.</span><span class="sxs-lookup"><span data-stu-id="f1da1-113">For each document, the BizTalk message object is created with its own context where all the properties promoted from the envelope and from the document itself get copied.</span></span> <span data-ttu-id="f1da1-114">Le composant extrait les propriétés de contenu de l’enveloppe et des instances de message en utilisant les XPath prédéfinis codés comme annotations dans les schémas XSD associés à l’enveloppe et au message.</span><span class="sxs-lookup"><span data-stu-id="f1da1-114">The component pulls the content properties from the envelope and message instances by using the predefined XPaths coded as annotations in the XSD schemas associated with the envelope and message.</span></span> <span data-ttu-id="f1da1-115">Les schémas d’enveloppe ainsi que chaque schéma de document sont associés au composant désassembleur dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="f1da1-115">The envelope schemas as well as the individual document schemas are associated with the disassembler component in Pipeline Designer.</span></span>  
  
 <span data-ttu-id="f1da1-116">Le Désassembleur XML ne traite que les données présentes dans le corps du message.</span><span class="sxs-lookup"><span data-stu-id="f1da1-116">The XML Disassembler only processes data in the body part of the message.</span></span> <span data-ttu-id="f1da1-117">Ainsi, seules les propriétés du corps du message peuvent être promues.</span><span class="sxs-lookup"><span data-stu-id="f1da1-117">Thus, only properties from body part can be promoted.</span></span> <span data-ttu-id="f1da1-118">Les valeurs date/heure des champs associés aux propriétés pouvant être promues sont converties au format UTC lorsque la promotion de la propriété se produit.</span><span class="sxs-lookup"><span data-stu-id="f1da1-118">Datetime values from the fields associated with the promotable properties get converted to UTC when property promotion occurs.</span></span> <span data-ttu-id="f1da1-119">Les parties autres que le corps sont copiées dans le message de sortie inchangé.</span><span class="sxs-lookup"><span data-stu-id="f1da1-119">Non-body parts are copied to the output message unchanged.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1da1-120">Le composant de pipeline Désassembleur XML force actuellement la conversion de toutes les propriétés date/heure en format UTC avant qu'elles n'atteignent la banque de messages.</span><span class="sxs-lookup"><span data-stu-id="f1da1-120">The XML Disassembler pipeline component currently forces conversion of all datetime properties to UTC before they reach the message store.</span></span> <span data-ttu-id="f1da1-121">BizTalk Server utilise un type date/heure SQL en interne qui ne contient pas d'informations sur le fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="f1da1-121">BizTalk Server uses an SQL datetime type internally, which does not have information about the time zone.</span></span> <span data-ttu-id="f1da1-122">Si vous générez une propriété date/heure dans une orchestration, puis essayez de l'utiliser pour la corrélation avec des messages ultérieurs, elle risque de ne pas fonctionner correctement car le composant de pipeline Désassembleur XML la convertira en réponse au format UTC et Microsoft SQL Server ne disposera d'aucun moyen pour identifier comme semblables les champs original et de temps de réponse.</span><span class="sxs-lookup"><span data-stu-id="f1da1-122">If you generate a datetime property in an orchestration, and then try to use it for correlation with subsequent messages, it may not work correctly, because the XML Disassembler pipeline component will convert it on response into UTC, and Microsoft SQL Server will have no way to identify the original and response time fields as identical.</span></span> <span data-ttu-id="f1da1-123">De même, vous risquez de rencontrer des différences lors de l'affichage des données de suivi des événements de message et des instances de service.</span><span class="sxs-lookup"><span data-stu-id="f1da1-123">Similarly, you may encounter discrepancies when viewing message event and service instance tracking data.</span></span>  
  
 <span data-ttu-id="f1da1-124">Pour plus d’informations sur la configuration du composant de pipeline Désassembleur XML, consultez [comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="f1da1-124">For information about configuring the XML Disassembler pipeline component, see [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1da1-125">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f1da1-125">In This Section</span></span>  
  
-   [<span data-ttu-id="f1da1-126">Éléments ensemble d’informations XML dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="f1da1-126">XML Information Set Elements in the XML Disassembler Pipeline Component</span></span>](../core/xml-information-set-elements-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="f1da1-127">Messages non reconnus dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="f1da1-127">Unrecognized Messages in the XML Disassembler Pipeline Component</span></span>](../core/unrecognized-messages-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="f1da1-128">Validation de document dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="f1da1-128">Document Validation in the XML Disassembler Pipeline Component</span></span>](../core/document-validation-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="f1da1-129">Mise en œuvre de Structure de document dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="f1da1-129">Document Structure Enforcement in the XML Disassembler Pipeline Component</span></span>](../core/document-structure-enforcement-in-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="f1da1-130">Encodage de caractères dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="f1da1-130">Character Encoding in XML Disassembler Pipeline Component</span></span>](../core/character-encoding-in-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="f1da1-131">Procédure pas à pas : Utilisation d’enveloppes XML (Basic)</span><span class="sxs-lookup"><span data-stu-id="f1da1-131">Walkthrough: Using XML Envelopes (Basic)</span></span>](../core/walkthrough-using-xml-envelopes-basic.md)