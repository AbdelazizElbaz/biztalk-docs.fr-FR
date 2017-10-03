---
title: "À l’aide de corrélations dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, orchestrations
- messages, correlation sets
- correlation sets
- orchestrations, messages
- messages, validating
ms.assetid: d919afa9-bada-406a-bf4b-7b46c831c6d5
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3be56c2171205bb49d2ff1f589c77ac309ea188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-correlations-in-orchestrations"></a>Utilisation des corrélations dans les orchestrations
La corrélation est le processus de mise en correspondance d'un message entrant et de l'instance appropriée d'une orchestration. Par exemple, une orchestration envoie un message et reçoit une ou plusieurs réponses. Il existe trois modèles d'échange de messages corrélés :  
  
-   établissement de liaison traditionnel ;  
  
-   convoi séquentiel ;  
  
-   convoi parallèle.  
  
 Dans le modèle d'établissement de liaison traditionnel, les établissements de liaison existent entre les échanges de messages entre orchestrations ou processus d'entreprise. De plus, vous pouvez établir des liaisons en définissant des ensembles de corrélations dans les orchestrations, les ensembles de corrélations étant des listes de propriétés promues dotées de valeurs spécifiques que vous utilisez pour acheminer les messages vers une instance d'orchestration spécifique.  
  
 Si, par exemple, votre orchestration est conçue pour émettre un bon de commande, recevoir une facture et envoyer le paiement, vous devez être certain que le message lié à la facture est reçu par l'instance d'orchestration qui a envoyé le bon de commande, car les numéros de bons de commande risquent d'être traités en même temps. Dans cet exemple, le numéro d'identification du bon de commande peut être utilisé en tant que paramètre dans l'ensemble de corrélations pour corréler le message du bon de commande et le message de la facture. Voici une illustration de cet exemple :  
  
1.  L'Orchestration A envoie le message de bon de commande à l'Orchestration B. Avant l'envoi de ce message, l'ensemble de corrélations est initialisé.  
  
2.  Dans l'Orchestration B, qui traite le bon de commande, génère, puis envoie la facture, la première forme Réception suit le même ensemble de corrélations pour recevoir le message de bon de commande.  
  
3.  Après traitement du message de bon de commande, lors de l'envoi du message de facture à l'Orchestration A, le même ensemble de corrélations est à nouveau suivi.  
  
4.  Dans l'Orchestration A, au niveau de la forme Réception qui reçoit le message de facture de la part de l'Orchestration B, le même ensemble de corrélations est également suivi, afin de garantir une réception du message de facture corrélé basée sur l'ensemble de corrélations prédéfini.  
  
 Les modèles de convoi séquentiel et de convoi parallèle sont utilisés chaque fois que plusieurs éléments uniques doivent être reliés de façon à obtenir une chose qu'un élément individuel ne peut pas accomplir seul. Pour plus d’informations, consultez [utilisation des convois](../core/working-with-convoy-scenarios.md).  
  
 Outre les modèles d'échange de messages corrélés, il existe deux types de corrélations dans les orchestrations :  
  
-   corrélation manuelle ;  
  
-   corrélation automatique.  
  
 Dans le cas d'une corrélation manuelle, vous configurez manuellement les orchestrations à initialiser et suivez l'ensemble de corrélations pour associer les messages aux instances appropriées. Lorsque la corrélation est automatique, le moteur de messagerie corrèle les messages avec les instances à votre place, par exemple, lorsque vous configurez le port Requête-Réponse ou le port Autocorrélation dans vos orchestrations.  
  
 Vous devez utiliser la corrélation chaque fois qu'une orchestration ne dispose pas d'une façon explicite d'associer un message à une instance, telle qu'une réception avec activation, une requête-réponse ou un port d'autocorrélation.  
  
## <a name="examples-of-using-correlations"></a>Exemples d'utilisation de corrélations  
  
-   [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md)  
  
-   Téléchargez l’exemple du Kit de développement logiciel « Corrélation des Messages avec des Instances d’Orchestration » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Téléchargez l’exemple du Kit de développement logiciel « Convoi parallèle » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Ensembles de corrélations](../core/correlation-sets.md) 
  
-   [Types de corrélations](../core/correlation-types.md) 
  
-   [Comment ajouter et supprimer des ensembles de corrélations](../core/how-to-add-and-remove-correlation-sets.md) 
  
-   [Comment configurer des ensembles de corrélations](../core/how-to-configure-correlation-sets.md)  
  
-   [Comment configurer les Types de corrélations](../core/how-to-configure-correlation-types.md)  
  
-   [Utilisation des convois](../core/working-with-convoy-scenarios.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ports de liaison de l’utilisation directe d’autocorrélation](../core/how-to-use-self-correlating-direct-bound-ports.md)