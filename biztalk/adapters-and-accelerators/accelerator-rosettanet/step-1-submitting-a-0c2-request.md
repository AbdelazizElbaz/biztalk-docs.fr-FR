---
title: "Étape 1 : Envoi d’un 0C 2 demande | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 698c4a43-20b9-46b7-ab66-1dfa24232024
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f05aa5200bd1df6207a962849cd776a03fe71805
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-submitting-a-0c2-request"></a>Étape 1 : Envoi d’un 0C la demande 2
Dans cette étape, vous préparez et soumettez une demande à l’aide du processus PIP (Partner Interface) pour un C 0 2 - asynchrone demande de Test. Ce processus PIP garantit qu’un canal de communication asynchrone fonctionne correctement entre les deux organisations différentes. Ce processus PIP suit le même modèle que les autres processus PIP action double asynchrones, telles que les 3 a 4 - demande de bon ordre PIP.  
  
### <a name="to-submit-a-0c2---asynchronous-test-request"></a>Pour envoyer un 0C 2 - asynchrone demande de Test  
  
1.  Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.  
  
2.  Dans la page **Envoyer un Message** , procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Organisation d’origine**|Tapez **FABRIKAM**.|  
    |**Organisation du partenaire**|Tapez **CONTOSO**.|  
    |**Code PIP**|Type **0C 2**.|  
    |**Version du PIP**|Tapez **R01.02**.|  
    |**ID d’Instance PIP**|Type **0C2_Test**. **Important :** vous devez vous assurer que le **PIP** est unique pour chaque message que vous envoyez pour éviter les erreurs d’ID de message en double. Si vous exécutez le 0 C 2 de test à l’avenir, vous devrez modifier ce champ.|  
    |**Catégorie de message**|Tapez **Action**.|  
  
3.  Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 0C2_Request.xml dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\ LOBApplication\SampleInstances dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.  
  
    > [!NOTE]
    >  Pour supprimer le texte existant dans le champ contenu du Service sous la forme d’envoyer un Message, placez le curseur au début du texte, maintenez la **MAJ** et **Ctrl** boutons, cliquez sur **fin** , puis cliquez sur **supprimer**.  
  
4.  Cliquez sur **Submit** pour envoyer la valeur 0, C 2 demande à l’ordinateur Contoso.  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>Pour vérifier la communication sur l'ordinateur Fabrikam  
  
-   Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso. Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso. Un message de catégorie -99 indique une erreur. Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>Pour vérifier la communication sur l'ordinateur Contoso  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2005**et cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.  
  
    > [!NOTE]
    >  Si l’Agent SQL Server n’est pas démarré, faites un clic droit, puis cliquez sur **Démarrer**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans le \<table\> boîte de dialogue texte, sélectionnez **BTARNDATA** dans la liste, puis cliquez sur **OK**.  
  
5.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Sur le **requête** menu, cliquez sur **Execute** pour exécuter l’instruction SQL.  
  
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
 [Étape 2 : Envoi d’un 0C de requête 4](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md)   
 [Flux de messages BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)