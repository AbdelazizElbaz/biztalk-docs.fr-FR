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
# <a name="step-8-view-messages-in-the-btarn-databases"></a><span data-ttu-id="ce8b9-102">Étape 8 : Afficher les Messages dans les bases de données BTARN</span><span class="sxs-lookup"><span data-stu-id="ce8b9-102">Step 8: View Messages in the BTARN Databases</span></span>
<span data-ttu-id="ce8b9-103">Dans cette étape, vous utilisez l’Analyseur de requêtes SQL pour afficher les messages de métier (LOB) stockés dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] base de données pour vérifier que votre scénario de bouclage fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-103">In this step, you use SQL Query Analyzer to view line-of-business (LOB) messages stored in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] database to verify that your loop-back scenario is working correctly.</span></span>  
  
 <span data-ttu-id="ce8b9-104">Après l’Application LOB utilitaire génère un message LOB et l’envoie à [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], les événements suivants se produisent pour l’initiateur (accueil) et le répondeur (partenaire) :</span><span class="sxs-lookup"><span data-stu-id="ce8b9-104">After the LOB Application utility generates an LOB message and submits it to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the following events occur for the initiator (home) and the responder (partner):</span></span>  
  
 <span data-ttu-id="ce8b9-105">Flux de travail initiateur</span><span class="sxs-lookup"><span data-stu-id="ce8b9-105">Initiator Workflow</span></span>  
  
-   <span data-ttu-id="ce8b9-106">SubmitRNIF envoie le message LOB à la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-106">SubmitRNIF submits the LOB message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA database.</span></span>  
  
-   <span data-ttu-id="ce8b9-107">L’adaptateur SQL, emplacement de réception sélectionne le message puis les remet à la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-107">The SQL adapter receive location picks up the message and delivers it to the MessageBox database.</span></span> <span data-ttu-id="ce8b9-108">L’adaptateur SQL récupère un message à une durée d’exécution le `GetMessagesFromLOB` procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-108">The SQL adapter picks up one message at a time running the `GetMessagesFromLOB` stored procedure.</span></span>  
  
-   <span data-ttu-id="ce8b9-109">L’initiateur privé récupère le message à partir de la base de données MessageBox et passe à nouveau la base de données MessageBox avec les propriétés de contexte promue supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-109">The private initiator picks the message from the MessageBox database and then drops it again to the MessageBox database with additional promoted context properties.</span></span>  
  
-   <span data-ttu-id="ce8b9-110">L’initiateur publique récupère le message à partir de la base de données MessageBox en fonction du filtre d’abonnement.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-110">The public initiator picks the message from the MessageBox database based on the subscription filter.</span></span>  
  
-   <span data-ttu-id="ce8b9-111">Le protocole HTTP port d’envoi récupère le message avec le pipeline RNIFSend basé sur les abonnements.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-111">The HTTP send port picks the message with the RNIFSend pipeline based on the subscriptions.</span></span> <span data-ttu-id="ce8b9-112">Il enregistre le message dans la table MessageStorageOut de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données de l’Archive de non répudiation et puis envoie le message via la page du fichier RNIFSend.aspx.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-112">It saves the message in the MessageStorageOut table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Archive database for non-repudiation, and then sends the message over to the RNIFSend.aspx page.</span></span>  
  
-   <span data-ttu-id="ce8b9-113">La page du fichier RNIFSend.aspx reçoit le message codé au format MIME avec des variables de chaîne de requête qui incluent la destination finale du message (URL de l’organisation partenaire).</span><span class="sxs-lookup"><span data-stu-id="ce8b9-113">The RNIFSend.aspx page receives the MIME-encoded message with query string variables that include the final destination of the message (partner organization URL).</span></span>  
  
 <span data-ttu-id="ce8b9-114">Répondeur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="ce8b9-114">Responder Workflow</span></span>  
  
