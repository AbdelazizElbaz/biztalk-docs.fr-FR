---
title: "Comment configurer le suivi d’une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, tracking
- HAT, policies
- managing [policies], tracking
- tracking, policies
- managing [policies], configuring
- policies, configuring
- configuring [HAT tracking], policies
- tracking, configuring
ms.assetid: f126e541-c183-4544-8b9d-ca07d2af303e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96fb7607bcdce8143901dabd3cdf6358f21a6a8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-policy"></a>Configuration du suivi d'une stratégie
Cette rubrique décrit la configuration du suivi d'une stratégie à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez sélectionner les options permettant d'afficher les données des instances, les résultats des conditions, les actions et les mises à jour de l'agenda dans les vues de requête de la page Hub du groupe de la console Administration.  
  
 Pour plus d’informations sur la création et l’utilisation de requêtes, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md). Pour plus d’informations sur l’instance de message et le service de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-tracking-for-a-policy"></a>Pour configurer le suivi d'une stratégie  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend la stratégie pour laquelle vous voulez configurer un suivi.  
  
3.  Cliquez sur **stratégies**, avec le bouton droit de la stratégie, cliquez sur **propriétés**, puis cliquez sur **suivi**.  
  
4.  Sélectionnez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Activité rapide**|Cette case à cocher doit être activée pour effectuer le suivi des données d'instance auxquelles s'applique la stratégie.|  
    |**Évaluation de condition**|Cette case à cocher doit être activée pour effectuer le suivi des résultats True/False des conditions de la stratégie sélectionnée.|  
    |**Déclenchements de règles**|Cette case à cocher doit être activée pour effectuer le suivi des opérations déclenchées par la stratégie.|  
    |**Mises à jour de l’agenda**|Cette case à cocher doit être activée pour effectuer le suivi des mises à jour de l'agenda. Celui-ci contient la liste des actions « True » qui doivent être déclenchées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des stratégies](../core/managing-policies.md)