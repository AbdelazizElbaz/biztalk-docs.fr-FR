---
title: "Paramètres de réglage et de Configuration du moteur de règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, registry keys
- registry keys
- Business Rules Engine, registry keys
- troubleshooting, business rules
- validating, business rules
- business rules, validating
ms.assetid: cb0bcffe-bbc6-4495-84d2-2a822c3413b3
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6d2acc5b70f7a2be120db5159f893922135a429
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rule-engine-configuration-and-tuning-parameters"></a>Configuration et paramètres de réglage du moteur de règles
Le tableau suivant contient la liste des clés de registre qui peuvent être utiles pour la configuration, la validation et le dépannage. Ces clés de Registre sont stockés sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BusinessRules\3.0**.  
  
 À l'exception des trois premières, ces clés sont conçues pour autoriser les produits, pas les utilisateurs, à personnaliser le moteur de règles. Toutes sont créées lors de l'installation, mais aucune interface n'est fournie pour définir ces valeurs.  
  
 Le tableau se compose des colonnes suivantes :  
  
-   **Nom**. nom de la clé de registre.  
  
-   **Description**. brève description de l'emplacement ou de l'utilisation de la clé.  
  
-   **Valeur par défaut de la configuration**. : valeur renvoyée si la clé n'existe pas.  
  
-   **Installation par défaut**. : valeur définie par BizTalk Server lors de l'installation du moteur de règles.  
  
|Nom| Description|Config. par défaut|Install. par défaut|  
|----------|-----------------|--------------------|---------------------|  
|InstallPath|Emplacement des fichiers du moteur des règles d'entreprise (BRE, Business Rules Engine) utilisés lors de la configuration.|(Null)|C:\Program Files\Common Files\Microsoft BizTalk (ou C:\Program Files (x86)\Common Files\Microsoft BizTalk sur un système d'exploitation 64 bits)|  
|DatabaseServer|Serveur de base de données utilisé.|(chaîne vide)|Nom du serveur de base de données spécifié lors de la configuration du moteur des règles d'entreprise.|  
|DatabaseName|Nom de base de données à utiliser.|(chaîne vide)|Nom de la base de données spécifiée lors de la configuration du moteur des règles d'entreprise. En règle générale, il s'agit de BizTalkRuleEngineDb.|  
|PubSubAdapterAssembly|Nom de l'assembly de l'adaptateur pub/sub.|Microsoft.RuleEngine|Microsoft.RuleEngine|  
|PubSubAdapterClass|Nom de classe de l'adaptateur de publication-abonnement.|Microsoft.RuleEngine.PubSubAdapter|Microsoft.RuleEngine.PubSubAdapter|  
|DeploymentDriverAssembly|Nom de l'assembly du pilote de déploiement.|Microsoft.RuleEngine|Microsoft.BizTalk.RuleEngineExtensions|  
|DeploymentDriverClass|Nom de la classe du pilote de déploiement.|Microsoft.RuleEngine.RuleSetDeploymentDriver|Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver|  
|TrackingInterceptorAssembly|Nom de l'assembly de l'intercepteur de suivi.|(chaîne vide)|Microsoft.BizTalk.RuleEngineExtensions|  
|TrackingInterceptorClass|Nom de la classe de l'intercepteur de suivi.|(chaîne vide)|Microsoft.BizTalk.RuleEngineExtensions.RuleSetTrackingInterceptor|  
|TranslationTimeout|Durée maximale en millisecondes octroyée pour traduire un ensemble de règles. **Remarque :** qui peut être substitué dans une base de l’ensemble de règles à l’aide de RuleSetConfiguration).|60000 (1 minute)|60000|  
|UpdateServiceName|Nom du service de mise à jour utilisé par le .NET remoting pour localiser le service.|RemoteUpdateService|RemoteUpdateService|  
|UpdateServiceHost|Ordinateur qui héberge le service de mise à jour, utilisé par le .NET remoting pour localiser le service. **Remarque :** le service limite actuellement les messages entrants à la même machine.|localhost|localhost|  
|UpdateServicePort|Numéro du port TCP utilisé par le service de mise à jour, utilisé par le .NET remoting pour localiser le service.|3132|3132|  
|CacheEntries|Nombre maximal d'ensembles de règles mis en cache par le service de mise à jour.|32|32|  
|CacheTimeout|Période, en secondes, au terme de laquelle les entrées trop anciennes sont supprimées du cache du service de mise à jour.|3600 (1 heure)|3600|  
|PollingInterval|Durée, en secondes, dont dispose le service de mise à jour pour rechercher des mises à jour dans SqlRuleStore.|60 (1 minute)|60|  
|SqlTimeout|La valeur de délai d'attente des commandes SQL qui accèdent au magasin de règles SQL. La valeur de cette clé est interprétée comme suit :<br /><br /> < 0 - Utilise la valeur par défaut .NET (30 secondes)<br /><br /> = 0 - Délai d'attente illimité<br /><br /> > 0 - Temps maximum dont dispose une requête avant d'expirer|-1|-1|  
  
 Vous pouvez également ajouter une clé de Registre appelée StaticSupport, comme indiqué dans [appel des membres statiques d’une classe](../core/invoking-static-members-of-a-class.md).  
  
 Les paramètres du registre s'appliquent à toutes les applications qui hébergent une instance du moteur de règles. Vous pouvez remplacer ces paramètres au niveau d'une application à l'aide du fichier de configuration de l'application. Pour les applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'application hôte est BTSNTSvc.exe et le fichier de configuration est BTSNTSvc.exe.config, situé dans le répertoire d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  Vous devrez spécifier les valeurs des paramètres de configuration que vous souhaitez remplacer dans le fichier de configuration de l'application, comme ci-dessous :  
  
```  
<configuration>  
    <configSections>  
        <section name="Microsoft.RuleEngine" type="System.Configuration.SingleTagSectionHandler" />  
    </configSections>  
    <Microsoft.RuleEngine  
        UpdateServiceHost="localhost"  
        UpdateServicePort="3132"  
        UpdateServiceName="RemoteUpdateService"  
        CacheEntries="32"  
        CacheTimeout="3600"  
        PollingInterval="60"  
        TranslationTimeout="3600"  
        CachePruneInterval="60"  
        DatabaseServer="(localhost)"  
        DatabaseName="BizTalkRuleEngineDb"  
        SqlTimeout="-1"  
        StaticSupport="1"  
    />  
</configuration>  
```