---
title: Comment utiliser des Ports dans les Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, adding ports
- Port Configuration Wizard [Orchestration Designer], configuring ports
- ports, operations
- operations, adding to ports
- configuring, ports
- ports, deleting
- deleting, ports
- ports, Port Configuration Wizard [Orchestration Designer]
- ports, adding to orchestrations
- ports, configuring
ms.assetid: da8665cd-ccde-4949-b5f5-01f9f8be5ce8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3edef29376d8724d93192040ee88951ced245ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-ports-in-orchestrations"></a>Utilisation des ports dans les orchestrations
Pour ajouter des ports à une orchestration, on procède sensiblement de la même façon que pour ajouter des contrôles à un formulaire Web ou Windows. Vous pouvez également ajouter des ports en utilisant la fenêtre Vue Orchestration.  
  
### <a name="to-add-a-new-port"></a>Pour ajouter un nouveau port  
  
-   Avec le bouton droit une **Surface du Port** ou un **lien de rôle**, puis cliquez sur **nouveau Port**.  
  
     — Ou :  
  
     Dans la fenêtre Vue Orchestration, cliquez sur **Ports** puis cliquez sur **nouveau Port**.  
  
     Un conseil DesignTip apparaît sur les ports dont la configuration n'est pas terminée.  
  
    > [!TIP]
    >  Vous pouvez également faire glisser les ports en un **lien de rôle**.  
  
### <a name="to-add-and-configure-a-new-port"></a>Pour ajouter et configurer un nouveau port  
  
1.  À partir de la **Orchestrations BizTalk** onglet de la boîte à outils, faites glisser le **Port** forme sur un **Surface du Port** ou un **lien de rôle**.  
  
     — Ou :  
  
     Avec le bouton droit une **Surface du Port** ou un **lien de rôle**, puis cliquez sur **nouveau Port configuré**.  
  
     — Ou :  
  
     Dans la fenêtre Vue Orchestration, cliquez sur **Ports** puis cliquez sur **nouveau Port configuré**.  
  
     L'Assistant Configuration du port s'affiche.  
  
2.  Suivez les instructions de l'Assistant pour configurer le port. Pour plus d’informations, consultez [comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md).  
  
### <a name="to-remove-a-port"></a>Pour supprimer un port  
  
-   Cliquez sur le port à supprimer, puis cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  Si vous supprimez un port qu’il a été connectée à un **envoyer** ou **réception** forme dans une orchestration qui a été compilée, les opérations de port sur la forme ne sera pas supprimé, et vous recevez des erreurs lors de la vous essayez de compiler. Connectez la forme à un autre port et reconfigurez les opérations associées au port.  
  
### <a name="to-configure-a-port-by-using-the-port-configuration-wizard"></a>Pour configurer un port à l'aide de l'Assistant Configuration du port  
  
1.  Cliquez sur le port à configurer, puis cliquez sur **configurer le Port**.  
  
2.  Suivez les instructions de l'Assistant Configuration du port pour configurer le port. Pour plus d’informations, consultez [comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md).  
  
### <a name="to-configure-a-port-manually-by-using-the-properties-window"></a>Pour configurer un port manuellement à l'aide de la fenêtre Propriétés  
  
1.  Sélectionnez le port à configurer.  
  
2.  Dans la fenêtre Propriétés, définissez les propriétés ci-dessous.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Type de port|Détermine le modèle de communication, les opérations et les types de messages à parties multiples associés à un port.|  
    |Direction de la communication|Détermine si cette orchestration est l'expéditeur ou le récepteur de la communication.|  
    |Modèle de communication|Détermine si ce port est utilisé pour une requête-réponse ou une communication unidirectionnelle. (Cette propriété est déterminée par le **Type de Port** propriété et est en lecture seule.)|  
    |Binding|Détermine comment un message atteint sa destination:<br /><br /> Direct — La communication se fait avec une autre orchestration.<br /><br /> Dynamique — La communication se fait avec un point de terminaison déterminé au moment de l'exécution.<br /><br /> Spécifier plus tard — La communication se fait avec un point de terminaison déterminé par un administrateur au moment de la configuration.<br /><br /> Spécifier maintenant — La communication se fait avec un point de terminaison connu au moment de la conception.|  
    |Identificateur|Nom utilisé pour ce port dans l'orchestration.|  
    |livraison chronologique des messages (éventuellement en anglais)|Pour les ports de réception, garantit que les messages publiés dans la base de données MessageBox dans un ordre indiqué sont remis à chaque abonné correspondant dans le même ordre que celui dans lequel ils ont été publiés dans la base MessageBox. Pour plus d’informations, consultez [classés de remise de Messages](../core/ordered-delivery-of-messages.md).|  
    |Accusé de réception|Pour les ports d'envoi, détermine si vous souhaitez recevoir un accusé de réception lorsqu'un message est correctement envoyé. Pour plus d’informations, consultez « Remise de Notification » dans [comment configurer la forme envoi](../core/how-to-configure-the-send-shape.md).|  
  
3.  Les propriétés restantes pour spécifier sont déterminées par la **liaison** propriété :  
  
    -   Liaison directe — utilisée lors d'une communication directe avec une autre orchestration.  
  
        |Propriété| Description|  
        |--------------|-----------------|  
        |Port d'orchestration des partenaires|Détermine le port auquel les orchestrations des partenaires sont automatiquement liées.|  
  
    -   Liaison dynamique — utilisée lors d'une communication avec un point de terminaison déterminé au moment de l'exécution.  
  
        |Propriété| Description|  
        |--------------|-----------------|  
        |Pipeline de réception|Détermine le pipeline à utiliser pour les messages entrants.|  
        |Pipeline d'envoi|Détermine le pipeline à utiliser pour les messages sortants.|  
  
    -   Spécifier plus tard — utilisée lors de la communication avec un point de terminaison configuré par un administrateur.  
  
    -   Spécifier maintenant — utilisée lors de la communication avec un point de terminaison connu au moment de la conception.  
  
        |Propriété| Description|  
        |--------------|-----------------|  
        |Pipeline de réception|Détermine le pipeline à utiliser pour les messages entrants.|  
        |Pipeline d'envoi|Détermine le pipeline à utiliser pour les messages sortants.|  
        |Transport|Détermine le transport à utiliser pour envoyer des messages.|  
        |URI|Détermine l'emplacement d'envoi des messages.|  
  
### <a name="to-add-a-port-operation"></a>Pour ajouter une opération de port  
  
-   Cliquez sur le port auquel vous souhaitez ajouter une opération, puis cliquez sur **nouvelle opération**.  
  
### <a name="to-remove-a-port-operation"></a>Pour supprimer une opération de port  
  
-   Avec le bouton droit de l’opération de port à supprimer, puis cliquez sur **supprimer**.