---
title: "Échec du décodage AS2 lors du déchiffrement d’un message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab6f7ecd-23cf-4f6f-8f63-acc6618dc544
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72ef95ad35e1da933197bac11a9d80f98ddabd6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-decoding-failed-while-decrypting-a-message"></a>Échec du décodage AS2 lors du déchiffrement d'un message
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Échec du décodage AS2 lors du déchiffrement d'un message.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu déchiffrer le message AS2. Cela peut se produire si le certificat utilisé dans le processus de déchiffrement n'est pas valide, n'est pas stocké dans l'emplacement approprié ou ne correspond pas au certificat utilisé dans le processus de chiffrement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Vérifiez que le wrapper de chiffrement du message AS2 est valide. Sinon, déterminez pour quelle raison le message était codé de manière inappropriée par l'encodeur.  
  
-   Vérifiez que la clé publique utilisée dans le processus de chiffrement et la clé privée utilisée dans le processus de déchiffrement correspondent.  
  
-   Vérifiez que la propriété Utilisation de la clé du certificat utilisé pour le chiffrement et le déchiffrement est définie sur « chiffrement des données ».  
  
-   Vérifiez l'existence d'une chaîne brisée d'autorités de certification intermédiaires. Si c'est le cas, supprimez l'ancien certificat, et créez-en un.  
  
-   Vérifiez que le certificat n'a pas expiré en examinant sa date d'expiration dans le magasin de certificats à l'aide de la console MMC et du composant logiciel enfichable Certificats.  
  
-   Vérifiez que le certificat n'a pas été révoqué en vérifiant la liste de révocation des certificats. (Vous pouvez automatiser cette opération en activant la propriété Vérifier la liste de révocation des certificats dans les propriétés AS2 générales de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)  
  
-   Vérifiez que le certificat utilisé pour le déchiffrement est stocké dans le magasin de certificats Utilisateur actuel\Personne de chaque serveur BizTalk qui héberge un pipeline Décodeur MIME/SMIME en tant que compte de service d'instance d'hôte.