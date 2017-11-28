---
title: "Document de Validation dans le composant de Pipeline de désassembleur de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Validate Document Structure property
- FFDasm.ValidateDocumentStructure property
- Flat File Disassembler [pipeline component], validating documents
- pipeline components, Flat File Disassembler
ms.assetid: 8cd777e4-8aba-4c17-92e8-958e5dd57d09
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 120d4664f922a653d0d532ca25213f3cb60a4e67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-validation-in-the-flat-file-disassembler-pipeline-component"></a><span data-ttu-id="8d9ae-102">Validation de document dans le composant de Pipeline de désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="8d9ae-102">Document Validation in the Flat File Disassembler Pipeline Component</span></span>
<span data-ttu-id="8d9ae-103">Par défaut, le composant Désassembleur de fichier plat ne valide pas les documents dont il assure le traitement.</span><span class="sxs-lookup"><span data-stu-id="8d9ae-103">By default, the Flat File Disassembler component does not validate documents it processes.</span></span> <span data-ttu-id="8d9ae-104">Toutefois, vous pouvez activer la validation en définissant le **valider la structure du document** propriété du composant sur **True**, ou en définissant le **FFDasm.ValidateDocumentStructure**propriété de contexte de message **True**.</span><span class="sxs-lookup"><span data-stu-id="8d9ae-104">However, you can turn validation on by setting the **Validate document structure** property on the component to **True**, or by setting the **FFDasm.ValidateDocumentStructure** message context property to **True**.</span></span> <span data-ttu-id="8d9ae-105">Lorsque la validation de document est définie de manière à être exécutée, le Désassembleur de fichier plat valide la structure du document ainsi que celles de l'en-tête et du code de fin afin de garantir leur conformité avec les schémas du document, de l'en-tête et du code de fin.</span><span class="sxs-lookup"><span data-stu-id="8d9ae-105">When document validation is set to run, the Flat File Disassembler validates the document structure as well as the header and trailer structures to ensure that they conform to the document, header, and trailer schemas.</span></span>  
  
 <span data-ttu-id="8d9ae-106">Le désassembleur de fichier plat peut supprimer des champs vides et enregistre lorsque **suppress_empty_nodes = « True »** est spécifiée par le **schemaInfo** annotation dans le schéma XSD de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="8d9ae-106">The Flat File Disassembler can remove empty fields and records when **suppress_empty_nodes="True"** is specified by the **schemaInfo** annotation in the flat file XSD schema.</span></span> <span data-ttu-id="8d9ae-107">Si vous utilisez la **schemaInfo** annotation de cette façon, le désassembleur de fichier plat supprime les champs vides et les enregistrements qu’il s’agisse facultatif.</span><span class="sxs-lookup"><span data-stu-id="8d9ae-107">If you use the **schemaInfo** annotation in this way, the Flat File Disassembler removes empty fields and records regardless of whether they are optional.</span></span> <span data-ttu-id="8d9ae-108">Cela peut entraîner des erreurs de validation si vous utilisez la validation XML (soit en définissant le désassembleur de fichier plat **valider la structure du document** propriété **True** ou en utilisant le composant de pipeline valideur XML) .</span><span class="sxs-lookup"><span data-stu-id="8d9ae-108">This may cause validation errors if you use XML validation (either by setting the Flat File Disassembler **Validate document structure** property to **True** or by using the XML Validator pipeline component).</span></span> <span data-ttu-id="8d9ae-109">Si une erreur de validation se produit, le message est interrompu.</span><span class="sxs-lookup"><span data-stu-id="8d9ae-109">If a validation error occurs, the message is suspended.</span></span> <span data-ttu-id="8d9ae-110">Pour plus d’informations sur la propriété suppress_empty_nodes, voir [des propriétés de fichier plat supplémentaires](../core/additional-flat-file-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8d9ae-110">For more information about the suppress_empty_nodes property, see [Additional Flat File Properties](../core/additional-flat-file-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d9ae-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d9ae-111">See Also</span></span>  
 <span data-ttu-id="8d9ae-112">[Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8d9ae-112">[Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="8d9ae-113">[Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8d9ae-113">[How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="8d9ae-114">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="8d9ae-114">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)