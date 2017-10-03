---
title: "Comment modifier les propriétés d’un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive locations], properties
- managing [receive locations], editing
- receive locations, properties
- receive locations, editing
- editing, receive locations
- editing, properties
ms.assetid: 2b622050-a875-4896-bed6-65ca39a26dd3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 578c5e2970e587180a7928563ebdd942c62dc396
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-edit-the-properties-of-a-receive-location"></a>Modification des propriétés d’un emplacement de réception
La présente rubrique explique comment modifier les propriétés d'un emplacement de réception à l'aide de la console Administration de BizTalk Server. Pour obtenir des instructions sur la création d’un emplacement de réception, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-edit-the-properties-of-a-receive-location"></a>Pour modifier les propriétés d’un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk et l’application BizTalk pour laquelle vous souhaitez modifier les propriétés d’un emplacement de réception, puis sur **emplacements de réception**.  
  
3.  Dans le volet droit, cliquez sur l’emplacement de réception, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de l’emplacement de réception** fenêtre, modifiez une ou plusieurs des propriétés suivantes, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Taper le nom de l'emplacement de réception.|  
    |**Type**|Sélectionner le type ou le protocole de transfert dans la liste déroulante. Si vous modifiez le type de transport, vous devez configurer les propriétés de transport, comme décrit ci-après.|  
    |**Configurer**|Après avoir sélectionné le type de transport, cliquez sur **configurer** pour afficher les **propriétés du Transport** boîte de dialogue zone et de configurer les propriétés de l’adaptateur pour l’emplacement de réception. Pour obtenir des instructions, cliquez sur **aide** dans la boîte de dialogue. Pour plus d’informations sur la configuration de chaque type d’adaptateur, consultez la rubrique appropriée sous [à l’aide des adaptateurs](../core/using-adapters.md).|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionner l'instance de l'hôte BizTalk Server dans laquelle l'emplacement de réception s'exécutera. Le gestionnaire de réception doit être exécuté sur cet hôte.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez le pipeline de réception à utiliser pour recevoir les messages à cet emplacement de réception.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez le pipeline d'envoi à utiliser pour envoyer des réponses à partir de cet emplacement de réception. Cette liste est uniquement disponible pour un emplacement de réception associé à un port de réception requête-réponse.|  
    |**Transformer en emplacement principal**|Cette case à cocher doit être activée si un port est associé à plusieurs emplacements de réception et que cet emplacement de réception est celui qui doit représenter le port de réception lorsque ce dernier est communiqué à une entité (un partenaire commercial, par exemple) souhaitant envoyer des messages à votre organisation. Le premier emplacement de réception créé est automatiquement sélectionné pour jouer le rôle d'emplacement de réception principal. Cette propriété demeure sélectionnée et indisponible tant que vous n'avez pas indiqué un emplacement de réception principal différent.|  
  
> [!NOTE]
>  Si vous modifiez un emplacement de réception, redémarrez les processus de travail de l'hôte isolé correspondant à l'emplacement de réception modifié.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)