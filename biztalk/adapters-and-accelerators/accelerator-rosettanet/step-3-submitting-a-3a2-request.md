---
title: "Étape 3 : Envoi d’une demande de 3A2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 09f22be8-6d7d-48bf-862b-73248bae0506
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e32122b2c77ee0e69f7890b5a681954ba986e220
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-submitting-a-3a2-request"></a>Étape 3 : Envoi d’une demande de 3A2
Dans cette étape, vous préparez et soumettez une demande à l’aide du processus PIP (Partner Interface) pour un 3A2 - demande de prix et disponibilité. Ce processus PIP permet à une organisation de l’acheteur obtenir des informations sur un produit donné, telles que le prix et le nombre d’unités disponibles. L’acheteur peut ensuite traiter ces informations via des règles d’entreprise pour déterminer si vous devez acheter le produit du fournisseur.  
  
### <a name="to-submit-a-3a2---request-price-and-availability"></a>Pour envoyer un 3A2 - demande de prix et disponibilité  
  
1.  Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.  
  
2.  Dans la page **Envoyer un Message** , procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Organisation d’origine**|Tapez **FABRIKAM**.|  
    |**Organisation du partenaire**|Type **Contoso**.|  
    |**Code PIP**|Type **3A2**. **Important :** pour éviter les erreurs d’ID de message en double, vous devez vous assurer que le **Pip** est unique pour chaque message que vous envoyez. Si vous exécutez le test 3A2 à l’avenir, vous devez modifier ce champ.|  
    |**Version du PIP**|Type **R02.00.00A**.|  
    |**ID d’Instance PIP**|Type **3A2_Test**.|  
    |**Catégorie de message**|Tapez **Action**.|  
  
3.  Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 3A2_Request.xml dans le  *\<lecteur >*: \ Programme Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances, dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.  
  
4.  Cliquez sur **Submit** pour envoyer la demande 3A2 à l’ordinateur Contoso.  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>Pour vérifier la communication sur l'ordinateur Fabrikam  
  
-   Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso. Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso. Un message de catégorie -99 indique une erreur. Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>Pour vérifier la communication sur l'ordinateur Contoso  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans le \<table > zone de texte, sélectionnez **BTARNDATA** dans la liste.  
  
5.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
7.  Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam. Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie l’accusé de réception.  
  
8.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
10. Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.  
  
    > [!NOTE]
    >  Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam. Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Envoi d’une demande de 3 a 4](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md)   
 [Flux de messages de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)