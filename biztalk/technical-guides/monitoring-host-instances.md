---
title: "Surveillance des Instances d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7c6b80-7371-46ea-bf9c-82acb22012a3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b41dd0e01aa1e28862a3e99cfc767b3dd6ddec3c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-host-instances"></a>Surveillance des Instances d’hôte
Cette rubrique décrit les instances d’hôte BizTalk analyses à l’aide de Microsoft System Center Operations Manager.  
  
## <a name="using-threshold-rules-to-monitor-health"></a>À l’aide des règles de seuil pour surveiller l’intégrité  
 Le Pack d’administration de BizTalk Server intègre des règles de seuil de performance qui fournissent une vue complète de l’intégrité des hôtes BizTalk. Deux types de règles de seuil différents sont proposés :  
  
-   Règles qui s’appliquent de façon générique (par exemple, pour tous les hôtes BizTalk et pour toutes les bases de données MessageBox).  
  
-   Règles qui sont propres à un hôte BizTalk donné.  
  
 Les règles génériques surveillent tous les hôtes BizTalk en fonction d’un seuil commun. Par exemple, la règle analyse HostQ taille surveille les files d’attente de travail de tous les hôtes BizTalk en fonction d’un seuil commun. S’il existe trois hôtes différents, toutes les files d’attente de travail sont analysées par la même règle et des alertes se produisent lorsque aucune file d’attente de travail hôte dépassent le seuil commun.  
  
 Les règles spécifiques à l’hôte BizTalk permettent de configurer des seuils différents pour différents hôtes. Par exemple, la règle analyse HostQ taille – BizTalkServerApplication est une règle spécifique à l’hôte qui surveille la file d’attente de travail de l’hôte BizTalkServerApplication. Dans cet exemple, vous pouvez définir un fournisseur d’Operations Manager spécifique pour l’instance de compteur de performance particuliers et utiliser ce fournisseur de la règle de seuil. Étant donné que ces règles sont spécifiques à l’hôte, vous devez définir les règles spécifiques à chaque hôte nouvellement créé.  
  
 Les règles spécifiques à l’hôte BizTalk sont fournis comme des règles de modèle pour créer des règles qui sont applicables dans votre environnement. Toutes les règles de surveillance de seuil sont désactivées par défaut :  
  
-   Vous devez configurer les règles génériques avec des valeurs de seuil spécifiques à votre environnement.  
  
-   Vous devez créer des règles spécifiques à l’hôte de BizTalk selon les règles de modèle et les seuils appropriés.  
  
## <a name="monitoring-biztalk-host-instances"></a>Surveillance des Instances d’hôte BizTalk  
 Les règles qui ciblent des hôtes BizTalk spécifiques sont plus flexibles du point de vue analyse. Toutes les règles d’analyse de seuil pour l’hôte BizTalkServerApplication fournies dans le Pack d’administration de BizTalk Server sont des règles de modèle. Pour pouvoir utiliser ces règles, vous devez utiliser la console Administrateur Operations Manager pour :  
  
-   créer une copie du modèle dans le groupe de règles [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la renommer ;  
  
-   Créer un nouveau fournisseur d’Operations Manager pour l’instance de compteur de performance spécifique à l’hôte BizTalk.  
  
-   Modifier le fournisseur d’Operations Manager utilisé par la règle et faites-le pointer vers le nouveau.  
  
 Supposons que votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation possède un hôte BizTalk ReceiveHost et que vous souhaitez surveiller la taille de la file d’attente hôte pour cet hôte. Dans ce cas, vous devez créer un fournisseur de Operations Manager basé sur l’instance ReceiveHost du compteur de performance pour la taille de la file d’attente de l’hôte BizTalk. Vous devez également définir dans la règle une valeur de seuil appropriée à votre environnement.  
  
 Si vous utilisez des règles d’analyse de seuil spécifique à l’ordinateur hôte, vous devez désactiver les règles de surveillance génériques. afin d'éviter les alertes redondantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de BizTalk Server avec System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)