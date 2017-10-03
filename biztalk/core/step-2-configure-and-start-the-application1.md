---
title: "Étape 2 : Configurer et démarrer l’Application1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cb061ca-acf4-4de4-a634-b3bb98876989
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc9c3c027126d3a461bf99329b70fda57b9be647
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-and-start-the-application"></a>Étape 2 : Configurer et démarrer l’Application
![Étape 2 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, configurer et démarrer l’application EAISolution.  
  
 **Objectif :** la configuration concerne principalement la liaison.  Une liaison crée un mappage entre un point de terminaison logique, tel qu'un port d'orchestration ou un lien de rôle, et un point de terminaison physique, tel qu'un tiers ou un port de réception/envoi. Elle permet aux différents composants d'une solution d'entreprise BizTalk de communiquer. Vous pouvez créer des liaisons dans la console Administration de BizTalk Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les conditions suivantes sont requises avant de commencer cette étape :  
  
-   Avant de commencer cette étape, vous devez effectuer [étape 1 : déployer les projets](../core/step-1-deploy-the-projects.md).  
  
-   Vous devez ouvrir une session en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="procedures"></a>Procédures  
 L'application BizTalk est une fonctionnalité de BizTalk Server qui facilite et accélère le déploiement, la gestion et la résolution des incidents sur les solutions d'entreprise BizTalk Server. Une application BizTalk est un regroupement logique d'éléments, appelés « artefacts », qui sont utilisés dans une solution d'entreprise BizTalk Server.  Pour plus d’informations, consultez [qu’est une Application BizTalk ?](../core/what-is-a-biztalk-application.md).  Dans [étape 1 : déployer les projets](../core/step-1-deploy-the-projects.md), nous configurons le nom de l’application à être « EAISolution » avant de déployer les projets.  Ainsi, l'application EAISolution contient l'orchestration, les deux schémas et le mappage.  
  
#### <a name="to-open-the-eaisolution-application-from-biztalk-server-administration-console"></a>Ouverture de l'application EAISolution à partir de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans l’arborescence de la console sur le côté gauche de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.  
  
3.  Développez **groupe BizTalk**, développez **Applications**, puis cliquez sur **EAISolution**.  
  
 Dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md), nous avons créé une orchestration.  Dans l'orchestration, nous avons défini les ports logiques.  Dans les procédures suivantes, vous allez définir les ports physiques, puis les lier aux ports logiques.  
  
#### <a name="to-create-the-receiverequest-port"></a>Création du port ReceiveRequest  
  
1.  À partir de la Console Administration de BizTalk Server, sous la **EAISolution** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **unidirectionnel Port de réception**.  
  
2.  Sous l'onglet Général, effectuez les paramétrages suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **EAISolutionReceiveRequestPort**.|  
    |**Activer le routage des messages ayant échoué**|(désactivé)|  
  
3.  Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.  
  
4.  Dans la boîte de dialogue ReceiveLocation1 - Propriétés d'emplacement de réception, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **EAISolutionReceiveRequestLocation**.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Gestionnaire de réception**|Sélectionnez **BizTalkServerApplication**.|  
    |**Pipeline de réception**|Sélectionnez **XMLReceive**.|  
  
5.  Cliquez sur **configurer**.  
  
6.  Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Type **C:\BTSTutorials\WareHouse\Request**.|  
  
7.  Cliquez sur **OK** trois fois.  
  
#### <a name="to-create-the-senddecline-port"></a>Création du port SendDecline  
  
1.  À partir de la Console Administration de BizTalk Server, sous la **EAISolution** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **unidirectionnel statique Port d’envoi**.  
  
2.  Sous l’onglet Général, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **EAISolutionSendDeclinePort**.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Gestionnaire d’envoi**|Sélectionnez **BizTAlkServerApplication**.|  
    |**Pipeline d’envoi**|Sélectionnez **XML Transmit**.|  
  
3.  Cliquez sur **configurer**.  
  
4.  Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Type **C:\BTSTutorials\WareHouse\RequestDecline**.|  
    |**Nom de fichier**|Type **RequestDecline_%MessageID%.xml**.|  
  
5.  Cliquez deux fois sur **OK** .  
  
#### <a name="to-create-the-sendtoerp-port"></a>Création du port SendToERP  
  
1.  À partir de la Console Administration de BizTalk Server, sous la **EAISolution** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **unidirectionnel statique Port d’envoi**.  
  
2.  Sous l’onglet Général, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **EAISolutionSendToERPPort**.|  
    |**Type**|Sélectionnez **fichier**.|  
    |**Gestionnaire d’envoi**|Sélectionnez **BizTAlkServerApplication**.|  
    |**Pipeline d’envoi**|Sélectionnez **XML Transmit**.|  
  
3.  Cliquez sur **configurer**.  
  
4.  Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Type **C:\BTSTutorials\ERP\Request**.|  
    |**Nom de fichier**|Type **Request_%MessageID%.xml**.|  
  
5.  Cliquez deux fois sur **OK** .  
  
#### <a name="to-bind-the-ports"></a>Liaison des ports  
  
1.  À partir de la Console Administration de BizTalk Server, avec le bouton droit **EAISolution**, puis cliquez sur **configurer**.  
  
2.  Configurer l’application, dans le volet gauche, cliquez sur **EAIProcess**.  Il s'agit de l'orchestration que nous avons créée.  
  
3.  Dans le volet droit, effectuez les opérations suivantes :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Hôte**|Sélectionnez **BizTalkServerApplication**.|  
    |**Port de réception** pour **ReceiveRequestPort**|Sélectionnez **EAISolutionReceiveReqeustPort**.|  
    |**Groupes de ports de ports d’envoi** pour **ReceiveRequestPort**|Sélectionnez **EAISolutionSendDeclinePort**.|  
    |**Port de réception** pour **ReceiveRequestPort**|Sélectionnez **EAISolutionSendToERPPort**.|  
  
4.  Cliquez sur **OK** pour enregistrer la configuration.  
  
#### <a name="to-start-the-application"></a>Pour démarrer l'application  
  
1.  À partir de la Console Administration de BizTalk Server, avec le bouton droit **EAISolution**, puis cliquez sur **Démarrer**.  
  
2.  Dans la boîte de dialogue, cliquez sur **Démarrer**.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Au cours de cette étape, vous avez configuré et démarré l'application EAIApplication.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous testez comment la solution EAI traite les messages de [étape 3 : tester la Solution](../core/step-3-test-the-solution2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Déployer des projets](../core/step-1-deploy-the-projects.md)   
 [Étape 3 : Tester la Solution](../core/step-3-test-the-solution2.md)