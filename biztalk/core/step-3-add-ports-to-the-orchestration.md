---
title: "Étape 3 : Ajouter des Ports à l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 245df16e-d327-4c79-be85-004134d5ea6f
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13af336b2162e0f784195bf7c789c0dff984cb04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-ports-to-the-orchestration"></a>Étape 3 : ajout des ports à l'orchestration
![Étape 3 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez trois ports à l’orchestration EAIProcess et les configurer.  
  
 **Objectif :** Ports indiquent comment votre orchestration envoie des messages à et recevoir des messages à partir d’autres processus d’entreprise. Chaque port possède un type, une direction et une liaison qui déterminent ensemble la direction de communication, le modèle de communication, l'emplacement vers et à partir duquel le message est envoyé ou reçu, et comment la communication a lieu. Les trois ports que vous allez créer et configurer lors de cette étape remplissent les rôles suivants :  
  
-   **ReceiveRequestPort** reçoit des messages de demande de réapprovisionnement de stock de l’entrepôt.  
  
-   **SendToERP** transfère les messages de demande au système ERP.  
  
-   **SendDeclinePort** envoie la demande des messages de refus à l’entrepôt.  
  
 Pour plus d’informations, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [étape 2 : définir le processus d’entreprise](../core/step-2-define-the-business-process.md).  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-and-configure-receiverequestport"></a>Pour créer et configurer le port ReceiveRequestPort  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur **EAIProcess.odx**.  
  
2.  Dans le Concepteur d’Orchestration, l’orchestration de boîte à outils, faites glisser le **Port** forme vers la gauche **Surface du Port**, parallèlement à la **ReceiveRequest** forme. L'Assistant Configuration du port démarre automatiquement.  
  
3.  Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.  
  
4.  Sur le **propriétés de Port** page, procédez comme suit, puis cliquez sur **suivant**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **ReceiveRequestPort**.|  
  
5.  Sur le **sélectionner un Type de Port** page, procédez comme suit, puis cliquez sur **suivant**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Sélectionnez le type de port à utiliser pour ce port**|Sélectionnez le **créer un nouveau Type de Port** option.|  
    |**Nom du Type de port :**|Type **ReceiveRequestPortType**.|  
    |**Modèle de communication**|Sélectionnez **unidirectionnel**.|  
    |**Restrictions d’accès**|Sélectionnez **interne - limité au projet**.|  
  
6.  Sur le **liaison de Port** page, procédez comme suit, puis cliquez sur **suivant**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Direction de communication du port**|Sélectionnez **toujours recevoir les messages sur ce port**.|  
    |**Liaison de port**|À partir de select **spécifier plus tard**.|  
  
7.  Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.  
  
#### <a name="to-create-and-configure-senddeclineport"></a>Pour créer et configurer le port SendDeclinePort  
  
1.  À partir de l’orchestration de boîte à outils, faites glisser le **Port** forme vers la gauche **Surface du Port**, parallèlement à la **SendRequestDecline** forme.  
  
2.  Utilisez les informations dans le tableau suivant pour créer le **SendDeclinePort** port d’envoi.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|Type **SendDeclinePort**.|  
    |**Sélectionnez le type de port à utiliser pour ce port**|Sélectionnez **créer un nouveau Type de Port**.|  
    |**Nom de Type de port**|Type **SendDeclinePortType**.|  
    |**Modèle de communication**|Sélectionnez **unidirectionnel**.|  
    |**Restrictions d’accès**|Sélectionnez **interne - limité au projet**.|  
    |**Direction de communication du port**|Dans la liste déroulante, sélectionnez **toujours envoyer les messages sur ce port**.|  
    |**Liaisons de port**|Dans la liste déroulante, sélectionnez **spécifier plus tard**.|  
  
#### <a name="to-create-and-configure-sendtoerpport"></a>Pour créer et configurer le port SendToERPPort  
  
1.  À partir de l’orchestration de boîte à outils, faites glisser le **Port** forme sur le côté droit **Surface du Port**, parallèlement à la **SendToERP** forme.  
  
2.  Utilisez les informations dans le tableau suivant pour terminer l’Assistant de Configuration de Port pour le **SendToERP** port d’envoi.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|Type **SendToERPPort**.|  
    |**Sélectionnez le type de port à utiliser pour ce port**|Sélectionnez **créer un nouveau Type de Port**.|  
    |**Nom de Type de port**|Type **SendToERPPortType**.|  
    |**Modèle de communication**|Sélectionnez le **unidirectionnel** option.|  
    |**Restrictions d’accès**|Sélectionnez le **interne - limité au projet** option.|  
    |**Direction de communication du port**|Dans la liste déroulante, sélectionnez **toujours envoyer les messages sur ce port**.|  
    |**Liaison de port**|Dans la liste déroulante, sélectionnez **spécifier plus tard**.|  
  
#### <a name="to-connect-the-ports-to-the-action-shapes"></a>Pour connecter les ports aux formes d'action  
  
-   Dans le Concepteur d'orchestration, dans la surface de conception, faites glisser la poignée (flèche verte) pour chaque port vers la poignée (flèche verte) correspondante de la forme d'action :  
  
    |Connexion de ce port|À cette forme d'action|  
    |-----------------------|--------------------------|  
    |**ReceiveReqPort**|**Receive_Request**|  
    |**SendDeclinePort**|**Send_ReqDenied**|  
    |**SendToERP**|**Send_ReqToERP**|  
  
     L'illustration suivante montre l'orchestration EAIProcess avec tous les ports connectés.  
  
     ![Orchestration EAIProcess avec ports connectés. ] (../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez ajouté trois ports à l'orchestration EAIProcess et vous les avez configurés.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous générez le projet [étape 4 : création du projet EAIOrchestration](../core/step-4-build-the-eaiorchestration-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md)   
 [Étape 2 : Définir le processus d’entreprise](../core/step-2-define-the-business-process.md)   
 [Étape 4 : Création du projet EAIOrchestration](../core/step-4-build-the-eaiorchestration-project.md)