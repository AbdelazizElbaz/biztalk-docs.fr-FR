---
title: "AS2 Rapports d’état du contenu du Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6244aa59-a80d-450b-ab95-9a5e14c0c40e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b2dadb3231136255dcf532e5054c1a6228880f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-message-content-status-reports"></a>Rapports d'état sur le contenu d'un message AS2

## <a name="overview"></a>Vue d'ensemble
Les rapports d'état suivants affichent les propriétés de contexte, les en-têtes et la charge d'un message AS2 ou d'un MDN. Trois rapports d'état sur le contenu d'un message AS2 existent :  
  
-   rapport de message au format câble ;  
  
-   rapport de message au format décodé ;  
  
-   rapport de message MDN.  
  
 Afficher l’un de ces rapports en double-cliquant sur un message AS2 dans le rapport d’état AS2/MDN, puis en cliquant **vue Message au Format câble**, **vue Message au Format décodé**, ou **vue Mdn Message**. La commande MDN affiche le MDN corrélé au message AS2.  
  
 Ces rapports ne sont disponibles que si vous avez sélectionné les propriétés « Stocker les messages dans une base de données de non-répudiation » correspondantes sur la page Tiers considéré comme expéditeur des messages AS2 ou la page Tiers considéré comme récepteur des messages AS2 de la boîte de dialogue Propriétés AS2 relative au tiers associé. La commande stocke les messages AS2 ou les MDN au format câble ou décodé dans la base de données BizTalkDTADb.  
  
 Ce rapport utilise la **boîte de dialogue Propriétés de Message détails** (consultez les détails de l’interface utilisateur [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) pour afficher les données du message, avec les informations séparées en pages :  
  
|Radiomessagerie|Données affichées|  
|----------|--------------------|  
|**Général**|Informations générales sur le message|  
|**Contexte**|Propriétés de contexte associées à ce message|  
|**Parties de message**|Charge du document individuel contenu dans ce message. Chaque document peut être affiché sous forme textuelle ou binaire :<br /><br /> -L’affichage au Format texte affiche le contenu du message AS2 ou MDN sous forme lisible, comme dans un fichier texte EDI. Cet affichage contient les en-têtes AS2, les codes de fin EDI et la charge EDI, chaque segment se trouvant sur une ligne distincte.<br />-L’affichage au Format binaire présente le contenu du message AS2 ou MDN dans un format texte non délimité et une table des représentations hexadécimales de chaque caractère ASCII dans le message AS2 ou MDN.|