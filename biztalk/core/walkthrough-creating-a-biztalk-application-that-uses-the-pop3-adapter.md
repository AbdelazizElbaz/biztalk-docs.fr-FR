---
title: "Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur POP3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, POP3 adapters
- configuring [POP3 adapters], mailboxes
- configuring [POP3 adapters], tutorials
- POP3 adapters, mailboxes
- POP3 adapters, tutorials
- configuring [POP3 adapters], Outlook Express
ms.assetid: b44c3b1d-7b4f-425c-831a-1ce5f6379595
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1af0d60eab23a3cbfff67a8b4b11dc73fb49afe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter"></a><span data-ttu-id="50c23-102">Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="50c23-102">Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter</span></span>
<span data-ttu-id="50c23-103">Cette section vous guide tout au long de la création d'une simple application Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur POP3.</span><span class="sxs-lookup"><span data-stu-id="50c23-103">This section takes you through creating a simple Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application using the POP3 adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50c23-104">L'application implique que vous avez accès à un ordinateur exécutant Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] avec des services de messagerie installés et configurés.</span><span class="sxs-lookup"><span data-stu-id="50c23-104">The application assumes that you have access to a computer running Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] with Email Services installed and configured.</span></span> <span data-ttu-id="50c23-105">Pour plus d'informations sur la configuration de [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] avec les services de messagerie, consultez l'aide de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="50c23-105">For information about configuring [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] with Email Services see Windows Server Help.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50c23-106">Dans cet exemple, Microsoft Outlook Express est utilisé comme client de messagerie et [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] comme serveur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="50c23-106">In this example Microsoft Outlook Express is used as the e-mail client and [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] is used as the e-mail server.</span></span> <span data-ttu-id="50c23-107">Toutefois, n'importe quel client de messagerie POP3 et serveur POP3 compatible RFC pourraient être utilisés dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="50c23-107">However, any POP3 e-mail client and RFC-compliant POP3 server could be used for this scenario.</span></span>  
  
 <span data-ttu-id="50c23-108">Cette application suppose que vous n'avez pas encore créé de ports d'envoi ou d'emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="50c23-108">This application assumes that you have not yet created any send ports or receive locations.</span></span> <span data-ttu-id="50c23-109">Si vous avez des ports d'envoi ou emplacements de réception existants, remplacez par les noms appropriés lorsque vous avancez dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="50c23-109">If you have existing send ports or receive locations, substitute appropriate names when you work through the steps.</span></span>  
  
 <span data-ttu-id="50c23-110">Il s'agit d'une application de routage simple basé sur le contenu utilisant uniquement un emplacement de réception et un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="50c23-110">The application is a simple content-based routing application using only a receive location and a send port.</span></span> <span data-ttu-id="50c23-111">L’emplacement de réception lit à partir d’une boîte aux lettres sur le serveur exécutant [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)](« Windows server »\).</span><span class="sxs-lookup"><span data-stu-id="50c23-111">The receive location reads from a mailbox on the server running [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]("the Windows server"\).</span></span> <span data-ttu-id="50c23-112">Le port d'envoi prend le message de l'emplacement de réception et l'envoie dans un dossier sur le système de fichiers local de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50c23-112">The send port takes the message from the receive location and sends it to a folder on the local file system of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="50c23-113">Pour créer l'application, vous devez créer la boîte aux lettres, configurer l'emplacement de réception et le port d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], démarrer le port d'envoi et activer l'emplacement de réception et envoyer un message de test à la boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="50c23-113">To create the application, you have to create the mailbox, set up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and send port, start the send port and enable the receive location, and send a test message to the mailbox.</span></span> <span data-ttu-id="50c23-114">Suivez les étapes ci-après pour créer l'application.</span><span class="sxs-lookup"><span data-stu-id="50c23-114">Follow the steps below to create the application.</span></span>  
  
## <a name="create-a-mailbox-on-windows-server-2003"></a><span data-ttu-id="50c23-115">Création d'une boîte aux lettres sous Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="50c23-115">Create a mailbox on Windows Server 2003</span></span>  
 <span data-ttu-id="50c23-116">Pour créer une boîte aux lettres sous Windows Server 2003 avec les services de messagerie installés, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="50c23-116">To create a mailbox on Windows Server 2003 with Email Services installed, follow these steps:</span></span>  
  
