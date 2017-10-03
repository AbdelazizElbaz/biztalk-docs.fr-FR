---
title: "Erreur rencontrée après le traitement de Transaction Set(s) car DocType n’a pas été définie. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a323658c-77d8-4059-aa15-d88c08e5450d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 874b0229eecdd5fe9c046f69789c4708b9280031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-after-processing-transaction-sets-because-doctype-was-not-set"></a>Erreur rencontrée après le traitement de document(s) informatisé(s) car DocType n'a pas été défini
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|DocTypeNotSet|  
|Texte du message|Erreur rencontrée après le traitement de {0} document(s) informatisé(s). Le type de document n'a pas été défini|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter un document informatisé entrant car STO1 (pour un échange X12) ou UNH2.1 (pour un échange EDIFACT) n'est pas défini pour le document informatisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le segment ST01 ou UNH1 pour le document informatisé indiqué dans l'erreur est défini sur un type de document valide.