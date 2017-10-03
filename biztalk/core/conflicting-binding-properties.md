---
title: "Conflit de propriétés de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b08c317e-a617-464b-9ee4-007fb41d99b2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6202385127a676d1f2714b2c3644d135a3d6a7a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conflicting-binding-properties"></a>Propriétés de liaison en conflit
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Conflit de propriétés de liaison : MsmqAuthenticationMode = {0} et MsmqProtectionLevel = \ {1\\} n’est pas valide. Modifiez l'une des propriétés pour résoudre le conflit|  
  
## <a name="explanation"></a>Explication  
 La valeur de la propriété de niveau de protection MSMQ d’un transport WCF-NetMsmq **signe** ou **EncryptAndSign** pour le mode d’authentification MSMQ aucun.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez le niveau de protection MSMQ ou la propriété de mode d'authentification MSMQ pour obtenir une cohérence avec la propriété de niveau de protection MSMQ.  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, cliquez sur le **sécurité** onglet.  
  
9. Vérifiez les valeurs dans MSMQ **mode d’authentification** liste et **niveau de protection MSMQ** liste.  
  
 Pour plus d’informations, consultez les ressources suivantes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide :  
  
-   [Comment configurer un Port d’envoi WCF-NetMsmq](../core/how-to-configure-a-wcf-netmsmq-send-port.md)  
  
-   [Pour configurer les emplacement de réception WCF-NetMsmq](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)