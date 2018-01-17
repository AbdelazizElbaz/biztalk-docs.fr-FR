---
title: "Configurer l’Adaptateurs FileAct et interagir adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3876ff-e8e4-47f4-9ca8-d4dad419ed67
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca2bc3aa739bf6914ea9943d84d58d44b1506323
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="configure-the-fileact-and-interact-adapter"></a><span data-ttu-id="deca4-102">Configurer l’Adaptateurs FileAct et interagir de carte</span><span class="sxs-lookup"><span data-stu-id="deca4-102">Configure the FileAct and InterAct Adapter</span></span>
<span data-ttu-id="deca4-103">Configurer les différents artefacts utilisés par le [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] runtime.</span><span class="sxs-lookup"><span data-stu-id="deca4-103">Configure the different artifacts used by the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] runtime.</span></span> 

  
## <a name="prerequisites"></a><span data-ttu-id="deca4-104">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="deca4-104">Prerequisites</span></span>  
   
-   <span data-ttu-id="deca4-105">Installer le[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deca4-105">Install the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]</span></span>
  
-   <span data-ttu-id="deca4-106">Connectez-vous en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs</span><span class="sxs-lookup"><span data-stu-id="deca4-106">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group</span></span>
  
-   <span data-ttu-id="deca4-107">Vérifiez que SQL Server est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="deca4-107">Confirm SQL Server is running</span></span>
  
## <a name="step-1-configure-the-fileact-and-interact-adapter"></a><span data-ttu-id="deca4-108">Étape 1 : Configurer l’adaptateur FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="deca4-108">Step 1: Configure the FileAct and InterAct adapter</span></span>  
  
1.  <span data-ttu-id="deca4-109">Dans le **Microsoft BizTalk FileAct et Configuration de l’adaptateur interagir** Assistant, accédez à **vue d’ensemble**.</span><span class="sxs-lookup"><span data-stu-id="deca4-109">In the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard, go to **Overview**.</span></span> <span data-ttu-id="deca4-110">Dans le volet gauche, sélectionnez **Runtime** pour configurer les composants d’exécution des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="deca4-110">In the left pane, select **Runtime** to configure the runtime components of the adapters.</span></span>  
  
2.  <span data-ttu-id="deca4-111">Dans **Configuration d’exécution**, sous **compte**, sélectionnez les points de suspension [...] pour entrer le COM ainsi que la configuration pour le mode magasin et le transfert.</span><span class="sxs-lookup"><span data-stu-id="deca4-111">In **Runtime Configuration**, under **Account**, select the ellipsis […] to enter the COM plus configuration for the Store and Forward mode.</span></span>  
  
3.  <span data-ttu-id="deca4-112">Dans **informations d’identification utilisateur**, entrez le nom d’utilisateur (dans le *domaine\nom d’utilisateur* format) et le mot de passe pour le compte utilisé dans le COM plus de la configuration.</span><span class="sxs-lookup"><span data-stu-id="deca4-112">In **User Credentials**, enter the user name (in the *domain\user name* format) and password for the account used in the COM plus configuration.</span></span> <span data-ttu-id="deca4-113">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="deca4-113">Select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deca4-114">A **informations d’identification utilisateur** avertissement s’affiche si le compte que vous avez entré a des privilèges plus élevés à sont recommandées.</span><span class="sxs-lookup"><span data-stu-id="deca4-114">A **User Credentials** warning appears if the account you entered has higher privileges than are recommended.</span></span> <span data-ttu-id="deca4-115">Sélectionnez **Oui** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="deca4-115">Select **Yes** to continue.</span></span>
  
4.  <span data-ttu-id="deca4-116">Sélectionnez **appliquer configuration** pour appliquer la COM + configuration aux adaptateurs FileAct et interagir de carte.</span><span class="sxs-lookup"><span data-stu-id="deca4-116">Select **Apply configuration** to apply the COM plus configuration to the FileAct and InterAct Adapter.</span></span>  
  
5.  <span data-ttu-id="deca4-117">Dans le **Résumé**, passez en revue, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="deca4-117">In the **Summary**, review, and select **Next**.</span></span>  
  
6.  <span data-ttu-id="deca4-118">Une fois la configuration terminée, passez en revue la liste des composants.</span><span class="sxs-lookup"><span data-stu-id="deca4-118">When the configuration completes, review the list of components.</span></span> <span data-ttu-id="deca4-119">Une coche signifie que le composant est correctement configuré.</span><span class="sxs-lookup"><span data-stu-id="deca4-119">A check mark means that the component is configured successfully.</span></span> <span data-ttu-id="deca4-120">Un « X » signifie qu’il existe un problème avec ce composant.</span><span class="sxs-lookup"><span data-stu-id="deca4-120">An "X" means that there is a problem with that component.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deca4-121">Utilisez le **Logfile** lien pour afficher les événements de configuration.</span><span class="sxs-lookup"><span data-stu-id="deca4-121">Use the **Logfile** link to view the configuration events.</span></span>  
  
7.  <span data-ttu-id="deca4-122">Sélectionnez **Terminer** pour terminer la configuration.</span><span class="sxs-lookup"><span data-stu-id="deca4-122">Select **Finish** to complete the configuration.</span></span> <span data-ttu-id="deca4-123">Le **vue d’ensemble** affiche l’état actuel de la configuration pour les composants d’exécution.</span><span class="sxs-lookup"><span data-stu-id="deca4-123">The **Overview** shows the current configuration status for the Runtime components.</span></span>  

<span data-ttu-id="deca4-124">Ensuite, créez l’hôte et les instances d’hôte pour exécuter ces adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="deca4-124">Next, create the host and host instances to run these adapters.</span></span>

## <a name="step-2-create-the-host-and-host-instances"></a><span data-ttu-id="deca4-125">Étape 2 : Créer l’hôte et les instances d’hôte</span><span class="sxs-lookup"><span data-stu-id="deca4-125">Step 2: Create the host and host instances</span></span>

<span data-ttu-id="deca4-126">Nous vous recommandons de créer un hôte dédié de l’adaptateur FileAct et un hôte dédié distinct pour l’adaptateur InterAct.</span><span class="sxs-lookup"><span data-stu-id="deca4-126">We recommend that you create a dedicated host for the FileAct adapter and a separate dedicated host for the InterAct adapter.</span></span> <span data-ttu-id="deca4-127">Pour chaque adaptateur, créez au moins une instance de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="deca4-127">For each adapter, create at least one host instance.</span></span>  

<span data-ttu-id="deca4-128">[La gestion des hôtes BizTalk et les Instances d’hôte](../../core/managing-biztalk-hosts-and-host-instances.md) répertorient les étapes pour créer des ordinateurs hôtes et les instances d’hôte.</span><span class="sxs-lookup"><span data-stu-id="deca4-128">[Managing BizTalk Hosts and Host Instances](../../core/managing-biztalk-hosts-and-host-instances.md) list the steps to create hosts and host instances.</span></span> 

<span data-ttu-id="deca4-129">Une fois créé, l’étape suivante consiste à ajouter le Gestionnaire d’envoi, utilisez le partenaire de Message Client que vous avez créé dans la passerelle de Alliance SWIFT (trous).</span><span class="sxs-lookup"><span data-stu-id="deca4-129">Once created, the next step is to add the send handler, and use the Client Message Partner you created in the SWIFT Alliance Gateway (SAG).</span></span>

## <a name="step-3-create-the-send-handler"></a><span data-ttu-id="deca4-130">Étape 3 : Créer le Gestionnaire d’envoi</span><span class="sxs-lookup"><span data-stu-id="deca4-130">Step 3: Create the send handler</span></span>

<span data-ttu-id="deca4-131">Vous utilisez le FileAct et InterAct envoyez propriétés du gestionnaire en tant que l’envoi les valeurs de configuration de port, si les propriétés ne sont pas définies sur le FileAct individuel ou un port d’envoi interagir.</span><span class="sxs-lookup"><span data-stu-id="deca4-131">You use the FileAct and InterAct send handler properties as the send port configuration values, if the properties are not set on the individual FileAct or InterAct send port.</span></span> 
  
1.  <span data-ttu-id="deca4-132">Dans le **Administration de BizTalk Server** de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="deca4-132">In the **BizTalk Server Administration** console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="deca4-133">Sélectionnez le **FileAct** ou **interagir** carte.</span><span class="sxs-lookup"><span data-stu-id="deca4-133">Select the **FileAct** or **InterAct** adapter.</span></span> <span data-ttu-id="deca4-134">Dans le volet droit, double-cliquez sur le Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="deca4-134">In the right pane, double-click the send handler.</span></span>  
  
3.  <span data-ttu-id="deca4-135">Dans le **nom d’hôte** liste déroulante, sélectionnez l’hôte que vous avez créé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="deca4-135">In the **Host name** drop-down list, select the host you created in the previous section.</span></span> <span data-ttu-id="deca4-136">Puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="deca4-136">Then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="deca4-137">Dans le **propriétés du Transport**, sélectionnez le **Argument** propriété, puis entrez l’argument suivant en tant que :</span><span class="sxs-lookup"><span data-stu-id="deca4-137">In the **Transport Properties**, select the **Argument** property, and enter the following argument as:</span></span>  
  
     `-SagMessagePartner <Client Message Partner created in SAG\>`
  
    > [!NOTE]
    >  <span data-ttu-id="deca4-138">Remplacez <`Client Message Partner created in SAG`> avec le nom du partenaire de message client.</span><span class="sxs-lookup"><span data-stu-id="deca4-138">Replace <`Client Message Partner created in SAG`> with the name of the client message partner.</span></span> <span data-ttu-id="deca4-139">Laissez les valeurs par défaut pour le Mode de chiffrement, FACrypto Mode et les propriétés LogMessages.</span><span class="sxs-lookup"><span data-stu-id="deca4-139">Leave the default values for the Crypto Mode, FACrypto Mode, and LogMessages properties.</span></span>  
  
5.  <span data-ttu-id="deca4-140">Sélectionnez **OK** pour enregistrer vos modifications, puis fermez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="deca4-140">Select **OK** to save your changes, and then to close the properties window.</span></span> 
  
6.  <span data-ttu-id="deca4-141">Sous **paramètres de plateforme**, sélectionnez **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="deca4-141">Under **Platform Settings**, select **Host Instances**.</span></span>  
  
7. <span data-ttu-id="deca4-142">Redémarrez les instances d’hôte :</span><span class="sxs-lookup"><span data-stu-id="deca4-142">Restart the host instances:</span></span> 

  - <span data-ttu-id="deca4-143">Cliquez sur l’instance d’hôte FileAct, et **redémarrer**</span><span class="sxs-lookup"><span data-stu-id="deca4-143">Right-click the FileAct host instance, and **Restart**</span></span>
  - <span data-ttu-id="deca4-144">Cliquez sur l’instance d’hôte interagir, et **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="deca4-144">Right-click the InterAct host instance, and **Restart**.</span></span>  

<span data-ttu-id="deca4-145">Ensuite, entrez les partenaires de message de serveur dans le paramfile SWIFTNet pour activer la FileAct et InterAct des adaptateurs de réception.</span><span class="sxs-lookup"><span data-stu-id="deca4-145">Next, enter the server message partners in the SWIFTNet paramfile to enable the FileAct and InterAct receive adapters.</span></span>
  
## <a name="step-4-configure-the-swiftnet-param-file"></a><span data-ttu-id="deca4-146">Étape 4 : Configurer le fichier param SWIFTNet</span><span class="sxs-lookup"><span data-stu-id="deca4-146">Step 4: Configure the SWIFTNet param file</span></span>

<span data-ttu-id="deca4-147">Pour activer les adaptateurs FileAct et InterAct adaptateurs de réception pour initialiser les valeurs, le message de serveur partenaires créés dans les trous doivent être entrés dans le paramfile SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="deca4-147">To enable the FileAct and InterAct receive adapters to initialize with the values, the Server message partners created in SAG must be entered in the SWIFTNet paramfile.</span></span> <span data-ttu-id="deca4-148">Le paramfile se trouve généralement dans `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`.</span><span class="sxs-lookup"><span data-stu-id="deca4-148">The paramfile is typically located in `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`.</span></span> <span data-ttu-id="deca4-149">Après avoir configuré le paramfile, démarrer **SnlReceiver.exe**.</span><span class="sxs-lookup"><span data-stu-id="deca4-149">After you configure the paramfile, start **SnlReceiver.exe**.</span></span>  
  
1. <span data-ttu-id="deca4-150">Ouvrez le **SWIFTNet paramfile**.</span><span class="sxs-lookup"><span data-stu-id="deca4-150">Open the **SWIFTNet paramfile**.</span></span> <span data-ttu-id="deca4-151">Dans l’emplacement marqué avec « \*\*\* « ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="deca4-151">In the location marked with "\*\*\*" add the following.</span></span> <span data-ttu-id="deca4-152">Notez que la `AdapterType` valeur peut être `Interact` ou `Fileact`.</span><span class="sxs-lookup"><span data-stu-id="deca4-152">Note that the `AdapterType` value can be `Interact` or `Fileact`.</span></span>  
  
     ```spawn "snlreceiver -SagMessagePartner <Server MessagePartnerName\> -AdapterMode <AdapterType\>"```  
       
  
   ```  
    username:snlowner  
    subsystem_name:SampleSubsystem  
    #subsystem_group: SampleSubsystem  
    #subsystem_dependency:Support,Swarm  
    subsystem_nature:critical  
    subsystem_start:  
    ***  
    *END  
    subsystem_stop:  
    *KILL9:snlreceiver  
    *END  
    subsystem_status:  
    *NB:1:snlreceiver  
    *END  
    start_event:SNL001:subsystem SampleSubsystem is up  
    stop_event:SNL002:subsystem SampleSubsystem is down  
   ```  
  
   > [!NOTE]
    >  <span data-ttu-id="deca4-153">Avant de commencer, SNLreceiver, activer les ports de réception de la carte que vous utilisez (FileAct ou interagir).</span><span class="sxs-lookup"><span data-stu-id="deca4-153">Before you start SNLreceiver, enable the receive ports for the adapter you are using (FileAct or InterAct).</span></span>  
  
2. <span data-ttu-id="deca4-154">Démarrer et arrêter les SnlReceiver.exe :</span><span class="sxs-lookup"><span data-stu-id="deca4-154">Start and stop SnlReceiver.exe:</span></span>

    1.  <span data-ttu-id="deca4-155">Sur le bureau, sélectionnez le **API distant** icône pour ouvrir l’invite de commandes à distance d’API.</span><span class="sxs-lookup"><span data-stu-id="deca4-155">On the desktop, select the **Remote API** icon to open the Remote API command prompt.</span></span>  
  
    2.  <span data-ttu-id="deca4-156">À l’invite de commandes, tapez `Swiftnet start`.</span><span class="sxs-lookup"><span data-stu-id="deca4-156">At the command prompt, type `Swiftnet start`.</span></span> <span data-ttu-id="deca4-157">Sélectionnez l’entrée pour démarrer SnlReceiver.exe.</span><span class="sxs-lookup"><span data-stu-id="deca4-157">Select ENTER to start SnlReceiver.exe.</span></span>  
  
    3.  <span data-ttu-id="deca4-158">À l’invite de commandes, tapez `Swiftnet stop`.</span><span class="sxs-lookup"><span data-stu-id="deca4-158">At the command prompt, type `Swiftnet stop`.</span></span> <span data-ttu-id="deca4-159">Sélectionnez l’entrée pour arrêter SnlReceiver.exe.</span><span class="sxs-lookup"><span data-stu-id="deca4-159">Select ENTER to stop SnlReceiver.exe.</span></span>  

  
<span data-ttu-id="deca4-160">Ensuite, mettez à jour le fichier **autoexec.bat** pour définir des variables d’environnement la SWIFT.</span><span class="sxs-lookup"><span data-stu-id="deca4-160">Next, update the file **autoexec.bat** to set the SWIFT environment variables.</span></span>

## <a name="step-5-update-autoexecbat-to-configure-the-receive-adapters"></a><span data-ttu-id="deca4-161">Étape 5 : Mise à jour autoexec.bat pour configurer les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="deca4-161">Step 5: Update autoexec.bat to configure the receive adapters</span></span>

<span data-ttu-id="deca4-162">Mise à jour la **autoexec.bat** fichier pour définir des variables d’environnement la SWIFT sur l’ordinateur où vous avez installé le [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] des adaptateurs de réception.</span><span class="sxs-lookup"><span data-stu-id="deca4-162">Update the **autoexec.bat** file to set the SWIFT environment variables on the computer where you installed the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] receive adapters.</span></span> <span data-ttu-id="deca4-163">Les variables d’environnement sont générés à partir du système qui a installé dans le chemin de l’adaptateur de réception `c:\SWIFTAlliance` avec une instance de l’adaptateur de réception nommé **Ra1**.</span><span class="sxs-lookup"><span data-stu-id="deca4-163">The environment variables are generated from the system that has the receive adapter installed in the path `c:\SWIFTAlliance` with an instance of the receive adapter named **Ra1**.</span></span> <span data-ttu-id="deca4-164">Mettre à jour les variables d’environnement SWIFT appropriée pour votre configuration.</span><span class="sxs-lookup"><span data-stu-id="deca4-164">Update the SWIFT environment variables appropriately for your configuration.</span></span>  
  
 <span data-ttu-id="deca4-165">Voici un exemple de fichier autoexe.bat :</span><span class="sxs-lookup"><span data-stu-id="deca4-165">The following is a sample of the autoexe.bat file:</span></span>
  
