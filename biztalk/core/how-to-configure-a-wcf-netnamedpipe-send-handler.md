---
title: "Comment configurer un gestionnaire d’envoi WCF-NetNamedPipe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-NetNamedPipe adapters, global adapters
- configuring [WCF-NetNamedPipe adapters], global adapters
- send handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], send handlers
ms.assetid: 1f281649-d09f-44eb-8af5-1f83233fab60
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 079d490ab8af28292c5f6adc6d98c8f64c5b16fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netnamedpipe-send-handler"></a>Configuration d'un gestionnaire d'envoi WCF-NetNamedPipe
La procédure suivante permet de configurer un gestionnaire d'envoi WCF-NetNamedPipe.  
  
### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-send-handler"></a>Pour modifier les variables globales d'un gestionnaire d'envoi WCF-NetNamedPipe  
  
1.  Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **WCF-NetNamedPipe**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.  
  
4.  Dans le **général** , cliquez sur **propriétés**. Sur le **Gestionnaire d’envoi** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre maximal de connexions**|Spécifiez le nombre maximal de connexions sortantes pour chaque point de terminaison mis en cache dans le pool de connexions. Cela limite le nombre de connexions sortantes mises en cache pour chaque point de terminaison unique distant. Vous devez choisir une valeur supérieure au nombre maximal de connexions sortantes que vous voulez mettre en cache pour chaque point de terminaison unique distant. Si le nombre de connexions sortantes actives est supérieur à cette valeur maximale, le service peut sembler inaccessible aux ports d'envoi WCF-NetNamedPipe dont l'exécution est suivie par le gestionnaire d'envoi.<br /><br /> La valeur par défaut est 10.|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des Services WCF](../core/consuming-wcf-services.md)   
 [Configuration de l’adaptateur WCF-NetNamedPipe](../core/configuring-the-wcf-netnamedpipe-adapter.md)