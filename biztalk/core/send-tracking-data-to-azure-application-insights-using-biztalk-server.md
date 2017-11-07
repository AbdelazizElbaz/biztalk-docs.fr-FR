---
title: "Envoyer des données de suivi à Azure Application Insights | Documents Microsoft"
description: "Installer le feature pack pour permettre l’analytique des données suivies avec Azure Application Insights dans BizTalk Server"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a65ffd2c5ee76d857effde6ab82dddf17b3de4b
ms.sourcegitcommit: 30189176c44873e3de42cc5f2b8951da51ffd251
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a>Envoyer des données de suivi à Azure Application Insights à l’aide de BizTalk Server

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez traiter et envoyer vos données de suivi à Azure Application Insights. Utiliser les fonctionnalités de l’Application Insights pour effectuer le suivi de vos instances à partir des orchestrations, ports d’envoi et ports de réception.
          
> [!IMPORTANT]
> Actuellement, cette fonctionnalité ne fonctionne pas avec des Instances nommées de SQL.

## <a name="prerequisites"></a>Conditions préalables
* Créer une nouvelle instance de [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource). Dans ses propriétés, copiez la **clé d’Instrumentation**. Collez-le dans un autre fichier afin que vous ayez prêt. Nous utilisons cette clé dans BizTalk Server. 
* Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## <a name="enable-analytics-for-your-environment"></a>Activer analytique pour votre environnement

1. Ouvrir le **Administration de BizTalk Server** de la console, cliquez sur le **groupe BizTalk**, puis sélectionnez **paramètres**. 
2. Vérifiez **activer au niveau du groupe analytique**.
3. Pour le **type cible**, sélectionnez **Application Insight** dans la liste.
4. Pour le **les paramètres de connexion**, entrez votre Application Insights  **[clé d’instrumentation](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)**  (disponible dans le portail Azure). Paramètres de votre groupe se présenter comme suit : 

    ![Activer analytique pour votre environnement](../core/media/environmentsettingapplicationinishgt.PNG)

5. Sélectionnez **OK** pour enregistrer vos modifications. 

Une fois activé, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] est prêt à transmettre des données à Application Insights. Ensuite, activez l’analytique sur vos orchestrations et les ports. 

## <a name="enable-analytics-on-your-artifacts"></a>Activer l’analytique sur vos artefacts

1. Dans la console Administration de BizTalk Server, cliquez sur un **port de réception**, **port d’envoi** ou **orchestration**, puis sélectionnez **suivi**.
2. Sous **Analytique**, vérifiez **activer l’Analytique**, semblable au suivant. Ce paramètre lance le suivi et la transmission de données à partir de l’artefact à Application Insights.
    
    ![Données de suivi pour l’Orchestration](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. Sélectionnez **OK** pour enregistrer vos modifications.
4. Redémarrez l’Instance d’hôte de suivi et confirmer le que démarrage de l’Application BizTalk.

Ensuite, exécutez les requêtes dans Application Insights pour afficher vos données.  

> [!TIP]
> Se connecter à votre Analytique du serveur BizTalk avec les autres systèmes pour avoir une idée davantage de données de votre organisation.

## <a name="view-your-data"></a>Afficher vos données
Une fois que les données sont envoyées à Application Insights, vous pouvez utiliser les outils d’analytique dans Azure pour créer des requêtes avancées et analyser vos données.

1. Se connecter à la [portail Azure](https://portal.azure.com).
2. Ouvrez votre ressource Application Insights, puis sélectionnez **Metrics Explorer**.
3. Peuvent afficher des graphiques vides. Dans un graphique, sélectionnez **modifier**. Sous **métriques**, sélectionnez **personnalisé** pour afficher les propriétés de suivi disponibles. Sélectionnez parmi les différentes options pour voir les modifications sur votre graphique : 

    ![Analytique Azure](../core/media/azure-stream-metrics-custom.png)

4. Revenez à votre ressource Application Insights, puis sélectionnez **Analytique**. Dans **utilisation**, sélectionnez **exécuter**. Un exemple de requête est exécutée, et les résultats sont affichés dans un graphique.  

> [!TIP]
> Azure Application Insights est un outil puissant. Il existe des ressources pour vous aider à écrire des requêtes dans Application Insights à [Analytique dans Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)et même de commencer à utiliser [Nouveautés d’Application Insights ?](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-overview).

## <a name="where-the-data-is-stored"></a>Où les données sont stockées.

Vos données de suivi doivent s’afficher assez rapidement (dans quelques minutes) au sein de l’Application Insights. Si ce n’est pas le cas, il peut y être un problème avec l’hôte de suivi. Dans SQL Server, les données Analytique sont stockées dans la base de données BizTalkMsgBoxDb, dans le TrackingData_2_*x* tables. Dans SQL Server Management Studio, retourner les 1000 lignes du haut sur ces quatre tables. Si les données, l’hôte de suivi ne bouge pas les données de la base de données BizTalkDTADb. 

Certaines solutions possibles :

1. Redémarrez l’hôte de suivi.
2. Créer un hôte de suivi dédié. Lorsque BizTalk Server est installé, le suivi peut être activé sur le **1 d’Application de BizTalk Server** hôte. En règle générale, cette application est également utilisée pour traiter les messages. Créer un hôte de suivi dédié en procédant comme suit : 

    1. Dans la console Administration de BizTalk Server, ouvrez les propriétés de l’hôte BizTalk Server Application 1 et désélectionnez **autoriser suivi de l’hôte**. Redémarrer cette instance d’hôte.

    2. Créer un hôte nommé **suivi**et vérifiez **autoriser suivi de l’hôte**. Créer une instance d’hôte et le démarrer.

À présent, interroger les tables BizTalkMsgBoxDb TrackingData_2_x à nouveau. Si les tables sont vides, les données a été déplacées et il doivent commencer à afficher dans Application Insights.
    
## <a name="see-also"></a>Voir aussi
 [Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)