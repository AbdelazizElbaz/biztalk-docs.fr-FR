---
title: "Qu'est-ce que l'adaptateur POP3 ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- POP3 adapters, availability
- authenticating, POP3 adapters
- POP3 adapters, data duplication
- data duplication
- POP3 adapters, receive adapters
- high availability, POP3 adapters
- POP3 adapters, supported platforms
- POP3 adapters, authenticating
- POP3 adapters, algorithims
- receive adapters, POP3 adapters
ms.assetid: 05e9598b-cdfe-4216-b6bf-1b84f8ddfeae
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 592e0475b607de3f9df528a4bab777aa0fb7635d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-pop3-adapter"></a><span data-ttu-id="64ed5-103">Qu'est-ce que l'adaptateur POP3 ?</span><span class="sxs-lookup"><span data-stu-id="64ed5-103">What Is the POP3 Adapter?</span></span>
<span data-ttu-id="64ed5-104">Cette rubrique décrit l'adaptateur de réception POP3.</span><span class="sxs-lookup"><span data-stu-id="64ed5-104">This section describes the POP3 receive adapter.</span></span>  
  
## <a name="pop3-receive-adapter"></a><span data-ttu-id="64ed5-105">Adaptateur de réception POP3</span><span class="sxs-lookup"><span data-stu-id="64ed5-105">POP3 Receive Adapter</span></span>  
 <span data-ttu-id="64ed5-106">L'adaptateur de réception POP3 permet de déplacer des données d'une boîte aux lettres POP3 vers BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="64ed5-106">The POP3 receive adapter enables you to move data from a POP3-enabled mailbox to BizTalk Server.</span></span>  
  
 <span data-ttu-id="64ed5-107">Les fonctionnalités principales de l'adaptateur de réception POP3 sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="64ed5-107">The key features of the POP3 receive adapter are:</span></span>  
  
-   <span data-ttu-id="64ed5-108">extraction de fichier de la boîte aux lettres du serveur POP3 à la demande ;</span><span class="sxs-lookup"><span data-stu-id="64ed5-108">Pulling files from the POP3 server mailbox on demand.</span></span>  
  
-   <span data-ttu-id="64ed5-109">exécution d'interrogations basées sur une planification configurable ;</span><span class="sxs-lookup"><span data-stu-id="64ed5-109">Running polls based on a configurable schedule.</span></span>  
  
-   <span data-ttu-id="64ed5-110">interrogation de la boîte aux lettres du serveur POP3 et envoi de données directement à BizTalk Server ;</span><span class="sxs-lookup"><span data-stu-id="64ed5-110">Polling the POP3 server mailbox and sending data directly to BizTalk Server.</span></span>  
  
-   <span data-ttu-id="64ed5-111">spécification de la boîte aux lettres du serveur POP3 comme adresse IP ou nom d'hôte, port, nom d'utilisateur et mot de passe ;</span><span class="sxs-lookup"><span data-stu-id="64ed5-111">Specifying the POP3 server mailbox as an IP address or host name, port, user name, and password.</span></span>  
  
-   <span data-ttu-id="64ed5-112">possibilité de télécharger des messages de serveurs de messagerie exigeant des connexions SSL ;</span><span class="sxs-lookup"><span data-stu-id="64ed5-112">Ability to download e-mail from mail servers that require Secure Sockets Layer (SSL) connections.</span></span>  
  
-   <span data-ttu-id="64ed5-113">remise de fichier garantie ;</span><span class="sxs-lookup"><span data-stu-id="64ed5-113">Guaranteed file delivery.</span></span>  
  
-   <span data-ttu-id="64ed5-114">traitement MIME implicite,</span><span class="sxs-lookup"><span data-stu-id="64ed5-114">Implicit MIME processing.</span></span> <span data-ttu-id="64ed5-115">sans nécessité d'utiliser un décodeur MIME dans un pipeline de réception en cas d'utilisation de l'adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="64ed5-115">It is not necessary to use a MIME decoder in a receive pipeline when using the POP3 adapter.</span></span>  
  
## <a name="pop3-adapter-supported-platforms"></a><span data-ttu-id="64ed5-116">Plateformes prises en charge par l'adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="64ed5-116">POP3 Adapter Supported Platforms</span></span>  
 <span data-ttu-id="64ed5-117">L'adaptateur POP3 est conçu pour opérer avec tout serveur POP3 conforme aux RFC suivantes :</span><span class="sxs-lookup"><span data-stu-id="64ed5-117">The POP3 adapter is designed to work with any POP3 servers that conform to the following RFCs:</span></span>  
  
