---
title: "Dépannage des échecs de Validation de Message en affichant le contenu hexadécimal de Messages suspendus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf14cd9-2d4b-43a3-9738-52bfd879e1e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f7dc0f24a85f206831e3706bd03f2206aaa2c15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-message-validation-failures-by-viewing-the-hexadecimal-contents-of-suspended-messages"></a>Dépannage des problèmes de validation de message par l'affichage du contenu hexadécimal des messages suspendus
Si un message est suspendu en raison d'un échec de validation, consulter la représentation hexadécimale des parties du message peut permettre de déterminer la cause de l'échec. Cette rubrique répertorie les étapes à suivre pour consulter la représentation hexadécimale des parties d'un message suspendu.  
  
## <a name="use-the-message-details-dialog-box-to-view-message-parts"></a>Utilisation de la boîte de dialogue Détails sur le message pour afficher les parties du message  
 Suivez la procédure ci-dessous pour afficher la représentation hexadécimale des parties du message :  
  
1.  Utilisez le **requête** onglet dans la Console Administration de BizTalk pour retourner un jeu de résultats avec un ou plusieurs messages suspendus. Consultez [comment rechercher des Messages](../core/how-to-search-for-messages.md) pour plus d’informations.  
  
2.  Double-cliquez sur le message suspendu qui vous intéresse pour afficher le **détails du Message** boîte de dialogue pour le message.  
  
3.  Cliquez sur une partie de message dans le volet gauche de la **détails du Message** boîte de dialogue pour afficher la partie de message.  
  
    > [!NOTE]
    >  Les messages peuvent comporter 0, 1 ou plusieurs parties. La plupart du temps, ils en contiennent une seule, appelée « corps ».  
  
4.  Cliquez sur le **binaire** onglet dans le volet de droite de la **détails du Message** boîte de dialogue pour afficher la représentation hexadécimale de la partie du message.  
  
5.  Recherchez les points suivants dans la représentation hexadécimale :  
  
    -   Une marque d'ordre de tri manquante ou non valide. Pour plus d’informations sur l’ordre d’octet marques consultez [http://go.microsoft.com/fwlink/?LinkId=196380](http://go.microsoft.com/fwlink/?LinkId=196380).  
  
    -   Des différences de codage des sauts de ligne entre Unix et Windows. Unix utilise le saut à la ligne hexadécimal (0A) pour indiquer le saut de ligne, tandis que Windows utilise à la fois le retour chariot hexadécimal (0D) et le saut à la ligne (0A).  
  
    -   Des caractères de contrôle non valides. Les caractères de contrôle qui ne s'affichent pas au format texte peuvent être visibles au format binaire.  
  
    -   Des caractères nuls non valides au milieu d'une partie de message peuvent tronquer la partie de message. Le caractère nul est représenté par la valeur hexadécimale (00).  
  
    -   Un décalage de caractères non valide dans les fichiers plats positionnels. Affichez la représentation hexadécimale d'une partie de message pour consulter le décalage de données dans un fichier plat positionnel.  
  
## <a name="see-also"></a>Voir aussi  
 [Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md)