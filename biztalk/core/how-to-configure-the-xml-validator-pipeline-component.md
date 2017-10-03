---
title: Comment configurer le composant de Pipeline valideur XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Validator [pipeline component]
- send pipelines, validating
- pipeline components, XML Validator
- receive pipelines, validating
ms.assetid: 3b3becaf-703c-4399-a5ed-e7082e31e6e9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 821ad6a1353c0aa29866fd36fe84a7ea6317690b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-xml-validator-pipeline-component"></a><span data-ttu-id="17266-102">Comment configurer le composant de Pipeline valideur XML</span><span class="sxs-lookup"><span data-stu-id="17266-102">How to Configure the XML Validator Pipeline Component</span></span>
<span data-ttu-id="17266-103">Vous pouvez utiliser le composant de pipeline Valideur XML dans n'importe quelle étape d'un pipeline d'envoi ou de réception (à l’exception de l’assemblage et du désassemblage).</span><span class="sxs-lookup"><span data-stu-id="17266-103">The XML Validator pipeline component can be used in any stage (except Disassemble or Assemble) in a send or receive pipeline.</span></span>  
  
### <a name="to-configure-the-properties-for-the-xml-validator-pipeline-component"></a><span data-ttu-id="17266-104">Pour configurer les propriétés du composant de pipeline Valideur XML</span><span class="sxs-lookup"><span data-stu-id="17266-104">To configure the properties for the XML Validator pipeline component</span></span>  
  
1.  <span data-ttu-id="17266-105">Faites glisser le composant de pipeline Valideur XML dans l'étape Valider d'un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="17266-105">Drag the XML Validator pipeline component into the Validate stage of a receive pipeline.</span></span>  
  
2.  <span data-ttu-id="17266-106">Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, définissez les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="17266-106">In the Properties window, in the **Pipeline Component Properties** section, set the following.</span></span>  
  
    |<span data-ttu-id="17266-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="17266-107">Use this</span></span>|<span data-ttu-id="17266-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="17266-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="17266-109">**Schémas de document**</span><span class="sxs-lookup"><span data-stu-id="17266-109">**Document schemas**</span></span>|<span data-ttu-id="17266-110">Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer au document.</span><span class="sxs-lookup"><span data-stu-id="17266-110">Indicates the namespace and typename of the schema or schemas to be applied to the document.</span></span> <span data-ttu-id="17266-111">Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md).</span><span class="sxs-lookup"><span data-stu-id="17266-111">For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).</span></span> <span data-ttu-id="17266-112">Si aucun schéma n’est spécifié, la détection de schéma d’exécution est réalisée à l’aide d’espace de noms cible du message et les informations de nom d’élément racine.</span><span class="sxs-lookup"><span data-stu-id="17266-112">If no schemas are specified, the run-time schema discovery will be done by using the message's target namespace and root element name information.</span></span> <span data-ttu-id="17266-113">**Remarque :** vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas de Document** propriété.</span><span class="sxs-lookup"><span data-stu-id="17266-113">**Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** property.</span></span> <br /><br /> <span data-ttu-id="17266-114">Valeur par défaut : regroupement vide</span><span class="sxs-lookup"><span data-stu-id="17266-114">Default value: Empty collection</span></span>|  
    |<span data-ttu-id="17266-115">Traitement des échanges récupérables</span><span class="sxs-lookup"><span data-stu-id="17266-115">Recoverable Interchange Processing</span></span>|<span data-ttu-id="17266-116">Si la valeur « false » est spécifiée, l'échange entier est validé en tant qu'unité (en cas d'échec d'un message, l'échange entier est suspendu).</span><span class="sxs-lookup"><span data-stu-id="17266-116">When "false" - indicates that entire interchange is validated as a unit (if any contained message fails, entire interchange is suspended).</span></span><br /><br /> <span data-ttu-id="17266-117">Si la valeur « true » est spécifiée, les messages sont extraits de l'échange individuellement par le valideur avec la possibilité d'une propagation de certains d'entre eux via la messagerie et d'une suspension des autres.</span><span class="sxs-lookup"><span data-stu-id="17266-117">When "true" - indicates that messages within interchange are extracted individually by validator with possibility of some propagating through messaging pathway and others being suspended.</span></span><br /><br /> <span data-ttu-id="17266-118">Pour plus d’informations sur le traitement des échanges récupérables, consultez [traitement des échanges récupérables](../core/recoverable-interchange-processing.md).</span><span class="sxs-lookup"><span data-stu-id="17266-118">For more information on recoverable interchange processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17266-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17266-119">See Also</span></span>  
 <span data-ttu-id="17266-120">[Composant de Pipeline valideur XML](../core/xml-validator-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="17266-120">[XML Validator Pipeline Component](../core/xml-validator-pipeline-component.md) </span></span>  
 [<span data-ttu-id="17266-121">Configuration des composants de Pipeline natifs</span><span class="sxs-lookup"><span data-stu-id="17266-121">Configuring Native Pipeline Components</span></span>](../core/configuring-native-pipeline-components.md)