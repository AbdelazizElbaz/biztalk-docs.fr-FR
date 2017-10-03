---
title: "Comment modifier l’URI d’un Service Web utilisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, modifying
- Web services, consuming
- consuming [Web services]
- modifying, Web services
ms.assetid: 907de565-8c99-4d34-939f-fd3dba37dd11
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b9ae7d7178fc24c5f16b28325fb627045e5273a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-uri-of-a-consumed-web-service"></a>Modification de l'URI d'un service web utilisé
Suite au déploiement de votre orchestration, BizTalk Server configure un port d'envoi pour chaque service Web qu'elle référence. Par défaut, BizTalk utilise l'URL du service Web au moment de l'exécution pour la même URL associée au service Web importé. Vous pouvez modifier cette URL à l'aide de la console Administration de BizTalk Server.  
  
> [!NOTE]
>  Vous devez déployer votre orchestration avant de modifier l'URI d'un service Web utilisé. Pour plus d’informations sur le déploiement de l’orchestration, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
### <a name="to-change-the-uri-of-a-consumed-web-service-using-biztalk-server-administration-console"></a>Pour modifier l'URI d'un service Web utilisé à l'aide de la console Administration de BizTalk Server  
  
1.  Dans la console Administration de BizTalk Server, développez une application BizTalk, puis développez le **Ports d’envoi** nœud.  
  
2.  Sur un port d’envoi configuré avec l’adaptateur SOAP, cliquez **propriétés**.  
  
3.  Si vous n’avez pas de ports physiques, vous pouvez créer des ports d’envoi et emplacements de réception à l’aide de la console Administration de BizTalk. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
4.  Sur le **propriétés d’envoi** boîte de dialogue, cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport SOAP** boîte de dialogue le **URL du Service Web** zone, tapez l’URL complète de l’emplacement du service Web, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Vous devez vous assurer qu'un service Web existe pour l'URL que vous avez spécifiée. BizTalk Server ne valide pas l'adresse de l'URL.  
  
6.  Cliquez sur OK pour quitter le **propriétés d’envoi** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md)   
 [Comment configurer un Port d’envoi SOAP](../core/how-to-configure-a-soap-send-port.md)   
 [En-têtes SOAP avec les Services Web utilisés](../core/soap-headers-with-consumed-web-services.md)   
 [Création de Ports Web](../core/creating-web-ports.md)