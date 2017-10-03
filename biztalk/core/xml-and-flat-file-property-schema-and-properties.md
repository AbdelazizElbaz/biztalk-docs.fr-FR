---
title: "Schéma de propriété de fichier plat et XML propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d917b82-62c6-489f-99a9-97e429b6f7c0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb69a5375603d307c15a0bf884c924c0f6e6bb31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-and-flat-file-property-schema-and-properties"></a><span data-ttu-id="23fc2-102">Propriétés et schéma de propriété de fichier plat et XML</span><span class="sxs-lookup"><span data-stu-id="23fc2-102">XML and Flat File Property Schema and Properties</span></span>
<span data-ttu-id="23fc2-103">Le **http://schemas.microsoft.com/BizTalk/2003/xmlnorm-properties** espace de noms contient les propriétés que vous pouvez utiliser pour configurer les composants de pipeline assembleur de fichier plat et désassembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="23fc2-103">The **http://schemas.microsoft.com/BizTalk/2003/xmlnorm-properties** namespace contains properties you can use to configure Flat File Assembler and Flat File Disassembler pipeline components.</span></span> <span data-ttu-id="23fc2-104">Ces propriétés sont décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="23fc2-104">The properties are described in the following table.</span></span>  

## <a name="properties-list"></a><span data-ttu-id="23fc2-105">Liste Propriétés</span><span class="sxs-lookup"><span data-stu-id="23fc2-105">Properties list</span></span>
  
