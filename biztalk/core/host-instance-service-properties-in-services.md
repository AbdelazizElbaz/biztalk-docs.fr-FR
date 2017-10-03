---
title: "Héberger des propriétés de Service dans les Services de l’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b317161-83a9-42d5-b24f-48ff1e54b94a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26d29575e282b7e558f223733ff7e7ce562f63ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="host-instance-service-properties-in-services"></a>Propriétés du service d’instance d’hôte dans Services
## <a name="host-instance-service-properties-in-services"></a>Propriétés du service d’instance d’hôte dans Services  
 Lorsqu’une instance d’hôte BizTalk est créée, un service est également créé dans Services. Le tableau ci-dessous répertorie les propriétés les plus courantes.  
  
|Option| Description|  
|------------|-----------------|  
|Général : **Type de démarrage**|Valeur par défaut est définie **automatique** pour permettre à l’instance d’hôte démarre automatiquement lorsque l’ordinateur est redémarré. Dans un environnement de Production, cette propriété est normalement toujours définie **automatique**.|  
|Ouverture de session : **compte**|Cette propriété est définie sur le compte d’utilisateur spécifié lors de la configuration de BizTalk ou lors de la création d’une instance d’hôte. Lorsque BizTalk et SQL Server sont exécutés sur des ordinateurs distincts, le compte doit être un compte de domaine. Si BizTalk et SQL Server sont exécutés sur le même ordinateur, le compte peut être un compte de domaine ou un compte local.|  
|Récupération : **première défaillance**|Valeur par défaut est définie **redémarrer le Service**. Si l’instance de l’hôte cesse de fonctionner de façon inattendue la première fois, ce paramètre tente de la redémarrer.<br /><br /> Si l’instance d’hôte démarre correctement puis s’arrête immédiatement, puis le **deuxième défaillance** propriété est appliquée.<br /><br /> Si l’instance d’hôte ne parvient pas à démarrer, puis le **deuxième défaillance** propriété ne s’applique pas. Aucune autre tentative de redémarrage ne sera effectuée. L’instance de l’hôte restera arrêtée.|  
|Récupération : **deuxième défaillance**|Valeur par défaut est définie **redémarrer le Service**. Si l’instance de l’hôte cesse de fonctionner de façon inattendue la deuxième fois, ce paramètre tente de la redémarrer.<br /><br /> Si l’instance d’hôte démarre correctement puis s’arrête immédiatement, puis le **défaillances suivantes** propriété est appliquée.<br /><br /> Si l’instance d’hôte ne parvient pas à démarrer, puis le **défaillances suivantes** propriété ne s’applique pas. Aucune autre tentative de redémarrage ne sera effectuée. L’instance de l’hôte restera arrêtée.|  
|Récupération : **défaillances suivantes**|Valeur par défaut est définie **redémarrer le Service**. Si l’instance de l’hôte cesse de fonctionner de façon inattendue la troisième fois, ce paramètre tente de la redémarrer.<br /><br /> Si l’instance d’hôte démarre correctement puis s’arrête immédiatement, puis le **défaillances suivantes** propriété continue à appliquer.<br /><br /> Si l’instance d’hôte ne parvient pas à démarrer, puis le **défaillances suivantes** propriété ne s’applique pas. Aucune autre tentative de redémarrage ne sera effectuée. L’instance de l’hôte restera arrêtée.|  
|Récupération : **redémarrer le service après**|La valeur par défaut est 1 minute et peut être augmentée le cas échéant.|  
|Dépendances|**Tous les** les composants doivent être démarrés avant le démarrage de l’instance d’hôte BizTalk. y compris l’authentification unique de l’entreprise. Si vous exécutez Windows Server 2008, consultez l’article de la Base de connaissances suivant :<br /><br /> [942284](http://support.microsoft.com/kb/942284) un service BizTalk peut ne pas démarre comme prévu lorsque vous redémarrez un ordinateur qui exécute Windows Vista ou Windows Server 2008|  
  
 **Remarque** propriétés de l’instance hôte BizTalk dans les Services sont également stockées dans le HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTSSvc$*Nom_hôte_biztalk* clé de Registre.  
  
### <a name="recovery"></a>Récupération  
 La fonctionnalité de récupération dans Services n’offre pas un nombre infini de tentatives de redémarrage du service lorsque le service de l’instance de l’hôte ne parvient pas à démarrer. En modifiant les propriétés de récupération, vous pouvez augmenter le temps d’activité d’une instance d’hôte BizTalk. Les scénarios les plus courants qui sont susceptibles de provoquer l’échec du fonctionnement d’une instance d’hôte BizTalk sont les suivants :  
  
-   Perte de la connectivité réseau avec le serveur SQL Server  
  
-   Exception de mémoire insuffisante  
  
-   Violation d’accès  
  
 **Scénarios potentiels**  
  
-   Le serveur SQL Server tombe en panne de façon inattendue. Dans ce cas, le **premier échec** propriété s’applique. La valeur par défaut **premier échec** et **redémarrer le service après** paramètres, une seule tentative de redémarrage est effectué après 1 minute. Si le serveur SQL Server n’est toujours pas disponible après 1 minute, aucune autre tentative de redémarrage ne sera effectuée. L’instance de l’hôte restera arrêtée.  
  
-   Le serveur SQL Server est mis en cluster et un basculement se produit. Le basculement prend plus de 5 minutes. Dans ce scénario, la valeur par défaut **premier échec** et **redémarrer le service après** paramètres essaie de redémarrer unique après 1 minute. Le redémarrage échouera, car le serveur SQL Server est toujours hors connexion. Par conséquent, aucune autre tentative de redémarrage ne sera effectuée. L’instance de l’hôte restera arrêtée.  
  
 **Recommandations**  
  
-   Lors de l’arrêt du serveur SQL Server ou du basculement vers un cluster SQL, arrêtez manuellement les instances d’hôte BizTalk. Redémarrez-les lorsque le serveur SQL Server est de nouveau en ligne.  
  
-   Si elle est une occurrence courante pour un cluster de basculement SQL dure plus de 1 minute, augmentez la **redémarrer le service après** valeur prend le cluster SQL doit être en ligne.  
  
-   Lorsque SQL Server est géré par un administrateur non - BizTalk, envisagez d’augmenter la **redémarrer le service après** valeur. ces administrateurs ont tendance à arrêter/démarrer un serveur SQL Server sans tenir compte de l’impact de cette opération sur BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des hôtes et des instances d’hôte BizTalk](../core/managing-biztalk-hosts-and-host-instances.md)