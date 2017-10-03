---
title: "Qu'est-ce qu'un gestionnaire d'adaptateur ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- handlers [adapters]
- adapters, handlers
- handlers [adapters], about handlers
ms.assetid: 4d1afa39-6320-467f-a7e8-f5f18236648e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c8a1b60661427776dd4e35ffce27bf120bf94a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-adapter-handler"></a>Qu'est-ce qu'un gestionnaire d'adaptateur ?
Un gestionnaire d'adaptateur est une instance d'un hôte BizTalk dans lequel le code d'adaptateur est exécuté. Lorsque vous spécifiez un gestionnaire d'envoi ou de réception pour un adaptateur, vous indiquez l'instance d'hôte dans le contexte de laquelle le code d'adaptateur sera exécuté. Un gestionnaire d'adaptateur est chargé d'exécuter l'adaptateur et contient les propriétés d'une instance spécifique d'un adaptateur. Une configuration BizTalk Server par défaut créera les gestionnaires d'adaptateur pour les adaptateurs installés, mais vous pouvez créer d'autres gestionnaires d'adaptateur à des fins d'équilibrage de la charge ou pour isoler le processus d'un gestionnaire d'adaptateur particulier.  
  
 Les gestionnaires d'adaptateur sont liés à une instance d'hôte BizTalk. Les instances d'hôte BizTalk sont liées à un serveur BizTalk. Par conséquent, vous devez ajouter des serveurs BizTalk supplémentaires à votre groupe BizTalk si vous souhaitez équilibrer la charge liée aux processus des adaptateurs entre les serveurs BizTalk. Il n'est pas nécessaire d'ajouter d'autres serveurs BizTalk à votre groupe BizTalk si vous créez des gestionnaires d'adaptateur supplémentaires afin d'isoler les processus.  
  
 Si vous devez créer une instance d'hôte dans laquelle exécuter un gestionnaire d'adaptateur, vous devez d'abord créer un hôte, puis créer une instance de cet hôte à exécuter sur un de vos serveurs BizTalk. Pour plus d’informations, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md) et [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).  
  
 Tous les gestionnaires d'adaptateur, à l'exception des gestionnaires de réception des adaptateurs HTTP et SOAP, doivent être configurés pour être exécutés sur un hôte In-process. Les gestionnaires de réception des adaptateurs HTTP et SOAP peuvent uniquement être exécutés sur un hôte isolé.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et suppression de gestionnaires d’adaptateur](../core/creating-and-deleting-adapter-handlers.md)