|<span data-ttu-id="23fc2-106">Propriété</span><span class="sxs-lookup"><span data-stu-id="23fc2-106">Property</span></span>|<span data-ttu-id="23fc2-107">Type</span><span class="sxs-lookup"><span data-stu-id="23fc2-107">Type</span></span>|<span data-ttu-id="23fc2-108"> Description</span><span class="sxs-lookup"><span data-stu-id="23fc2-108">Description</span></span>|  
|--------------|----------|-----------------|  
|<span data-ttu-id="23fc2-109">**FlatFileHeaderDocument**</span><span class="sxs-lookup"><span data-stu-id="23fc2-109">**FlatFileHeaderDocument**</span></span>|<span data-ttu-id="23fc2-110">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-110">xs:string</span></span>|<span data-ttu-id="23fc2-111">L’en-tête d’un fichier plat entrant peut être stocké avec cette propriété.</span><span class="sxs-lookup"><span data-stu-id="23fc2-111">The header of an incoming flat file document can be stored with this property.</span></span>|  
|<span data-ttu-id="23fc2-112">**AllowUnrecognizedMessage**</span><span class="sxs-lookup"><span data-stu-id="23fc2-112">**AllowUnrecognizedMessage**</span></span>|<span data-ttu-id="23fc2-113">xs:Boolean</span><span class="sxs-lookup"><span data-stu-id="23fc2-113">xs:Boolean</span></span>|<span data-ttu-id="23fc2-114">Spécifie si les messages non reconnus doivent être traités par les composants XML.</span><span class="sxs-lookup"><span data-stu-id="23fc2-114">Specifies whether unrecognized messages should be processed by XML components.</span></span>|  
|<span data-ttu-id="23fc2-115">**ProcessingInstruction**</span><span class="sxs-lookup"><span data-stu-id="23fc2-115">**ProcessingInstruction**</span></span>|<span data-ttu-id="23fc2-116">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-116">xs:string</span></span>|<span data-ttu-id="23fc2-117">Texte d’instructions de traitement des documents sortants.</span><span class="sxs-lookup"><span data-stu-id="23fc2-117">Processing instruction text for outgoing documents.</span></span>|  
|<span data-ttu-id="23fc2-118">**DocumentSpecName**</span><span class="sxs-lookup"><span data-stu-id="23fc2-118">**DocumentSpecName**</span></span>|<span data-ttu-id="23fc2-119">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-119">xs:string</span></span>|<span data-ttu-id="23fc2-120">Schéma des composants XML à utiliser pour l'analyse ou la sérialisation des documents.</span><span class="sxs-lookup"><span data-stu-id="23fc2-120">The schema for XML components to use for parsing or serializing documents.</span></span><br /><br /> <span data-ttu-id="23fc2-121">Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms #  racine cibles uniques.</span><span class="sxs-lookup"><span data-stu-id="23fc2-121">Schemas specified in this property should have unique target namespaces # root.</span></span> <span data-ttu-id="23fc2-122">Si plusieurs schémas ont le même espace de noms #  racine, la validation des instances de document risque de ne pas fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="23fc2-122">If any of the schemas have the same namespace # root, the validation of the document instances may not work as expected.</span></span> <span data-ttu-id="23fc2-123">L'espace de noms # racine doit être unique.</span><span class="sxs-lookup"><span data-stu-id="23fc2-123">The namespace # root must be unique.</span></span>  <span data-ttu-id="23fc2-124">Si des schémas doivent avoir le même espace de noms #  racine, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur XML, ou utiliser un seul pipeline sans spécifier de schémas comme paramètres pour le composant de pipeline Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="23fc2-124">If schemas must have the same namespace # root, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.</span></span>  <span data-ttu-id="23fc2-125">Cette opération fonctionne également si aucun espace de noms n'existe.</span><span class="sxs-lookup"><span data-stu-id="23fc2-125">This will also work if there is no target namespace.</span></span>|  
|<span data-ttu-id="23fc2-126">**EnvelopeSpecName**</span><span class="sxs-lookup"><span data-stu-id="23fc2-126">**EnvelopeSpecName**</span></span>|<span data-ttu-id="23fc2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-127">xs:string</span></span>|<span data-ttu-id="23fc2-128">Spécification de l’enveloppe des composants XML à utiliser pour l'analyse et la sérialisation des documents.</span><span class="sxs-lookup"><span data-stu-id="23fc2-128">The envelope specification for XML components to use for parsing or serializing documents.</span></span><br /><br /> <span data-ttu-id="23fc2-129">Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms #  racine cibles uniques.</span><span class="sxs-lookup"><span data-stu-id="23fc2-129">Schemas specified in this property should have unique target namespaces # root.</span></span> <span data-ttu-id="23fc2-130">Si plusieurs schémas ont le même espace de noms #  racine, la validation des instances de document risque de ne pas fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="23fc2-130">If any of the schemas have the same namespace # root, the validation of the document instances may not work as expected.</span></span> <span data-ttu-id="23fc2-131">L'espace de noms # racine doit être unique.</span><span class="sxs-lookup"><span data-stu-id="23fc2-131">The namespace # root must be unique.</span></span>  <span data-ttu-id="23fc2-132">Si des schémas doivent avoir le même espace de noms #  racine, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur XML, ou utiliser un seul pipeline sans spécifier de schémas comme paramètres pour le composant de pipeline Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="23fc2-132">If schemas must have the same namespace # root, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.</span></span>  <span data-ttu-id="23fc2-133">Cette opération fonctionne également si aucun espace de noms n'existe.</span><span class="sxs-lookup"><span data-stu-id="23fc2-133">This will also work if there is no target namespace.</span></span>|  
|<span data-ttu-id="23fc2-134">**TargetCharset**</span><span class="sxs-lookup"><span data-stu-id="23fc2-134">**TargetCharset**</span></span>|<span data-ttu-id="23fc2-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-135">xs:string</span></span>|<span data-ttu-id="23fc2-136">Jeu de caractères des composants XML à utiliser pour le codage des messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="23fc2-136">The character set for XML components to use for encoding output messages.</span></span>|  
|<span data-ttu-id="23fc2-137">**SourceCharset**</span><span class="sxs-lookup"><span data-stu-id="23fc2-137">**SourceCharset**</span></span>|<span data-ttu-id="23fc2-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-138">xs:string</span></span>|<span data-ttu-id="23fc2-139">Jeu de caractères utilisé pour coder un document avant qu’il ne soit traité par le Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="23fc2-139">The character set used to encode a document before being processed by the XML Disassembler.</span></span>|  
|<span data-ttu-id="23fc2-140">**ProcessingInstructionOption**</span><span class="sxs-lookup"><span data-stu-id="23fc2-140">**ProcessingInstructionOption**</span></span>|<span data-ttu-id="23fc2-141">xs:int</span><span class="sxs-lookup"><span data-stu-id="23fc2-141">xs:int</span></span>|<span data-ttu-id="23fc2-142">Indique comment les instructions de traitement sont ajoutées aux documents sortants.</span><span class="sxs-lookup"><span data-stu-id="23fc2-142">Specifies how processing instructions are added to outgoing documents.</span></span> <span data-ttu-id="23fc2-143">Pour plus d’informations sur la ProcessingInstructionOption, voir [d’Instructions de traitement dans le composant de Pipeline assembleur XML](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="23fc2-143">For more information about the ProcessingInstructionOption, see [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md).</span></span>|  
|<span data-ttu-id="23fc2-144">**AddXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="23fc2-144">**AddXMLDeclaration**</span></span>|<span data-ttu-id="23fc2-145">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="23fc2-145">xs:boolean</span></span>|<span data-ttu-id="23fc2-146">Spécifier si une déclaration XML doit être ajoutée à un document sortant.</span><span class="sxs-lookup"><span data-stu-id="23fc2-146">Specifies whether an XML declaration should be added to an outgoing document.</span></span>|  
|<span data-ttu-id="23fc2-147">**HeaderSpecName**</span><span class="sxs-lookup"><span data-stu-id="23fc2-147">**HeaderSpecName**</span></span>|<span data-ttu-id="23fc2-148">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-148">xs:string</span></span>|<span data-ttu-id="23fc2-149">Spécifie un en-tête de document de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="23fc2-149">Specifies a flat file document header.</span></span>|  
|<span data-ttu-id="23fc2-150">**TrailerSpecName**</span><span class="sxs-lookup"><span data-stu-id="23fc2-150">**TrailerSpecName**</span></span>|<span data-ttu-id="23fc2-151">xs:string</span><span class="sxs-lookup"><span data-stu-id="23fc2-151">xs:string</span></span>|<span data-ttu-id="23fc2-152">Spécifie un code de fin de document de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="23fc2-152">Specifies a flat file document trailer.</span></span>|  
|<span data-ttu-id="23fc2-153">**PromotePropertiesOnly**</span><span class="sxs-lookup"><span data-stu-id="23fc2-153">**PromotePropertiesOnly**</span></span>|<span data-ttu-id="23fc2-154">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="23fc2-154">xs:boolean</span></span>|<span data-ttu-id="23fc2-155">Lorsque la valeur **True**, le composant désassembleur XML ne pas supprimer une enveloppe de message ou désassembler.</span><span class="sxs-lookup"><span data-stu-id="23fc2-155">When set to **True**, the XML Disassembler component does not remove a message envelope or disassemble it.</span></span> <span data-ttu-id="23fc2-156">Seule une promotion des propriétés est effectuée.</span><span class="sxs-lookup"><span data-stu-id="23fc2-156">Only property promotion is performed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23fc2-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23fc2-157">See Also</span></span>  
-  [<span data-ttu-id="23fc2-158">Configuration du composant de Pipeline assembleur fichier plat</span><span class="sxs-lookup"><span data-stu-id="23fc2-158">Configure the Flat File Assembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
-  [<span data-ttu-id="23fc2-159">Configurer le composant de Pipeline de désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="23fc2-159">Configure the Flat File Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
-  [<span data-ttu-id="23fc2-160">Configuration du composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="23fc2-160">Configure the XML Assembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
-  [<span data-ttu-id="23fc2-161">Configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="23fc2-161">Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
-  [<span data-ttu-id="23fc2-162">Configurer les composants de Pipeline natifs</span><span class="sxs-lookup"><span data-stu-id="23fc2-162">Configure Native Pipeline Components</span></span>](../core/configuring-native-pipeline-components.md)   
-  <span data-ttu-id="23fc2-163">**Les propriétés de contexte du message**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="23fc2-163">**Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>