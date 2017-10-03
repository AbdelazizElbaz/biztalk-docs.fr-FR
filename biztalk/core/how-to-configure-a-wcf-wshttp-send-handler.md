---
title: "Comment configurer un gestionnaire d’envoi WCF-WSHttp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-WSHttp adapters, global variables
- configuring [WCF-WSHttp adapters], send handlers
- configuring [WCF-WSHttp adapters], global variables
- send handlers, WCF-WSHttp adapters
ms.assetid: b2c30edb-8f7b-4d3c-812b-5b877c47fda1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11566bcc902ccbda33b6b15922292390df3d5201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-wshttp-send-handler"></a>Configuration d'un gestionnaire d'envoi WCF-WSHttp
La procédure suivante permet de configurer le gestionnaire d'envoi WCF-WSHttp.  
  
> [!CAUTION]
>  Lors de l'utilisation des gestionnaires de l'adaptateur WCF-WSHttp, il est recommandé d'installer les instances d'hôte pour ces gestionnaires sur des ordinateurs [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].  
  
### <a name="to-change-global-variables-for-a-wcf-wshttp-send-handler"></a>Pour modifier les variables globales d'un gestionnaire d'envoi WCF-WSHttp  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **WCF-WSHttp**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.  
  
4.  Dans le **général** onglet, cliquez sur **propriétés**, dans le **Proxy** onglet, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utiliser le proxy**|Indiquer si ce port d’envoi fait appel ou non à un serveur proxy.<br /><br /> Par défaut, cette case à cocher est désactivée.|  
    |**Adresse**|Indiquer l’adresse du serveur proxy. Utilisez le **https** ou **http** schéma selon la configuration de sécurité. Cette adresse peut être suivie d'un deux-points et du numéro de port. Par exemple, http://127.0.0.1:8080.<br /><br /> Cette propriété requiert une valeur uniquement si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur maximale : 256<br /><br /> La valeur par défaut est une chaîne vide.|  
    |**Nom d'utilisateur**|Indiquer le nom d’utilisateur nécessaire à l’authentification. Si l'authentification intégrée ou de base est utilisée, ce nom comprend le domaine, c'est-à-dire domaine\nom_utilisateur. Si l’authentification Digest est utilisée, le nom d’utilisateur n’inclut pas le domaine\\.<br /><br /> Cette propriété requiert une valeur uniquement si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256<br /><br /> La valeur par défaut est une chaîne vide.|  
    |**Mot de passe**|Indiquer le mot de passe nécessaire à l’authentification.<br /><br /> Cette propriété requiert une valeur uniquement si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256<br /><br /> La valeur par défaut est une chaîne vide.|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-WSHttp](../core/configuring-the-wcf-wshttp-adapter.md)