---
title: "Comment sélectionner une Source de données actives ou archivées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Management database, archived data
- Management database, real-time data
- HAT, real-time data
- archived data, Management database
- HAT, archived data
- real-time data, HAT
- real-time data, Management database
- archived data, HAT
ms.assetid: e2325823-22e1-4a1a-865b-15757b215b29
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7172a822a71e2b0d7dc621e6c1e11b055b723bd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-a-live-or-archived-data-source"></a>Sélection d'une source de données actives ou archivées
BizTalktracking permet d'accéder aux données archivées et actives. Vous sélectionnez une source de données actives ou archivées à partir de la main **Administration de BizTalk Server** nœud Console d’Administration de BizTalk Server.  La source employée par défaut est celle comprenant les données actives, extraites de la base de données de gestion BizTalk. Si vous choisissez de travailler sur les données archivées, vous devez sélectionner le ou les serveurs et la ou les bases de données appropriés à cet usage.  
  
-   Les données archivées : l’analyse des données archivées permet à examiner les tendances dans votre entreprise et sur votre système, car vous pouvez en remontant jusqu'à nécessaire. Si vous souhaitez consulter des données archivées, vous devez également sélectionner les bases de données et les serveurs SQL Server appropriés, qui contiennent lesdites données.  
  
     Données archivées sont désignées en sélectionnant **se connecter à une base de données de suivi existant...** .  
  
-   Données actives : analyse des données en direct permet de vous permettent de surveiller les orchestrations et pipelines, afin que vous puissiez identifier et résoudre des problèmes dans l’environnement d’intermédiaire ou de développement. De même, elle permet de résoudre les problèmes apparaissant dans le système, par exemple de savoir pourquoi les messages sont suspendus.  
  
     Données actives sont désignées en sélectionnant **se connecter à un groupe existant...** .  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe opérateurs BizTalk Server pour effectuer cette procédure.  
  
### <a name="to-select-live-data"></a>Pour sélectionner des données actives  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Cliquez sur le principal **Administration de BizTalk Server** nœud.  
  
3.  Cliquez sur **se connecter à un groupe existant...**  
  
4.  Dans le **nom SQL Server** , tapez le nom du serveur qui héberge la base de données de gestion BizTalk.  
  
5.  Dans le **nom de la base de données** zone de liste déroulante, sélectionnez **BizTalkMgmtDb**.  
  
6.  Cliquez sur **OK**.  
  
### <a name="to-select-archived-data"></a>Pour sélectionner des données archivées  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Cliquez sur le principal **Administration de BizTalk Server** nœud.  
  
3.  Cliquez sur **se connecter à une base de données de suivi existant...**  
  
4.  Dans le **nom SQL Server** , tapez le nom du serveur qui héberge la base de données de gestion BizTalk.  
  
5.  Dans le **nom de la base de données** zone de liste déroulante, sélectionnez **BizTalkMgmtDb**.  
  
6.  Cliquez sur **OK**.