---
title: "Désignation d’un nouveau serveur de secret principal manuellement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fa44143-8d29-49ba-9c71-96be2c9ded67
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b6d635312d3765c37f1ab9c2b64505698f93e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designating-a-new-master-secret-server-manually"></a>Désignation d’un nouveau serveur de secret principal manuellement
Matériel de cluster peut être coûteux. Si le coût du matériel est un problème, vous pouvez envisager de manuellement désigner un autre serveur Enterprise Single Sign-On (SSO) comme serveur de secret principal durant les scénarios de défaillance. À l’aide de cette option, tout autre serveur de l’authentification unique dans le groupe de l’authentification unique peut être promue pour le serveur de secret principal. Lorsque le masque est arrêté, vous pouvez promouvoir manuellement un des serveurs d’authentification unique pour être le serveur de secret principal. L’inconvénient majeurs de cette technique est que vous ne peut pas modifier les déploiements existants, redémarrez existants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services, ou déployer des applications BizTalk jusqu'à ce que vous promouvez un nouveau serveur de secret principal.  
  
 Pour faciliter le processus transparente, vous devez implémenter un mécanisme d’analyse afin de vous allez découvrir l’échec dès que possible. Vous pouvez également automatiser le processus de promotion à l’aide d’une application de surveillance tels que System Center Operations Manager.  
  
 Pour plus d’informations sur le déplacement de manuellement le serveur de secret principal, consultez [comment déplacer le serveur de secret principal](http://go.microsoft.com/fwlink/?LinkId=156841) (http://go.microsoft.com/fwlink/?LinkId=156841) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Clustering du serveur de secret principal](../technical-guides/clustering-the-master-secret-server.md)