-   <span data-ttu-id="64ed5-118">**RFC 1939.**</span><span class="sxs-lookup"><span data-stu-id="64ed5-118">**RFC 1939.**</span></span> <span data-ttu-id="64ed5-119">Post Office Protocol Version 3 (voir [http://go.microsoft.com/fwlink/?LinkId=58808](http://go.microsoft.com/fwlink/?LinkId=58808))</span><span class="sxs-lookup"><span data-stu-id="64ed5-119">Post Office Protocol Version 3 (see [http://go.microsoft.com/fwlink/?LinkId=58808](http://go.microsoft.com/fwlink/?LinkId=58808))</span></span>  
  
-   <span data-ttu-id="64ed5-120">**RFC 1734.**</span><span class="sxs-lookup"><span data-stu-id="64ed5-120">**RFC 1734.**</span></span> <span data-ttu-id="64ed5-121">Commande d’authentification POP3 (consultez [http://go.microsoft.com/fwlink/?LinkId=58809](http://go.microsoft.com/fwlink/?LinkId=58809))</span><span class="sxs-lookup"><span data-stu-id="64ed5-121">POP3 AUTHentication command (see [http://go.microsoft.com/fwlink/?LinkId=58809](http://go.microsoft.com/fwlink/?LinkId=58809))</span></span>  
  
-   <span data-ttu-id="64ed5-122">**RFC 2045.**</span><span class="sxs-lookup"><span data-stu-id="64ed5-122">**RFC 2045.**</span></span> <span data-ttu-id="64ed5-123">Multipurpose Internet Mail Extensions (MIME), partie un : Format du corps de Message Internet (consultez [http://go.microsoft.com/fwlink/?LinkId=58810](http://go.microsoft.com/fwlink/?LinkId=58810))</span><span class="sxs-lookup"><span data-stu-id="64ed5-123">Multipurpose Internet Mail Extensions (MIME) Part One: Format of Internet Message Bodies (see [http://go.microsoft.com/fwlink/?LinkId=58810](http://go.microsoft.com/fwlink/?LinkId=58810))</span></span>  
  
-   <span data-ttu-id="64ed5-124">**RFC 2046.**</span><span class="sxs-lookup"><span data-stu-id="64ed5-124">**RFC 2046.**</span></span> <span data-ttu-id="64ed5-125">Multipurpose Internet Mail Extensions (MIME), partie deux : Types de médias (consultez [http://go.microsoft.com/fwlink/?LinkId=58811](http://go.microsoft.com/fwlink/?LinkId=58811))</span><span class="sxs-lookup"><span data-stu-id="64ed5-125">Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types (see [http://go.microsoft.com/fwlink/?LinkId=58811](http://go.microsoft.com/fwlink/?LinkId=58811))</span></span>  
  
-   <span data-ttu-id="64ed5-126">**RFC 2047.**</span><span class="sxs-lookup"><span data-stu-id="64ed5-126">**RFC 2047.**</span></span> <span data-ttu-id="64ed5-127">MIME (Multipurpose Internet Mail Extensions), partie trois : Extensions d’en-tête de Message pour texte Non-ASCII (consultez [http://go.microsoft.com/fwlink/?LinkId=58812](http://go.microsoft.com/fwlink/?LinkId=58812))</span><span class="sxs-lookup"><span data-stu-id="64ed5-127">MIME (Multipurpose Internet Mail Extensions) Part Three: Message Header Extensions for Non-ASCII Text (see [http://go.microsoft.com/fwlink/?LinkId=58812](http://go.microsoft.com/fwlink/?LinkId=58812))</span></span>  
  
 <span data-ttu-id="64ed5-128">L'adaptateur POP3 a fait l'objet de tests intensifs avec Microsoft Exchange Server 2003.</span><span class="sxs-lookup"><span data-stu-id="64ed5-128">The POP3 adapter was tested extensively against Microsoft Exchange Server 2003.</span></span>  
  
## <a name="considerations-for-preventing-data-duplication-when-using-the-pop3-adapter"></a><span data-ttu-id="64ed5-129">Considérations relatives au blocage de la duplication de données en cas d'utilisation de l'adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="64ed5-129">Considerations for Preventing Data Duplication When Using the POP3 Adapter</span></span>  
 <span data-ttu-id="64ed5-130">L'adaptateur POP3 n'est pas un adaptateur transactionnel. Il est donc sujet au traitement de plusieurs copies d'un même message, ce qui peut entraîner une duplication de données.</span><span class="sxs-lookup"><span data-stu-id="64ed5-130">The POP3 adapter is not a transactional adapter and therefore is subject to processing multiple copies of the same message, potentially causing data duplication.</span></span> <span data-ttu-id="64ed5-131">Il peut arriver que l'adaptateur POP3 produise des copies en double d'un message dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="64ed5-131">It is possible that the POP3 adapter will deliver duplicate copies of a message in the following scenarios:</span></span>  
  
-   <span data-ttu-id="64ed5-132">L'adaptateur POP3 supprime toujours les messages de la boîte aux lettres pour la surveillance de laquelle il est configuré après les avoir soumis à BizTalk pour traitement.</span><span class="sxs-lookup"><span data-stu-id="64ed5-132">The POP3 adapter always deletes e-mails from the mailbox that it is configured to monitor after the e-mail has been successfully submitted to BizTalk Server for processing.</span></span> <span data-ttu-id="64ed5-133">Si l'adaptateur POP3 extrait un message d'une boîte aux lettres, le soumet à BizTalk Server pour traitement, puis échoue à le supprimer, ce message est de nouveau soumis à BizTalk Server lors de l'interrogation suivante de la boîte aux lettres par l'adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="64ed5-133">If the POP3 adapter retrieves an e-mail from a mailbox, submits the e-mail to BizTalk Server for processing, and fails to delete the e-mail from the mailbox, the e-mail will be resubmitted to BizTalk Server the next time that the POP3 adapter polls the mailbox.</span></span>  
  
-   <span data-ttu-id="64ed5-134">Si plusieurs instances de l'adaptateur POP3 dans des instances de l'hôte BizTalk distinctes surveillent simultanément la même boîte aux lettres, alors que le serveur POP3 autorise plusieurs connexions simultanées à ses boîtes aux lettres, l'adaptateur remet parfois des copies en double de certains messages.</span><span class="sxs-lookup"><span data-stu-id="64ed5-134">If multiple instances of the POP3 adapter in separate BizTalk Host instances are monitoring the same mailbox simultaneously and the POP3 server allows multiple concurrent connections to its mailboxes, then the adapter may deliver duplicate copies of messages.</span></span>  
  
## <a name="high-availability-for-the-pop3-adapter"></a><span data-ttu-id="64ed5-135">Haute disponibilité pour l'adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="64ed5-135">High Availability for the POP3 Adapter</span></span>  
 <span data-ttu-id="64ed5-136">Certains serveurs POP3 autorisent plusieurs connexions simultanées à une boîte aux lettres donnée.</span><span class="sxs-lookup"><span data-stu-id="64ed5-136">Some POP3 servers permit multiple concurrent connections to a given mailbox.</span></span> <span data-ttu-id="64ed5-137">Si plusieurs instances de l'adaptateur POP3 sont configurées pour extraire des messages d'une boîte aux lettres d'un tel serveur POP3, des données sont dupliquées.</span><span class="sxs-lookup"><span data-stu-id="64ed5-137">If more than one instance of the POP3 adapter is configured to retrieve mail from a mailbox on such a POP3 server then data duplication can occur.</span></span> <span data-ttu-id="64ed5-138">Vous devez donc configurer une seule instance de l'adaptateur POP3 pour extraire des messages d'une boîte aux lettres autorisant plusieurs connexions simultanées.</span><span class="sxs-lookup"><span data-stu-id="64ed5-138">Therefore you should configure only one instance of the POP3 adapter to retrieve mail from a mailbox that permits multiple concurrent connections.</span></span>  
  
 <span data-ttu-id="64ed5-139">Pour assurer la tolérance de pannes de l'adaptateur POP3 dans ce scénario, il convient de ne configurer qu'un seul gestionnaire de réception pour s'exécuter sur un hôte BizTalk en cluster.</span><span class="sxs-lookup"><span data-stu-id="64ed5-139">To provide fault tolerance for the POP3 adapter in this scenario, a single POP3 adapter receive handler should be configured to run in a clustered BizTalk Host.</span></span> <span data-ttu-id="64ed5-140">Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span><span class="sxs-lookup"><span data-stu-id="64ed5-140">For more information see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
## <a name="authentication-warnings-when-multiple-instances-of-the-pop3-adapter-connect-to-the-same-mailbox"></a><span data-ttu-id="64ed5-141">Avertissements d'authentification quand plusieurs instances de l'adaptateur POP3 se connectent à la même boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="64ed5-141">Authentication Warnings When Multiple Instances of the POP3 Adapter Connect to the Same Mailbox</span></span>  
 <span data-ttu-id="64ed5-142">Vous pouvez configurer BizTalk Server de façon à ce que plusieurs instances de l'adaptateur POP3 extraient des messages d'une même boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="64ed5-142">BizTalk Server may be configured to have more than one instance of the POP3 adapter retrieve mail from the same mailbox.</span></span> <span data-ttu-id="64ed5-143">Dans ce cas, il se peut que des avertissements d'authentification soient générés dans le journal des applications de BizTalk Server en raison du mécanisme de verrouillage que certains serveurs POP3 utilisent.</span><span class="sxs-lookup"><span data-stu-id="64ed5-143">In such a case, it is possible that authentication warnings may be generated in the BizTalk Server Application log because of the locking mechanism employed by some POP3 servers.</span></span> <span data-ttu-id="64ed5-144">Ces avertissements n'ayant aucune incidence sur la fonctionnalité de l'adaptateur POP3, vous pouvez les ignorer dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="64ed5-144">These warnings will have no impact on the POP3 adapter functionality and can be safely ignored in this scenario.</span></span>  
  
## <a name="encrypted-messages-received-by-the-pop3-adapter-that-are-sent-to-the-suspended-queue-may-be-viewable-in-clear-text"></a><span data-ttu-id="64ed5-145">Possibilité d'afficher en texte clair des messages chiffrés reçus par l'adaptateur POP3 et envoyés à la file d'attente de messages interrompus</span><span class="sxs-lookup"><span data-stu-id="64ed5-145">Encrypted Messages Received by the POP3 Adapter that are sent to the Suspended Queue may be Viewable in Clear Text</span></span>  
 <span data-ttu-id="64ed5-146">Vous pouvez configurer l'adaptateur POP3 pour déchiffrer des messages ayant fait l'objet d'un chiffrement numérique.</span><span class="sxs-lookup"><span data-stu-id="64ed5-146">You can configure the POP3 adapter to decrypt digitally encrypted e-mails.</span></span> <span data-ttu-id="64ed5-147">Cela est effectué en définissant le **appliquer le décodage MIME** propriété **True** pour les emplacements de réception qui utilisent l’adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="64ed5-147">This is done by setting the **Apply MIME Decoding** property to **True** for receive locations that use the POP3 adapter.</span></span> <span data-ttu-id="64ed5-148">Si l’adaptateur POP3 reçoit un message chiffré numériquement et la **appliquer le décodage MIME** pour l’emplacement de réception est définie sur **True** l’adaptateur POP3 tente de déchiffrer le message comme suit :</span><span class="sxs-lookup"><span data-stu-id="64ed5-148">If the POP3 Adapter receives a digitally encrypted e-mail and the **Apply MIME Decoding** property for the receive location is set to **True** then the POP3 adapter attempts to decrypt the e-mail as follows:</span></span>  
  
-   <span data-ttu-id="64ed5-149">L'adaptateur POP3 recherche un certificat privé correspondant au certificat public utilisé pour chiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="64ed5-149">The POP3 Adapter searches for a private certificate that matches the public certificate used to encrypt the e-mail.</span></span> <span data-ttu-id="64ed5-150">Ce certificat privé doit se trouver dans le magasin de certificats personnels du serveur exécutant l'instance de l'hôte à laquelle le gestionnaire de réception POP3 est lié.</span><span class="sxs-lookup"><span data-stu-id="64ed5-150">The private certificate must be in the Personal certificate store of the server that is running the host instance that the POP3 receive handler is bound to.</span></span>  
  
-   <span data-ttu-id="64ed5-151">Si l'adaptateur POP3 repère un certificat privé correspondant, il l'utilise pour déchiffrer le message électronique.</span><span class="sxs-lookup"><span data-stu-id="64ed5-151">If the POP3 Adapter locates a corresponding private certificate, it uses the private certificate to decrypt the e-mail message.</span></span>  
  
-   <span data-ttu-id="64ed5-152">Le message est déchiffré et conservé dans la MessageBox BizTalk.</span><span class="sxs-lookup"><span data-stu-id="64ed5-152">The e-mail is decrypted and persisted to the BizTalk MessageBox.</span></span>  
  
 <span data-ttu-id="64ed5-153">Si un message est interrompu après avoir été déchiffré et conservé dans la MessageBox BizTalk, son contenu est visible en texte clair dans la file d'attente de messages interrompus de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="64ed5-153">If a message is suspended after being decrypted and persisted to the BizTalk MessageBox, the contents of the message will be visible in clear text in the BizTalk suspended queue.</span></span>  
  
 <span data-ttu-id="64ed5-154">Pour empêcher l'affichage du texte de messages sécurisés dans la file d'attente de messages interrompus, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="64ed5-154">If you need to prevent the display of secure message text in the suspended queue, follow these steps:</span></span>  
  
-   <span data-ttu-id="64ed5-155">Définir le **appliquer le décodage MIME** propriété **False** pour les emplacements de réception qui utilisent l’adaptateur POP3 et déchiffrer le message dans un pipeline avec le composant de pipeline SMIME.</span><span class="sxs-lookup"><span data-stu-id="64ed5-155">Set the **Apply MIME Decoding** property to **False** for receive locations that use the POP3 adapter and decrypt the message in a pipeline with the SMIME pipeline component.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64ed5-156">Cette approche vous empêche de promouvoir des propriétés de messagerie spécifiques vers le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="64ed5-156">This approach will prevent you from being able to promote e-mail specific properties to the message context.</span></span>  
  
-   <span data-ttu-id="64ed5-157">Si vous voulez promouvoir des propriétés de messagerie spécifiques vers le contexte du message tout en veillant à ce que les messages chiffrés restent chiffrés en cas de routage vers la file d'attente de messages interrompus, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="64ed5-157">If you need to promote e-mail specific properties to the message context and ensure that encrypted messages remain encrypted if they are routed to the suspended queue, follow these steps:</span></span>  
  
    -   <span data-ttu-id="64ed5-158">Cochez l’option **activer le routage pour les messages ayant échoué** sur le port de réception qui héberge les emplacements de réception qui utilisent l’adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="64ed5-158">Check the option to **Enable routing for failed messages** on the receive port that houses the receive location(s) that use the POP3 adapter.</span></span>  
  
    -   <span data-ttu-id="64ed5-159">Créez une orchestration pour vous abonner aux messages confrontés à un échec de remise au port de réception hébergeant les emplacements de réception qui utilisent l'adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="64ed5-159">Create an orchestration to subscribe to messages that fail delivery to the receive port that houses the receive location(s) that use the POP3 adapter.</span></span>  
  
    -   <span data-ttu-id="64ed5-160">Configurez l'orchestration avec un port d'envoi qui chiffre le message dans un pipeline à l'aide du composant de pipeline SMIME.</span><span class="sxs-lookup"><span data-stu-id="64ed5-160">Configure the orchestration with a send port that encrypts the message in a pipeline using the SMIME pipeline component.</span></span>  
  
    -   <span data-ttu-id="64ed5-161">Configurez l'orchestration avec une forme de suspension, afin d'interrompre l'instance d'orchestration et le message.</span><span class="sxs-lookup"><span data-stu-id="64ed5-161">Configure the orchestration with a suspend shape to suspend the orchestration instance and the message.</span></span>  
  
    -   <span data-ttu-id="64ed5-162">Créez et déployez l'orchestration, puis liez l'orchestration déployée au port de réception approprié.</span><span class="sxs-lookup"><span data-stu-id="64ed5-162">Build and deploy the orchestration, bind the deployed orchestration to the appropriate receive port.</span></span>  
  
## <a name="maximum-message-size-supported-by-the-pop3-adapter"></a><span data-ttu-id="64ed5-163">Taille maximale de message prise en charge par l'adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="64ed5-163">Maximum Message Size Supported by the POP3 Adapter</span></span>  
 <span data-ttu-id="64ed5-164">L'adaptateur POP3 a été testé pour la réception de messages d'une taille maximale de 50 Mo.</span><span class="sxs-lookup"><span data-stu-id="64ed5-164">The POP3 adapter has been tested with and supports receiving messages up to 50 MB in size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ed5-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64ed5-165">See Also</span></span>  
 [<span data-ttu-id="64ed5-166">Adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="64ed5-166">POP3 Adapter</span></span>](../core/pop3-adapter.md)