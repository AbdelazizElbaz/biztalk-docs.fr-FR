---
title: "Étape 8 : Afficher les Messages dans les bases de données BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, viewing
- loopback tutorial, viewing messages
- databases, viewing messages
ms.assetid: c549670c-4428-483c-906c-eff163ddef9a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2324cca59a9104d8f40b5b6b69eca76af1004384
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-view-messages-in-the-btarn-databases"></a>Étape 8 : Afficher les Messages dans les bases de données BTARN
Dans cette étape, vous utilisez l’Analyseur de requêtes SQL pour afficher les messages de métier (LOB) stockés dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] base de données pour vérifier que votre scénario de bouclage fonctionne correctement.  
  
 Après l’Application LOB utilitaire génère un message LOB et l’envoie à [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], les événements suivants se produisent pour l’initiateur (accueil) et le répondeur (partenaire) :  
  
 Flux de travail initiateur  
  
-   SubmitRNIF envoie le message LOB à la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données.  
  
-   L’adaptateur SQL, emplacement de réception sélectionne le message puis les remet à la base de données MessageBox. L’adaptateur SQL récupère un message à une durée d’exécution le `GetMessagesFromLOB` procédure stockée.  
  
-   L’initiateur privé récupère le message à partir de la base de données MessageBox et passe à nouveau la base de données MessageBox avec les propriétés de contexte promue supplémentaires.  
  
-   L’initiateur publique récupère le message à partir de la base de données MessageBox en fonction du filtre d’abonnement.  
  
-   Le protocole HTTP port d’envoi récupère le message avec le pipeline RNIFSend basé sur les abonnements. Il enregistre le message dans la table MessageStorageOut de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données de l’Archive de non répudiation et puis envoie le message via la page du fichier RNIFSend.aspx.  
  
-   La page du fichier RNIFSend.aspx reçoit le message codé au format MIME avec des variables de chaîne de requête qui incluent la destination finale du message (URL de l’organisation partenaire).  
  
 Répondeur de flux de travail  
  
-   [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]envoie le message RNIF à la page RNIFReceive.aspx dans laquelle le wrapper décodée MIME est supprimé. Le message est identifié en tant que de manière synchrone ou asynchrone et transmis à emplacement (RNIF_Sync_Receive ou RNIF_Async_Receive) de réception de manière synchrone ou asynchrone.  
  
-   La réception HTTP enregistre de premier emplacement le format câble du message dans la table MessageStorageIn de non répudiation de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données de l’Archive. Emplacement de réception HTTP puis décode, déchiffre (pour RNIF 2.0), valide dans sa signature, Désassemble les parties de message XML, l’autorise en fonction de la signature, puis le dépose dans la base de données MessageBox avec les propriétés promues correctes  
  
-   Le répondeur public récupère les parties de message en fonction de l’abonnement et valide et traite le message en fonction de la norme de RNIF correct. La partie de contenu de service dépose le message dans la base de données MessageBox avec les propriétés de contexte correct.  
  
-   L’instruction SQL port d’envoi récupère le message en fonction du filtre d’abonnement. Elle enregistre ensuite le message dans la table MessagesToLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données.  
  
> [!NOTE]
>  Sur le côté répondeur, le répondeur Public est chargé de générer l’accusé de réception ou le signal d’exception à l’initiateur. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]n’enregistre pas le message de signal dans la table MessagesFromLOB. Il s’agit, car l’application métier ne génère pas le message de signal. Le message d’Action continue via le répondeur privé, et [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] enregistre dans la table MessagesToLOB.  
  
> [!NOTE]
>  Pour des PIP double action, le système métier sur le côté du répondeur est chargé de générer un message de réponse. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Il supprime la table MessagesFromLOB passent par le même processus que le processus côté initiateur. Dans ce cas, le processus initiateur Public sur le côté initiateur envoie un signal d’accusé de réception ou d’une exception accusé de réception pour le message de réponse.  
  
### <a name="to-view-messages-in-the-btarn-databases"></a>Pour afficher les messages dans les bases de données BTARN  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la connexion de la boîte de dialogue, cliquez sur **connexion**.  
  
    > [!NOTE]
    >  Dans le volet de l’Explorateur d’objets, vérifiez que l’Agent SQL Server est démarré. Avec le bouton droit dans le cas contraire, **l’Agent SQL Server**, puis cliquez sur **Démarrer**.  
  
3.  Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.  
  
4.  Dans la fenêtre de requête vide, tapez ce qui suit :  
  
    ```  
    use BTARNArchive  
    SELECT * FROM         MessageStorageIn ORDER BY TIMECREATED ASC  
    SELECT * FROM         MessageStorageOut ORDER BY TIMECREATED ASC  
  
    use BTARNData  
    SELECT     * FROM         MessagesFromLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         MessagesToLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         Attachments ORDER BY TIMECREATED ASC  
    ```  
  
5.  Dans Microsoft SQL Server Management Studio, cliquez sur **Execute**.  
  
 Vous verrez un message d’action dans la table MessagesFromLOB, et si vous exécutez la requête dans quelques minutes (durée peut varier selon votre configuration système), vous verrez deux messages générés dans la table MessagesToLOB avec les valeurs MessageCategory AsyncAckSignal (25) et AsyncAction (10).  
  
## <a name="see-also"></a>Voir aussi  
 [Bouclage](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)   
 [Didacticiel de bouclage](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)