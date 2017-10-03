---
title: "Identificateur du jeu de transactions manquante ou non valide ou dupliquée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8580aab2-9fa4-43fb-b643-10621926591e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75251d0210be4ed34a74ba0f3f5cadf84d9941b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="missing-or-invalid-or-duplicate-transaction-set-identifier"></a>Identificateur du jeu de transactions manquante ou non valide ou en double
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12TsMissingOrInvalidTsIdentiferDescription2|  
|Texte du message|Identificateur de document informatisé « {0} » manquant, non valide ou dupliqué|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception ou d'envoi n'a pas réussi à traiter l'échange X12 car la valeur de l'identificateur de document informatisé (champ ST01) était manquante, dupliquée ou non valide. Cette erreur se produit si le schéma de document ne possède pas d'en-tête ST ni de code de fin SE.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, assurez-vous que le champ ST01 de l'échange possède une valeur et que le schéma dispose d'une entrée pour l'en-tête ST et le code de fin SE. Vérifiez que la valeur de ST01 est un indicateur de type de document à trois chiffres valide. Vérifiez que le champ ST01 n'est pas un doublon du champ ST01 d'un autre document informatisé.