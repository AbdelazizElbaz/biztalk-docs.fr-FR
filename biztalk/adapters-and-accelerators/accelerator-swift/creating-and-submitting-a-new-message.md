---
title: "Création et envoi d’un nouveau Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- submitting, messages
- messages, submitting
- messages, creating
ms.assetid: 88b7a2d3-44a4-44e4-ba8c-527c10290925
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42cd2a82fe0ecde75446e68f9f58e17f103e5efa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-submitting-a-new-message"></a>Création et envoi d’un nouveau Message
Cette section décrit comment envoyer un message. Comme avec un message réparé, un nouveau message doit être vérifié et approuvé par des personnes autres que le créateur de message.  
  
 Pour envoyer un message, vous devez télécharger dans la bibliothèque de documents de nouveaux Messages SWIFT un fichier de modèle de message pour le type de message que vous souhaitez envoyer. Vous pouvez télécharger manuellement un modèle de message unique, ou vous pouvez télécharger tous les modèles de message à l’aide de l’outil FormPublish.  
  
### <a name="to-upload-a-single-message-template-into-the-new-document-library"></a>Pour télécharger un modèle de message unique dans la bibliothèque de documents  
  
1.  Reportez-vous à la section [formulaire générateur utilitaire pour générer des formulaires InfoPath MT/MX](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md) pour obtenir des instructions.  
  
### <a name="to-create-and-submit-a-new-message"></a>Pour créer et envoyer un message  
  
1.  Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.  
  
2.  Cliquez sur **Documents**, puis cliquez sur **nouveaux Messages SWIFT**.  
  
3.  Dans la page nouveaux Messages SWIFT, double-cliquez sur le nom de la catégorie qui contient le type du message que vous souhaitez créer.  
  
4.  Cliquez sur le modèle de formulaire pour le message que vous souhaitez créer.  
  
5.  Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, dans le message d’écran, données de message de type pour tous les champs obligatoires (tel que signalé par un astérisque) et les champs facultatifs que vous souhaitez utiliser.  
  
6.  Pour rechercher un BIC, dans le rôle actuel : créer le volet, cliquez sur **recherche BIC**.  
  
7.  Tapez le nom de l’établissement, le code de la banque et le pays/région, puis cliquez sur **recherche**.  
  
8.  Dans le volet de recherche BIC, copiez le code BIC dans le champ de code bancaire approprié sous la forme de message.  
  
9. Dans le rôle actuel : créer le volet, cliquez sur **Validation**, puis cliquez sur **valider le Message**.  
  
10. Dans le volet de résultats du rôle actuel : créer le volet, déterminer les erreurs que vous devez corriger dans le message.  
  
    > [!NOTE]
    >  Vous pouvez uniquement soumettre un nouveau message si vous avez résolu toutes les erreurs de validation dans le message.  
  
11. Dans la barre d’outils Standard en haut de la fenêtre, cliquez sur **Submit**.  
  
12. Dans la page Assistant Signature numérique pour sélectionner le certificat de signature de l’écran, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le créateur). Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte. Cliquez sur **Suivant**.  
  
    > [!NOTE]
    >  Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.  
  
13. Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.  
  
14. Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct. Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte. Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.  
  
15. Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.  
  
16. Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.  
  
17. Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.