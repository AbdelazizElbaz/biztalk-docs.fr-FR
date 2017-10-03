---
title: Comment configurer la forme attente | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer], configuring
- Delay shape [Orchestration Designer]
- Delay shape [Orchestration Designer], timeouts
- Delay shape [Orchestration Designer], about Delay shape
- configuring [Orchestration Designer], Delay shapes
ms.assetid: 727be28d-932a-41d5-af3f-3ee6f7129a17
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b76448398facd3af7f3b9712491f9895ffb406d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-delay-shape"></a>Configuration de la forme Attente
![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")  
Forme Attente  
  
 Il existe deux façons de spécifier le délai d’attente pour un **délai**:  
  
-   Vous pouvez utiliser **System.DateTime**, ce qui entraîne l’orchestration en attente jusqu'à la date et heure est atteinte.  
  
     System.DateTime.UtcNow.AddSeconds(60)  
  
    > [!NOTE]
    >  Retards doivent être exprimées en temps universel coordonné (UTC) lors de l’utilisation **DateTime**.  
  
-   Vous pouvez utiliser **System.TimeSpan**, ce qui entraîne l’orchestration en attente pendant la durée spécifiée.  
  
     System.TimeSpan(0, 1, 0)  
  
 Si votre **délai** forme se trouve dans un **écouter** forme, vous n’avez pas besoin d’ajouter un point-virgule à la fin de l’expression.  
  
 Pour plus d’informations sur **System.DateTime** et **System.TimeSpan**, consultez « Structure DateTime » et « TimeSpan Structure » dans la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection combinée.  
  
> [!NOTE]
>  Dans un environnement à plusieurs ordinateurs installation où [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server sont installés sur des ordinateurs séparés, la **délai** forme peut prendre fin plus tôt que prévu en raison du temps sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs ne sont pas synchronisées.  
  
> [!NOTE]
>  Condition de stress, le délai d’expiration spécifié dans le **délai** forme peut se produire plus tard que ce que vous avez spécifié. Ceci est dû à la pénurie de threads constatée en condition de stress.  
  
### <a name="to-configure-a-delay-shape"></a>Pour configurer une forme Attente  
  
1.  Si l’éditeur d’Expression BizTalk n’est pas visible, cliquez sur le **délai** mettre en forme et cliquez sur **modifier le délai**, ou dans la fenêtre Propriétés, cliquez sur le **points de suspension** ( **...** ) bouton pour le **Expression** propriété.  
  
2.  Dans Éditeur d’Expression BizTalk, créez une expression qui retourne un **System.DateTime** objet ou un **System.TimeSpan** objet. Pour plus d’informations, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md).