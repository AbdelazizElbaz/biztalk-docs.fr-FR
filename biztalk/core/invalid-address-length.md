---
title: "Longueur d’adresse non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8e16eb6-e77e-4361-ac91-0730004c4433
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2df1666fbbd399ef71852b9b9049959830749e99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-length"></a>Longueur d'adresse non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Longueur d’adresse non valide ; longueur de l’adresse spécifiée est {0} caractères, la limite est de {{1} caractères|  
  
## <a name="explanation"></a>Explication  
 Vous avez fourni une adresse qui dépasse la longueur maximale de 255 caractères pour un transport WCF. Cette limitation est imposée par BizTalk Server, et non par WCF.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer une adresse valide.  
  
#### <a name="to-configure-a-valid-address"></a>Pour configurer une adresse valide  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.  
  
9. Dans le **adresse (URI)** texte zone, vérifiez que l’adresse ne dépasse pas la longueur maximale de 255 caractères.