-   [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ce8b9-115">envoie le message RNIF à la page RNIFReceive.aspx dans laquelle le wrapper décodée MIME est supprimé.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-115"> sends the RNIF message to the RNIFReceive.aspx page where the MIME-decoded wrapper is removed.</span></span> <span data-ttu-id="ce8b9-116">Le message est identifié en tant que de manière synchrone ou asynchrone et transmis à emplacement (RNIF_Sync_Receive ou RNIF_Async_Receive) de réception de manière synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-116">The message is identified as either synchronous or asynchronous, and then forwarded to either the synchronous or asynchronous receive location (RNIF_Sync_Receive or RNIF_Async_Receive).</span></span>  
  
-   <span data-ttu-id="ce8b9-117">La réception HTTP enregistre de premier emplacement le format câble du message dans la table MessageStorageIn de non répudiation de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données de l’Archive.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-117">The HTTP receive location first saves the wire format of the message in the MessageStorageIn table for non-repudiation of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Archive database.</span></span> <span data-ttu-id="ce8b9-118">Emplacement de réception HTTP puis décode, déchiffre (pour RNIF 2.0), valide dans sa signature, Désassemble les parties de message XML, l’autorise en fonction de la signature, puis le dépose dans la base de données MessageBox avec les propriétés promues correctes</span><span class="sxs-lookup"><span data-stu-id="ce8b9-118">The HTTP receive location then decodes, decrypts (for RNIF 2.0), validates on its signature, disassembles the XML message parts, authorizes based on the signature, and then drops it in the MessageBox database with the correct promoted properties</span></span>  
  
-   <span data-ttu-id="ce8b9-119">Le répondeur public récupère les parties de message en fonction de l’abonnement et valide et traite le message en fonction de la norme de RNIF correct.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-119">The public responder picks the message parts based on subscription, and then validates and processes the message based on the correct RNIF standard.</span></span> <span data-ttu-id="ce8b9-120">La partie de contenu de service dépose le message dans la base de données MessageBox avec les propriétés de contexte correct.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-120">The service content part drops the message into the MessageBox database with the correct context properties.</span></span>  
  
-   <span data-ttu-id="ce8b9-121">L’instruction SQL port d’envoi récupère le message en fonction du filtre d’abonnement.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-121">The SQL send port picks the message based on the subscription filter.</span></span> <span data-ttu-id="ce8b9-122">Elle enregistre ensuite le message dans la table MessagesToLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-122">It then saves the message in the MessagesToLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce8b9-123">Sur le côté répondeur, le répondeur Public est chargé de générer l’accusé de réception ou le signal d’exception à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-123">On the responder side, the Public Responder is responsible for generating the acknowledgement receipt or the exception signal back to the initiator.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ce8b9-124">n’enregistre pas le message de signal dans la table MessagesFromLOB.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-124"> does not save the signal message in the MessagesFromLOB table.</span></span> <span data-ttu-id="ce8b9-125">Il s’agit, car l’application métier ne génère pas le message de signal.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-125">This is because the LOB application does not generate the signal message.</span></span> <span data-ttu-id="ce8b9-126">Le message d’Action continue via le répondeur privé, et [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] enregistre dans la table MessagesToLOB.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-126">The Action message will continue through the Private Responder, and [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves it to the MessagesToLOB table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce8b9-127">Pour des PIP double action, le système métier sur le côté du répondeur est chargé de générer un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-127">For double-action PIPs, the LOB on the responder side is responsible for generating a response message.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ce8b9-128">Il supprime la table MessagesFromLOB passent par le même processus que le processus côté initiateur.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-128"> drops it to the MessagesFromLOB table to go through the same process as the initiator-side process.</span></span> <span data-ttu-id="ce8b9-129">Dans ce cas, le processus initiateur Public sur le côté initiateur envoie un signal d’accusé de réception ou d’une exception accusé de réception pour le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-129">In this case, the Public Initiator Process on the initiator side sends back an acknowledgement receipt or exception signal for the response message.</span></span>  
  
### <a name="to-view-messages-in-the-btarn-databases"></a><span data-ttu-id="ce8b9-130">Pour afficher les messages dans les bases de données BTARN</span><span class="sxs-lookup"><span data-stu-id="ce8b9-130">To view messages in the BTARN databases</span></span>  
  
1.  <span data-ttu-id="ce8b9-131">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-131">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="ce8b9-132">Dans la connexion de la boîte de dialogue, cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-132">In the Connect to Server dialog box, click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce8b9-133">Dans le volet de l’Explorateur d’objets, vérifiez que l’Agent SQL Server est démarré.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-133">In the Object Explorer pane, verify that the SQL Server Agent is started.</span></span> <span data-ttu-id="ce8b9-134">Avec le bouton droit dans le cas contraire, **l’Agent SQL Server**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-134">If not, right-click **SQL Server Agent**, and click **Start**.</span></span>  
  
3.  <span data-ttu-id="ce8b9-135">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-135">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="ce8b9-136">Dans la fenêtre de requête vide, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ce8b9-136">In the Blank Query window, type the following:</span></span>  
  
    ```  
    use BTARNArchive  
    SELECT * FROM         MessageStorageIn ORDER BY TIMECREATED ASC  
    SELECT * FROM         MessageStorageOut ORDER BY TIMECREATED ASC  
  
    use BTARNData  
    SELECT     * FROM         MessagesFromLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         MessagesToLOB ORDER BY TIMECREATED ASC  
    SELECT     * FROM         Attachments ORDER BY TIMECREATED ASC  
    ```  
  
5.  <span data-ttu-id="ce8b9-137">Dans Microsoft SQL Server Management Studio, cliquez sur **Execute**.</span><span class="sxs-lookup"><span data-stu-id="ce8b9-137">In the Microsoft SQL Server Management Studio, click **Execute**.</span></span>  
  
 <span data-ttu-id="ce8b9-138">Vous verrez un message d’action dans la table MessagesFromLOB, et si vous exécutez la requête dans quelques minutes (durée peut varier selon votre configuration système), vous verrez deux messages générés dans la table MessagesToLOB avec les valeurs MessageCategory AsyncAckSignal (25) et AsyncAction (10).</span><span class="sxs-lookup"><span data-stu-id="ce8b9-138">You will see an action message in the MessagesFromLOB table, and if you run the query again in several minutes (time may vary depending on your system configuration), you will see two messages generated in the MessagesToLOB table with MessageCategory values of AsyncAckSignal (25) and AsyncAction (10).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8b9-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce8b9-139">See Also</span></span>  
 <span data-ttu-id="ce8b9-140">[Bouclage](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md) </span><span class="sxs-lookup"><span data-stu-id="ce8b9-140">[Loopback](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md) </span></span>  
 [<span data-ttu-id="ce8b9-141">Didacticiel de bouclage</span><span class="sxs-lookup"><span data-stu-id="ce8b9-141">Loopback Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)