---
title: "Erreur rencontrée lors de la lecture des délimiteurs de données ISA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cb60abd-53c8-45e1-a840-d27dc974aad7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fcde2519740adc5531363911146164f460f9b3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-in-reading-delimiters-from-isa-data"></a>Erreur rencontrée lors de la lecture des délimiteurs à partir des données ISA
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|InvalidIsaData|  
|Texte du message|Erreur rencontrée lors de la lecture des délimiteurs à partir des données ISA|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors du traitement d'un échange X12 entrant car il n'a pas pu analyser les séparateurs du segment ISA.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que les séparateurs du segment ISA de l'échange entrant sont uniques et valides. Sinon, demandez à l'expéditeur de l'échange d'entrer des valeurs uniques et valides dans chaque champ de séparateur (segment ISA11 du séparateur de répétition et segment ISA16 du séparateur de composants), puis de renvoyer l'échange.