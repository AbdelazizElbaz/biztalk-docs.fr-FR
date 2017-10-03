---
title: "Aurait dû contenir l’échange EDIFACT TransactionSetGroup ou FunctionalGroup Xml balises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34318133-211f-422d-acdf-b841ece5d2b0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb93582daf235a7f1f0633231e536f3c5b14ab0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-should-have-contained-transactionsetgroup-or-functionalgroup-xml-tags"></a>L'échange EDIFACT aurait dû contenir les balises Xml TransactionSetGroup ou FunctionalGroup
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|L'échange EDIFACT aurait dû contenir les balises Xml TransactionSetGroup ou FunctionalGroup|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter un échange reçu par lot EDIFACT qui a été préservé, car les balises TransactionSetGroup ou FunctionalGroup n'étaient pas incluses dans le fichier d'échange XML.  
  
 Lorsque BizTalk traite un échange reçu par lot qui est préservé, une balise XML est attribuée à un groupe de documents informatisés ou à un groupe de groupes dans le fichier XML de l'échange. La balise TransactionSetGroup est attribuée à un groupe de documents informatiques. Une balise FunctionalGroup est attribuée au groupe de groupes. Cette condition d'erreur se produit si vous configurez un lot préservé via un pipeline de réception et un pipeline d'envoi de transmission de transfert. Les balises sont définies par le pipeline de réception et sont supprimées par le pipeline d'envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour remédier à cette erreur, vérifiez que la structure XML du fichier XML généré pour le lot préservé est bien formée, avec la balise TransactionSetGroup (pour un groupe doté de plusieurs documents informatisés) et/ou la balise FunctionalGroup (pour plusieurs groupes).