---
title: "Gestion d’un Message non analysé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unparsed messages
- messages, unparsed messages
ms.assetid: c6a67ff3-3295-489f-9d5f-fb35b2bf8b19
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b7683a598169b8ece75788584e8bb9b3c7f4861
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-an-unparsed-message"></a>Gestion d’un Message non analysé
Cette section décrit comment gérer un message non analysé. Contrairement aux messages dont la validation échouent, vous ne pouvez pas réparer un message qui [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ne peut pas analyser. Message Repair et New Submission affiche le message et la nature de l’erreur d’analyse et vous permet d’afficher le message ou l’enregistrer dans un fichier local. Vous pouvez ensuite avertir l’entité qui a envoyé le message de la nature spécifique de l’échec de l’analyse.  
  
### <a name="to-handle-an-unparsed-message"></a>Pour gérer un message non analysé  
  
1.  Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.  
  
2.  Dans la fenêtre d’accueil, cliquez sur **Documents**.  
  
3.  Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur **Unparsed**.  
  
4.  Dans la fenêtre non analysée, cliquez sur **boîte de réception**.  
  
5.  Dans la fenêtre de la boîte de réception non analysée, pointez sur le message qui ne pas analyser, cliquez sur la flèche à droite du message et puis cliquez sur **modifier dans Microsoft Office InfoPath**.  
  
6.  Dans le volet SWIFT accélérateur, cliquez sur **erreurs**.  
  
7.  Dans le volet analyse et des erreurs de Validation XML, lire l’erreur d’analyse.  
  
8.  Dans le volet de Message non analysée, examinez le message.  
  
    > [!NOTE]
    >  Si vous souhaitez afficher le message, dans le volet de Message non analysée, sur le **fichier** menu, cliquez sur **imprimer**.  
  
    > [!NOTE]
    >  Si vous souhaitez enregistrer le message dans un fichier local, dans le volet de Message non analysée, dans le **fichier** menu, cliquez sur **Enregistrer sous**. Dans le **enregistrer en tant que** boîte de dialogue le **enregistrer dans** la liste déroulante, accédez au dossier que vous souhaitez enregistrer le fichier, puis cliquez sur **OK**. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]enregistre le message au format XML.  
  
9. Dans le volet de Message non analysée, apportez les modifications nécessaires, puis cliquez sur **Submit**.  
  
    > [!NOTE]
    >  Impossible de valider un message non analysé que vous avez réparé.  
  
10. Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message réparé avec les modifications acceptées, cliquez sur **rejeter** pour rejeter les modifications, ou cliquez sur **Annuler** pour annuler la soumission, puis revenez à l’écran.  
  
11. Si vous avez cliqué sur **accepter** ou **rejeter** à l’étape 11, dans la page Assistant Signature numérique, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le Réparateur), puis Cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.  
  
    > [!NOTE]
    >  Tout utilisateur d’effectuer n’importe quel rôle peut envoyer un message de non analysé qui leur ont réparé.  
  
12. Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.  
  
13. Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct. Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte. Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.  
  
14. Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.  
  
15. Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.  
  
16. Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.