1.  <span data-ttu-id="50c23-117">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **Service POP3**.</span><span class="sxs-lookup"><span data-stu-id="50c23-117">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **POP3 Service**.</span></span>  
  
2.  <span data-ttu-id="50c23-118">Développez  *\<nom_serveur >* et cliquez sur le domaine dans lequel vous souhaitez créer une boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="50c23-118">Expand *\<servername>* and click the domain where you would like to create a mailbox.</span></span>  
  
3.  <span data-ttu-id="50c23-119">Dans le **Service POP3** boîte de dialogue, dans le volet droit, cliquez sur le **ajouter une boîte aux lettres** option.</span><span class="sxs-lookup"><span data-stu-id="50c23-119">In the **POP3 Service** dialog box, in the right pane, click the **Add Mailbox** option.</span></span>  
  
4.  <span data-ttu-id="50c23-120">Dans le **ajouter une boîte aux lettres** boîte de dialogue le **nom de la boîte aux lettres** , tapez **EmailTest**.</span><span class="sxs-lookup"><span data-stu-id="50c23-120">In the **Add Mailbox** dialog box, in the **Mailbox Name** box, type **EmailTest**.</span></span>  
  
5.  <span data-ttu-id="50c23-121">Sélectionnez le **créer un utilisateur associé pour cette boîte aux lettres** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="50c23-121">Select the **Create associated user for this mailbox** check box.</span></span>  
  
6.  <span data-ttu-id="50c23-122">Dans le **mot de passe** et **confirmer le mot de passe** zones, tapez un mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50c23-122">In the **Password** and **Confirm Password** boxes, type a password, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="50c23-123">Prenez note de la **nom de compte** et **serveur de messagerie** ouvrir une session sur les informations affichées pour une utilisation avec l’authentification en texte clair dans le **Service POP3** boîte de dialogue, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50c23-123">Make a note of the **Account name** and **Mail Server** log on information displayed for use with clear text authentication in the **POP3 Service** dialog box, and then click **OK**.</span></span> <span data-ttu-id="50c23-124">Ces informations sont utilisées par l'emplacement de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que vous configurez avec le type de transport POP3.</span><span class="sxs-lookup"><span data-stu-id="50c23-124">This information will be used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location that you configure with the POP3 transport type.</span></span>  
  
## <a name="create-the-receive-location"></a><span data-ttu-id="50c23-125">Pour créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="50c23-125">Create the receive location</span></span>  
 <span data-ttu-id="50c23-126">Suivez ces étapes pour créer l'emplacement de réception :</span><span class="sxs-lookup"><span data-stu-id="50c23-126">Follow these steps to create the receive location:</span></span>  
  
1.  <span data-ttu-id="50c23-127">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration double-cliquez sur la base de données par défaut  **\<**  *Nom_Ordinateur***>. BizTalkMgmtDb.dbo**, où *Nom_Ordinateur* est le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="50c23-127">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console double-click the default database **\<***machine_name***>.BizTalkMgmtDb.dbo**, where *machine_name* is the name of your computer.</span></span> <span data-ttu-id="50c23-128">Cliquez sur **Applications**, puis cliquez sur **BizTalk.Application.1**.</span><span class="sxs-lookup"><span data-stu-id="50c23-128">Click **Applications**, then click **BizTalk.Application.1**.</span></span>  
  
2.  <span data-ttu-id="50c23-129">Avec le bouton droit **Ports de réception**, cliquez sur **nouveau**, cliquez sur **unidirectionnel port de réception**.</span><span class="sxs-lookup"><span data-stu-id="50c23-129">Right-click **Receive Ports**, click **New**, click **One-way receive port**.</span></span>  
  
3.  <span data-ttu-id="50c23-130">Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , tapez **POP3Receive**.</span><span class="sxs-lookup"><span data-stu-id="50c23-130">In the **Receive Port Properties** dialog box, in the **Name** box, type **POP3Receive**.</span></span>  
  
4.  <span data-ttu-id="50c23-131">Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="50c23-131">Click **Receive Locations**, and then click **New**.</span></span>  <span data-ttu-id="50c23-132">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **POP3Receive**.</span><span class="sxs-lookup"><span data-stu-id="50c23-132">In the **Receive Location Properties** dialog box, in the **Name** box, type **POP3Receive**.</span></span>  
  
