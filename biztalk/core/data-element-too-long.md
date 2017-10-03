---
title: "Élément de données trop long | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf608cc1-d482-4e19-8f56-10d9e03feb79
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbfe63fccc442c35411bfae04c7f27629ce066ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-element-too-long"></a>Élément de données trop long
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Élément de données trop long|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI ou le pipeline d'envoi EDI n'a pas pu traiter l'échange entrant car la longueur de l'élément de données est supérieure à la longueur maximale spécifiée par le schéma.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, réduisez la longueur de l'élément de données de l'échange afin qu'elle soit inférieure à la longueur maximale. Pour déterminer la longueur maximale, ouvrez le schéma dans le dossier \XSD_Schema, recherchez l'ID d'élément de données et identifiez la valeur maxLength.