```  
SET COMPUTERNAME=<Machine Name>  
SET GENLOG_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET GENUTIL_DIR=C:\SWIFTAlliance\RA\bin  
SET HOMEDRIVE=C:  
SET LOGONSERVER=\\SERVERNAME  
SET OSA_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET OSA_INSTANCE=Ra1  
SET PKIEXECDIR=C:\SWIFTAlliance\RA  
SET SAGRA_HOME=C:\SWIFTAlliance\RA  
SET SESSIONNAME=RDP-Tcp#1  
SET SLP_ENV=DEFAULT  
SET SLP_FILE=server.slp  
SET SNL_DOMAIN_NAME=Ra1  
SET SPK_DATA_DIR=C:\SWIFTAlliance\RA\data\pki  
SET SWNET_BIN_PATH=C:\SWIFTAlliance\RA\Ra1\bin  
SET SWNET_CFG_PATH=C:\SWIFTAlliance\RA\Ra1\cfg  
SET SWNET_HOME=C:\SWIFTAlliance\RA  
SET SWNET_HOST=HOSTNAME  
SET SWNET_INST=Ra1  
SET SWNET_LOG_PATH=C:\SWIFTAlliance\RA\Ra1\log  
SET SWNET_SLP_PATH=C:\SWIFTAlliance\RA\data\  
SET SWNET_VERSION=5.0.20  
SET SWTRACE=C:\SWIFTAlliance\RA\Ra1\log  
SET Path=%PATH%;C:\SWIFTAlliance\RA\bin  
SET Path=%PATH%;C:\SWIFTAlliance\RA\lib  
  
```  
  
## <a name="see-some-examples"></a><span data-ttu-id="deca4-166">Voir des exemples</span><span class="sxs-lookup"><span data-stu-id="deca4-166">See some examples</span></span>
<span data-ttu-id="deca4-167">Pour obtenir des exemples de messages des adaptateurs FileAct et InterAct, consultez [exemple interagir et les Messages de FileAct](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md).</span><span class="sxs-lookup"><span data-stu-id="deca4-167">For examples of FileAct and InterAct messages, see [Sample InterAct and FileAct Messages](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deca4-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deca4-168">See Also</span></span>  

[<span data-ttu-id="deca4-169">Installer les adaptateurs FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="deca4-169">Install the FileAct and InterAct Adapter</span></span>](../../adapters-and-accelerators/fileact-interact/install-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="deca4-170">Désinstaller ou réparer l’adaptateur FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="deca4-170">Uninstall or repair the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="deca4-171">Découvrir les problèmes d’installation connus</span><span class="sxs-lookup"><span data-stu-id="deca4-171">Read the installation known issues</span></span>](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
