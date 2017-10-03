---
title: "Pour configurer les Gestionnaire de réception WCF-NetNamedPipe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [WCF-NetNamedPipe adapters], global variables
- receive handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], receive handlers
- WCF-NetNamedPipe adapters, global variables
ms.assetid: f7ab2228-1049-40f0-87f7-6330a8f40cfe
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9339cca7f8065d3412686cfcc84d84028ef39faf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netnamedpipe-receive-handler"></a>Configuration d'un gestionnaire de réception WCF-NetNamedPipe
La procédure suivante permet de configurer un gestionnaire de réception WCF-NetNamedPipe.  
  
### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-receive-handler"></a>Pour modifier les variables globales d'un gestionnaire de réception WCF-NetNamedPipe  
  
1.  Dans la console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **WCF-NetNamedPipe**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.  
  
4.  Dans le **général** , cliquez sur **propriétés**. Sur le **Gestionnaire de réception** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre maximal de connexions**|Spécifier un nombre maximal de connexions que l’écouteur peut mettre en attente d’acceptation par l’application. Lorsque ce quota est dépassé, les nouvelles connexions entrantes sont interrompues plutôt que mises en attente d'acceptation.<br /><br /> La valeur par défaut est 10.|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des Services WCF](../core/publishing-wcf-services.md)   
 [Configuration de l’adaptateur WCF-NetNamedPipe](../core/configuring-the-wcf-netnamedpipe-adapter.md)