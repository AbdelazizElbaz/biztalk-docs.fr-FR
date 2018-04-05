---
title: 'Étape 4 : Envoi d’une demande de 3 a 4 | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, submitting requests
ms.assetid: 2d812cbc-51bc-48d5-b0b2-3698d33664ec
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff36b6181b167d70340a65913e1e85e7acfeeaf4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-submitting-a-3a4-request"></a>Étape 4 : Envoi d’une demande de 3 a 4
Dans cette étape, vous préparez et soumettez une demande à l’aide du processus PIP (Partner Interface) pour un 3 a 4 - demande de bon de commande. Ce processus PIP permet à une organisation de l’acheteur soumettre une demande de bon de commande à un fournisseur. En règle générale, vous demandez le 3 a 4 - demande de bon de commande après l’exécution d’une requête de disponibilité de produit à l’aide de la 3A2 - demande de prix et disponibilité PIP. Le PIP 3 a 4 est une adresse PIP asynchrone qui envoie les accusés de réception.  
  
 ![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a4flow.gif "RN3_Intro_EETut_3A4Flow")  
  
### <a name="to-submit-a-3a4---request-purchase-order"></a>Pour soumettre un 3 a 4 - demande de bon de commande  
  
1.  Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.  
  
2.  Dans la page **Envoyer un Message** , procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Organisation d’origine**|Tapez **FABRIKAM**.|  
    |**Organisation du partenaire**|Type **Contoso**.|  
    |**Code PIP**|Type **3 a 4**.|  
    |**Version du PIP**|Type **V02.02.00**.|  
    |**ID d’Instance PIP**|Type **3A4_Test**. **Important :** pour éviter les erreurs d’ID de message en double, vous devez vous assurer que le **ID d’Instance Pip** est unique pour chaque message que vous envoyez. Si vous exécutez le test de 3 a 4 dans le futur, vous devrez modifier ce champ.|  
    |**Catégorie de message**|Tapez **Action**.|  
  
3.  Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 3A4_Request.xml dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\ LOBApplication\SampleInstances dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.  
  
4.  Cliquez sur **Submit** pour envoyer la demande de 3 a 4 à l’ordinateur Contoso.  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>Pour vérifier la communication sur l'ordinateur Fabrikam  
  
-   Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso. Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso. Un message de catégorie -99 indique une erreur. Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>Pour vérifier la communication sur l'ordinateur Contoso  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans le \<table\> boîte de dialogue texte, sélectionnez **BTARNDATA** dans la liste.  
  
5.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
7.  Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam. Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie le message acknowledegment de réception.  
  
8.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
10. Dans la fenêtre de requête, dans le **résultats** volet, vérifiez que vous voyez un message sortant.  
  
    > [!NOTE]
    >  Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam. Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel double Action](../../adapters-and-accelerators/accelerator-rosettanet/double-action-tutorial.md)   
 [Flux de messages BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)