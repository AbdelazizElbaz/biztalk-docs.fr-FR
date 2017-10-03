---
title: "L’approbation d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, approving
- approving messages
ms.assetid: e6abfef3-aab2-470e-a7a7-a6d091ffba53
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b5b77ca46be2e6a3fb4c882947eb47829f591ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="approving-a-message"></a>L’approbation d’un Message
Cette section décrit comment approuver un message qui a été réparé et vérifié.  
  
### <a name="to-approve-a-message"></a>Pour approuver un message  
  
1.  Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.  
  
2.  Dans la fenêtre d’accueil, cliquez sur **Documents**.  
  
3.  Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur  **\<* nom du service informatique*> _Approver **.  
  
4.  Dans le \<nom service > _Approver fenêtre, cliquez sur **boîte de réception**.  
  
5.  Dans la fenêtre de la boîte de réception, pointez sur le titre du message, cliquez sur la flèche à droite du titre du message, puis cliquez sur **modifier dans Microsoft Office InfoPath**.  
  
6.  Dans le volet SWIFT accélérateur de le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, cliquez sur **erreurs**. Consulter toutes les erreurs affichées dans le **Parse et erreurs de Validation XML** , boîte de la **BRE les erreurs de Validation** zone et le **erreurs d’exécution** boîte de.  
  
7.  Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forme, faites défiler jusqu'à l’emplacement de l’erreur et vérifiez que l’erreur a été corrigée. Vous pouvez voir ce que l’erreur d’origine a été en cliquant sur **erreurs** dans le rôle actuel : approuver volet et l’affichage de l’erreur dans un des volets de l’erreur. Vous pouvez également comparer les versions non réparées et réparées du message en cliquant sur **détails du Message** dans le rôle actuel : approuver volet.  
  
8.  Pour vous assurer que ce dernier est validé, cliquez sur **Validation** dans le rôle actuel : approuver volet, puis cliquez sur **valider le Message**. Vérifiez que le volet de résultats affiche le message **le message est valide**.  
  
9. Si vous approuvez des modifications qui ont été apportées au document, dans le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, cliquez sur **Submit**.  
  
    > [!NOTE]
    >  Lorsque vous cliquez sur **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] exécute une validation XML sur le message. Si la validation ne réussit pas, vous devez corriger les erreurs de validation avant de continuer.  
  
10. Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message approuvé avec les modifications acceptées. Cliquez sur **rejeter** pour envoyer le message avec les modifications rejetées. Cliquez sur **Annuler** pour annuler l’envoi et de revenir à l’écran.  
  
    > [!NOTE]
    >  Si vous acceptez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] effectue les validations BRE sur le message.  
  
    > [!NOTE]
    >  Si vous le rejetez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] renvoie le message à la première étape du flux de travail (créer ou réparer) et réinitialise le flux de travail de réparation.  
  
11. Dans la page Assistant Signature numérique pour sélectionner le certificat de signature de l’écran, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour l’approbateur). Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte. Cliquez sur **Suivant**.  
  
    > [!NOTE]
    >  Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**. Vous pouvez également voir quels rôles ont signé le formulaire précédemment (un formulaire peut uniquement être signé par une personne, une fois par flux de travail) en cliquant sur **Signatures numériques** sur la **outils** menu. Si vous devez ajouter une autre signature pour ce rôle, effectuez cette opération dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Console de gestion.  
  
12. Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.  
  
13. Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct. Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte. Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.  
  
14. Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.  
  
15. Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.  
  
16. Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.  
  
17. Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, ouvrez le dossier que vous avez configurée pour recevoir des messages envoyés. Vérifiez que le dossier contient le message approuvé. Ouvrez le message dans un éditeur de texte pour vérifier que le message a été réparé.