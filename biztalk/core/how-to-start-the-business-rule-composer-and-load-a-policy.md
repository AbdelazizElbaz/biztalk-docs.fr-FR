---
title: "Comment démarrer l’éditeur des règles d’entreprise et de charger une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, loading
- opening, Busines Rule Composer
- Business Rule Composer, policies
- Business Rule Composer, opening
ms.assetid: 34a6034d-90b3-4ce0-9770-3790763affe3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 420517c51fd6c7a6c854afe161a11a58f952db83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-the-business-rule-composer-and-load-a-policy"></a>Comment démarrer l’éditeur des règles d’entreprise et de charger une stratégie
Cette section explique comment démarrer l'Éditeur des règles d'entreprise et charger une stratégie.  
  
### <a name="to-start-the-business-rule-composer"></a>Pour démarrer l'Éditeur des règles d'entreprise  
  
-   Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
### <a name="to-load-a-policy"></a>Pour charger une stratégie  
  
1.  Dans l’éditeur des règles d’entreprise, sur le **magasin de règles** menu, cliquez sur **charge**.  
  
2.  Dans le **magasin de règles** boîte de dialogue le **SQL Server** liste déroulante, sélectionnez l’ordinateur SQL Server™ auquel vous souhaitez vous connecter.  
  
3.  Dans le **base de données** liste déroulante, sélectionnez la base de données qui contient le magasin de règles que vous souhaitez ouvrir.  
  
> [!NOTE]
>  La base de données par défaut pour le magasin de règles installé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est **BizTalkRuleEngineDb**.  
  
> [!NOTE]
>  Si vous utilisez un compte SQL Server nouvellement créé qui a le **appliquer l’expiration du mot de passe** et **utilisateur doit changer de mot de passe à la prochaine connexion** options set, l’éditeur des règles d’entreprise ne pourront pas se connecter à la règle Moteur de base de données.