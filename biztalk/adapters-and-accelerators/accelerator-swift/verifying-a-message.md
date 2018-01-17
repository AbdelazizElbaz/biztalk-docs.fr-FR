---
title: "Vérification d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, verifying
- verifying, messages
ms.assetid: df2b72bb-4dc1-4fdd-8f63-35fc73a12151
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f2fdc186e93bd182b3021a3ef8fc258cee59923
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="verifying-a-message"></a>Vérification d’un Message
Cette section décrit comment vérifier si un message a été réparé.  
  
### <a name="to-verify-a-message"></a>Pour vérifier un message  
  
1.  Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.  
  
2.  Dans la fenêtre d’accueil, cliquez sur **Documents**.  
  
3.  Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur  **\< *nom du service informatique*\>_Verifier**.  
  
4.  Dans la fenêtre de confirmation, cliquez sur **boîte de réception**.  
  
5.  Dans la fenêtre Vérifier la boîte de réception, pointez sur le titre du message, cliquez sur la flèche à droite du titre du message, puis cliquez sur **modifier dans Microsoft Office InfoPath**.  
  
6.  Dans le **télécharger le fichier** boîte de dialogue, cliquez sur **ouvrir**.  
  
7.  Dans les rôles actuels : volet RekeyVerify de le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, cliquez sur **erreurs**. Consulter toutes les erreurs affichées dans le **Parse et erreurs de Validation XML** boîte et la **BRE les erreurs de Validation** boîte.  
  
8.  Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forme, faites défiler jusqu'à l’emplacement de l’erreur et vérifiez que l’erreur a été corrigée. Vous pouvez voir ce que l’erreur d’origine a été en cliquant sur **erreurs** dans le rôle actuel : RekeyVerify volet et l’affichage de l’erreur dans un des volets de l’erreur. Vous pouvez également comparer les versions non réparées et réparées du message en cliquant sur **détails du Message** dans le rôle actuel : RekeyVerify volet.  
  
9. Pour vous assurer que ce dernier est validé, cliquez sur **Validation** dans le rôle actuel : RekeyVerify volet, puis cliquez sur **valider le Message**.  
  
    > [!NOTE]
    >  Le volet de résultats sous la Validation du Message dans le rôle actuel : RekeyVerify volet indique tous les champs dans le message que vous devez générer une nouvelle clé. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]marque ces champs dans le volet de Message avec un astérisque rouge.  
  
10. Recomposition des données dans tous les champs dans le volet messages signalés par un astérisque rouge (indiquant que les données doivent être régénérées avant la soumission).  
  
    > [!NOTE]
    >  Vous pouvez afficher les données dont vous avez besoin pour générer une nouvelle clé dans les champs de message en cliquant sur **détails du Message** dans le rôle actuel : RekeyVerify volet et faire défiler le message d’origine dans le champ. Cela est vrai, sauf si une erreur de validation dans un des champs de changement de clé dans le message d’origine, auquel cas vous devez réparer le champ lorsque vous le recomposition.  
  
11. Cliquez sur **Validation** dans les **rôle actuel : RekeyVerify** volet, puis cliquez sur **valider le Message**. Vérifiez que le volet de résultats affiche le message **le message est valide**.  
  
12. Cliquez sur **Submit** dans les [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007.  
  
    > [!NOTE]
    >  Lorsque vous cliquez sur **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] exécute une validation XML sur le message. Si la validation ne réussit pas, vous devez corriger les erreurs de validation avant de continuer.  
  
13. Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message vérifié avec les modifications acceptées. Cliquez sur **rejeter** pour envoyer le message avec les modifications rejetées. Cliquez sur **Annuler** pour annuler l’envoi et de revenir à l’écran.  
  
    > [!NOTE]
    >  Si vous acceptez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] effectue les validations BRE sur le message.  
  
    > [!NOTE]
    >  Si vous le rejetez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] renvoie le message à la première étape du flux de travail (créer ou réparer) et réinitialise le flux de travail de réparation.  
  
14. Dans la page Assistant Signature numérique pour sélectionner le certificat de signature de l’écran, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le vérificateur), puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**. Si vous devez ajouter une autre signature pour ce rôle, effectuez cette opération dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Console de gestion.  
  
15. Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.  
  
16. Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct. Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte. Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.  
  
17. Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.  
  
18. Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.  
  
19. Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.  
  
20. Dans le site MRSR, cliquez sur **Documents et listes**. Si vous avez cliqué sur **accepter** pour accepter les modifications apportées à l’étape 13, vérifiez que le \<nom du service informatique\>bibliothèque de documents _Approve contient le message qui a été modifié. Si vous avez déjà ouvert la fenêtre de Documents et listes, cliquez sur **Actualiser** sur la **vue** menu. Si vous avez cliqué sur **rejeter** pour rejeter les modifications apportées à l’étape 13, vérifiez que le  *\<nom de l’ordinateur\>*bibliothèque de documents _Outbox contient le message qui a été modifié.