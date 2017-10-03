---
title: "Une erreur s’est produite lors de la validation d’un message AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0cf97c63-2bff-4474-9cd8-f68634493dcc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73f1c9b7cf4e444e256aadc3ade717fcf30735bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-error-occurred-when-validating-an-as2-message"></a>Une erreur s'est produite lors de la validation d'un message AS2
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|Une erreur s'est produite lors de la validation d'un message AS2. Assurez-vous que les certificats utilisés n'ont pas dépassé le délai de temporisation ou été révoqués.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception AS2 ou le pipeline d'envoi AS2 n'a pas pu valider le message AS2. Cela peut se produire si le certificat utilisé dans le processus de vérification des signatures n'est pas valide, n'est pas stocké à l'emplacement approprié ou ne correspond pas au certificat utilisé dans le processus de signature.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Vérifier que le wrapper de signature dans le message AS2 est valide. Si ce n'est pas le cas, déterminer la raison pour laquelle le message a été incorrectement signé par l'encodeur.  
  
-   Vérifier que la clé privée utilisée dans le processus de signature et la clé publique utilisée dans le processus de vérification des signatures concordent.  
  
-   Vérifier que la propriété KeyUsage du certificat utilisé pour la signature et la vérification des signatures est définie sur « data encipherment ».  
  
-   Vérifiez l'existence d'une chaîne brisée d'autorités de certification intermédiaires. Si c'est le cas, supprimez l'ancien certificat, et créez-en un.  
  
-   Vérifiez que le certificat n'a pas expiré en examinant sa date d'expiration dans le magasin de certificats à l'aide de la console MMC et du composant logiciel enfichable Certificats.  
  
-   Vérifiez que le certificat n'a pas été révoqué en vérifiant la liste de révocation des certificats. (Vous pouvez automatiser cette opération en activant la propriété Vérifier la liste de révocation des certificats dans les propriétés AS2 générales de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)  
  
-   Vérifier que le certificat utilisé pour la vérification des signatures est stocké dans le magasin Ordinateur local \Autres personnes de chaque serveur BizTalk qui héberge un pipeline de décodeur MIME/SMIME en tant que compte de service de chaque instance hôte.