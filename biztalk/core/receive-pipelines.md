---
title: "Pipelines de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, about receive pipelines
- receive pipelines, message flow
- receive pipelines
- messages, receive pipelines
- messages, message flow
- pipelines, receive pipelines
- receive pipelines, stages
ms.assetid: ee75c1d4-00b7-4177-bca3-1447a39d2238
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a248c69cb96603e9c4883e5d21caa39165da13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-pipelines"></a>Pipelines de réception
La figure suivante présente le workflow de traitement d'un message en mettant en avant le rôle du pipeline de réception.  
  
 ![Diagramme du workflow de traitement de message. ] (../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")  
Illustration du workflow de traitement d'un message  
  
 Un pipeline de réception intervient sur un message une fois qu’il est reçu par l’adaptateur de réception. Le pipeline de réception prend en charge le message initial, effectue quelques transformations et désassemble les données brutes en zéro message, un message ou plusieurs messages. Ces messages peuvent ensuite être traités par BizTalk Server.  
  
> [!NOTE]
>  Un pipeline de réception peut ne produire aucun message si un composant de consommation lui est ajouté. Dans ce cas, le composant de pipeline consomme le message et ne produit plus de messages de sortie. Si un composant de consommation est placé après un composant de désassemblage, le pipeline s’arrête une fois que le premier message est consommé et aucun autre message n’est extrait du composant de désassemblage.  
  
 Lors de la création d’un processus d’entreprise, vous pouvez créer un pipeline de réception ou utiliser l'un des deux pipelines de réception par défaut fournis avec BizTalk Server, à savoir le pipeline de réception de transfert ou le pipeline de réception XML. Pour plus d’informations sur ces pipelines par défaut, consultez [Pipelines par défaut](../core/default-pipelines.md).  
  
 Le pipeline de réception se compose de quatre étapes : décoder, désassembler, valider et Résoudretiers. Cette rubrique regroupe des considérations relatives à la conception pour compléter ces étapes.  
  
> [!NOTE]
>  Dans cette version, la modification de l’ordre de ces étapes dans un pipeline n’est pas prise en charge.  
  
## <a name="decode-stage"></a>Étape Décoder  
  
-   Cette étape est destinée aux composants qui décodent ou déchiffrent le message.  
  
    -   Il convient que le composant de pipeline Décodeur MIME/SMIME ou un composant de décodage personnalisé soit placé à cette étape si les messages entrants doivent être décodés d’un format en un autre.  
  
-   Cette étape prend en charge un message et produit un message.  
  
-   Cette étape peut contenir entre 0 et 255 composants.  
  
-   Tous les composants de cette étape sont exécutés.  
  
## <a name="disassemble-stage"></a>Étape Désassembler  
  
-   Cette étape est destinée aux composants qui analysent ou désassemblent le message.  
  
    -   Les composants de cette étape testent le message pour déterminer si son format est reconnu. En fonction de la reconnaissance du format, un des composants désassemble le message.  
  
    -   Si cette étape comprend plusieurs composants, seul le premier composant qui reconnaît le format du message est exécuté. Si aucun composant de cette étape ne reconnaît le format du message, le traitement du message échoue.  
  
    -   Il convient que cette étape inclue des composants personnalisés implémentant un comportement particulier pour désassembler le contenu des messages.  
  
    -   Cette étape peut contenir entre 0 et 255 composants. Si cette étape ne comporte aucun composant, le message est transmis.  
  
## <a name="validate-stage"></a>Étape Valider  
  
-   Cette étape est destinée aux composants qui valident le format du message.  
  
    -   Un composant de pipeline traite uniquement les messages conformes aux schémas spécifiés dans ce composant. Si un pipeline reçoit un message dont le schéma n’est pas associé à un composant du pipeline, ce message n’est pas traité. Selon l'adaptateur qui soumet le message, soit le message est suspendu, soit une erreur s’affiche au niveau de l’expéditeur.  
  
    -   Cette étape est destinée aux composants qui valident les messages XML produits par l’étape Désassembler. Ils spécifient les schémas pour procéder à la validation XML.  
  
-   Cette étape peut contenir entre 0 et 255 composants.  
  
-   Tous les composants de cette étape sont exécutés.  
  
    -   Cette étape peut être exécutée plusieurs fois. Elle est exécutée une fois par message créé par l’étape Désassembler.  
  
## <a name="resolveparty-stage"></a>Étape RésoudreTiers  
  
-   Cette étape est un espace réservé pour le [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).  
  
-   Cette étape peut être exécutée plusieurs fois. Elle est exécutée une fois par message créé par l’étape Désassembler.  
  
-   Cette étape peut contenir entre 0 et 255 composants.  
  
-   Tous les composants de cette étape sont exécutés.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines d’envoi](../core/send-pipelines.md)   
 [À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)   
 [Types de composants de Pipeline](../core/types-of-pipeline-components.md)   
 [Pipelines par défaut](../core/default-pipelines.md)   
 [Modèles de pipeline](../core/pipeline-templates.md)   
 [Composants de pipeline](../core/pipeline-components.md)   
 [Types de Pipelines](../core/types-of-pipelines.md)