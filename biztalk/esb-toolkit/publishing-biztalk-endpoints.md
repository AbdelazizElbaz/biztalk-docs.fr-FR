---
title: Publication des points de terminaison BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8e8cc81-c6c7-4269-81e3-8725082a0c98
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e33517f1261324ad01eb0d9cad0f51b74c280828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-biztalk-endpoints"></a>Points de terminaison de publication BizTalk
Vous pouvez utiliser le portail de gestion ESB pour créer et publier des entrées dans le serveur Universal Description, Discovery and Integration (UDDI) configuré actuellement.  
  
### <a name="to-publish-a-microsoft-biztalk-server-endpoint-into-the-current-uddi-server"></a>Pour publier un point de terminaison de Microsoft BizTalk Server sur le serveur UDDI en cours  
  
1.  Pointez sur le **Registre** onglet dans le menu principal de portail, puis cliquez sur **nouvelle entrée de Registre** pour ouvrir le [nouvelle Page d’entrée de Registre](../esb-toolkit/new-registry-entry-page.md).  
  
2.  Pour filtrer sur le type de point de terminaison, l’état et l’application où se trouve le point de terminaison, utilisez les listes déroulantes dans la page.  
  
3.  Cliquez sur l’icône de flèche en regard du point de terminaison que vous voulez publier pour créer une demande d’inscription UDDI.  
  
4.  Si un administrateur a activé la publication automatique des points de terminaison, le portail publie automatiquement la nouvelle entrée dans le serveur UDDI.  
  
5.  Si un administrateur n’a pas activé la publication automatique des points de terminaison, les demandes reste dans la file d’attente jusqu'à ce qu’un administrateur approuve ou refuse la demande.