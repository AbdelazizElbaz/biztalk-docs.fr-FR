---
title: "Meilleures pratiques pour l’analyse d’Operations Manager 2007 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67a5026c-ef59-498b-9bef-ea0f1c932eae
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29d83f647c40801260890a99cef4b0b2bfa0551b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-monitoring-with-operations-manager-2007"></a>Meilleures pratiques pour l’analyse d’Operations Manager 2007
Respecter les méthodes conseillées répertoriées dans cette rubrique pour surveiller efficacement vos applications à l’aide d’Operations Manager 2007.  
  
 **Installer des packs d’administration supplémentaires pour une couverture plus complète**  
  
-   Pour vous assurer qu’Operations Manager 2007 surveille les applications principales dans votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, vous devez installer les packs d’administration suivants :  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)](obligatoire)  
  
    -   Système d’exploitation Windows Server (facultatif)  
  
    -   Microsoft Windows Server Failover Cluster (si les clusters sont utilisés, facultatif)  
  
    -   Surveillance de SQL Server  
  
    -   Internet Information Services 7  
  
    -   Message Queuing (MSMQ) 5.0 (facultatif)  
  
 **Passez en revue et hiérarchiser les alertes sur une base quotidienne**  
  
-   Consulter les alertes chaque jour et définir un ordre de priorité permet de s'assurer que les problèmes sont résolus en temps voulu.  
  
 **Vérifiez que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] communique avec le serveur Operations Manager 2007.**  
  
-   Si l’échec de la communication entre les serveurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l’infrastructure d’analyse, vous ne recevrez pas d’alertes.  
  
 **Activer et désactiver les règles selon les besoins**  
  
-   Par défaut, certaines des règles du pack d'administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont désactivées. Ces règles désactivées sont les suivants : les règles nécessitant une personnalisation, les règles qui servent de modèles et les règles de surveillance supplémentaires [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] événements. Assurez-vous que les règles appropriées votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement sont activés.  
  
 **Personnaliser les règles selon les besoins de votre environnement**  
  
-   Vous devez personnaliser les règles dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pack d’administration en fonction de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement. Certaines règles requièrent la surveillance des seuils ou les seuils de temps qui sont définis en fonction des vos [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement.  
  
 **Créer des règles supplémentaires si nécessaire, selon les règles incluses dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration**  
  
-   Les règles sont fournies pour une utilisation en tant que modèles pour les artefacts que vous créez, tel que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hôtes. Vous devez utiliser ces modèles comme référence lorsque vous créez des règles spécifiques à un artefact, par exemple :  
  
    -   Les règles spécifiques à l’hôte, par exemple, hébergent la surveillance de la file d’attente et hébergent la limitation d’analyse  
  
    -   Règles spécifiques à la MessageBox  
  
    -   des règles pour des composants tiers supplémentaires, comme l'adaptateur MQSeries.  
  
 **Surveiller tous les composants liés à BizTalk Server**  
  
 Les composants de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement que vous devez surveiller pour vous assurer qu’ils sont en cours d’exécution incluent, mais ne sont pas nécessairement limité à :  
  
-   Instances d'hôte BizTalk  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Travaux de l’agent installé avec[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Des services personnalisés développés pour la solution BizTalk  
  
-   État de toutes les bases de données personnalisés développés pour la solution BizTalk  
  
-   Toutes les entrées de journal des événements personnalisé pertinentes pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de BizTalk Server avec System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)