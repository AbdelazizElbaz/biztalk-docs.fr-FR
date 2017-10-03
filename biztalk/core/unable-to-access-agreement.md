---
title: "Impossible d’accéder au contrat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72890ee9-54c9-48ed-8c6e-8b329d79c68b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a28b2b3587781d66e8788ca88931c7c5522bac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-agreement"></a>Impossible d'accéder à l'accord
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|UnableToLocateAS2PartyError|  
|Texte du message|Impossible d'accéder à l'accord. AS2From : {0} AS2To : {1}. Erreur : {{2}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que BizTalk Server n'a pas pu détecter un tiers correspondant au qualificateur et à la valeur donnés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, créez un alias de tiers pour le qualificateur donné :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis cliquez sur **Parties**.  
  
3.  Cliquez avec le bouton droit sur le tiers approprié.  
  
4.  Cliquez sur **Propriétés**.  
  
5.  Dans le [*nom du tiers*] **propriétés de tiers** boîte de dialogue, entrez **EDIINT-AS2 From Value** dans les **nom** colonne.  
  
6.  Entrez le nom du tiers dans le **valeur** colonne.  
  
7.  Cliquez sur **OK**.