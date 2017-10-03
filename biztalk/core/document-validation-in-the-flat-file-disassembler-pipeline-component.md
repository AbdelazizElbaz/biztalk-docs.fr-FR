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
# <a name="document-validation-in-the-flat-file-disassembler-pipeline-component"></a>Validation de document dans le composant de Pipeline de désassembleur de fichier plat
Par défaut, le composant Désassembleur de fichier plat ne valide pas les documents dont il assure le traitement. Toutefois, vous pouvez activer la validation en définissant le **valider la structure du document** propriété du composant sur **True**, ou en définissant le **FFDasm.ValidateDocumentStructure**propriété de contexte de message **True**. Lorsque la validation de document est définie de manière à être exécutée, le Désassembleur de fichier plat valide la structure du document ainsi que celles de l'en-tête et du code de fin afin de garantir leur conformité avec les schémas du document, de l'en-tête et du code de fin.  
  
 Le désassembleur de fichier plat peut supprimer des champs vides et enregistre lorsque **suppress_empty_nodes = « True »** est spécifiée par le **schemaInfo** annotation dans le schéma XSD de fichier plat. Si vous utilisez la **schemaInfo** annotation de cette façon, le désassembleur de fichier plat supprime les champs vides et les enregistrements qu’il s’agisse facultatif. Cela peut entraîner des erreurs de validation si vous utilisez la validation XML (soit en définissant le désassembleur de fichier plat **valider la structure du document** propriété **True** ou en utilisant le composant de pipeline valideur XML) . Si une erreur de validation se produit, le message est interrompu. Pour plus d’informations sur la propriété suppress_empty_nodes, voir [des propriétés de fichier plat supplémentaires](../core/additional-flat-file-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)