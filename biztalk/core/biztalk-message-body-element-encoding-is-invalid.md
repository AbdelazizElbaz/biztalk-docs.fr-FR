---
title: "Codage d’élément de corps du message BizTalk n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbf134b390af1904d74f1652aac00f6ea4b33ad2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-message-body-element-encoding-is-invalid"></a>Le codage de l'élément corps de message BizTalk est non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Le codage de l'élément corps de message BizTalk " {0}" est non valide. Codage attendu : « xml », « base64 », « hex » ou « chaîne »|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique l'utilisation de l'option de modèle de corps BizTalk pour les messages sortants. Toutefois, le type de codage spécifié pour le corps BizTalk est non valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer le type de codage.  
  
#### <a name="to-configure-the-encoding-type"></a>Pour configurer le type de codage  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Messages** onglet.  
  
9. Dans le **le corps du message WCF sortant** , cliquez sur le **modèle--contenu spécifié par le modèle** case d’option. Dans le **XML** zone de texte, le format du corps BizTalk doit être   
    \<**BTS-msg-body xmlns = « http://www.microsoft.com/schemas/bts2007 » encoding = « [xml &#124; base64 &#124; hex &#124; chaîne] » /**> (valeurs valides, qui respectent la casse, pour le codage est xml &#124; base64 &#124; hex &#124; chaîne)