5.  <span data-ttu-id="50c23-133">Dans le **Type de Transport** boîte, sélectionnez **POP3**.</span><span class="sxs-lookup"><span data-stu-id="50c23-133">In the **Transport Type** box, select **POP3**.</span></span>  
  
6.  <span data-ttu-id="50c23-134">Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="50c23-134">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
7.  <span data-ttu-id="50c23-135">Dans le **Pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="50c23-135">In the **Receive Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
8.  <span data-ttu-id="50c23-136">Dans le **Transport** , cliquez sur le **configurer** bouton.</span><span class="sxs-lookup"><span data-stu-id="50c23-136">In the **Transport** box, click the **Configure** button.</span></span>  
  
9. <span data-ttu-id="50c23-137">Dans le **propriétés du Transport POP3** boîte de dialogue le **appliquer le décodage MIME** boîte, sélectionnez **False**.</span><span class="sxs-lookup"><span data-stu-id="50c23-137">In the **POP3 Transport Properties** dialog box, in the **Apply MIME Decoding** box, select **False**.</span></span>  
  
10. <span data-ttu-id="50c23-138">Dans le **serveur de messagerie** , tapez le nom du serveur Windows Server où vous avez créé une boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="50c23-138">In the **Mail Server** box, type the name of the Windows Server-based server where you created a mailbox.</span></span>  
  
11. <span data-ttu-id="50c23-139">Dans le **schéma d’authentification** boîte, sélectionnez **base**.</span><span class="sxs-lookup"><span data-stu-id="50c23-139">In the **Authentication Scheme** box, select **Basic**.</span></span>  
  
12. <span data-ttu-id="50c23-140">Dans le **mot de passe** zone, cliquez sur la flèche déroulante et tapez le mot de passe pour la boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="50c23-140">In the **Password** box, click the drop-down arrow and type the password for the mailbox.</span></span>  
  
13. <span data-ttu-id="50c23-141">Dans le **nom d’utilisateur** , tapez le nom d’utilisateur complet pour la boîte aux lettres, par exemple  *username@host.domain.toplevel_domain.*</span><span class="sxs-lookup"><span data-stu-id="50c23-141">In the **User Name** box, type the fully qualified user name for the mailbox, for example *username@host.domain.toplevel_domain.*</span></span>  
  
14. <span data-ttu-id="50c23-142">Dans le **fréquence d’interrogation** , tapez **1**, cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="50c23-142">In the **Polling Interval** box, type **1**, click **OK**, and then click **OK** again.</span></span>  
  
## <a name="create-the-send-port-and-destination-folder-on-the-biztalk-server"></a><span data-ttu-id="50c23-143">Création du port d'envoi et du dossier de destination sur le serveur BizTalk</span><span class="sxs-lookup"><span data-stu-id="50c23-143">Create the send port and destination folder on the BizTalk server</span></span>  
 <span data-ttu-id="50c23-144">Suivez ces étapes pour créer le port d'envoi et le dossier de destination sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="50c23-144">Follow these steps to create the send port and destination folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="50c23-145">Créez un dossier sur le système de fichiers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50c23-145">Create a folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] file system.</span></span> <span data-ttu-id="50c23-146">Il s'agit de la destination du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="50c23-146">This will be the destination for the send port.</span></span>  
  
2.  <span data-ttu-id="50c23-147">Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau,** puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="50c23-147">Right-click **Send Ports**, click **New,** then click **Static one-way Send Port.**</span></span>  
  
3.  <span data-ttu-id="50c23-148">Dans le **propriétés de Port d’envoi** boîte de dialogue le **Type de Transport** boîte, sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="50c23-148">In the **Send Port Properties** dialog box, in the **Transport Type** box, select **FILE**.</span></span>  
  
4.  <span data-ttu-id="50c23-149">Dans le **nom** , tapez **SendToFile**.</span><span class="sxs-lookup"><span data-stu-id="50c23-149">In the **Name** box, type **SendToFile**.</span></span>  
  
5.  <span data-ttu-id="50c23-150">Dans le **Transport** , cliquez sur le **configurer** bouton.</span><span class="sxs-lookup"><span data-stu-id="50c23-150">In the **Transport** box, click the **Configure** button.</span></span>  
  
