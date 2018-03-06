---
title: "Suivre les données à Application Insights ou concentrateurs d’événements | Documents Microsoft"
description: "Installer le feature pack pour permettre l’analytique des données suivies avec Azure Application Insights ou Azure Event Hubs dans BizTalk Server"
ms.custom: fp1, fp2
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: 
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5ddd60f72955c7196edfc8bf2310b73226d2abe
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="send-biztalk-tracking-data-to-azure-application-insights-or-event-hubs"></a>Envoyer des données de suivi pour Azure Application Insights ou concentrateurs d’événements de BizTalk

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez traiter et envoyer vos données de suivi à Azure Application Insights. 
          
**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**:

* Application Insights prend en charge les instances par défaut SQL et les instances nommées de SQL
* Vous pouvez traiter et envoyer des données de suivi vers Azure Event Hubs

Utilisez ces services Azure pour effectuer le suivi de vos instances à partir des orchestrations, ports d’envoi et ports de réception.

## <a name="prerequisites"></a>Configuration requise
* Créer une nouvelle instance de [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource). BizTalk Server utilise le **clé d’Instrumentation** pour s’authentifier.
* Créer un [hub d’espace de noms et événements Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-create). BizTalk Server utilise le SAS (espace de noms de niveau) ou la stratégie au niveau du concentrateur d’événements pour l’authentification.
* Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## <a name="enable-analytics-for-your-environment"></a>Activer analytique pour votre environnement

1. Ouvrir le **Administration de BizTalk Server** de la console, cliquez sur le **groupe BizTalk**, puis sélectionnez **paramètres**. 
2. Vérifiez **activer au niveau du groupe analytique**.
3. Pour le **type cible**, sélectionnez **Application Insight** ou **concentrateur d’événements** dans la liste.
    ![Activer analytique pour votre environnement](../core/media/environmentsettingapplicationinishgt.PNG)

4. Pour le **les paramètres de connexion**, sélectionnez le **...**  bouton, et **connexion** à votre compte Azure.  

    **Pour Application Insights**  
    Sélectionnez votre **abonnement**, **groupe de ressources**et l’instance de votre Application Insights.

    ![Activer analytique pour votre environnement](../core/media/analytics-group-application-insights.png)

    **Pour le concentrateur d’événements**  
    Sélectionnez votre **abonnement**, **groupe de ressources**, espace de noms de concentrateur d’événements et concentrateur d’événements. Pour l’authentification, vous pouvez utiliser une signature d’accès (SAS) sur le niveau de l’espace de noms, ou la signature d’entité à l’événement au niveau du concentrateur. Vos clés disponibles sont remplis automatiquement avec les valeurs précédemment configurées dans [Azure](https://portal.azure.com).

    ![Activer analytique pour votre environnement](../core/media/send-tracking-data-to-azure.png)

5. Sélectionnez **OK** pour enregistrer vos modifications. 

Une fois activé, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] est prêt à transmettre des données à vos ressources Azure. Ensuite, activez l’analytique sur vos orchestrations et les ports. 

## <a name="enable-analytics-on-your-artifacts"></a>Activer l’analytique sur vos artefacts

