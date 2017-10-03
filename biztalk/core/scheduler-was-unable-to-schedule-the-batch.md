---
title: "Le planificateur n’a pas pu planifier le traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac6d79c-c995-4c95-a4da-ee2f50b9a13a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bef1df18d88f8497fde440383d63bc64eefdd69a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scheduler-was-unable-to-schedule-the-batch"></a>Le planificateur n'a pas réussi à planifier le lot
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|-|  
|Texte du message|Le planificateur n'a pas réussi à planifier le lot|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le planificateur n'a pas réussi à identifier l'occurrence suivante du déclenchement d'un lot.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que la planification du déclenchement du lot est valide :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis cliquez sur **Parties**.  
  
3.  Cliquez avec le bouton droit sur le tiers approprié.  
  
4.  Cliquez sur **Propriétés**.  
  
5.  Dans le [*nom du tiers*] **propriétés de tiers** boîte de dialogue, dans le volet gauche, cliquez sur **Ports d’envoi**.  
  
6.  Entrez le nom de port d’envoi dans le **Ports d’envoi** liste.  
  
7.  Cliquez sur **OK**.