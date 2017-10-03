---
title: "Le certificat utilisé pour chiffrer un message a été révoqué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c90690-002a-43bc-85f2-8aa5e7511ffa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fbe34dcd2906d79a8d80ebdd00c3d9f293e6559
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-to-encrypt-a-message-has-been-revoked"></a>Le certificat utilisé pour chiffrer un message a été révoqué
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|EncryptionCertificateHasBeenRevokedError|  
|Texte du message|Le certificat utilisé pour chiffrer un message a été révoqué. Empreinte numérique du certificat : {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter le message sortant, car le certificat identifié comme étant le certificat de chiffrement a été révoqué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Demandez au récepteur du message de créer un certificat et de vous envoyer la clé publique. Ajoutez le certificat dans le magasin de certificats Ordinateur local\Autres personnes, puis, dans la boîte de dialogue Propriétés de port d'envoi, dans la page Certificat, identifiez-le comme étant le certificat de chiffrement.  
  
-   Désactivez la vérification de la liste de révocation. Pour ce faire, ouvrez la console Administration de BizTalk Server, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message sortant, cliquez sur le nœud Général, puis désactivez la propriété Vérifier la liste de révocation des certificats.