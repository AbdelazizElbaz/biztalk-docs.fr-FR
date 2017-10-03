---
title: "Comment configurer les mappages entrants pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], inbound maps
- configuring, send ports
- send ports, inbound maps
- configuring, inbound maps
- managing [send ports], configuring
- send ports, configuring
ms.assetid: 213c66ba-928f-4c00-9a87-f45eaa9f7dca
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04179476795e7b7c224b3db1b5e83c8a87f68b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-send-port"></a>Configuration des mappages entrants pour un port d'envoi
La présente rubrique explique comment configurer des mappages entrants pour un port d'envoi à l'aide de la console Administration de BizTalk Server. Les mappages entrants sont uniquement utilisés avec des ports d'envoi statiques ou dynamiques avec sollicitation-réponse. Vous utilisez un mappage pour appliquer une transformation XSL à un message de réponse reçu par le port sans faire passer le message dans un processus d'orchestration. Vous avez la possibilité d'ajouter un mappage entrant, de supprimer un mappage ou de transformer un mappage en un autre. Vous pouvez ajouter plusieurs mappages à un port d'envoi, sachant que tous doivent avoir un schéma source unique. Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).  
  
> [!NOTE]
>  Le développeur peut configurer des cartes au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-inbound-maps-for-a-send-port"></a>Pour configurer des mappages entrants pour un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer un mappage entrant.  
  
3.  Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **mappages entrants**.  
  
4.  Configurer les mappages entrants comme décrit dans le tableau suivant, puis cliquez sur **OK**. Répétez la procédure selon les besoins pour ajouter ou supprimer plusieurs mappages.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Supprimer**|Cliquez pour supprimer le mappage sélectionné.|  
    |**Document source**|Dans la liste déroulante, sélectionner le document source du mappage entrant.|  
    |**Carte**|Dans la liste déroulante, sélectionnez le mappage à associer aux documents source et cible.|  
    |**Document cible**|Dans la liste déroulante, sélectionner le document cible du mappage entrant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)   
 [La gestion des mappages](../core/managing-maps.md)