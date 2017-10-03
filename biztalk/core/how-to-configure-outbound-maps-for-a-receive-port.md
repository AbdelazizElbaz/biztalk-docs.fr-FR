---
title: "Comment configurer les mappages sortants pour un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- maps, outbound
- configuring, maps
- managing [receive ports], outbound maps
- maps, configuring
- receive ports, configuring
- configuring, receive ports
- receive ports, outbound maps
ms.assetid: 01a864a1-9e8c-4b82-9d03-91be09d556da
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9006f655879bcb5d8fe2c2448c8feba0642c9a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-outbound-maps-for-a-receive-port"></a>Configuration des mappages sortants pour un port de réception
La présente rubrique explique comment configurer les mappages sortants pour un port de réception à l'aide de la console Administration de BizTalk Server. Vous pouvez employer les mappages sortants avec les ports de réception requête-réponse pour transformer les messages sortants d'un schéma en un autre, par exemple pour convertir les messages utilisés par votre société en un format utilisé par vos partenaires.  
  
 Vous utilisez un mappage pour appliquer une transformation XSL à un message de réponse envoyé par le port de réception sans faire passer le message dans un processus d'orchestration. Vous avez la possibilité d'ajouter un mappage sortant, de supprimer un mappage ou de transformer un mappage en un autre. Vous pouvez ajouter plusieurs mappages à un port de réception, sachant que tous doivent avoir un schéma source unique. Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-outbound-maps-for-a-receive-port"></a>Pour configurer les mappages sortants pour un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer les mappages sortants.  
  
3.  Développez **Ports de réception**, cliquez sur le port de réception, cliquez sur **propriétés**, puis cliquez sur **mappages sortants**.  
  
4.  Configurer les mappages sortants comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Supprimer**|Cliquez pour supprimer le mappage sélectionné.|  
    |**Document source**|Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.|  
    |**Carte**|Sélectionner, dans la liste déroulante, le mappage à associer à ce port.|  
    |**Document cible**|Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)   
 [La gestion des mappages](../core/managing-maps.md)