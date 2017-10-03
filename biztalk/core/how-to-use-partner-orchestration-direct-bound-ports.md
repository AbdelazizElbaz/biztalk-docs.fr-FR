---
title: "Comment utiliser les Ports liés aux Direct du partenaire d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f9987f-79fb-4cb6-bf6e-542f6eea9ce0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a77988ea233ca63fa227eaa00a6da1c3b611808
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-partner-orchestration-direct-bound-ports"></a>Utilisation des ports à liaison directe de l'orchestration du partenaire
Les ports à liaison directe de l'orchestration du partenaire vous proposent une communication asynchrone entre orchestrations. Vous pouvez créer deux modèles de communication : une liaison directe d’orchestration vers l’avant et l’orchestration du partenaire inverse de liaison dirigent. Ces deux modèles permettent une communication explicite entre orchestrations, ce qui signifie qu'il existe une orchestration destinataire prévue dans le cas de la liaison directe vers l'avant de l'orchestration du partenaire, et une orchestration d'expédition prévue dans le cas de la liaison directe inversée de l'orchestration du partenaire.  
  
 Vous pouvez également concevoir une liaison directe  implicite de l'orchestration du partenaire en suivant l'une de ces méthodes :  
  
-   Choisissez un port à liaison directe MessageBox comme destinataire et créez un filtre qui acceptera les messages provenant d'une orchestration d'expédition particulière.  
  
-   Choisissez un port à liaison directe MessageBox comme expéditeur et promouvez des propriétés qui correspondront à un abonnement de l'orchestration de réception.  
  
 Pour configurer un partenaire d’orchestration port à liaison directe, dans l’Assistant Configuration du Port, spécifiez **Direct** pour **liaison de Port** et sélectionnez **pour recevoir des messages à partir d’autres orchestrations, Sélectionnez le port et ces orchestration** ou **pour envoyer des messages vers d’autres orchestrations, sélectionnez le port et ces orchestration** selon que vous recevoir ou envoyer des messages ce port. Sélectionnez ensuite le port à partir de la **Port sur l’orchestration du partenaire** liste déroulante. Le type de port doit être identique pour les deux ports, ce qui implique que le type de message doit également être le même. En outre, pour être en mesure de liaison directe vers un port d’orchestration du partenaire, le **modificateur de Type** du port doit être de type **interne** pour les orchestrations dans le même assembly ou **Public**  pour permettre une orchestration à partir d’un autre assembly à lier à ce dernier. Les polarités des ports doivent être opposées. Par exemple, si l'une des extrémités est un port d'envoi, l'autre extrémité doit être un port de réception.  
  
 Pour obtenir un exemple montrant comment utiliser les ports à liaison directe partenaire d’orchestration, consultez l’exemple SDK « Direct Binding to an Orchestration » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="forward-partner-orchestration-direct-binding"></a>Liaison directe vers l'avant de l'orchestration du partenaire   
 Il s'agit du modèle de communication typique utilisé pour la liaison directe de l'orchestration du partenaire. Ce type de liaison vers l'avant vous permet de lier des expéditeurs multiples au même destinataire.  
  
 **Pour configurer une liaison directe d’orchestration vers l’avant, procédez comme suit :**  
  
1.  Dans l’Orchestration A, sélectionnez le **Port** forme dans la boîte à outils de l’orchestration. L'Assistant Configuration du port démarre.  
  
2.  Sur le **propriétés de Port** page, dans le **nom** , tapez `MyReceivePort`. Cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner un Type de Port** , sélectionnez **créer un nouveau Type de Port**. Dans le **nom du Type de Port** , tapez `MyPartnerPortType`. Cliquez sur **Suivant**.  
  
4.  Sur le **liaison de Port** page, dans le **direction de communication du Port** la liste déroulante, sélectionnez **toujours recevoir les messages sur ce port**. Dans le **liaison de Port** la liste déroulante, sélectionnez **Direct**.  
  
5.  Sélectionnez **pour recevoir des messages d’autres orchestrations, sélectionnez le port et les orchestrations**, puis, dans le **Port sur l’orchestration du partenaire** la liste déroulante, sélectionnez  **.Myreceiveport**. Cliquez sur **Suivant**.  
  
6.  Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.  
  
7.  Dans l’Orchestration B, sélectionnez le **Port** forme dans la boîte à outils de l’orchestration. L'Assistant Configuration du port démarre.  
  
8.  Sur le **propriétés de Port** page, dans le **nom** , tapez `MySendPort`. Cliquez sur **Suivant**.  
  
9. Dans la page **Sélectionner un type de port** , sélectionnez **Utiliser un type de port existant**. Sous **Types de ports disponibles**, sélectionnez **MyPartnerPortType**, puis cliquez sur **suivant**.  
  
10. Sur le **liaison de Port** page, dans le **direction de communication du Port** la liste déroulante, sélectionnez **toujours envoyer les messages sur ce port**. Dans le **liaison de Port** la liste déroulante, sélectionnez **Direct**.  
  
11. Sélectionnez **pour envoyer des messages vers d’autres orchestrations, sélectionnez le port et les orchestrations**, puis, dans le **Port sur l’orchestration du partenaire** la liste déroulante, sélectionnez  **.Myreceiveport**. Cliquez sur **Suivant**.  
  
12. Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Une liaison directe forte est créée depuis l'orchestration d'expédition vers l'orchestration de réception. Donc, si vous voulez modifier l'orchestration de réception ou si vous voulez modifier la version de l'orchestration de réception, vous devez mettre à jour la configuration de conception du port à liaison directe d'expédition de l'orchestration du partenaire. Cependant, vu que l'orchestration de réception n'a aucune connaissance explicite de l'orchestration d'expédition, vous pouvez mettre à jour l'orchestration d'expédition sans affecter l'orchestration de réception.  
  
 Dans la configuration précédente, l'Orchestration A est le destinataire et l'Orchestration B est l'expéditeur. La configuration permet l’Orchestration B d’envoyer des messages à **.myreceiveport**et permet à l’Orchestration A de recevoir des messages envoyés à **.myreceiveport**. De plus, vous pouvez ajouter l'Orchestration C en tant que deuxième expéditeur et ajouter l'Orchestration D en tant que troisième expéditeur en utilisant la même configuration que pour l'Orchestration B.  
  
## <a name="inverse-partner-orchestration-direct-binding"></a>Liaison directe inversée de l'orchestration du partenaire   
 Il ne s'agit pas du modèle de communication typique utilisé pour la liaison directe de l'orchestration du partenaire. Dans ce modèle, la direction de la liaison est l'inverse de la direction de la communication. Ce type de liaison inversée vous permet de lier un expéditeur unique à de multiples destinataires.  
  
> [!NOTE]
>  Si vous utilisez un type de port bidirectionnel dans une liaison directe inversée de l'orchestration du partenaire, vous devez définir vos filtres de réception de manière à ce qu'un seul destinataire consomme le message. Cela est dû au fait qu'un port de sollicitation-réponse attend une réponse unique. Si plusieurs destinataires reçoivent le message, le port de sollicitation-réponse accepte la première réponse et toutes les réponses suivantes sont interrompues sans reprise possible. Le moteur de messagerie génère une exception lorsque vous essayez d'envoyer le message dans cette situation, et indique qu'il existe des destinataires multiples pour un port de sollicitation-réponse.  
  
 **Pour configurer la liaison directe de partenaires inversée d’orchestration, procédez comme suit :**  
  
1.  Dans l’Orchestration A, sélectionnez le **Port** forme dans la boîte à outils de l’orchestration. L'Assistant Configuration du port démarre.  
  
2.  Sur le **propriétés de Port** page, dans le **nom** , tapez `MySendPort`. Cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner un Type de Port** , sélectionnez **créer un nouveau Type de Port**. Dans le **nom du Type de Port** , tapez `MyPartnerPortType`. Cliquez sur **Suivant**.  
  
4.  Sur le **liaison de Port** page, dans le **direction de communication du Port** la liste déroulante, sélectionnez **toujours envoyer les messages sur ce port**. Dans le **liaison de Port** la liste déroulante, sélectionnez **Direct**.  
  
5.  Sélectionnez **pour envoyer des messages vers d’autres orchestrations, sélectionnez le port et les orchestrations**, puis, dans le **Port sur l’orchestration du partenaire** la liste déroulante, sélectionnez  **.Mysendport**. Cliquez sur **Suivant**.  
  
6.  Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.  
  
7.  Dans l’Orchestration B, sélectionnez le **Port** forme dans la boîte à outils de l’orchestration. L'Assistant Configuration du port démarre.  
  
8.  Sur le **propriétés de Port** page, dans le **nom** , saisissez `MyReceivePort`. Cliquez sur **Suivant**.  
  
9. Dans la page **Sélectionner un type de port** , sélectionnez **Utiliser un type de port existant**. Sous **Types de ports disponibles**, sélectionnez **MyPartnerPortType**, puis cliquez sur **suivant**.  
  
10. Sur le **liaison de Port** page, dans le **direction de communication du Port** la liste déroulante, sélectionnez **toujours recevoir les messages sur ce port**. Dans le **liaison de Port** la liste déroulante, sélectionnez **Direct**.  
  
11. Sélectionnez **pour recevoir des messages d’autres orchestrations, sélectionnez le port et les orchestrations**, puis, dans le **Port sur l’orchestration du partenaire** la liste déroulante, sélectionnez  **.Mysendport**. Cliquez sur **Suivant**.  
  
12. Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Une liaison directe forte est créée depuis l'orchestration de réception vers l'orchestration d'expédition. Donc, si vous voulez modifier l'orchestration de réception ou mettre à jour la version de l'orchestration de réception, vous devez mettre à jour la configuration de conception du port d'expédition. Cependant, vu que l'orchestration d'expédition n'a aucune connaissance explicite de l'orchestration de réception, vous pouvez mettre à jour l'orchestration de réception sans affecter l'orchestration d'expédition.  
  
 Dans la configuration précédente, l'Orchestration A est l'expéditeur et l'Orchestration B est le destinataire. Permet à la configuration d’Orchestration pour envoyer des messages vers l’Orchestration B via une **.mysendport**et permet l’Orchestration B de recevoir des messages **.mysendport**. De plus, vous pouvez ajouter l'Orchestration C en tant que deuxième destinataire et ajouter l'Orchestration D en tant que troisième destinataire en utilisant la même configuration que pour l'Orchestration B.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser des Ports à liaison directe MessageBox](../core/how-to-use-messagebox-direct-bound-ports.md)   
 [Ports de liaison de l’utilisation directe d’autocorrélation](../core/how-to-use-self-correlating-direct-bound-ports.md)