---
title: "Échec de la sérialisation Xml de l’échange EDIFACT en raison d’une structure non valide, aucun transactionSet ou de UNE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ce1c219-f2ed-46c1-ae4b-8a4206f7cd01
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5c6aae4bc3ed16afffadec774eaeac9ed64808d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-transactionset-or-une"></a>Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide, absence de transactionSet ou UNE.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactTransactionSetOrUneNotFound|  
|Texte du message|Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide. Recherche de TransactionSet ou de UNE infructueuse.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI n'a pas pu traiter l'échange EDIFACT entrant, car le premier segment n'était ni de type UNA, ni de type UNB. Le segment UNA est facultatif ; le segment UNB est obligatoire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que l'expéditeur de l'échange structure le message de telle manière qu'un document informatisé dans un groupe soit suivi d'un autre document informatisé ou d'un segment UNE. Demandez ensuite à l'expéditeur de renvoyer l'échange.