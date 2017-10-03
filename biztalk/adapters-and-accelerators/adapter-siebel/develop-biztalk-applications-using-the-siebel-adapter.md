---
title: "Développer des applications BizTalk à l’aide de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 08/02/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
- CBR
- Content-Based Routing
ms.assetid: 1a2a9765-305c-44b2-aed7-5437725e4c19
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8267c07027d9994b0115ebaf49fde96e76f2716
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-siebel-adapter"></a>Développer des applications BizTalk à l’aide de l’adaptateur Siebel

## <a name="overview"></a>Vue d'ensemble
Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer le schéma XML. Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.  
  
 CBR peut être utilisé dans les scénarios où les messages envoyés à un système Siebel nécessitent un traitement intensif. Par exemple, si vous savez que le port de réception recevra les messages uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour acheminer les messages correspondant à l’expression de filtre pour le port d’envoi.  
  
 Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer des opérations sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] capable d’interagir avec une liaison WCF.  

## <a name="before-you-begin"></a>Avant de commencer  

* Pour utiliser le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], affectez toujours la **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Pour connaître les étapes, consultez [configurer les propriétés de liaison pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).
  
* Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] ne figure pas automatiquement dans la console Administration de BizTalk Server. C’est parce que le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est une liaison WCF personnalisée. 

* Pour générer des métadonnées, utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. N’utilisez pas le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Pour obtenir des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).   

  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)