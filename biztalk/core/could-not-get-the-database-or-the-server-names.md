---
title: "Ne peut pas obtenir la base de données ou les noms de serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0590f43b-0aec-491f-bca5-c50ab12552a5
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16c694acdc78b704eb6f2578df99239442fd897e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-get-the-database-or-the-server-names"></a>Impossible d'obtenir les noms de la base de données ou du serveur
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Impossible d'obtenir les noms de la base de données ou du serveur|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que BizTalk n'a pas pu lire le nom BizTalkMgmtDb et le nom du serveur depuis le registre. Une raison possible de cette erreur est que le groupe BizTalk n'est pas configuré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, configurez le groupe BizTalk :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  À la racine de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
3.  Avec le bouton droit **groupe BizTalk**.  
  
4.  Cliquez sur **Propriétés**.  
  
5.  Dans le volet gauche, cliquez sur **général**.  
  
6.  Vérifiez le **Server** nom et **base de données** nom sont corrects.