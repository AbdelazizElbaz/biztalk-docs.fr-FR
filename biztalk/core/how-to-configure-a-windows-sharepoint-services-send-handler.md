---
title: "Comment faire pour configurer Windows SharePoint Services de gestionnaire d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], send handlers
- send handlers, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, send handlers
ms.assetid: 457767d9-6e39-4553-9bbe-212fcb7c04bc
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 654fb0eb246cdc8507d1830afce29ebd71fe6a4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-windows-sharepoint-services-send-handler"></a>Configuration d'un gestionnaire d'envoi Windows SharePoint Services
La procédure suivante permet de modifier l'hôte auquel le gestionnaire d'envoi Windows SharePoint Services est associé.  
  
> [!NOTE]
>  Un seul gestionnaire d'envoi peut être associé à chaque hôte.  
  
### <a name="to-change-global-variables-for-a-windows-sharepoint-services-send-handler"></a>Pour modifier les variables globales d'un gestionnaire d'envoi Windows SharePoint Services  
  
1.  Dans la console Administration de BizTalk Server, cliquez pour développer [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, puis cliquez pour développer **groupe BizTalk [\<nom_serveur > :\<base de données de gestion > ]**, cliquez pour développer **paramètres de plateforme**, puis cliquez pour développer **cartes**. La liste des adaptateurs est affichée dans le dossier.  
  
2.  Cliquez sur **Windows SharePoint Services**, dans le volet droit, cliquez sur le Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.  
  
4.  Sur le **général** , cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du Transport Windows SharePoint Services** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Taille du lot d'envoi|Nombre maximal de documents que le service Web Windows SharePoint Services va traiter en un seul lot. La valeur par défaut est 20. **Remarque :** la valeur minimale est 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer Windows SharePoint Services emplacement de réception](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [Comment configurer un Port d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)   
 [Référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Expressions de l’adaptateur de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md)   
 [Prise en charge des Types de colonnes Windows SharePoint Services](../core/supported-windows-sharepoint-services-column-types.md)