---
title: "Comment configurer le composant de Pipeline de désassembleur de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Flat File Disassembler [pipeline component], configuring
- pipeline components, Flat File Disassembler
- messages, flat files
ms.assetid: c09996f6-6035-42a3-a75f-4def4ac39a95
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 403262bc18115923cdc5552a3b5e9e68d52f013e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-flat-file-disassembler-pipeline-component"></a>Comment configurer le composant de Pipeline de désassembleur de fichier plat
Le composant de pipeline Désassembleur de fichier plat permet de désassembler les documents dans un format de fichier plat et de les convertir au format XML.  
  
### <a name="to-configure-the-properties-for-the-flat-file-disassembler-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Désassembleur de fichier plat  
  
1.  Faites glisser le composant de pipeline Désassembleur de fichier plat vers l'étape de désassemblage d'un pipeline de réception.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Schéma de document**|Sélectionner le schéma de document du fichier plat à utiliser pour convertir le message d'un format de fichier plat au format XML. Le schéma de document de fichier plat pour l’analyse peut être créé dans l’Éditeur BizTalk.<br /><br /> Valeur par défaut : aucun **Remarque :** vous devez spécifier un schéma pour cette propriété, ou une erreur de compilation se produit.|  
    |**Schéma d’en-tête**|Sélectionner un schéma pour l'en-tête du message de fichier plat. Ce schéma peut être créé dans l'Éditeur BizTalk.<br /><br /> Valeur par défaut : Aucun|  
    |**Préserver l’en-tête**|Définissez cette propriété sur **True** si vous avez besoin de stocker l’en-tête de message de fichier plat dans le contexte du message. Préserver l'en-tête du message d'un fichier plat permet à la structure de l'en-tête et au contenu de circuler avec le message dans BizTalk Server. L'en-tête peut ensuite être utilisé lors de la reconversion du message au format de fichier plat dans le composant de pipeline Assembleur de fichier plat.<br /><br /> Lorsque l'en-tête conservé est sérialisé par l'assembleur de fichier plat, il manque parfois le nom du schéma d'en-tête dans la propriété générée durant la conception du document « en-tête », et ce parce que cette information peut être obtenue dynamiquement pendant l'exécution, en utilisant le type de message de l'en-tête conservé.<br /><br /> Valeur par défaut : **False**|  
    |**Schéma de code de fin**|Sélectionner un schéma pour la partie « code de fin » du message d'un fichier plat. Le schéma pour la partie du code de fin du message de fichier plat peut être créé dans l’Éditeur BizTalk.<br /><br /> Valeur par défaut : Aucun|  
    |**Traitement des échanges récupérables**|Si la valeur « false » est spécifiée, tous les échanges sont désassemblés en tant qu'unité (en cas d'échec d'un message, tous les échanges sont suspendus).<br /><br /> Si la valeur « true » est spécifiée, les messages sont extraits individuellement par le désassembleur avec la possibilité d'une propagation de certains d'entre eux via la messagerie et la suspension des autres.<br /><br /> Pour plus d’informations sur le traitement des échanges récupérables, consultez [traitement des échanges récupérables](../core/recoverable-interchange-processing.md).|  
    |**Valider la structure du document**|Définissez cette propriété sur **True** si vous devez valider toutes les parties du message de fichier plat (en-tête, corps et code de fin) pour vous assurer qu’elles sont conformes à leur schéma. Cette option réduit les performances du désassembleur de fichier plat, donc elle est définie sur **False** par défaut.<br /><br /> Valeur par défaut : **False**|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Propriétés et schéma de propriété de fichier plat et XML](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)