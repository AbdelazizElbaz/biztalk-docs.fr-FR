---
title: "Génération de l’erreur-accusé de réception a échoué car la limite maximale de X12 transaction globale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bbcae14-6e5c-4f79-87c6-311b4b54c7ff
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1eaef5e736ad01a9b49a3b46188b85b85a97e06
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="error-ack-generation-has-failed-as-maximum-limit-of-x12-transaction-global"></a>Génération de l’erreur-accusé de réception a échoué car la limite maximale de X12 transactions globales
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|EDI de BizTalk Server|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle acceptable du document informatisé X12 a été atteinte pour les paramètres Invité. Réinitialisez le compteur en naviguant jusqu'au champ ST 2 de l'écran du rôle de l'expéditeur de la configuration globale, dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer un accusé de réception pour l'échange X12, car le numéro de contrôle qu'il a entré dans le numéro de contrôle du document informatisé (ST2) de l'accusé de réception est supérieur à la valeur maximale autorisée pour ST2. Dans cette instance, BizTalk Server a créé l'accusé de réception à l'aide des propriétés globales EDI.  
  
 La valeur maximale du numéro de contrôle du document informatisé dépend du nombre de chiffres utilisés pour le numéro de contrôle. La longueur maximale des trois champs réunis est de 9. La longueur maximale des champs du préfixe et du suffixe est de 8.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la page Définition des segments GS et ST, rétablissez le champ du numéro de contrôle (ST2.2) du numéro de contrôle du document informatisé (ST2) sur une valeur inférieure à la limite maximale. Définissez cette propriété dans la boîte de dialogue Propriétés globales EDI dans la Console Administration de BizTalk Server.