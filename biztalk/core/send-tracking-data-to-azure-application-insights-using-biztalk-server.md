---
title: "Envoyer des données de suivi à Azure Application Insights à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: f587c3049e191505c87ba456b5ddfd41011862c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a>Envoyer des données de suivi à Azure Application Insights à l’aide de BizTalk Server
Envoyer [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] les données de suivi à Inisights d’Application Azure. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez traiter et envoyer vos données de suivi à Azure Application Insights. Utiliser les fonctionnalités de l’Application Insights pour effectuer le suivi de vos instances à partir des orchestrations, ports d’envoi et ports de réception.

## <a name="prerequisites"></a>Conditions préalables
* Créer une nouvelle instance de [Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)
* Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## <a name="enable-analytics-for-your-environment"></a>Activer analytique pour votre environnement

1. Ouvrir le **Administration de BizTalk Server** de la console, développez **Administration de BizTalk**, avec le bouton droit le **groupe BizTalk**, puis sélectionnez **paramètres**. 
2. Vérifiez **activer au niveau du groupe analytique**.
3. Pour le **type cible**, sélectionnez **Application Insight** dans la liste.
4. Pour le **les paramètres de connexion**, entrez votre Application Insights  **[clé d’instrumentation](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)**  (disponible dans le portail Azure).

    Paramètres de votre groupe se présenter comme suit : 

    ![Activer analytique pour votre environnement](../core/media/environmentsettingapplicationinishgt.PNG)

5. Sélectionnez **OK** pour enregistrer vos modifications. 

Une fois activé, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] est prêt à transmettre des données à Application Insights. Ensuite, activez l’analytique sur vos orchestrations et les ports. 

## <a name="enable-analytics-on-your-artifacts"></a>Activer l’analytique sur vos artefacts

1. Dans la console Administration de BizTalk Server, cliquez sur un **port de réception**, **port d’envoi** ou **orchestration**, puis sélectionnez **suivi**.
2. Sous **Analytique**, vérifiez **activer l’Analytique**. Ce paramètre lance le suivi et la transmission de données à partir de l’artefact à Application Insights.

    Vos paramètres de l’artefact se présenter comme suit : 
    
    ![Données de suivi pour l’Orchestration](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. Sélectionnez **OK** pour enregistrer vos modifications.

Ensuite, exécutez les requêtes dans Application Insights pour afficher vos données.  

> [!TIP]
> Se connecter à votre Analytique du serveur BizTalk avec les autres systèmes pour avoir une idée davantage de données de votre organisation.

## <a name="run-queries-on-your-data"></a>Exécuter des requêtes sur vos données
Une fois que les données sont envoyées à Application Insights, vous pouvez utiliser les outils d’analytique dans Azure pour créer des requêtes avancées et analyser vos données.

1. Se connecter à la [portail Azure](https://portal.azure.com).
2. Ouvrez votre ressource Application Insights, puis sélectionnez **Analytique**.
3. Sélectionnez **utilisation**, et exécutez la requête fournie.

    > [!TIP]
    > En savoir plus sur la façon d’écrire des requêtes dans Application Insights à [Analytique dans Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics).
    
## <a name="see-also"></a>Voir aussi
 [Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)