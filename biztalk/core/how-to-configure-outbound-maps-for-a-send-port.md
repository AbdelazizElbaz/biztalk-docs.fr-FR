---
title: "Comment configurer les mappages sortants pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, outbound maps
- configuring, send ports
- managing [send ports], configuring
- send ports, outbound maps
- send ports, configuring
- managing [send ports], outbound maps
ms.assetid: 9f5f5504-5a7f-4b21-9a65-91dce9d35890
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51d3feaba929d1a7585a8e7c3b29f6868dcc9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-outbound-maps-for-a-send-port"></a>Configuration des mappages sortants pour un port d'envoi
La présente rubrique explique comment configurer des mappages sortants pour un port d'envoi à l'aide de la console Administration de BizTalk Server. Vous utilisez un mappage pour appliquer une transformation XSL à un message envoyé par le port d'envoi sans faire passer le message dans un processus d'orchestration. Vous avez la possibilité d'ajouter un mappage sortant, de supprimer un mappage ou de transformer un mappage en un autre. Vous pouvez ajouter plusieurs mappages à un port d'envoi, sachant que tous doivent avoir un schéma source unique. Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-outbound-maps-for-a-send-port"></a>Pour configurer des mappages sortants pour un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer les mappages sortants.  
  
3.  Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **mappages sortants**.  
  
4.  Configurer les mappages sortants comme décrit dans le tableau suivant, puis cliquez sur **OK**. Répétez la procédure selon les besoins pour ajouter ou supprimer plusieurs mappages.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Supprimer**|Cliquez pour supprimer le mappage sélectionné.|  
    |**Mappages sortants - Document Source**|Sélectionner le document source du mappage sortant dans la liste déroulante.|  
    |**Mappages sortants - mappage**|Dans la liste déroulante, sélectionnez le mappage à associer aux documents source et cible.|  
    |**Mappages sortants - Document cible**|Sélectionner le document cible du mappage sortant dans la liste déroulante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)   
 [La gestion des mappages](../core/managing-maps.md)