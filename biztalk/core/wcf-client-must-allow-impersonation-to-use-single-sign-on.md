---
title: "Client WCF doit autoriser l’emprunt d’identité à utiliser l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5b9f294-4d8a-4a12-91e8-8d325db7c420
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5e43039a69d057b0d20767ff9061a8d6b4e4f70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-client-must-allow-impersonation-to-use-single-sign-on"></a>Le client WCF doit autoriser l'emprunt d'identité pour utiliser l'authentification unique
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Le client WCF doit autoriser l'emprunt d'identité pour utiliser l'authentification unique.|  
  
## <a name="explanation"></a>Explication  
 Bien que l'authentification unique soit activée dans l'emplacement de réception, le client WCF n'autorise pas l'emprunt d'identité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que le client WCF appelant le service autorise l'emprunt d'identité.  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** liste, sélectionnez **WCF-Custom** (ou **WCF-CustomIsolate**).  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **comportement** onglet.  
  
9. Dans le **comportement** , cliquez sur **ServiceAuthorization**. Dans le **Configuration** section, la propriété **ImpersonateCallerForAllOperations** doit être défini sur **True**.  
  
10. Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **autres** onglet.  
  
11. Dans les sections informations d’identification, sélectionnez l’option **utilisez Single Sign-On**.