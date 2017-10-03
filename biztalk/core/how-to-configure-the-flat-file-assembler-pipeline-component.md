---
title: Comment configurer le composant de Pipeline assembleur fichier plat | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component], configuring
- messages, flat files
ms.assetid: 5af61bba-4eb2-4bb9-a655-394a76d08d3b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fe9c7a0720db68d8e629410dd3f0a443a99d7a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-flat-file-assembler-pipeline-component"></a>Comment configurer le composant de Pipeline d’assembleur de fichier plat
Le composant de pipeline Assembleur de fichier plat sert à sérialiser les documents XML dans un format de fichier plat délimité ou positionnel avant de les envoyer à partir du serveur.  
  
### <a name="to-configure-the-properties-for-the-flat-file-assembler-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Assembleur de fichier plat  
  
1.  Faites glisser le composant de pipeline Assembleur de fichier plat dans la phase d'assemblage du pipeline d'envoi.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Schéma de document**|Sélectionner un schéma de document de fichier plat à utiliser pour convertir le message XML au format de fichier plat. Si aucun schéma n'est spécifié, la fonction de détection de schéma d'exécution est utilisée. Vous pouvez créer le schéma de document de fichier plat dans l'Éditeur BizTalk.<br /><br /> Valeur par défaut : Aucun|  
    |**Schéma d’en-tête**|Sélectionner un schéma pour l'en-tête du message de fichier plat. Un schéma d’en-tête peut également être spécifié dans la propriété de contexte de message nommée **HeaderSpecName** sous l’espace de noms xmlnorm. Dans ce cas, il remplacera le schéma d'en-tête spécifié dans le Concepteur de pipeline.<br /><br /> Vous pouvez créer le schéma de l'en-tête du message de fichier plat avec l'Éditeur BizTalk.<br /><br /> Valeur par défaut : Aucun|  
    |**Conserver la marque d’ordre d’octet**|Indiquer si une marque d'ordre de tri doit être ajoutée au documents généré par le composant Assembleur.<br /><br /> Valeur par défaut : **False**|  
    |**Jeu de caractères cible**|Spécifier le jeu de caractères cible utilisé pour le codage des messages sortants.<br /><br /> Valeur par défaut : Aucun|  
    |**Schéma de code de fin**|Sélectionner un schéma pour la partie « code de fin » du message d'un fichier plat. Vous pouvez créer le schéma de la partie « code de fin » du message d'un fichier plat dans l'Éditeur BizTalk.<br /><br /> Valeur par défaut : Aucun|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur de fichier plat](../core/flat-file-assembler-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Propriétés et schéma de propriété de fichier plat et XML](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)