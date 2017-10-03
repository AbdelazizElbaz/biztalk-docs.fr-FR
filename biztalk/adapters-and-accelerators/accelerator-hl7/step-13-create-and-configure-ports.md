---
title: "Étape 13 : Créer et configurer des Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, creating
- message enrichment tutorial, ports
- creating, ports
- configuring, ports
- ports, configuring
ms.assetid: cc0540d7-46fc-4d9f-bcf3-0b0e0179fd51
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 256b1618313605f0847d9328abfd003f41ac61cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-13-create-and-configure-ports"></a>Étape 13 : Créer et configurer des Ports
Dans cette étape, vous utilisez l’Assistant Configuration du Port pour créer et configurer des ports dans le Concepteur d’Orchestration. Ports indiquent comment votre orchestration envoie et reçoit des messages vers et depuis des processus d’entreprise. Chaque port a un type, une direction et une liaison. Les propriétés déterminent ensemble la direction de communication, le modèle de communication de l’emplacement vers ou à partir de laquelle [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] envoie ou reçoit le message, et comment la communication a lieu. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]utilise l’adaptateur minimale inférieure couche protocole (MLLP) comme un port d’envoi. L’adaptateur MLLP utilise les communications de sockets TCP pour interagir avec d’autres applications, telles que les applications de laboratoire, des applications d’assurance et les applications héritées line-of-business. L’adaptateur d’envoi MLLP représente un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] carte :  
  
-   Personnalisé. L’adaptateur est uniquement fourni avec [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], par opposition à l’envoi de journaux avec [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
-   Protocole/Transport. La carte n’est pas un adaptateur de données ou application.  
  
-   Statique. La configuration de l’adaptateur n’implique pas une interface utilisateur personnalisée.  
  
-   Asynchrone. L’adaptateur ne bloque pas le thread du moteur de messagerie, ce qui permet d’améliorer les performances de toutes les cartes qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hôtes.  
  
-   Non transactionnel. L’adaptateur n’est pas une réception traitée ou envoyer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] carte.  
  
-   Régulière. L’adaptateur ne fonctionne pas dans un processus d’application distincte.  
  
-   Unidirectionnelles et bidirectionnelles. L’adaptateur prend en charge unidirectionnelles et requête-réponse/avec sollicitation-réponse modes d’interaction.  
  
 L’adaptateur MLLP peut envoyer des messages individuels ou envoyer des messages dans un lot. Le début d’un message MLLP est marqué avec un caractère de wrapper, 0x0b hexadécimal (également connu sous le début de bloc ou SB caractère), et la fin du message est marquée par la combinaison d’un caractère 0x1c hexadécimal (également connu sous le caractère de fin de bloc ou EB) immédiatement suivis par le caractère 0x0d (retour chariot). Les compteurs de performance BTAHL7 comptent uniquement ces caractères de wrapper pour les messages envoyés. Les compteurs de performance BTAHL7 ne comptent pas ces caractères de wrapper lors de la réception des messages.  
  
> [!NOTE]
>  Le protocole MLLP standard n’autorise pas les caractères sous 0 x 20 dans la charge utile du message, car il interfère avec la possibilité de détecter les caractères SB et EB. Vous pouvez configurer les valeurs de caractère SB et EB, par conséquent, veillez à ne pas ce problème lorsque des modifications apportées.  
  
 Dans cette étape, vous configurez l’adaptateur MLLP et l’adaptateur SOAP.  
  
### <a name="to-create-and-configure-the-ports"></a>Pour créer et configurer les ports  
  
1.  Dans le Concepteur d’Orchestration, faites glisser le **Port** mettre en forme à partir de la boîte à outils vers la Surface du Port sur le côté gauche de la surface en mode conception et déposez-la afin qu’il s’aligne horizontalement avec la **DoorbellReceive** forme.  
  
2.  Dans le **Assistant Configuration du Port**, cliquez sur **suivant**.  
  
