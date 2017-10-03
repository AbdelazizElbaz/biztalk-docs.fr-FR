---
title: "Erreur rencontrée lors de la génération de l’instance : champ peut se répéter mais le délimiteur de répétition n’a pas été défini. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a6783c-cb35-4ce8-9164-ec34ae500de1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 366caec69fd84b91cf815a58e4975e8e5d7b4d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-instance-generation--field-can-repeat-but-repetition-delimiter-has-not-been-defined"></a>Erreur rencontrée lors de la création de l'instance. Le champ peut se répéter mais le délimiteur de répétition n'a pas été défini
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Erreur rencontrée lors de la création de l'instance. Le champ {0} peut se répéter mais le délimiteur de répétition n'a pas été défini.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer une instance du message X12, car le champ spécifié peut se répéter (comme indiqué par le schéma), mais aucun séparateur de répétition n'a été défini. Cette situation se produit lorsque la valeur du paramètre minOccurs d'un champ de schéma est supérieure à 1, mais qu'un identificateur standard a été défini à la place d'un séparateur de répétition. (Pour les échanges EDIFACT, un séparateur de répétition est défini par défaut).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la page Définition des segments ISA pour le tiers en tant que récepteur d'échanges, sélectionnez un séparateur de répétition au lieu d'un identificateur standard pour ISA11, puis entrez un caractère pour le séparateur. Si aucun tiers n'a été résolu pour l'échange, définissez le séparateur de répétition dans la page Définition des segments ISA des propriétés globales (pour les échanges X12).