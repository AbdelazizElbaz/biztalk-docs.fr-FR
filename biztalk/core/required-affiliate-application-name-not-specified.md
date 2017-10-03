---
title: "Nom de l’application associée obligatoire non spécifié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e82a39-b052-4702-bfe2-700756a0ee6a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c5ecbbcc1a1df97da5339118de873391a5d3ec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="required-affiliate-application-name-not-specified"></a>Le nom de l'application associée obligatoire n'a pas été indiqué
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Le nom de l'application associée obligatoire n'a pas été indiqué|  
  
## <a name="explanation"></a>Explication  
 **Utiliser l’authentification unique sur** option a été sélectionnée mais le nom de l’application associée n’a pas été spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer le nom de l'application associée.  
  
#### <a name="to-configure-the-affiliate-application-name"></a>Pour configurer le nom de l'application associée  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications BizTalk**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** liste, sélectionnez **WCF-Custom**.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet.  
  
9. Dans le **informations d’identification utilisateur** section, spécifiez une valeur pour **application associée**.  
  
 Pour plus d’informations sur la création d’une application associée SSO, consultez [http://go.microsoft.com/fwlink/?LinkId=94347](http://go.microsoft.com/fwlink/?LinkId=94347)