---
title: "Comment créer une Continuation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, relating events
- tracking profiles, relating events
- continuations, tracking profiles
- activities, continuations
- events, relating
- orchestrations, business events
- tracking profiles, updating
- activities, tracking profiles
- tracking profiles, continuations
- tracking profiles, connecting activities
ms.assetid: 31d6fc24-676e-418c-8e78-1a46b045905d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e63983b290f0f4d7dff544cd2faea45f6cf46adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-continuation"></a>Création d'une continuation
Créez des continuations pour indiquer les événements commerciaux associés dans une ou plusieurs orchestrations. Pour cela, construisez des activités connectées.  
  
> [!IMPORTANT]
>  La mise à jour d'un modèle de suivi peut avoir des conséquences sur les instances d'activité en cours si l'activité comprend une continuation d'analyse BAM. Notamment, si la mise à jour du modèle de suivi indique une interception en aval des données pour un élément d'activité déjà enregistré, il est possible que la valeur d'origine soit remplacée. Par définition, un flux d'événements unique ne sera pas affecté par les mises à jour du modèle de suivi, car chaque objet de flux est lié à la version du modèle en place au moment où l'activité ou le flux a démarré.  Cependant, les continuations étant le moyen de mettre en corrélation plusieurs flux d'événements, les flux n'ayant pas encore été lancés au moment de la mise à jour du modèle récupèrent les modifications dans la mise à jour. Il existe alors un risque pour les données d'être remplacées, comme décrit plus haut.  
  
> [!NOTE]
>  Vous pouvez créer des continuations avec des orchestrations qui ne traitent pas les messages. Pour cela, obtenez la même fonctionnalité que pour les orchestrations qui traitent des messages en faisant passer des paramètres dans des appels d'exécution entre les orchestrations et en utilisant les API de l'analyse BAM pour traiter la continuation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer la procédure suivante, vous devez avoir déployé les définitions d'activité BAM et les orchestrations que vous allez connecter.  
  
### <a name="to-create-a-continuation"></a>Pour créer une continuation  
  
1.  Ouvrir un modèle de suivi existant ou créer un modèle de suivi. Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).  
  
2.  Identifier un *le jeton de continuation,* qui est un élément d’information unique qui est disponible pour les deux activités. Par exemple, si un **CreditHistory** activité est activée par un message envoyé à partir d’un **LoanProcess** activité au sein d’un **EquityLoan**d’orchestration, le champ SSN de le message peut être utilisé comme un jeton de liaison, car il est courant pour les deux activités.  
  
3.  Cliquez sur l’activité, puis sélectionnez **Nouvelle Continuation** pour créer une continuation (CreditHistory). Nommez le nœud de continuation que vous venez de créer.  
  
4.  Dans la vue de planification d'orchestration, copiez le jeton de continuation que vous avez choisi à l'étape 2 (dans le cas présent, le numéro SSN de l'action Envoi) et collez-le dans le nœud de continuation que vous avez créé à l'étape 3.  
  
5.  Cliquez sur l’activité et sélectionnez **nouveau ContinuationID** pour créer un nœud Continuationid. Nommez-le en utilisant le nom que vous avez choisi à l'étape 3 et déposez-le sur le nœud contenant les éléments de données correspondants (dans le cas présent, le numéro SSN de l'action Réception).  
  
6.  Sur le **fichier**menu, cliquez sur **Enregistrer sous**enregistrer le modèle de suivi sous la forme d’un fichier .btt à la base de données de gestion BizTalk et pour éviter de remplacer tout fichier .btt existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Nœuds continuation et ContinuationID](../core/continuation-and-continuationid-nodes.md)   
 [Création de modèles de suivi](../core/creating-tracking-profiles.md)