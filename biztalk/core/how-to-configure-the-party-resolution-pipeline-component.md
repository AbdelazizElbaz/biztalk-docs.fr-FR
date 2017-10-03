---
title: "Comment configurer le composant de Pipeline résolution du tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authenticating, Partner Management
- Party Resolution [pipeline component], configuring
- Partner Management, authenticating
- pipeline components, Party Resolution
ms.assetid: 0ebd30f7-3a6b-4457-8e30-80bf81fbd28d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0c78792cd7c61ed1297954625fbd7da5aedfa04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-party-resolution-pipeline-component"></a>Configuration du composant de pipeline Résolution du tiers
Le composant de pipeline Résolution du tiers permet de mapper l'ID de sécurité de l’utilisateur et l'objet du certificat du client vers un tiers BizTalk Server. Le mappage est utilisé pour appliquer l’authentification des tiers envoyant des messages à BizTalk Server. Pour plus d’informations sur la gestion des partenaires, consultez[la création d’un accord](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).  
  
> [!NOTE]
>  Pour permettre au composant de pipeline Résolution du tiers de valider un utilisateur Windows, vous devez ajouter l’alias WindowsUser à un tiers. Pour plus d’informations, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).  
  
### <a name="to-configure-the-properties-for-the-party-resolution-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Résolution du tiers  
  
1.  Faites glisser le composant de pipeline Résolution du tiers dans la phase de résolution de tiers d'un pipeline de réception.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Résoudre le tiers par le certificat**|La valeur **True** si vous souhaitez activer la résolution de tiers en fonction de l’empreinte numérique du certificat de signature du tiers à partir duquel les messages sont reçus.<br /><br /> Valeur par défaut : **True**|  
    |**Résoudre le tiers par le SID**|La valeur **True** si vous souhaitez activer la résolution de tiers en fonction de l’identificateur de sécurité (SID) du compte de l’expéditeur.<br /><br /> Si les deux propriétés sont définies sur **True**, le **résoudre le tiers par certificat** propriété est prioritaire sur la **résoudre le tiers par SID** propriété, ce qui signifie que si les deux le certificat et l’identificateur de sécurité sont disponibles, le sujet du certificat est utilisé. Si le tiers ne peut pas être résolu à l’aide de l’objet du certificat, le composant ne tombe pas dans le **résoudre le tiers par SID** propriété et la valeur par défaut (s-1-5-7) est appliquée pour **BTS. SourcePartyID**.<br /><br /> Valeur par défaut : **True**|  
  
> [!NOTE]
>  Si vous utilisez l’adaptateur BizTalk Message Queuing et vous souhaitez résoudre le tiers en fonction de nom d’utilisateur, définissez **résoudre le tiers par certificat** à **False** et **résoudre le tiers par SID** à **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline résolution du tiers](../core/party-resolution-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Résolution du tiers personnalisé (exemple BizTalk Server)](../core/custom-party-resolution-biztalk-server-sample.md)