---
title: "Échec de la sérialisation XML de l'échange X12 dû à une structure incorrecte. Recherche de TransactionSet ou GE, mais introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d058fdbb-6be5-499f-86f7-0eb8a85c5fb2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3d4081c901e95dbd1b9911b2cd957dbe7319761
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="x12-interchange-xml-serialization-failed-due-to-invalid-structure-looking-for-transactionset-or-ge-but-not-found"></a>Échec de la sérialisation XML de l'échange X12 dû à une structure incorrecte. TransactionSet ou GE recherchés mais non trouvés
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12TransactionSetOrGeNotFound|  
|Texte du message|Échec de la sérialisation XML de l'échange X12 dû à une structure incorrecte. TransactionSet ou GE recherchés mais non trouvés|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu sérialiser l'échange sortant, car la structure de l'échange est non valide. Cela peut être dû au fait que les en-têtes ou les codes de fin requis ne sont pas présents ou valides. Cette erreur peut se produire si un document informatisé de groupe n'est pas suivi par un autre document informatisé ou par le code de fin de groupe. Elle peut également survenir si les vérifications au niveau de l'intégrité de la structure échouent.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez la structure de l'échange en vous assurant que les en-têtes et les codes de fin du groupe ou du document informatisé sont valides, puis renvoyez l'échange.