3.  Sur le **propriétés de Port** page, dans le **nom** , tapez **SOAPReceivePort**, puis cliquez sur **suivant**.  
  
4.  Sur le **sélectionner un Type de Port** page, entrez les informations suivantes, puis cliquez sur **suivant** pour continuer.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de Type de port**|Type **SOAPReceivePortType**.|  
    |**Modèle de communication**|Sélectionnez **unidirectionnel**.|  
    |**Restrictions d’accès**|Sélectionnez **Public - aucune limite**.|  
  
5.  Sur le **liaison de Port** , cliquez sur **suivant** pour accepter les valeurs par défaut.  
  
6.  Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.  
  
7.  Faites glisser le **Port** mettre en forme à partir de la boîte à outils vers la Surface du Port sur le côté droit de la surface en mode conception et déposez-la afin qu’il s’aligne horizontalement avec la **DoorbellSend** forme.  
  
8.  À l’aide de la **Assistant Configuration du Port** comme vous l’avez fait dans les étapes 2 à 7, créez un port d’envoi supplémentaires avec les paramètres suivants :  
  
    |Propriété|Paramètre|  
    |--------------|---------------|  
    |**Nom des propriétés de port**|MLLPSendPort|  
    |**Nom de Type de port**|MLLPSendPortType|  
    |**Modèle de communication**|Unidirectionnel|  
    |**Restrictions d’accès**|Public - aucune limite|  
    |**Liaison de port**|Spécifier plus tard|  
    |**Direction de communication du port**|Toujours envoyer les messages sur ce port.|  
  
9. Dans le **Vue Orchestration** fenêtre, avec les **Types**, **les Types de Ports**, et **SOAPReceivePortType** nœuds développés, développez  **Operation_1**, puis cliquez sur **demande**.  
  
10. Dans le **propriétés** fenêtre, dans la liste déroulante pour **Type de Message**, développez **schémas**, puis cliquez sur **BTAHL7_Project.Doorbell** .  
  
11. Dans le **Vue Orchestration** fenêtre, développez **MLLPSendPortType**, développez **Operation_1**, puis cliquez sur **demande**.  
  
12. Dans le **propriétés** fenêtre, dans la liste déroulante pour **Type de Message**, développez **Types Message à parties multiples**, puis cliquez sur **BTAHL7_ Project.DoorbellFinalMessageType**.  
  
13. Dans le **nom** , tapez **réponse**, puis appuyez sur **entrée**.  
  
14. Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellReceive** forme action.  
  
15. Dans le **propriétés** fenêtre, dans la liste déroulante pour **Message**, sélectionnez **DoorbellInputMessage**.  
  
16. Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellSend** forme.  
  
17. Dans le **propriétés** fenêtre, dans la liste déroulante pour **Message**, sélectionnez **DoorbellFinalMessage**.  
  
18. Cliquez sur la poignée verte dans la **SOAPReceivePort** et faites-le glisser vers la poignée verte le **DoorbellReceive** réception shape pour se connecter le **SOAPReceivePort** à la  **DoorbellReceive** forme réception.  
  
19. Cliquez sur la poignée verte dans la **DoorbellSend** mettre en forme et faites-la glisser sur la poignée verte sur le **MLLPSendPort** port à connecter le **DoorbellSend** forme envoi pour le **MLLPSendPort** port.  
  
20. Cliquez sur le **l’Explorateur de solutions** onglet sous la vue Orchestration.  
  
21. Dans l’Explorateur de solutions, cliquez sur **BTAHL7V22Common**, puis cliquez sur **Build**. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si aucun message de réussite s’affiche, résolvez les problèmes de la solution.  
  
22. Avec le bouton droit **BTAHL7 projet**, puis cliquez sur **déployer** pour déployer le projet de BTAHL7.  
  
 Passez à [étape 14 : publier l’Orchestration en tant que Service Web](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)