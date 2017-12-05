---
title: "Étape 2 : Envoi d’une 0c4 requête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: ce50b892-c87c-414a-94c5-b40947fec68f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c621b6891b816f72603202bd6f2214882eb4b5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-submitting-a-0c4-query"></a>Étape 2 : Envoi d’un 0C de requête 4
Au cours de cette étape, vous allez préparer une demande et l'envoyer à l'aide du processus d'interface entre partenaires (PIP) pour une requête de test synchrone 0C4. RosettaNet définit ce processus PIP pour vérifier qu'un canal de communication synchrone fonctionne correctement entre deux organisations différentes. Étant donné que ce processus PIP a un modèle de communication synchrone, [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] n’envoie pas d’accusés de réception. Ce processus PIP suit le même modèle que les autres processus PIP double action synchrones, comme le processus PIP 2A9 (requête d'informations techniques sur un produit).  
  
### <a name="to-submit-a-0c4---synchronous-test-query"></a>Pour envoyer une requête de test synchrone 0C4  
  
1.  Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.  
  
2.  Dans la page **Envoyer un Message** , procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Organisation d’origine**|Tapez **FABRIKAM**.|  
    |**Organisation du partenaire**|Tapez **CONTOSO**.|  
    |**Code PIP**|Tapez **0C4**.|  
    |**Version du PIP**|Tapez **R01.02**.|  
    |**ID d’Instance PIP**|Tapez **0C4_Test**. **Important :** pour éviter les erreurs d’ID de message en double, vous devez vous assurer que le **PIP** est unique pour chaque message que vous envoyez. Si vous exécutez le test 0C4 ultérieurement, vous devrez modifier ce champ.|  
    |**Catégorie de message**|Tapez **Action**.|  
  
3.  Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 0C4_Request.xml dans le  *\<lecteur\>*: \Program Files\Microsoft BizTalk 2009 Accelerator pour RosettaNet\SDK\LOBApplication\SampleInstances, dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.  
  
4.  Cliquez sur **Envoyer** pour envoyer la requête 0C4 à l'ordinateur Contoso.  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>Pour vérifier la communication sur l'ordinateur Fabrikam  
  
-   Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez recevoir un message de catégorie 50 qui correspond au message de réponse de l'ordinateur Contoso. Un message de catégorie -99 indique une erreur. Vous pouvez utiliser l'Observateur d'événements pour déterminer le message d'erreur réel.  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>Pour vérifier la communication sur l'ordinateur Contoso  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2005**et cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.  
  
    > [!NOTE]
    >  Si l’Agent SQL Server n’est pas démarré, faites un clic droit, puis cliquez sur **Démarrer**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans le \<table\> zone de texte, sélectionnez **BTARNDATA** dans la liste.  
  
5.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
7.  Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message entrant.  
  
    > [!NOTE]
    >  Vous devez voir un message de catégorie 10 qui correspond à la demande d'origine envoyée par l'ordinateur Fabrikam.  
  
8.  Dans la fenêtre SQL, tapez l'instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
10. Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.  
  
    > [!NOTE]
    >  Vous devez voir un message de catégorie 50 qui correspond à la réponse Contoso à la requête PIP 0C4 envoyée par Fabrikam. Dans un scénario synchrone double action, l'ordinateur récepteur n'envoie pas d'accusé de réception à l'ordinateur initiateur en réponse au message de requête initial. Le message de réponse sert d'accusé de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Envoi d’une demande de 3A2](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md)   
 [Flux de messages BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)