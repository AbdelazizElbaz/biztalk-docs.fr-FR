---
title: "La réparation d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: repairing messages
ms.assetid: 3a61b73b-5433-4249-b580-6194ccb4aebc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4071fd04b89681f9f7d6948798dd665b96a0c1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-a-message"></a>La réparation d’un Message
Cette section décrit comment réparer un message d’échec de la validation.  
  
### <a name="to-repair-a-message"></a>Pour réparer un message  
  
1.  Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.  
  
2.  Dans la fenêtre d’accueil, cliquez sur **Documents**.  
  
3.  Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur  **\<* nom du service informatique*>**_** Réparateur **.  
  
4.  Dans le \< *nom du service informatique*> _Repair fenêtre, cliquez sur **boîte de réception**.  
  
5.  Dans la fenêtre de la boîte de réception, pointez sur le titre du message, cliquez sur la flèche à droite du titre du message, puis cliquez sur **modifier dans Microsoft Office InfoPath**.  
  
6.  Dans le volet SWIFT accélérateur de le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, assurez-vous que **erreurs** est sélectionnée. Examinez les erreurs affichées dans le **Parse et erreurs de Validation XML**, **BRE les erreurs de Validation**, et **erreurs d’exécution** zones.  
  
7.  Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran, faites défiler jusqu'à l’emplacement de l’erreur et corrigez l’erreur. S’il s’agit d’une erreur de validation XML, l’erreur est mises en surbrillance en rouge.  
  
    > [!NOTE]
    >  Erreurs de validation BRE ne seront pas mis en surbrillance en rouge dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire. Pour plus d’informations sur les erreurs de validation BRE, consultez [Codes d’erreur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md).  
  
    > [!NOTE]
    >  Si l’erreur se produit dans un champ qui est accompagné d’une liste déroulante, vous ne serez pas en mesure d’afficher la valeur d’origine qui a provoqué l’erreur. Le champ affiche « Select » au lieu de la valeur d’origine. Dans la liste déroulante, sélectionnez la valeur appropriée.  
  
8.  Pour vous assurer que ce dernier est validé, cliquez sur **Validation** dans le rôle actuel : réparer volet, puis cliquez sur **valider le Message**. Vérifiez que le volet de résultats affiche **le message est valide**.  
  
9. Dans le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, cliquez sur **Submit**.  
  
    > [!NOTE]
    >  Lorsque vous cliquez sur **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] exécute une validation XML sur le message. Si la validation ne réussit pas, vous devez corriger les erreurs de validation avant de continuer.  
  
10. Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message réparé avec les modifications acceptées, cliquez sur **rejeter** pour rejeter les modifications, ou cliquez sur **Annuler** pour annuler la soumission, puis revenez à l’écran.  
  
    > [!NOTE]
    >  Si vous acceptez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] effectue les validations BRE sur le message.  
  
    > [!NOTE]
    >  Si vous le rejetez les modifications de message dans la phase de réparation, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] achemine le message vers la MessageBox et publications dans l’Observateur d’événement de message d’erreur « Impossible de réinitialiser à la première étape dans le flux de travail. ».  
  
11. Si vous avez cliqué sur **accepter** ou **rejeter** à l’étape 10, sur le **Assistant Signature numérique** page, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le Réparateur), puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.  
  
12. Dans la page Assistant Signature numérique permettant d’entrer un commentaire, cliquez sur **Terminer**.  
  
13. Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous signez et votre signature sont corrects. Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.  
  
14. Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.  
  
15. Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.  
  
16. Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.  
  
17. Dans le site MRSR, cliquez sur **Documents**. Si vous avez cliqué sur **accepter** pour accepter les modifications apportées à l’étape 11, vérifiez que le  *\<nom service >*bibliothèque de documents _ReKeyVerify contient le message que vous venez de réparer. Si vous avez cliqué sur **rejeter** pour rejeter les modifications apportées à l’étape 11, vérifiez que la bibliothèque de documents A4SWIFT_Outbox contient le message qui a été modifié.