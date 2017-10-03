---
title: "Comment configurer un gestionnaire d’envoi WCF-NetTcp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], send handlers
- WCF-NetTcp adapters, global variables
- configuring [WCF-NetTcp adapters], global variables
ms.assetid: c60fe03d-7e11-4e08-9a24-8ff443eee9c1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02451dba6755e4db0c10d7cce20141468a67694f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-nettcp-send-handler"></a>Comment configurer un gestionnaire d'envoi WCF-NetTcp
La procédure suivante permet de configurer le gestionnaire d'envoi WCF-NetTcp.  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-send-handler"></a>Pour modifier les variables globales d'un gestionnaire d'envoi WCF-NetTcp  
  
1.  Dans la Console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **WCF-NetTcp**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.  
  
4.  Sur le **général** , cliquez sur **propriétés**. Sur le **Gestionnaire d’envoi** onglet, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre maximal de connexions**|Spécifiez le nombre maximal de connexions sortantes pour chaque point de terminaison mis en cache dans le pool de connexions. Cela limite le nombre de connexions sortantes mises en cache pour chaque point de terminaison unique distant. Vous devez choisir une valeur supérieure au nombre maximal de connexions sortantes que vous voulez mettre en cache pour chaque point de terminaison unique distant. Si le nombre de connexions sortantes actives est supérieur à cette valeur maximale, le service peut sembler inaccessible aux ports d'envoi WCF-NetTcp dont l'exécution est suivie par le gestionnaire d'envoi.<br /><br /> La valeur par défaut est 10.|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des Services WCF](../core/consuming-wcf-services.md)   
 [Configuration de l’adaptateur WCF-NetTcp](../core/configuring-the-wcf-nettcp-adapter.md)