1. Dans la console Administration de BizTalk Server, cliquez sur un **port de réception**, **port d’envoi** ou **orchestration**, puis sélectionnez **suivi**.
2. Sous **Analytique**, vérifiez **activer l’Analytique**, semblable au suivant. Ce paramètre lance le suivi et la transmission de données à partir de l’artefact à vos ressources Azure.
    
    ![Données de suivi pour l’Orchestration](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. Sélectionnez **OK** pour enregistrer vos modifications.
4. Redémarrez l’Instance d’hôte de suivi et confirmer le que démarrage de l’Application BizTalk.

> [!TIP]
> Se connecter à votre Analytique du serveur BizTalk avec les autres systèmes pour avoir une idée davantage de données de votre organisation.

## <a name="view-your-data"></a>Afficher vos données

#### <a name="use-application-insights"></a>Utilisez Application Insights
Une fois que les données sont envoyées à Application Insights, vous pouvez utiliser les outils d’analytique dans Azure pour créer des requêtes avancées et analyser vos données.

1. Se connecter à la [portail Azure](https://portal.azure.com).
2. Ouvrez votre ressource Application Insights, puis sélectionnez **Metrics Explorer**.
3. Peuvent afficher des graphiques vides. Dans un graphique, sélectionnez **modifier**. Sous **métriques**, sélectionnez **personnalisé** pour afficher les propriétés de suivi disponibles. Sélectionnez parmi les différentes options pour voir les modifications sur votre graphique : 

    ![Azure Analytics](../core/media/azure-stream-metrics-custom.png)

4. Revenez à votre ressource Application Insights, puis sélectionnez **Analytique**. Dans **utilisation**, sélectionnez **exécuter**. Un exemple de requête est exécutée, et les résultats sont affichés dans un graphique.  

> [!TIP]
> Azure Application Insights est un outil puissant. Il existe des ressources pour vous aider à écrire des requêtes dans Application Insights à [Analytique dans Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)et même de commencer à utiliser [Nouveautés d’Application Insights ?](https://docs.microsoft.com/azure/application-insights/app-insights-overview).

#### <a name="use-event-hubs"></a>Utiliser des concentrateurs d’événements
Une fois que les données sont envoyées à des concentrateurs d’événements, il existe deux manières d’afficher les données. De nombreux utilisateurs de concentrateurs d’événements sont à l’aide de capturer des concentrateurs d’événements pour charger des données de diffusion en continu dans Azure. Le but est pour vous concentrer sur le traitement des données, plutôt que sur la capture de données. [Capturer des concentrateurs d’événements](https://docs.microsoft.com/azure/event-hubs/event-hubs-capture-overview) explique comment il fonctionne et comment la configurer.

Une autre option consiste à créer un port de réception et un emplacement de réception à l’aide de l’adaptateur de concentrateur d’événements. Ensuite, vous pouvez exporter les données dans un dossier. Cette idée est préférable si vous souhaitez tester le scénario. [Adaptateur de concentrateurs d’événements](event-hubs-adapter.md) présente les étapes permettant de recevoir des messages dans BizTalk Server à partir de concentrateurs d’événements.

## <a name="where-the-data-is-stored"></a>Où les données sont stockées.

Vos données de suivi doivent s’afficher assez rapidement (dans quelques minutes) au sein de vos ressources Azure. Si ce n’est pas le cas, il peut y être un problème avec l’hôte de suivi. Dans SQL Server, les données Analytique sont stockées dans la base de données BizTalkMsgBoxDb, dans le TrackingData_2_*x* tables. Dans SQL Server Management Studio, retourner les 1000 lignes du haut sur ces quatre tables. Si les données, l’hôte de suivi ne bouge pas les données de la base de données BizTalkDTADb. 

Certaines solutions possibles :

1. Redémarrez l’hôte de suivi.
2. Créer un hôte de suivi dédié. Lorsque BizTalk Server est installé, le suivi peut être activé sur le **1 d’Application de BizTalk Server** hôte. En règle générale, cette application est également utilisée pour traiter les messages. Créer un hôte de suivi dédié en procédant comme suit : 

    1. Dans la console Administration de BizTalk Server, ouvrez les propriétés de l’hôte BizTalk Server Application 1 et désélectionnez **autoriser suivi de l’hôte**. Redémarrer cette instance d’hôte.

    2. Créer un hôte nommé **suivi**et vérifiez **autoriser suivi de l’hôte**. Créer une instance d’hôte et le démarrer.

À présent, interroger les tables BizTalkMsgBoxDb TrackingData_2_x à nouveau. Si les tables sont vides, les données a été déplacées et il doivent commencer à afficher dans Application Insights.
    
## <a name="see-also"></a>Voir aussi
 [Installer et configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)