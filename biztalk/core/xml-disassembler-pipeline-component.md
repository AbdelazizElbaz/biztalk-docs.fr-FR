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
# <a name="xml-disassembler-pipeline-component"></a>Composant de pipeline Désassembleur XML
Le composant de pipeline Désassembleur XML associe le désassemblage et l’analyse XML dans un seul composant. Ses principales fonctions consistent à :  
  
-   supprimer des enveloppes ;  
  
-   désassembler l'échange ;  
  
-   promouvoir les propriétés de contenu du niveau des documents individuels et de l'échange au contexte du message.  
  
 Les actions suivantes se produisent dans le composant Désassembleur XML après la réception d’une enveloppe :  
  
1.  Le désassembleur analyse l’enveloppe à l'aide des schémas d'enveloppe associés statiquement au composant au moment de la conception ou dynamiquement en déterminant les schémas d'enveloppe à partir du type de message au moment de l’exécution. Le schéma permet de vérifier la structure de l’enveloppe pendant son analyse. Si la structure d’enveloppe n’est pas définie, elle est déterminée de manière récursive à l’aide de l’espace de noms du nœud racine et du nom de base pour consulter les schémas.  
  
2.  Le composant désassembleur analyse chaque document de l’enveloppe. Pour chaque document, l’objet de message BizTalk est créé avec son propre contexte dans lequel toutes les propriétés promues de l'enveloppe et du document lui-même sont copiées. Le composant extrait les propriétés de contenu de l’enveloppe et des instances de message en utilisant les XPath prédéfinis codés comme annotations dans les schémas XSD associés à l’enveloppe et au message. Les schémas d’enveloppe ainsi que chaque schéma de document sont associés au composant désassembleur dans le Concepteur de pipeline.  
  
 Le Désassembleur XML ne traite que les données présentes dans le corps du message. Ainsi, seules les propriétés du corps du message peuvent être promues. Les valeurs date/heure des champs associés aux propriétés pouvant être promues sont converties au format UTC lorsque la promotion de la propriété se produit. Les parties autres que le corps sont copiées dans le message de sortie inchangé.  
  
> [!NOTE]
>  Le composant de pipeline Désassembleur XML force actuellement la conversion de toutes les propriétés date/heure en format UTC avant qu'elles n'atteignent la banque de messages. BizTalk Server utilise un type date/heure SQL en interne qui ne contient pas d'informations sur le fuseau horaire. Si vous générez une propriété date/heure dans une orchestration, puis essayez de l'utiliser pour la corrélation avec des messages ultérieurs, elle risque de ne pas fonctionner correctement car le composant de pipeline Désassembleur XML la convertira en réponse au format UTC et Microsoft SQL Server ne disposera d'aucun moyen pour identifier comme semblables les champs original et de temps de réponse. De même, vous risquez de rencontrer des différences lors de l'affichage des données de suivi des événements de message et des instances de service.  
  
 Pour plus d’informations sur la configuration du composant de pipeline Désassembleur XML, consultez [comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Éléments ensemble d’informations XML dans le composant de Pipeline désassembleur XML](../core/xml-information-set-elements-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Messages non reconnus dans le composant de Pipeline désassembleur XML](../core/unrecognized-messages-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Validation de document dans le composant de Pipeline désassembleur XML](../core/document-validation-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Mise en œuvre de Structure de document dans le composant de Pipeline désassembleur XML](../core/document-structure-enforcement-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Encodage de caractères dans le composant de Pipeline désassembleur XML](../core/character-encoding-in-xml-disassembler-pipeline-component.md)  
  
-   [Procédure pas à pas : Utilisation d’enveloppes XML (Basic)](../core/walkthrough-using-xml-envelopes-basic.md)