6.  <span data-ttu-id="50c23-151">À côté du **dossier de Destination** , cliquez sur **Parcourir**, sélectionnez le dossier que vous avez créé sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50c23-151">Next to the **Destination folder** box, click **Browse**, select the folder that you created on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="50c23-152">Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50c23-152">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="50c23-153">Dans le **Pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="50c23-153">In the **Send Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
9. <span data-ttu-id="50c23-154">Cliquez sur **Filtres**.</span><span class="sxs-lookup"><span data-stu-id="50c23-154">Click **Filters**.</span></span>  
  
10. <span data-ttu-id="50c23-155">Dans le **propriété** boîte, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="50c23-155">In the **Property** box, select **BTS.ReceivePortName**.</span></span>  
  
11. <span data-ttu-id="50c23-156">Dans le **valeur** , tapez **POP3Receive**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50c23-156">In the **Value** box, type **POP3Receive**, and then click **OK**.</span></span>  
  
## <a name="enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="50c23-157">Activer l’emplacement de réception et de démarrer le port d’envoi</span><span class="sxs-lookup"><span data-stu-id="50c23-157">Enable the receive location and start the send port</span></span>  
 <span data-ttu-id="50c23-158">Procédez comme suit pour activer l'emplacement de réception et démarrer le port d'envoi :</span><span class="sxs-lookup"><span data-stu-id="50c23-158">Follow these steps to enable the receive location and start the send port:</span></span>  
  
1.  <span data-ttu-id="50c23-159">Cliquez sur le **POP3Receive** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="50c23-159">Right-click the **POP3Receive** receive location, and then click **Enable**.</span></span>  
  
2.  <span data-ttu-id="50c23-160">Cliquez sur le **SendToFile** port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="50c23-160">Right-click the **SendToFile** send port, and then click **Start**.</span></span>  
  
 <span data-ttu-id="50c23-161">La prochaine étape consiste à tester l'application en envoyant un message de test à la boîte aux lettres surveillée par l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="50c23-161">The next step is to test the application by sending a test message to the mailbox monitored by the receive location.</span></span>  
  
## <a name="configure-outlook-express-to-send-an-e-mail-message-to-the-mailbox"></a><span data-ttu-id="50c23-162">Configuration d'Outlook Express pour envoyer un message électronique à la boîte aux lettres</span><span class="sxs-lookup"><span data-stu-id="50c23-162">Configure Outlook Express to send an e-mail message to the mailbox</span></span>  
 <span data-ttu-id="50c23-163">Procédez comme suit pour configurer Outlook Express pour envoyer un message électronique à la boîte aux lettres :</span><span class="sxs-lookup"><span data-stu-id="50c23-163">Follow these steps to configure Outlook Express to send an e-mail message to the mailbox:</span></span>  
  
1.  <span data-ttu-id="50c23-164">Cliquez sur **Démarrer**, pointez sur **programmes**, puis cliquez sur **Outlook Express**.</span><span class="sxs-lookup"><span data-stu-id="50c23-164">Click **Start**, point to **Programs**, and then click **Outlook Express**.</span></span>  
  
2.  <span data-ttu-id="50c23-165">Dans Outlook Express, sur le **outils** menu, cliquez sur **comptes**.</span><span class="sxs-lookup"><span data-stu-id="50c23-165">In Outlook Express, on the **Tools** menu, click **Accounts**.</span></span>  
  
3.  <span data-ttu-id="50c23-166">Cliquez sur **ajouter** puis cliquez sur **Mail**.</span><span class="sxs-lookup"><span data-stu-id="50c23-166">Click **Add** and then click **Mail**.</span></span>  
  
4.  <span data-ttu-id="50c23-167">Dans le **nom d’affichage** zone, tapez un nom d’affichage, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="50c23-167">In the **Display name** box, type a display name, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="50c23-168">Dans le **adresse de messagerie Internet** boîte de dialogue le **adresse de messagerie** , tapez **EmailTest @< nom_domaine >**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="50c23-168">In the **Internet E-mail address** dialog box, in the **E-mail address** box, type **EmailTest@<domain_name>**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="50c23-169">Veillez à entrer la valeur appropriée pour *< nom_domaine >*.</span><span class="sxs-lookup"><span data-stu-id="50c23-169">Make sure to enter the appropriate value for *<domain_name>*.</span></span> <span data-ttu-id="50c23-170">Cette valeur doit correspondre au nom du domaine sous lequel cette boîte aux lettres a été créée dans l'interface Administration du service POP3 sur le serveur Windows.</span><span class="sxs-lookup"><span data-stu-id="50c23-170">This value should match the name of the domain under which this mailbox was created in the POP3 Service Administration interface on the Windows server.</span></span>  
  
