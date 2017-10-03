---
title: "Suite algorithmique de sécurité non pris en charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11696fed-c3a8-4b11-8249-9f99f7abc8f2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43cce7cd315c3bdfa3835014c2cf1f6a8c7077f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-security-algorithm-suite"></a>Valeur de suite d'algorithmes de sécurité non prise en charge
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Suite algorithmique de sécurité non pris en charge : {0}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lorsque la propriété de la suite d'algorithmes de sécurité d'un emplacement de réception ou d'un port d'envoi est définie sur une valeur erronée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que la propriété de protocole de transaction est définie sur une valeur valide.  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** liste, sélectionnez **WCF-NetTcp**.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-NetTcp** boîte de dialogue, cliquez sur le **sécurité** onglet.  
  
9. Dans le **la sécurité de Message** section, vérifiez que les valeurs de **suite d’algorithmes** sont corrects.