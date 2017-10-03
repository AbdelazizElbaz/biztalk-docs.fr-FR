---
title: "Impossible de trouver le certificat utilisé pour signer un message dans le magasin de certificats local | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ff3c7a2-954c-4c62-a7b2-06f7a38d61b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94049a0ecca4e7aec89c5163231c0b9bf4c9e3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-for-signing-a-message-cannot-be-located-in-the-local-certificate-store"></a>Le certificat utilisé pour la signature d'un message ne peut pas être localisé dans le magasin de certificats local.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|CertificateMissingError|  
|Texte du message|Impossible de trouver le certificat utilisé pour signer un message dans le magasin de certificats local. Empreinte numérique du certificat : {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter le message sortant, car le certificat identifié comme le certificat de signature ne se trouvait pas dans le magasin de certificats requis.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
1.  Identifiez le certificat de signature en ouvrant la console Administration BizTalk Server, en cliquant avec le bouton droit de la souris sur Groupe BizTalk, puis en cliquant sur le nœud Certificat.  
  
2.  Ouvrez MMC, ajoutez le composant logiciel enfichable pour Mon compte d'utilisateur, puis ouvrez les nœuds Certificats et Personnel.  
  
3.  Assurez-vous que le magasin de certificats Utilisateur actuel contient la clé privée correspondant à ce certificat de signature en recherchant l'empreinte identifiée dans le texte du message d'erreur.