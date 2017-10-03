---
title: "Didacticiel 1 : Intégration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial
- getting started tutorials, integrating enterprise applications
- enterprise application integration tutorial, about the tutorial
ms.assetid: aca5fc97-0fd6-4964-9cf1-482aa4f444b8
caps.latest.revision: "37"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb6ddbd6c2a3e25619c684036eee3fb0fa46a18f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-enterprise-application-integration"></a>Didacticiel 1 : Intégration d'applications d'entreprise (EAI, Enterprise Application Integration)
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit un environnement de développement et d'exécution pour l'intégration d'applications et la gestion des processus d'entreprise (BPM). Ce didacticiel présente un exercice de configuration et de déploiement complets de l'intégration des applications de l'entreprise (IAE) à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##  <a name="BKMK_Tut1_scenario"></a>Scénario d’entreprise  
 Contoso est une boutique en ligne spécialisée dans la vente de matériel et de logiciels informatiques.  La société a récemment investi dans un système ERP afin de mieux gérer ses ressources.  Dans ce didacticiel, vous allez développer une solution IAE (Intégration des applications de l'entreprise) utilisant BizTalk Server pour intégrer un système d'entrepôt existant au système ERP, puis automatiser le processus de requête de l'entrepôt.  
  
 Cette solution d'intégration soulève plusieurs difficultés :  
  
-   **Transfert des messages**.  Le système d'entrepôt et le système ERP peuvent résider sur deux plates-formes différentes et utiliser des protocoles de transport différents pour l'envoi et la réception de messages. La solution doit être capable de recevoir les messages à l'aide des protocoles pris en charge par le système d'envoi, puis de les transférer en utilisant les protocoles pris en charge par le système de réception.  BizTalk Server utilise *cartes* pour transporter les messages.  De nombreux adaptateurs natifs sont fournis avec le programme d'installation de BizTalk Server et avec le pack BizTalk Adapter.  Vous pouvez acheter d'autres adaptateurs auprès de vos fournisseurs ou en développer vous-même grâce à l'infrastructure d'adaptateurs fournie par BizTalk Server. Pour plus d’informations à propos des adaptateurs, consultez [http://go.microsoft.com/fwlink/?LinkId=191131](http://go.microsoft.com/fwlink/?LinkId=191131).  
  
-   **Conversion de messages**. Les types de messages sont très divers : XML (eXtended Markup Language), EDI (Electronic Data Interchange), fichiers délimités, etc. BizTalk Server utilise le protocole XML. Dans la plupart des cas, les messages entrants sont d'abord convertis au format XML.  Ce processus est appelé *l’analyse*.  Les messages sortants (XML) peuvent quant à eux être convertis dans d'autres types.  Ce processus est appelé *sérialisation*.  
  
-   **Processus d’entreprise**. En règle générale, les scénarios IAE ne se résument pas au simple transfert de messages entre deux systèmes.  Ils impliquent souvent plus de systèmes et des workflows complexes.  Dans ce scénario, l'entrepôt envoie un message demandant un réapprovisionnement des stocks. La solution reçoit le message et vérifie le total général de la requête.  Si celui-ci dépasse un certain montant, la solution rejette automatiquement la requête et envoie un message de rejet ; dans le cas contraire, la solution transfère la requête au système ERP.  
  
     Le diagramme suivant illustre le processus d'entreprise.  
  
     ![Flux de messages du didacticiel 1](../core/media/tut1-msg-flow.gif "tut1_msg_flow")  
  
 Dans ce didacticiel, vous utilisez les outils de développement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour concevoir et déployer le processus d'entreprise.  
  
## <a name="preparation"></a>Préparation  
 Avant de créer une solution d'intégration BizTalk Server, vous devez recueillir certaines informations élémentaires :  
  
-   Combien d'applications/systèmes la solution BizTalk Server doit-elle intégrer ?  Dans ce scénario, il existe deux systèmes : ERP et entrepôt.  
  
-   Quels sont les protocoles de transport pris en charge par chacune des applications ?  Pour simplifier la solution, nous partons de l'hypothèse que les deux applications utilisent des fichiers.  Le système d'entrepôt place la requête sous forme de fichier dans un dossier. La solution BizTalk Server récupère le fichier dans le dossier, le traite, puis place la requête dans un autre dossier contrôlé par le système ERP.  
  
-   Quels sont les types de messages utilisés par les applications ?  Pour simplifier la solution, nous partons de l'hypothèse que les deux applications utilisent le type XML. Les schémas BizTalk sont des documents qui définissent la structure des données XML dans les messages BizTalk ; ils visent à créer des modèles de traitement et de validation des messages XML. BizTalk Server est fourni avec un Éditeur BizTalk qui permet la création de schémas BizTalk.  
  
-   Qu'est-ce que le processus d'entreprise ?  Ce processus a été expliqué plus haut.  
  
## <a name="biztalk-server-architecture"></a>Architecture BizTalk Server  
 Il est utile de comprendre comment BizTalk Server exécute la solution.  L'illustration suivante décrit le flux de données qui transite par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
 ![Flux de données de scénario de didacticiel 1](../core/media/tut1-dataflow.gif "Tut1_Dataflow")  
  
-   Le système d'entrepôt dépose une requête dans un dossier de fichiers.  
  
-   Un emplacement de réception BizTalk Server est configuré avec l'adaptateur File et un pipeline de transmission XML.  L'adaptateur File interroge régulièrement le fichier contenu dans le dossier. À la réception d'un message, le moteur de messagerie BizTalk Server transfère le message par le biais d'un pipeline.  Le message de requête étant au format XML, il s'agit ici du pipeline de transmission XML.  Le pipeline de transmission XML vérifie que le message est un fichier XML correctement formé.  Le message est ensuite enregistré dans la base de données MessageBox.  
  
-   Lorsque le moteur d'orchestration identifie un message prêt à être traité par une orchestration, il génère une instance de l'orchestration.  Selon le total général du message, le moteur d'orchestration enregistre un message de requête ou de rejet de requête dans la base de données MessageBox.  
  
-   Là encore, suivant le type de message (message de requête ou de rejet), le moteur de messagerie utilise l'un ou l'autre des ports d'envoi pour traiter le message.  Le moteur de messagerie transmet d'abord le message par le biais d'un pipeline de transmission XML, puis utilise l'adaptateur File pour envoyer le message dans différents dossiers, selon la configuration du port d'envoi.  
  
-   Le système d'entrepôt et le système ERP surveillent les dossiers désignés afin de récupérer les messages.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md) 
  
-   [Leçon 1 : Définir des schémas et un mappage](../core/lesson-1-define-schemas-and-a-map.md) 
  
-   [Leçon 2 : Définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md)  
  
-   [Leçon 3 : Déployer la Solution](../core/lesson-3-deploy-the-solution.md)