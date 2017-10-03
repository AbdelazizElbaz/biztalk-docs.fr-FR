---
title: "Comment configurer les mappages entrants pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring, maps
- configuring, inbound maps
- maps, configuring
- receive ports, configuring
- receive ports, inbound maps
- configuring, receive ports
- maps, inbound
- managing [receive ports], inbound maps
ms.assetid: b7448b39-f024-4353-818b-f753c2d60751
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5275b2701d42240df06810ef43563ca4a200151f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-receive-port"></a>Configuration des mappages entrants pour un port de réception
La présente rubrique explique comment configurer des mappages entrants pour un port de réception à l'aide de la console Administration de BizTalk Server. Vous pouvez employer des mappages entrants pour transformer les messages entrants d'un schéma en un autre, par exemple pour convertir les messages envoyés par un partenaire en un format utilisé par votre entreprise.  
  
 Vous utilisez un mappage pour appliquer une transformation XSL à un message envoyé par le port de réception sans faire passer le message dans un processus d'orchestration. Vous avez la possibilité d'ajouter un mappage entrant, de supprimer un mappage ou de transformer un mappage en un autre. Vous pouvez ajouter plusieurs mappages à un port de réception, sachant que tous doivent avoir un schéma source unique. Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).  
  
> [!NOTE]
>  Le développeur peut configurer des cartes pour un ports de réception au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-inbound-maps-for-a-receive-port"></a>Pour configurer des mappages entrants pour un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer les mappages entrants.  
  
3.  Cliquez sur **Ports de réception**, cliquez sur le port de réception, cliquez sur **propriétés**, puis cliquez sur **mappages entrants**.  
  
4.  Configurer les mappages entrants comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Supprimer**|Cliquez pour supprimer le mappage sélectionné.|  
    |**Document source**|Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.|  
    |**Carte**|Sélectionner, dans la liste déroulante, le mappage à associer à ce port.|  
    |**Document cible**|Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)   
 [La gestion des mappages](../core/managing-maps.md)