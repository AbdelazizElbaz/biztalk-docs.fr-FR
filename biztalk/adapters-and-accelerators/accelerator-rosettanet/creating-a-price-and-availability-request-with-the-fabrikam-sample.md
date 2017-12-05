---
title: "Création d’un prix et la disponibilité de demande avec l’exemple Fabrikam | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating requests
ms.assetid: 6e4f4589-8f01-4b9e-93ee-c9371f32e04a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0619dc77496fd1547505221ff2f437bf486fb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-price-and-availability-request-with-the-fabrikam-sample"></a>Création d’un prix et la demande de disponibilité avec l’exemple Fabrikam
Dans cette étape, vous créez une demande de prix et de disponibilité 3A2 à l’aide de l’outil LOBWebApplication.  
  
### <a name="to-submit-a-3a2-price-and-availability-request-to-contoso"></a>Pour envoyer une demande de prix et de disponibilité 3A2 à Contoso  
  
1.  Dans Internet Explorer, accédez à http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx.  
  
2.  Sur le **LOBWebApplication** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Organisation d’origine**|Tapez **FABRIKAM**.|  
    |**Organisation du partenaire**|Tapez **CONTOSO**.|  
    |**Code PIP**|Type **3A2**.|  
    |**Version PIP**|Type **R02.00.00A**.|  
    |**Catégorie de message**|Tapez **Action**.|  
  
3.  À l’aide du bloc-notes ou un autre éditeur de texte, ouvrez le **3A2_Request.xml** fichier dans C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder Copiez et collez le texte dans le **contenu du Service** champ dans l’outil LOBWebApplication.  
  
4.  Cliquez sur **Submit** pour envoyer la demande 3A2 à Contoso.  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a>Pour vérifier la communication sur l'ordinateur Fabrikam  
  
1.  Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso. Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso. Un message de catégorie -99 indique une erreur. Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
3.  Dans la connexion de la boîte de dialogue, dans le **SQL Server** , tapez **localhost**, sélectionnez **l’authentification Windows**, puis cliquez sur **Connect**.  
  
4.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
5.  Dans le  **\<table\> texte** boîte de dialogue, sélectionnez **BTARNDATA** dans la liste.  
  
6.  Dans le **SQL** fenêtre, tapez l’instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
7.  Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
8.  Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam. Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam. Vous pouvez également utiliser le champ ServiceContent pour vérifier la réponse.  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a>Pour vérifier la communication sur l'ordinateur Contoso  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la connexion de la boîte de dialogue, dans le **SQL Server** , tapez **localhost**, sélectionnez **l’authentification Windows**, puis cliquez sur **Connect**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans le  **\<table\> texte** boîte de dialogue, sélectionnez **BTARNDATA** dans la liste.  
  
5.  Dans le **SQL** fenêtre, tapez l’instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
7.  Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.  
  
    > [!NOTE]
    >  Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam. Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie l’accusé de réception.  
  
8.  Dans le **SQL** fenêtre, tapez l’instruction SQL suivante :  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. Cliquez sur **Exécuter** pour exécuter l'instruction SQL.  
  
10. Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.  
  
    > [!NOTE]
    >  Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam. Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur le processus privé](../../adapters-and-accelerators/accelerator-rosettanet/private-process-tutorial.md)