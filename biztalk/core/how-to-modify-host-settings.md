---
title: "Comment modifier les paramètres de l’hôte | Documents Microsoft"
description: "Modifier les paramètres de l’hôte BizTalk dans l’Administration de BizTalk Server pour améliorer les performances et limitation"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0759b3a0-560e-4a11-92e6-9de0e15f463b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 998c668bf787c9db260597c3a350e0e571492212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-biztalk-host-settings"></a>Mettre à jour les paramètres de l’hôte BizTalk

## <a name="overview"></a>Vue d'ensemble
Le panneau de configuration permet de modifier les informations de configuration d'un hôte donné à l'intérieur d'un groupe BizTalk. Cette rubrique contient une procédure pas à pas permettant de modifier les paramètres de performance au niveau de l'hôte dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Vous pouvez également modifier les paramètres d'instance du groupe et de l'hôte. Pour plus d’informations sur la façon de modifier les paramètres, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).  
  
 Vous pouvez exporter les paramètres actuels de BizTalk Server dans un fichier XML. Plus tard, vous pourrez les importer dans le panneau de configuration au lieu de configurer de nouvelles valeurs. Pour plus d’informations sur l’importation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] paramètres, voir [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) et [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md). 
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="update-the-host-level-settings"></a>Mettre à jour les paramètres au niveau de l’hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** , effectuez une ou plusieurs des opérations suivantes.  
  
    -   Modifiez les paramètres de performances généraux de l'hôte BizTalk. Consultez [comment modifier les paramètres généraux](../core/how-to-modify-general-settings.md).  
  
    -   Modifiez les paramètres de limitation basée sur la ressource de l'hôte BizTalk. Consultez [comment modifier la ressource en fonction de paramètres de limitation](../core/how-to-modify-resource-based-throttling-settings.md).  
  
    -   Modifier les paramètres de limitation basée sur la fréquence de l’hôte BizTalk. Consultez [comment modifier la fréquence en fonction de paramètres de limitation](../core/how-to-modify-rate-based-throttling-settings.md).  
  
    -   Modifiez les paramètres de limitation de l'orchestration de l'hôte BizTalk. Consultez [comment modifier les paramètres de limitation d’Orchestration](../core/how-to-modify-orchestration-throttling-settings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez le panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)