6.  <span data-ttu-id="50c23-171">Dans le **les noms de serveur de messagerie** boîte de dialogue le **courrier entrant** et **courrier sortant** zones, tapez le nom du serveur ou l’adresse IP du serveur Windows, puis cliquez sur  **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="50c23-171">In the **E-mail Server names** dialog box, in the **Incoming mail** and **Outgoing mail** boxes, type the server name or IP address of the Windows server, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="50c23-172">Dans le **connexion à la messagerie Internet** boîte de dialogue le **nom de compte** , tapez **EmailTest**.</span><span class="sxs-lookup"><span data-stu-id="50c23-172">In the **Internet Mail Logon** dialog box, in the **Account name** box, type **EmailTest**.</span></span>  
  
8.  <span data-ttu-id="50c23-173">Dans le **mot de passe** , tapez le mot de passe du compte EmailTest, sélectionnez le **Mémoriser le mot de passe** , cliquez sur **suivant**, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="50c23-173">In the **Password** box, type the password for the EmailTest account, select the **Remember password** option, click **Next**, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="50c23-174">Cliquez pour sélectionner le compte que vous venez de créer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="50c23-174">Click to select the account that you just created, and then click **Properties**.</span></span>  
  
10. <span data-ttu-id="50c23-175">Dans le **propriétés** boîte de dialogue, cliquez sur le **avancé** onglet, sélectionnez l’option à **laisser un exemplaire des messages sur le serveur**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="50c23-175">In the **Properties** dialog box, click the **Advanced** tab, click to select the option to **Leave a copy of messages on the server**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="50c23-176">Dans le **comptes Internet** boîte de dialogue, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="50c23-176">In the **Internet Accounts** dialog box, click **Close**.</span></span>  
  
12. <span data-ttu-id="50c23-177">Utilisez Outlook Express pour composer un message de test, type **Test** dans les **sujet** champ et le type **EmailTest @< nom_domaine >** dans le **à** champ.</span><span class="sxs-lookup"><span data-stu-id="50c23-177">Use Outlook Express to compose a test message, type **Test** into the **Subject** field, and type **EmailTest@<domain_name>** into the **To** field.</span></span>  
  
13. <span data-ttu-id="50c23-178">Cliquez sur **envoyer** pour envoyer le message de test.</span><span class="sxs-lookup"><span data-stu-id="50c23-178">Click **Send** to send the test message.</span></span> <span data-ttu-id="50c23-179">Pour vous assurer qu’Outlook Express envoie le message de test immédiatement, cliquez sur le **Envoyer/Recev** bouton dans la barre d’outils Outlook Express.</span><span class="sxs-lookup"><span data-stu-id="50c23-179">To ensure that Outlook Express sends the test message immediately, click the **Send/Recv** button in the Outlook Express toolbar.</span></span>  
  
## <a name="view-the-message"></a><span data-ttu-id="50c23-180">Affichage du message</span><span class="sxs-lookup"><span data-stu-id="50c23-180">View the message</span></span>  
 <span data-ttu-id="50c23-181">Procédez comme suit pour afficher le message :</span><span class="sxs-lookup"><span data-stu-id="50c23-181">Follow these steps to view the message:</span></span>  
  
1.  <span data-ttu-id="50c23-182">Utilisez l’Explorateur Windows pour ouvrir le dossier que vous avez spécifié comme le **dossier de Destination** pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="50c23-182">Use Windows Explorer to open the folder that you specified as the **Destination Folder** for the send port.</span></span>  
  
2.  <span data-ttu-id="50c23-183">Double-cliquez sur le document dans le dossier pour afficher le contenu du document dans le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="50c23-183">Double click the document in the folder to view the contents of the document in Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c23-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50c23-184">See Also</span></span>  
 [<span data-ttu-id="50c23-185">Nouveautés de l’adaptateur POP3 ?</span><span class="sxs-lookup"><span data-stu-id="50c23-185">What Is the POP3 Adapter?</span></span>](../core/what-is-the-pop3-adapter.md)