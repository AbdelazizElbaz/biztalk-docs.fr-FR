---
title: "Développer des applications BizTalk à l’aide de l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Content-Based Routing (CBR)
- BizTalk orchestrations, using orchestrations to perform operations
ms.assetid: 65689c83-4a57-4aad-b0e9-f1bad901a7b9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1b3f688987c0c8339a2fd81c1b1ddf67128818
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-oracle-database-adapter"></a>Développer des applications BizTalk à l’aide de l’adaptateur de base de données Oracle
Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer le schéma XML. Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.  
  
 CBR peut être utilisé dans les scénarios où les messages envoyés à la base de données Oracle nécessitent un traitement intensif. Par exemple, si vous savez que le port de réception recevra les messages uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour acheminer les messages correspondant à l’expression de filtre pour le port d’envoi.  
  
 Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer des opérations sur la base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], ce qui peut interagir avec une liaison WCF.  
  
> [!IMPORTANT]
>  Pour utiliser le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
> [!IMPORTANT]
>  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] inclus avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] ne figure pas dans la console Administration de BizTalk Server. Les adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] sont basées sur WCF et utiliser une liaison WCF personnalisée. La console Administration de BizTalk Server affiche la [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]. Il ne pas automatiquement afficher les liaisons personnalisées WCF et par conséquent n’affiche pas de WCF en fonction [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
> 
> En outre, pour générer des métadonnées, utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. N’utilisez pas le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Pour obtenir des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md). 
> 
> Pour les autres différences entre les versions d’adaptateur, consultez [migration BizTalk projets créés à l’aide de l’adaptateur ODBC pour base de données Oracle pour BizTalk](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).  
  
  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)