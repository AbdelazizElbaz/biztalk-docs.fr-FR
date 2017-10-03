---
title: "Le certificat utilisé pour signer un message a été révoqué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f822235a-8ad8-4b63-94de-9b7f9361a071
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8527f89d03d3250a7685380fcabf484254fbbf86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-for-signing-a-message-has-been-revoked"></a>Le certificat utilisé pour signer un message a été révoqué
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|SigningCertificateHasBeenRevokedError|  
|Texte du message|Le certificat utilisé pour signer un message a été révoqué. Empreinte numérique du certificat : {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter le message sortant, car le certificat identifié comme étant le certificat de signature a été révoqué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Créez un certificat pour remplacer le certificat révoqué. Ajoutez-le au magasin de certificats Utilisateur actuel, identifiez-le en tant que certificat de signature dans la page Certificat de la boîte de dialogue Propriétés du groupe, puis envoyez la clé publique du certificat au destinataire du message AS2.  
  
-   Désactivez la vérification de la liste de révocation. Pour ce faire, ouvrez la console Administration de BizTalk Server, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message sortant, cliquez sur le nœud Général, puis désactivez la propriété Vérifier la liste de révocation des certificats.