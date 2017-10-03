---
title: "Erreur structurelle s’est produite pendant la sérialisation d’un message XML d’échange | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97939bfd-d1ee-455a-9952-4f25db020e7c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b56cce9fdd3704f7e6ddc2ba5b5bebb62d36e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structural-error-encountered-during-serialization-of-an-interchange-xml-message"></a>Erreur structurelle s’est produite pendant la sérialisation d’un message XML d’échange
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|InvalidXmlNodeFound|  
|Texte du message|Erreur structurelle rencontrée durant la sérialisation d'un message Xml d'échange|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique qu'une erreur structurelle a été rencontrée durant la sérialisation d'un message XML d'échange. Alors que BTS recherchait un élément XML StartElement ou EndElement, un type de nœud XML différent a été rencontré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que la structure du message est correcte, puis réessayez :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez sur **groupe BizTalk**.  
  
3.  Dans le volet droit, cliquez sur le **Hub du groupe** onglet.  
  
4.  Cliquez sur **instances de Service suspendues**.  
  
5.  Double-cliquez sur le message.  
  
6.  Dans le **détails du Service** fenêtre, cliquez sur le **Messages** onglet.  
  
7.  Double-cliquez de nouveau sur le message.  
  
8.  Dans le volet gauche, cliquez sur **parties de messages / corps**.  
  
9. Déterminez si la structure du message est correcte.