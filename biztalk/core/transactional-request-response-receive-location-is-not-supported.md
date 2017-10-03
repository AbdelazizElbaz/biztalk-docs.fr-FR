---
title: "Emplacement de réception requête-réponse transactionnelles n’est pas prise en charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89b619-280c-4ab5-b6aa-06b14a075f8e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34de32b338a78b598941d4e828c1a0b736dde4e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactional-request-response-receive-location-is-not-supported"></a>L'emplacement de réception requête-réponse transactionnelles n'est pas pris en charge
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|L'emplacement de réception requête-réponse transactionnelles n'est pas pris en charge.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que la transaction a été activée pour un emplacement de réception de requête-réponse WCF. Les transactions ne sont pas prises en charge dans BizTalk pour un emplacement de réception de requête-réponse en raison de la base de données MessageBox.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour les adaptateurs WCF standard, accédez au code de configuration de l'emplacement de réception de requête-réponse. Vérifiez que le **EnableTransaction** élément dans les données XML pour le **TransportTypeData** propriété de la **ITransportInfo** interface est définie sur **False** .  
  
 Pour les adaptateurs WCF-Custom :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Assurez-vous que la propriété transactionFlow est définie sur **False**.