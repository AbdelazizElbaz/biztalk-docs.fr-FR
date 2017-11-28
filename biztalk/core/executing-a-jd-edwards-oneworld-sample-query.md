---
title: "Exécutez JD Edwards OneWorld requête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b060d383-a2df-472f-90cc-e79078b0bcfd
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58e06eb1b606217aea6fe5e40ac645a2eaf623c2
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="execute-a-jd-edwards-oneworld-sample-query"></a><span data-ttu-id="1b5ce-102">Exécuter une requête d’exemple de OneWorld de JD Edwards</span><span class="sxs-lookup"><span data-stu-id="1b5ce-102">Execute a JD Edwards OneWorld Sample Query</span></span>
<span data-ttu-id="1b5ce-103">Le système JD Edwards OneWorld (JDEOW) est accessible à partir d'un système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-103">The JD Edwards OneWorld (JDEOW) system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="1b5ce-104">Cette carte est incluse avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b5ce-104">This adapter is included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>
  
 <span data-ttu-id="1b5ce-105">Il s'agit de la deuxième partie de l'atelier JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-105">This is the second part of the JD Edwards OneWorld lab work.</span></span> <span data-ttu-id="1b5ce-106">Au cours de la première partie (Atelier 1), vous avez consulté les données du système JD Edwards OneWorld sans utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou d'autres technologies Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-106">In the first part (Lab 1), you manually accessed data on the JD Edwards OneWorld system without the assistance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or other Microsoft technologies.</span></span> <span data-ttu-id="1b5ce-107">Dans la deuxième partie (Atelier 2), vous allez créer une orchestration BizTalk au sein d'un projet BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b5ce-107">In this part (Lab 2), you will create a BizTalk orchestration as part of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project.</span></span> <span data-ttu-id="1b5ce-108">Vous allez configurer les ports de cette orchestration de manière à ce qu'ils utilisent l'adaptateur JD Edwards OneWorld pour extraire des données du système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-108">You will configure ports on this orchestration to use the JD Edwards OneWorld adapter to get data from a JD Edwards OneWorld system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1b5ce-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="1b5ce-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="1b5ce-110">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b5ce-110">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>
  
-   <span data-ttu-id="1b5ce-111">Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b5ce-111">Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]</span></span> 
  
-   <span data-ttu-id="1b5ce-112">Logiciel client JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="1b5ce-112">JD Edwards OneWorld Client software</span></span>  
  
-   <span data-ttu-id="1b5ce-113">Connectivité réseau à un système JD Edwards OneWorld sur un autre serveur</span><span class="sxs-lookup"><span data-stu-id="1b5ce-113">Network connectivity to a JD Edwards OneWorld system on another server</span></span>  
  
-   <span data-ttu-id="1b5ce-114">Adaptateurs Microsoft BizTalk pour les applications d'entreprise</span><span class="sxs-lookup"><span data-stu-id="1b5ce-114">Microsoft BizTalk Adapters for Enterprise Applications</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b5ce-115">Consultez [installer et configurer les adaptateurs pour les applications d’entreprise](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) pour des informations de configuration de la clé pour les adaptateurs JD Edwards, PeopleSoft et TIBCO.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-115">See [Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) for key configuration information for the JD Edwards, PeopleSoft, and TIBCO adapters.</span></span>  
  
## <a name="lab-2---executing-a-jd-edwards-oneworld-sample-query"></a><span data-ttu-id="1b5ce-116">Atelier 2 : l’exécution de JD Edwards OneWorld requête</span><span class="sxs-lookup"><span data-stu-id="1b5ce-116">Lab 2 - Executing a JD Edwards OneWorld Sample Query</span></span>  
 <span data-ttu-id="1b5ce-117">Dans cet atelier, vous allez exécuter un **obtenir** opération sur le système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-117">In this lab, you will execute a **Get** operation against the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-118">Vous allez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-118">Specifically you will perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1b5ce-119">vérification des composants requis pour JD Edwards OneWorld ;</span><span class="sxs-lookup"><span data-stu-id="1b5ce-119">Verify the JD Edwards OneWorld prerequisites</span></span>  
  
-   <span data-ttu-id="1b5ce-120">configuration d'un port d'envoi JD Edwards OneWorld dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="1b5ce-120">Set up a JD Edwards OneWorld send port in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="1b5ce-121">création d'un projet d'orchestration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="1b5ce-121">Create a BizTalk orchestration project</span></span>  
  
-   <span data-ttu-id="1b5ce-122">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="1b5ce-122">Build and deploy the project</span></span>  
  
-   <span data-ttu-id="1b5ce-123">test de l'application et affichage de la sortie XML.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-123">Test the application and view the XML output</span></span>  
  
 <span data-ttu-id="1b5ce-124">Vous allez utiliser l'adaptateur JD Edwards OneWorld pour accéder aux données du système JD Edwards OneWorld à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b5ce-124">You will use the JD Edwards OneWorld adapter to access data on the JD Edwards OneWorld system from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1b5ce-125">Cet adaptateur permet de traiter les objets JD Edwards OneWorld à l'aide de requêtes et de réponses exécutées par une orchestration.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-125">This adapter enables the processing of JD Edwards OneWorld objects by using requests and responses executed by an orchestration.</span></span> <span data-ttu-id="1b5ce-126">De nombreuses méthodes sont disponibles pour un objet de schéma.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-126">Many methods are available for a schema object.</span></span> <span data-ttu-id="1b5ce-127">Cet atelier montre comment utiliser le **Address Book MBF** (méthode).</span><span class="sxs-lookup"><span data-stu-id="1b5ce-127">This lab demonstrates how to use the **Address Book MBF** method.</span></span>  
  
 <span data-ttu-id="1b5ce-128">Avant d'exécuter une requête de service, vous devez créer des schémas associés aux requêtes et aux réponses de service pour l'objet JD Edwards OneWorld spécifique.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-128">Before running a service request, you must create service request and response schemas for the specific JD Edwards OneWorld object.</span></span> <span data-ttu-id="1b5ce-129">L'Assistant Ajouter les éléments générés/Ajout d'adaptateur crée ces schémas en interrogeant directement l'objet de métadonnées de support dans JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-129">The Add Generated Items/Add Adapter Wizard creates these schemas by directly interrogating the supporting metadata object in JD Edwards OneWorld.</span></span> <span data-ttu-id="1b5ce-130">Cet atelier présente les étapes requises pour créer des schémas pour le **Address Book MBF** (méthode) et de traiter une requête.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-130">This lab illustrates the steps required to create schemas for the **Address Book MBF** method and to process a query.</span></span>  
  
## <a name="step-1-verify-the-jd-edwards-oneworld-prerequisites"></a><span data-ttu-id="1b5ce-131">Étape 1 : Vérifier les conditions préalables de JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="1b5ce-131">Step 1: Verify the JD Edwards OneWorld prerequisites</span></span>  
 <span data-ttu-id="1b5ce-132">Avant de commencer la création d'un projet BizTalk à des fins d'utilisation avec l'adaptateur JD Edwards OneWorld, vous devez vous assurer que les fichiers et l'adaptateur permettant d'accéder au système JD Edwards OneWorld sont configurés correctement.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-132">Before you start creating a BizTalk project for use with the JD Edwards OneWorld adapter, you need to be sure the files and the adapter are set up correctly to access the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-133">Sur l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'adaptateur JD Edwards OneWorld communique avec le système JD Edwards OneWorld à l'aide de l'interface Java.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-133">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, the JD Edwards OneWorld adapter communicates with the JD Edwards OneWorld system by using the Java interface.</span></span>    

1. <span data-ttu-id="1b5ce-134">Quatre fichiers sont nécessaires pour l’accès de l’interface appropriée pour un système JD Edwards OneWorld à l’aide de l’adaptateur JD Edwards OneWorld : Connector.jar, Kernel.jar, BTSLIBinterop.jar et JDEJAccess.jar.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-134">Four files are necessary for proper interface access to a JD Edwards OneWorld system using the JD Edwards OneWorld adapter: Connector.jar, Kernel.jar, BTSLIBinterop.jar, and JDEJAccess.jar.</span></span>  
  
    -   <span data-ttu-id="1b5ce-135">Les fichiers Connector.jar et Kernel.jar sont fournis avec le système JD Edwards OneWorld et sont obtenus auprès d'un administrateur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-135">The Connector.jar and Kernel.jar files come with the JD Edwards OneWorld system and are obtained from a JD Edwards OneWorld administrator.</span></span> <span data-ttu-id="1b5ce-136">Ces fichiers se trouvent dans le dossier C:\JDEOWJars.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-136">These files are located in the C:\JDEOWJars folder.</span></span>  
  
    -   <span data-ttu-id="1b5ce-137">Le fichier BTSLIBinterop.jar est généré par le système JD Edwards OneWorld en suivant les instructions indiquées dans le guide d'installation associé aux adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-137">The BTSLIBinterop.jar file is generated by the JD Edwards OneWorld system by following the instructions included in the Installation Guide for the adapters.</span></span> <span data-ttu-id="1b5ce-138">Il se trouve dans le dossier C:\JDEOWJars.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-138">This file is located in the C:\JDEOWJars folder.</span></span>  
  
    -   <span data-ttu-id="1b5ce-139">Le fichier JDEJAccess.jar fait partie de l'adaptateur JDEOW et est inclus dans l'installation de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-139">The JDEJAccess.jar file is a part of the JDEOW adapter and is included with the installation of the adapter.</span></span> <span data-ttu-id="1b5ce-140">Par défaut, il se trouve dans le C:\Program Files\Microsoft BizTalk Adapters pour applications\j.d d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-140">By default, it is located in the C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D.</span></span> <span data-ttu-id="1b5ce-141">Dossier de \Classes Edwards.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-141">Edwards OneWorld®\Classes folder.</span></span>  
  
2. <span data-ttu-id="1b5ce-142">Confirmer la Connector.jar, Kernel.jar, et BTSLIBinterop.jar fichiers existent sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur dans le dossier C:\JDEOWJars.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-142">Confirm the Connector.jar, Kernel.jar, and BTSLIBinterop.jar files exist on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer in the C:\JDEOWJars folder.</span></span>  
  
3. <span data-ttu-id="1b5ce-143">Vérifiez que le fichier JDEJAccess.jar existe sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur dans le C:\Program Files\Microsoft BizTalk Adapters pour applications\j.d d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-143">Confirm the JDEJAccess.jar file exists on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer in the C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D.</span></span> <span data-ttu-id="1b5ce-144">Edwards OneWorld\Classes dossier.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-144">Edwards OneWorld\Classes folder.</span></span>  
  
## <a name="step-2-configure-biztalk-send-ports"></a><span data-ttu-id="1b5ce-145">Étape 2 : Configurer les ports d’envoi BizTalk</span><span class="sxs-lookup"><span data-stu-id="1b5ce-145">Step 2: Configure BizTalk send ports</span></span>  
<span data-ttu-id="1b5ce-146">Ensuite, vérifiez que l’adaptateur JD Edwards OneWorld est installé et créer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-146">Next, verify that the JD Edwards OneWorld adapter is installed, and create the send port.</span></span>  

1.  <span data-ttu-id="1b5ce-147">Ouvrez **Administration de BizTalk Server**, développez **racine de la Console**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, Développez **paramètres de plateforme**, puis développez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-147">Open **BizTalk Server Administration**, expand **Console Root**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
    <span data-ttu-id="1b5ce-148">Confirmer la **JDE_OneWorld** carte est répertorié.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-148">Confirm the **JDE_OneWorld** adapter is listed.</span></span> <span data-ttu-id="1b5ce-149">Si l’adaptateur JD Edwards OneWorld n’est pas installé, installez les adaptateurs BizTalk pour les Applications d’entreprise (voir la section « Conditions préalables » plus haut).</span><span class="sxs-lookup"><span data-stu-id="1b5ce-149">If the JD Edwards OneWorld adapter is not installed, install the BizTalk Adapters for Enterprise Applications (see the earlier "Prerequisites" section).</span></span> <span data-ttu-id="1b5ce-150">Une fois que les adaptateurs sont installés, cliquez sur **cartes** puis cliquez sur **nouveau - adaptateur** pour installer l’adaptateur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-150">After the adapters are installed, right-click **Adapters** and then click **New - Adapter** to install the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="1b5ce-151">Redémarrez l’instance d’hôte pour que cela prenne effet.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-151">Restart the host instance for this to take effect.</span></span>  
  
2. <span data-ttu-id="1b5ce-152">Développez **Applications**, puis développez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-152">Expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="1b5ce-153">Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**. Pour ces champs, entrez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-153">Right-click **Send Ports**, click **New**, and then click **Static Solicit-Response Send Port**.Enter the following values for these fields:</span></span>  
  
    1.  <span data-ttu-id="1b5ce-154">**Nom :**  `JDE_OneWorldPort`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-154">**Name:**  `JDE_OneWorldPort`</span></span>  
  
    2.  <span data-ttu-id="1b5ce-155">**Type :**  `JDE_OneWorld`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-155">**Type:**  `JDE_OneWorld`</span></span>  
  
    3.  <span data-ttu-id="1b5ce-156">**Gestionnaire d’envoi :**  `BizTalkServerApplication`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-156">**Send handler:**  `BizTalkServerApplication`</span></span>  
  
    4.  <span data-ttu-id="1b5ce-157">**Pipeline d’envoi :**  `XMLTransmit`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-157">**Send pipeline:**  `XMLTransmit`</span></span>  
  
    5.  <span data-ttu-id="1b5ce-158">**Pipeline de réception :**  `XMLReceive`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-158">**Receive pipeline:**  `XMLReceive`</span></span>  
  
4.  <span data-ttu-id="1b5ce-159">Cliquez sur **Configurer**, puis entrez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-159">Click **Configure**, and then enter the following property values:</span></span>  
  
    1.  <span data-ttu-id="1b5ce-160">**Hôte :** \<Entrez votre nom d’hôte JDEOW ></span><span class="sxs-lookup"><span data-stu-id="1b5ce-160">**Host:** \<enter your JDEOW host name></span></span>  
  
    2.  <span data-ttu-id="1b5ce-161">**JAVA_HOME :**`C:\j2sdk1.4.2_08`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-161">**JAVA_HOME:** `C:\j2sdk1.4.2_08`</span></span>  
  
    3.  <span data-ttu-id="1b5ce-162">**Environnement JDEdwards :** \<Entrez votre environnement JDEOW ></span><span class="sxs-lookup"><span data-stu-id="1b5ce-162">**JDEdwards Environment:** \<enter your JDEOW environment></span></span>  
  
    4.  <span data-ttu-id="1b5ce-163">**Fichiers JAR JDEdwards :** \<Entrez le chemin d’accès complet des fichiers JAR ></span><span class="sxs-lookup"><span data-stu-id="1b5ce-163">**JDEdwards JAR files:** \<enter full path of JAR files></span></span>  
  
         `C:\JDEOWJars\BTSLIBInterop.jar; C:\JDEOWJars\Connector.jar; C:\JDEOWJars\Kernel.jar;C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D. Edwards OneWorld®\Classes\JDEJAccess.jar`  
  
    5.  <span data-ttu-id="1b5ce-164">**Mot de passe :** utilisez la liste déroulante, puis entrez votre mot de passe JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-164">**Password:** Use the drop-down list and then enter your JD Edwards OneWorld password.</span></span>  
  
    6.  <span data-ttu-id="1b5ce-165">**Port :**  `6009`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-165">**Port:**  `6009`</span></span>  
  
    7.  <span data-ttu-id="1b5ce-166">**Nom d’utilisateur :** \<Entrez votre nom d’utilisateur JD Edwards ></span><span class="sxs-lookup"><span data-stu-id="1b5ce-166">**User Name:** \<enter your JD Edwards User Name></span></span>  
  
     ![](../core/media/jdeow-transportproperties-configurebutton.gif "JDEOW_TransportProperties_ConfigureButton")  
  
5.  <span data-ttu-id="1b5ce-167">Sélectionnez **OK** pour fermer la **propriétés de Port d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-167">Select **OK** to close the **Send Port Properties**.</span></span>  
  
## <a name="step-3-create-a-biztalk-orchestration-project"></a><span data-ttu-id="1b5ce-168">Étape 3 : Créer un projet d’Orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="1b5ce-168">Step 3: Create a BizTalk Orchestration Project</span></span>  
<span data-ttu-id="1b5ce-169">Ensuite, créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]et configurer une orchestration dans le projet pour gérer les communications entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-169">Next, create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and configure an orchestration in the project to handle communication between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-170">Vous allez ajouter des ports d'envoi et de réception, créer le projet, puis le déployer.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-170">You will add send and receive ports, build the project, and then deploy the project.</span></span>  

  
1.  <span data-ttu-id="1b5ce-171">Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]et créer un nouveau projet BizTalk dans le dossier C:\LABS.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-171">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and create a new BizTalk project in the C:\LABS folder.</span></span> <span data-ttu-id="1b5ce-172">Dans le menu **Fichier** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-172">On the **File** menu, click **New**.</span></span> <span data-ttu-id="1b5ce-173">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-173">The **New Project** dialog box appears.</span></span> <span data-ttu-id="1b5ce-174">Dans la boîte de dialogue **Modèles** , sélectionnez **Projet BizTalk Server vide**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-174">In the **Templates** section, select **Empty BizTalk Server project.**</span></span> <span data-ttu-id="1b5ce-175">Entrez `JDE_OW_Test` comme le nom unique du projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-175">Enter `JDE_OW_Test` as the unique project name, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="1b5ce-176">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter**, puis sur **Ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-176">In Solution Explorer, right-click the project, click **Add**, and then click **Add Generated Items**.</span></span> <span data-ttu-id="1b5ce-177">Dans le volet des catégories, sélectionnez **ajouter les métadonnées de l’adaptateur**, dans le volet Modèles, sélectionnez **ajouter les métadonnées de l’adaptateur**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-177">In the Categories pane, select **Add Adapter Metadata**, in the Templates pane, select **Add Adapter Metadata**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="1b5ce-178">Dans l’Assistant Ajout d’adaptateur, sélectionnez le **JD Edwards OneWorld** carte, sélectionnez le **JDE_OneWorldPort** port d’envoi qui vous avez créé dans la procédure précédente, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-178">In the Add Adapter Wizard, select the **JD Edwards OneWorld** adapter, select the **JDE_OneWorldPort** send port that you created in the preceding procedure, and then click **Next**.</span></span>  
  
     ![](../core/media/jdeow-addadapterwizardselectadapter.gif "JDEOW_AddAdapterWizardSelectAdapter")  
  
4.  <span data-ttu-id="1b5ce-179">Sur le **sélectionner les Services à importer** page, ouvrez **JD Edwards OneWorld**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-179">On the **Select Services to Import** page, open **JD Edwards OneWorld**.</span></span> <span data-ttu-id="1b5ce-180">Le système JDEOW est contacté via l'adaptateur à l'aide du programme BrowsingAgent.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-180">The JDEOW system is contacted through the adapter by using the BrowsingAgent program.</span></span> <span data-ttu-id="1b5ce-181">BrowsingAgent renvoie les services suivants.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-181">The BrowsingAgent returns the following services.</span></span>  
  
     ![](../core/media/jdeow-callbsfn.gif "JDEOW_CALLBSFN")  
  
5.  <span data-ttu-id="1b5ce-182">Développez **CALLBSFN** et faites défiler jusqu'à **N0100041 - Address Book MBF**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-182">Expand **CALLBSFN** and scroll down to **N0100041 - Address Book MBF**.</span></span> <span data-ttu-id="1b5ce-183">Sélectionnez N0100041, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-183">Select N0100041 and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="1b5ce-184">L'Explorateur de solutions inclut une nouvelle orchestration BizTalk comprenant deux nouveaux fichiers de schémas associés.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-184">In Solution Explorer, there is a new BizTalk orchestration with two new associated schema files.</span></span> <span data-ttu-id="1b5ce-185">Ces derniers sont créés par l'Assistant Ajout d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-185">These files are created by the Add Adapter Wizard.</span></span> <span data-ttu-id="1b5ce-186">Double-cliquez sur le fichier **BizTalk Orchestration.odx** pour ouvrir l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-186">Double-click the **BizTalk Orchestration.odx** file to open the orchestration.</span></span>  
  
     ![](../core/media/jdeow-solution-explorer-jde-ow-test-schemas.gif "JDEOW_Solution_Explorer_JDE_OW_TEST_Schemas")  
  
 <span data-ttu-id="1b5ce-187">Celle-ci accepte comme entrée en provenance de l'adaptateur FILE un fichier XML mis en forme pour le système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-187">This orchestration accepts as input from the File adapter an XML file formatted for the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-188">L'orchestration fait appel à l'adaptateur JD Edwards OneWorld pour envoyer le fichier XML au système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-188">The orchestration uses the JD Edwards OneWorld adapter to send the XML file to the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-189">JD Edwards OneWorld traite la requête et génère un fichier XML de sortie qui contient les résultats.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-189">JD Edwards OneWorld processes the query and generates an output XML file containing the results.</span></span> <span data-ttu-id="1b5ce-190">Ce fichier XML est renvoyé à l'orchestration via l'adaptateur JD Edwards OneWorld, et l'adaptateur FILE écrit le fichier XML à l'emplacement de sortie sur le disque.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-190">This XML file returns to the orchestration through the JD Edwards OneWorld adapter, and the File adapter writes the XML file to the output location on disk.</span></span>  
  
 <span data-ttu-id="1b5ce-191">Pour terminer l'orchestration, vous devez créer et configurer les ports pour recevoir et envoyer les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-191">To complete the orchestration, you need to create and configure ports to receive and send the XML files.</span></span> <span data-ttu-id="1b5ce-192">Commencez par configurer un port de réception que l'adaptateur FILE utilisera pour entrer le XML contenant la requête dans l'orchestration sur le disque.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-192">First, configure a receive port to be used by the File adapter to input the XML containing the query into the orchestration from disk.</span></span>  
  
#### <a name="configure-a-receive-port-to-accept-the-input-xml-file"></a><span data-ttu-id="1b5ce-193">Configurer un port de réception pour accepter le fichier XML d’entrée</span><span class="sxs-lookup"><span data-stu-id="1b5ce-193">Configure a receive port to accept the input XML file</span></span>  
  
1.  <span data-ttu-id="1b5ce-194">Double-cliquez sur le fichier **BizTalk Orchestration.odx** pour ouvrir l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-194">Double-click the **BizTalk Orchestration.odx** file to open the orchestration.</span></span>  
  
2.  <span data-ttu-id="1b5ce-195">Dans le fichier Biztalkorchestration.odx, avec le bouton droit de la surface du port de gauche, puis **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-195">In the BizTalk Orchestration.odx file, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="1b5ce-196">L'Assistant Configuration du port démarre.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-196">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="1b5ce-197">Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-197">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="1b5ce-198">Sur le **propriétés de Port** , entrez `JDE_File_In` pour **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-198">On the **Port Properties** page, enter `JDE_File_In` for **Name**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="1b5ce-199">Dans la page **Sélectionner un type de port** , sélectionnez **Créer un type de port**, puis entrez ou sélectionnez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-199">On the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
     <span data-ttu-id="1b5ce-200">**Nom du Type de port**:`JDE_FileIn_Port`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-200">**Port Type Name**: `JDE_FileIn_Port`</span></span>  
  
     <span data-ttu-id="1b5ce-201">**Modèle de communication**: **Unidirectionnel**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-201">**Communication Pattern**: **One Way**</span></span>  
  
     <span data-ttu-id="1b5ce-202">**Restrictions d'accès**: **Interne - limité au projet**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-202">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
5.  <span data-ttu-id="1b5ce-203">Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-203">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
     <span data-ttu-id="1b5ce-204">**Direction de communication du port**: **Toujours recevoir les messages sur ce port**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-204">**Port direction of communication**: **I'll always be receiving messages on this port**</span></span>  
  
     <span data-ttu-id="1b5ce-205">**Liaison de port**: **Spécifier plus tard**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-205">**Port binding**: **Specify later**</span></span>  
  
6.  <span data-ttu-id="1b5ce-206">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-206">Click **Next**, and then click **Finish**.</span></span>  
  
 <span data-ttu-id="1b5ce-207">Créez ensuite un port d'envoi/réception pour envoyer le fichier d'entrée XML initial contenant la requête passée au système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-207">Next, create a send/receive port to send the initial XML input file containing the query to the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-208">Ce port reçoit également un fichier XML de sortie contenant les résultats de la requête issus de l'appel auprès du système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-208">This port will also receive an output XML file containing the query results from the call to the JD Edwards OneWorld system.</span></span>  
  
#### <a name="configure-a-sendreceive-port-to-interface-with-jd-edwards-oneworld"></a><span data-ttu-id="1b5ce-209">Configurer un port d’envoi/réception pour interagir avec JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="1b5ce-209">Configure a send/receive port to interface with JD Edwards OneWorld</span></span>  
  
1.  <span data-ttu-id="1b5ce-210">Dans le fichier Biztalkorchestration.odx, avec le bouton droit de la surface du port de droite, puis **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-210">In the BizTalk Orchestration.odx file, right-click the right port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="1b5ce-211">L'Assistant Configuration du port démarre.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-211">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="1b5ce-212">Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-212">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2.  <span data-ttu-id="1b5ce-213">Dans la page **Sélectionner un type de port** , sélectionnez **Utiliser un type de port existant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-213">On the **Select a Port Type** page, select **Use an existing Port Type**.</span></span> <span data-ttu-id="1b5ce-214">Sous **Types de ports disponibles**, sélectionnez **JD_OW_Test.N0100041**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-214">Under **Available Port Types**, select **JD_OW_Test.N0100041**,and then click **Next**.</span></span>  
  
     ![](../core/media/a421358c-6e90-4fe0-b243-6beb1b51955a.gif "a421358c-6e90-4fe0-b243-6beb1b51955a")  
  
3.  <span data-ttu-id="1b5ce-215">Sélectionnez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-215">Select the following property values:</span></span>  
  
     <span data-ttu-id="1b5ce-216">**Direction de communication du port**: **puis-je envoyer une demande et recevoir une réponse**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-216">**Port direction of communication**: **I'll be sending a request and receiving a response**</span></span>  
  
     <span data-ttu-id="1b5ce-217">**Liaison de port**: **Spécifier plus tard**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-217">**Port binding**: **Specify later**</span></span>  
  
4.  <span data-ttu-id="1b5ce-218">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-218">Click **Next**, and then click **Finish**.</span></span> <span data-ttu-id="1b5ce-219">Sur la surface de port, le port et les méthodes disponibles s'affichent.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-219">On the port surface you will see the port and the available methods.</span></span>  
  
 <span data-ttu-id="1b5ce-220">Pour terminer, configurez un port d'envoi que l'adaptateur FILE utilisera pour transmettre en sortie le XML contenant les résultats de la requête vers le disque.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-220">Finally, configure a send port to be used by the File adapter to output the XML containing the query results to disk.</span></span>  
  
#### <a name="configure-a-send-port-to-output-the-xml-file-to-disk"></a><span data-ttu-id="1b5ce-221">Configurer un port d’envoi pour générer le fichier XML sur le disque</span><span class="sxs-lookup"><span data-stu-id="1b5ce-221">Configure a send port to output the XML file to disk</span></span>  
  
1.  <span data-ttu-id="1b5ce-222">Dans le fichier Biztalkorchestration.odx, avec le bouton droit de la surface du port de gauche, puis **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-222">In the BizTalk Orchestration.odx file, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="1b5ce-223">L'Assistant Configuration du port démarre.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-223">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="1b5ce-224">Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-224">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2.  <span data-ttu-id="1b5ce-225">Sur le **propriétés de Port** , entrez `JDE_FileOut` pour **nom**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-225">On the **Port Properties** page, enter `JDE_FileOut` for **Name**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="1b5ce-226">Dans la page **Sélectionner un type de port** , sélectionnez **Créer un type de port**, puis entrez ou sélectionnez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-226">On the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
     <span data-ttu-id="1b5ce-227">**Nom du Type de port**:`JDE_FileOut_Port`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-227">**Port Type Name**: `JDE_FileOut_Port`</span></span>  
  
     <span data-ttu-id="1b5ce-228">**Modèle de communication**: **Unidirectionnel**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-228">**Communication Pattern**: **One Way**</span></span>  
  
     <span data-ttu-id="1b5ce-229">**Restrictions d'accès**: **Interne - limité au projet**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-229">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
4.  <span data-ttu-id="1b5ce-230">Cliquez sur **Suivant** pour accéder à la page **Liaison de port** , puis sélectionnez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-230">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
     <span data-ttu-id="1b5ce-231">**Direction de communication du port**: **Toujours envoyer les messages sur ce port**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-231">**Port direction of communication**: **I'll always be sending messages on this port**</span></span>  
  
     <span data-ttu-id="1b5ce-232">**Liaison de port**: **Spécifier plus tard**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-232">**Port binding**: **Specify later**</span></span>  
  
5.  <span data-ttu-id="1b5ce-233">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-233">Click **Next**, and then click **Finish**.</span></span>  
  
 <span data-ttu-id="1b5ce-234">Les nouveaux ports et les méthodes disponibles pour les services JD Edwards OneWorld s'affichent sur la surface du port.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-234">Displayed on the port surface are the new ports and the available methods for the JD Edwards OneWorld services.</span></span> <span data-ttu-id="1b5ce-235">Lors d'une étape ultérieure, vous indiquerez à l'adaptateur JD Edwards OneWorld d'envoyer et de recevoir des fichiers à partir du système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-235">Later you will specify the JD Edwards OneWorld adapter to send and receive files from the JD Edwards OneWorld system.</span></span>  
  
 <span data-ttu-id="1b5ce-236">Le **JDE_File_In** et **JDE_File_Out** ports que vous venez de créer nécessitent des types de messages associés.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-236">The **JDE_File_In** and **JDE_File_Out** ports you just created need associated message types.</span></span>  
  
#### <a name="assign-message-types-to-the-ports"></a><span data-ttu-id="1b5ce-237">Assigner des types de messages aux ports</span><span class="sxs-lookup"><span data-stu-id="1b5ce-237">Assign message types to the ports</span></span>  
  
1.  <span data-ttu-id="1b5ce-238">Sur la surface du port de gauche, sur le **JDE_File_In** de port, cliquez sur **demande**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-238">On the left port surface, on the **JDE_File_In** port, click **Request**.</span></span> <span data-ttu-id="1b5ce-239">Dans la fenêtre Propriétés, développez **Type de Message**, développez **messages à parties multiples**, puis cliquez sur **JDE_OW_TestAddressBookMasterMBF**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-239">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **JDE_OW_TestAddressBookMasterMBF**.</span></span>  
  
2.  <span data-ttu-id="1b5ce-240">Sur la surface du port de gauche, sur le **JDE_File_Out** de port, cliquez sur **demande**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-240">On the left port surface, on the **JDE_File_Out** port, click **Request**.</span></span> <span data-ttu-id="1b5ce-241">Dans la fenêtre Propriétés, développez **Type de Message**, développez **messages à parties multiples**, puis cliquez sur **JDE_OW_TestAddressBookMasterMBFResponse**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-241">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **JDE_OW_TestAddressBookMasterMBFResponse**.</span></span>  
  
 <span data-ttu-id="1b5ce-242">Insérez deux **envoyer** formes et deux **réception** formes dans l’orchestration à lier aux ports.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-242">Insert two **Send** shapes and two **Receive** shapes into the orchestration to link to the ports.</span></span>  
  
#### <a name="add-send-and-receive-shapes"></a><span data-ttu-id="1b5ce-243">Ajouter d’envoyer et recevoir des formes</span><span class="sxs-lookup"><span data-stu-id="1b5ce-243">Add Send and Receive shapes</span></span>  
  
1.  <span data-ttu-id="1b5ce-244">Faites glisser un composant **Réception** à partir de la Boîte à outils, puis déposez-le sous le début de l'orchestration (cercle vert).</span><span class="sxs-lookup"><span data-stu-id="1b5ce-244">Drag a **Receive** component from the Toolbox and drop it immediately below the start of the orchestration (the green circle).</span></span> <span data-ttu-id="1b5ce-245">Cliquez sur le **réception** mettre en forme et dans la fenêtre Propriétés, entrez `Get_File` pour le **nom**et la valeur **activer** à `true`.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-245">Click the **Receive** shape, and in the Properties window, enter `Get_File` for the **Name**, and set **Activate** to `true`.</span></span> <span data-ttu-id="1b5ce-246">Cette opération permet d'activer l'orchestration lorsque ce port de réception reçoit un document entrant.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-246">Doing so will activate the orchestration when an incoming document is received on this receive port.</span></span>  
  
2.  <span data-ttu-id="1b5ce-247">Faites glisser un **envoyer** composant à partir de la boîte à outils et déposez-le sous le **GetFileReceive** forme.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-247">Drag a **Send** component from the Toolbox and drop it immediately below the **GetFileReceive** shape.</span></span> <span data-ttu-id="1b5ce-248">Cliquez sur la nouvelle **envoyer** mettre en forme et dans la fenêtre Propriétés, entrez `SendToJDEOW` pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-248">Click the new **Send** shape, and in the Properties window, enter `SendToJDEOW` for the **Name**.</span></span>  
  
3.  <span data-ttu-id="1b5ce-249">Faites glisser un **réception** composant à partir de la boîte à outils et déposez-le sous le **SendToJDEOWSend** forme.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-249">Drag a **Receive** component from the Toolbox and drop it immediately below the **SendToJDEOWSend** shape.</span></span> <span data-ttu-id="1b5ce-250">Cliquez sur le **réception** mettre en forme et dans la fenêtre Propriétés, entrez `JDEOW_Resp` pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-250">Click the **Receive** shape, and in the Properties window, enter `JDEOW_Resp` for the **Name**.</span></span>  
  
4.  <span data-ttu-id="1b5ce-251">Faites glisser un **envoyer** composant à partir de la boîte à outils et déposez-le sous le **JDEOW_RespReceive** forme.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-251">Drag a **Send** component from the Toolbox and drop it immediately below the **JDEOW_RespReceive** shape.</span></span> <span data-ttu-id="1b5ce-252">Cliquez sur la nouvelle **envoyer** mettre en forme et dans la fenêtre Propriétés, entrez `FileToDisk` pour le **nom**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-252">Click the new **Send** shape, and in the Properties window, enter `FileToDisk` for the **Name**.</span></span>  
  
     ![](../core/media/jdeow-orchestration-multipartmessages.gif "JDEOW_Orchestration_MultiPartMessages")  
  
5.  <span data-ttu-id="1b5ce-253">Connecter le **JDE_FileIn** port pour le **GetFileReceive** composant.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-253">Connect the **JDE_FileIn** port to the **GetFileReceive** component.</span></span>  
  
6.  <span data-ttu-id="1b5ce-254">Connecter le **JDE_FileOut** port pour le **FileToDiskReceive** composant.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-254">Connect the **JDE_FileOut** port to the **FileToDiskReceive** component.</span></span>  
  
7.  <span data-ttu-id="1b5ce-255">Accédez à **Vue Orchestration** et développez **Messages**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-255">Go to **Orchestration View** and expand **Messages**.</span></span> <span data-ttu-id="1b5ce-256">L’identificateur **Message_1** à `MsgToJDEOW`et pour **Message_2** à`JDEOW_Resp.`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-256">Change the identifier for **Message_1** to `MsgToJDEOW`, and for **Message_2** to `JDEOW_Resp.`</span></span>  
  
8.  <span data-ttu-id="1b5ce-257">Mettez en surbrillance le **SendToJDEOWSend** composant et définissez son **Message** propriété **MsgToJDEOW**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-257">Highlight the **SendToJDEOWSend** component and set its **Message** property to **MsgToJDEOW**.</span></span>  
  
9. <span data-ttu-id="1b5ce-258">Mettez en surbrillance le **JDEOW_RespReceive** composant et définissez son **Message** propriété **JDEOW_Resp**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-258">Highlight the **JDEOW_RespReceive** component and set its **Message** property to **JDEOW_Resp**.</span></span>  
  
10. <span data-ttu-id="1b5ce-259">Se connecter **SendToJDEOW** à la **demande** partie de la **JDE_OW_Port** port.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-259">Connect **SendToJDEOW** to the **Request** portion of the **JDE_OW_Port** port.</span></span>  
  
11. <span data-ttu-id="1b5ce-260">Se connecter **JDEOW_Resp** à la **réponse** partie de la **JDE_OW_Port** port.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-260">Connect **JDEOW_Resp** to the **Response** portion of the **JDE_OW_Port** port.</span></span>  
  
     ![](../core/media/jdeow-portsurface-connectcomponentstoports.gif "JDEOW_PortSurface_ConnectComponentsToPorts")  
  
## <a name="step-4-build-and-deploy-the-project"></a><span data-ttu-id="1b5ce-261">Étape 4 : Créer et déployer le projet</span><span class="sxs-lookup"><span data-stu-id="1b5ce-261">Step 4: Build and deploy the project</span></span>  
 <span data-ttu-id="1b5ce-262">Le projet BizTalk étant à présent terminé, vous pouvez le créer et le déployer dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b5ce-262">Now the BizTalk project is complete and you can build and deploy it in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="1b5ce-263">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-263">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1b5ce-264">Pour créer le projet, un fichier de clé de nom fort est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-264">To build the project, you need a strong name key file.</span></span> <span data-ttu-id="1b5ce-265">Pour en créer un, à l'invite de commandes, entrez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-265">At the command prompt, enter the following to create a strong name key file:</span></span>  
  
     <span data-ttu-id="1b5ce-266">**sn -k labs.snk**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-266">**sn -k labs.snk**</span></span>  
  
3.  <span data-ttu-id="1b5ce-267">Dans l’Explorateur de solutions, cliquez sur le **JD_OW_Test** de projet, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-267">In Solution Explorer, right-click the **JD_OW_Test** project, and then click **Properties** to launch the Project Designer for the project.</span></span>  
  
4.  <span data-ttu-id="1b5ce-268">Cliquez sur l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="1b5ce-268">Click the **Signing** tab.</span></span>  
  
5.  <span data-ttu-id="1b5ce-269">Sélectionnez l'option **Signer l'assembly** , cliquez sur l'option **Choisir un fichier de clé de nom fort** dans la liste déroulante, puis sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-269">Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.</span></span>  
  
6.  <span data-ttu-id="1b5ce-270">Recherchez puis sélectionnez le fichier de clé : **labs.snk**, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-270">Browse to select the key file: **labs.snk**, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="1b5ce-271">Dans le Concepteur de projet, cliquez sur l'onglet **Déploiement** .</span><span class="sxs-lookup"><span data-stu-id="1b5ce-271">Click **Deployment** tab in the Project Designer.</span></span>  
  
8.  <span data-ttu-id="1b5ce-272">Définir le **nom de l’Application** à `JDE_OW_Test`.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-272">Set the **Application Name** to `JDE_OW_Test`.</span></span>  
  
9. <span data-ttu-id="1b5ce-273">Dans l’Explorateur de solutions, cliquez sur le **JDE_OW_Test** de projet, puis cliquez sur **générer.**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-273">In Solution Explorer, right-click the **JDE_OW_Test** project, and then click **Build.**</span></span>  
  
     ![](../core/media/jdeow-buildcompleteoutput.gif "JDEOW_BuildCompleteOutput")  
  
10. <span data-ttu-id="1b5ce-274">Une fois la build terminée, cliquez sur le **XX_JD Edwards OneWorldQuery** de projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-274">After the build completes successfully, right-click the **XX_JD Edwards OneWorldQuery** project, and then click **Deploy**.</span></span> <span data-ttu-id="1b5ce-275">La sortie suivante s'affiche dans la fenêtre Sortie :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-275">In the output window the following output will be displayed:</span></span>  
  
     ![](../core/media/jdeow-deployoutput.gif "JDEOW_DeployOutput")  
  
## <a name="step-5-test-the-application-and-viewing-the-xml-output"></a><span data-ttu-id="1b5ce-276">Étape 5 : Tester l’Application et afficher la sortie XML</span><span class="sxs-lookup"><span data-stu-id="1b5ce-276">Step 5: Test the Application and Viewing the XML Output</span></span>  
 <span data-ttu-id="1b5ce-277">Vous allez à présent tester l'application que vous avez créée et déployée.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-277">Now you will test the application that you have created and deployed.</span></span> <span data-ttu-id="1b5ce-278">Vous allez créer le fichier XML qui démarre le processus d'orchestration, puis vous allez configurer les dossiers afin qu'ils reçoivent et envoient des fichiers XML au sein de l'application.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-278">You will create the XML file that starts the orchestration process, and then you will configure folders to receive and send XML files within the application.</span></span> <span data-ttu-id="1b5ce-279">Une fois l'application configurée, vous allez l'exécuter et afficher les fichiers XML qu'elle renvoie.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-279">After you have configured the application, you will run it and view the XML files that the orchestration returns.</span></span>  
  
#### <a name="generate-the-xml-file-for-the-query"></a><span data-ttu-id="1b5ce-280">Générer le fichier XML de la requête</span><span class="sxs-lookup"><span data-stu-id="1b5ce-280">Generate the XML file for the query</span></span>  
  
1.  <span data-ttu-id="1b5ce-281">Dans l’Explorateur de solutions, double-cliquez sur **N0100041Service_N0100041.xsd** pour ouvrir le fichier.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-281">In Solution Explorer, double-click **N0100041Service_N0100041.xsd** to open the file.</span></span>  
  
2.  <span data-ttu-id="1b5ce-282">Avec le bouton droit **N0100041Service_N0100041.xsd** puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-282">Right-click **N0100041Service_N0100041.xsd** and then click **Properties**.</span></span> <span data-ttu-id="1b5ce-283">Pour **Nom de fichier d'instance de sortie** , entrez les chemin d'accès et nom suivants pour l'exemple de fichier XML :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-283">For the **Output Instance Filename** enter the following path and file name for the sample XML:</span></span>  
  
     `C:\LABS\JDE_OW_TEST\SAMPLE.XML`  
  
3.  <span data-ttu-id="1b5ce-284">Cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-284">Click **OK.**</span></span> <span data-ttu-id="1b5ce-285">Dans la fenêtre Propriétés, sélectionnez  **\<schéma >** et **référence de racine :** à `AddressBookMasterMBF`.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-285">In the Properties window, select **\<Schema>** and set **Root Reference:** to `AddressBookMasterMBF`.</span></span> <span data-ttu-id="1b5ce-286">Cela entraîne le code XML généré inclure uniquement les **requête** xml.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-286">This will cause the generated XML to include only the **Query** xml.</span></span>  
  
     ![](../core/media/jdeow-jde-ow-test-msvisualstudio-schemas.gif "JDEOW_JDE_OW_Test_MSVISUALSTUDIO_SCHEMAS")  
  
4.  <span data-ttu-id="1b5ce-287">Avec le bouton droit **N0100041Service_N0100041.xsd** puis cliquez sur **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-287">Right-click **N0100041Service_N0100041.xsd** and then click **Generate Instance**.</span></span> <span data-ttu-id="1b5ce-288">Cette opération génère le **Sample.xml** fichier.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-288">This generates the **Sample.xml** file.</span></span> <span data-ttu-id="1b5ce-289">Ce fichier sera transmis à l'emplacement de réception en tant qu'entrée de l'adaptateur pour démarrer le processus d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-289">This file will be dropped in the receive location as input to the adapter to start the orchestration process.</span></span>  
  
#### <a name="configure-and-start-the-biztalk-application"></a><span data-ttu-id="1b5ce-290">Configurer et démarrer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="1b5ce-290">Configure and start the BizTalk application</span></span>  
  
1.  <span data-ttu-id="1b5ce-291">Configurez les dossiers afin qu'ils reçoivent les fichiers entrants et envoient les fichiers sortants.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-291">Configure folders for receiving the incoming files and sending the outgoing files.</span></span> <span data-ttu-id="1b5ce-292">Accédez à **C:\LABS\JDE_OW_Test** et créez deux sous-dossiers nommés `FileIn` et `FileOut`.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-292">Go to **C:\LABS\JDE_OW_Test** and create two new subfolders named `FileIn` and `FileOut`.</span></span>  
  
2.  <span data-ttu-id="1b5ce-293">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **racine de la Console**, développez**Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-293">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,expand **Console Root**, expand**BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="1b5ce-294">Avec le bouton droit **JDE_OW_Test**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-294">Right-click **JDE_OW_Test**, and then click **Configure**.</span></span>  
  
     ![](../core/media/jdeow-configureapplicationjde-ow-test.gif "JDEOW_ConfigureApplicationJDE_OW_Test")  
  
4.  <span data-ttu-id="1b5ce-295">Sélectionnez **Orchestration_1** , puis cliquez sur la zone déroulante **Hôte** .</span><span class="sxs-lookup"><span data-stu-id="1b5ce-295">Select **Orchestration_1** and click the **Host** drop-down box.</span></span> <span data-ttu-id="1b5ce-296">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-296">Select **BizTalkServerApplication**.</span></span>  
  
5.  <span data-ttu-id="1b5ce-297">Sous **Ports de réception**, cliquez sur  **\<aucun >**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-297">Under **Receive Ports**, click **\<None>**.</span></span> <span data-ttu-id="1b5ce-298">Dans la liste déroulante, sélectionnez **Nouveau port de réception**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-298">In the drop-down list, select **New Receive Port**.</span></span>  
  
6.  <span data-ttu-id="1b5ce-299">Pour **nom**, type `JDE_FileIn_Port`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-299">For **Name**, type `JDE_FileIn_Port`, and then click **OK**.</span></span> <span data-ttu-id="1b5ce-300">Le message qui s'affiche indique que vous devez désigner un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-300">A message box appears stating that you need to designate a receive location.</span></span> <span data-ttu-id="1b5ce-301">Cliquez sur **OK**, puis sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-301">Click **OK**, and then click **New**.</span></span>  
  
     ![](../core/media/jdeow-filein-port-receiveportproperties.gif "JDEOW_FileIn_Port_ReceivePortProperties")  
  
7.  <span data-ttu-id="1b5ce-302">Tapez ou sélectionnez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-302">Type or select the following values for the properties:</span></span>  
  
     <span data-ttu-id="1b5ce-303">**Nom**: JDE_`FileInLoc`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-303">**Name**: JDE_`FileInLoc`</span></span>  
  
     <span data-ttu-id="1b5ce-304">**Type**: **Fichier**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-304">**Type**: **File**</span></span>  
  
     <span data-ttu-id="1b5ce-305">**Gestionnaire de réception**: **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-305">**Receive Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="1b5ce-306">**Pipeline de réception**: **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-306">**Receive Pipeline**: **XMLReceive**</span></span>  
  
     ![](../core/media/jdeow-filein-loc-receivelocationproperties.gif "JDEOW_FileIn_Loc_ReceiveLocationProperties")  
  
8.  <span data-ttu-id="1b5ce-307">Cliquez sur **configurer**, type `C:\LABS\JDE_OW_Test\FileIn` pour **dossier de réception**, puis cliquez sur **OK** trois fois.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-307">Click **Configure**, type `C:\LABS\JDE_OW_Test\FileIn` for **Receive Folder**, and then click **OK** three times.</span></span>  
  
     ![](../core/media/jdeow-file-transport-properties-filein.gif "JDEOW_File_Transport_Properties_FileIn")  
  
9. <span data-ttu-id="1b5ce-308">Cliquez sur  **\<aucun >** pour **JDE_OW_Port** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-308">Click **\<None>** for **JDE_OW_Port** in the drop-down list.</span></span>  
  
10. <span data-ttu-id="1b5ce-309">Sélectionnez **nouveau Port d’envoi** , puis sélectionnez ou tapez les valeurs suivantes pour les propriétés :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-309">Select **New Send Port** and then select or type the following values for the properties:</span></span>  
  
     <span data-ttu-id="1b5ce-310">**Nom de**:`JDE_OW_Port`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-310">**Name**: `JDE_OW_Port`</span></span>  
  
     <span data-ttu-id="1b5ce-311">**Type**: **JDE_OneWorld**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-311">**Type**: **JDE_OneWorld**</span></span>  
  
     <span data-ttu-id="1b5ce-312">**Gestionnaire d'envoi**: **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-312">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="1b5ce-313">**Pipelines**: **XMLTransmit** et **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-313">**Pipelines**: **XMLTransmit** and **XMLReceive**</span></span>  
  
11. <span data-ttu-id="1b5ce-314">Cliquez sur **Configurer**, puis entrez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-314">Click **Configure**, and then enter the following property values:</span></span>  
  
     <span data-ttu-id="1b5ce-315">**Hôte :** \<Entrez votre nom d’hôte JDEOW ></span><span class="sxs-lookup"><span data-stu-id="1b5ce-315">**Host:** \<enter your JDEOW host name></span></span>  
  
     <span data-ttu-id="1b5ce-316">**JAVA_HOME :**`C:\j2sdk1.4.2_08`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-316">**JAVA_HOME:** `C:\j2sdk1.4.2_08`</span></span>  
  
     <span data-ttu-id="1b5ce-317">**Environnement JDEdwards :** \<Entrez votre environnement JDEOW ></span><span class="sxs-lookup"><span data-stu-id="1b5ce-317">**JDEdwards Environment:** \<enter your JDEOW environment></span></span>  
  
     <span data-ttu-id="1b5ce-318">**Fichiers JAR JDEdwards :**<enter full path of JAR files></span><span class="sxs-lookup"><span data-stu-id="1b5ce-318">**JDEdwards JAR files:** <enter full path of JAR files></span></span>  
  
     `C:JDEOWJarsBTSLIBInterop.jar; C:JDEOWJarsConnector.jar; C:JDEOWJarsKernel.jar;C:Program FilesMicrosoft BizTalk Adapters for Enterprise ApplicationsJ.D. Edwards OneWorld®ClassesJDEJAccess.jar`  
  
     <span data-ttu-id="1b5ce-319">**Mot de passe :** utilisez la liste déroulante, puis entrez votre mot de passe JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-319">**Password:** Use the drop-down list and then enter your JD Edwards OneWorld password.</span></span>  
  
     <span data-ttu-id="1b5ce-320">**Port :**  `6009`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-320">**Port:**  `6009`</span></span>  
  
     <span data-ttu-id="1b5ce-321">**Nom d’utilisateur :**<enter your JD Edwards User Name></span><span class="sxs-lookup"><span data-stu-id="1b5ce-321">**User Name:** <enter your JD Edwards User Name></span></span>  
  
     ![](../core/media/jdeow-transportproperties-configurebutton2.gif "JDEOW_TransportProperties_ConfigureButton2")  
  
12. <span data-ttu-id="1b5ce-322">Cliquez sur **OK** à deux reprises pour fermer les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-322">Click **OK** twice to close the dialog boxes.</span></span>  
  
13. <span data-ttu-id="1b5ce-323">Dans la Applicationwindow configurer, cliquez sur  **\<aucun >** pour **JDE_FileOut** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-323">In the Configure Applicationwindow, click **\<None>** for **JDE_FileOut** in the drop-down list.</span></span>  
  
14. <span data-ttu-id="1b5ce-324">Sélectionnez **Nouveau port d'envoi** , puis sélectionnez ou tapez les valeurs de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-324">Select **New Send Port** and type or select the following values for the properties:</span></span>  
  
     <span data-ttu-id="1b5ce-325">**Nom de**:`FileOutPort`</span><span class="sxs-lookup"><span data-stu-id="1b5ce-325">**Name**: `FileOutPort`</span></span>  
  
     <span data-ttu-id="1b5ce-326">**Type**: **Fichier**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-326">**Type**: **File**</span></span>  
  
     <span data-ttu-id="1b5ce-327">**Gestionnaire d'envoi**: **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-327">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="1b5ce-328">**Pipeline d'envoi**: **XMLTransmit**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-328">**Send Pipeline**: **XMLTransmit**</span></span>  
  
15. <span data-ttu-id="1b5ce-329">Cliquez sur **configurer** et type`C:\Labs\JDE_OW_Test\FileOut` pour **dossier de Destination.**</span><span class="sxs-lookup"><span data-stu-id="1b5ce-329">Click **Configure** and type`C:\Labs\JDE_OW_Test\FileOut` for **Destination Folder.**</span></span> <span data-ttu-id="1b5ce-330">. Conservez le **Nom de fichier** sur **%MessageID%.xml** because this results in a unique file sur each message.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-330">Keep **%MessageID%.xml** for **File Name** because this results in a unique file for each message.</span></span>  
  
     ![](../core/media/jdeow-file-transport-properties-fileout.gif "JDEOW_File_Transport_Properties_FileOut")  
  
16. <span data-ttu-id="1b5ce-331">Cliquez sur **OK** à trois reprises pour fermer les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-331">Click **OK** three times to close the dialog boxes.</span></span>  
  
17. <span data-ttu-id="1b5ce-332">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez à droite la **JDE_OW_Test** application, puis sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-332">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,right-click the **JDE_OW_Test** application, and then click **Start**.</span></span>  
  
#### <a name="test-the-orchestration"></a><span data-ttu-id="1b5ce-333">Tester l’orchestration</span><span class="sxs-lookup"><span data-stu-id="1b5ce-333">Test the orchestration</span></span>  
  
1.  <span data-ttu-id="1b5ce-334">Dans le **C:\Labs\JDE_OW_Test** Active le **Sample.xml** fichier apparaîtront en tant que :</span><span class="sxs-lookup"><span data-stu-id="1b5ce-334">In the **C:\Labs\JDE_OW_Test** directory the **Sample.xml** file will appear as:</span></span>  
  
     ![](../core/media/jdeow-samplexml-notepad-addressbookmastermbf.gif "JDEOW_SampleXML_Notepad_AddressBookMasterMBF")  
  
2.  <span data-ttu-id="1b5ce-335">Modifier la **Sample.xml** fichier à supprimer tout sauf la **cActionCode** et **mnAddressBookNumber** éléments.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-335">Edit the **Sample.xml** file to remove everything except the **cActionCode** and **mnAddressBookNumber** elements.</span></span>  
  
     ![](../core/media/jdeow-samplexml-notepad-cactioncode.gif "JDEOW_SampleXML_Notepad_cActionCode")  
  
3.  <span data-ttu-id="1b5ce-336">Pour le **cActionCode** élément insérer la lettre `i`.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-336">For the **cActionCode** element insert the letter `i`.</span></span>  
  
4.  <span data-ttu-id="1b5ce-337">Pour **mnAddressBookNumber** insérer le nombre `500`.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-337">For **mnAddressBookNumber** insert the number `500`.</span></span>  
  
5.  <span data-ttu-id="1b5ce-338">Enregistrer les modifications et copiez le fichier dans le **C:\Labs\JDE_OW_Test\FileIn** dossier.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-338">Save the changes and copy the file to the **C:\Labs\JDE_OW_Test\FileIn** folder.</span></span> <span data-ttu-id="1b5ce-339">Il s'agit de l'emplacement de réception qui démarre le processus d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-339">This is the receive location that starts the orchestration process.</span></span>  
  
6.  <span data-ttu-id="1b5ce-340">En quelques secondes, un fichier XML doit apparaître dans le **C:\Labs\JDE_OW_Test\FileOut** dossier.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-340">In a few seconds, an XML file should appear in the **C:\Labs\JDE_OW_Test\FileOut** folder.</span></span> <span data-ttu-id="1b5ce-341">Il doit contenir tous les enregistrements dans lesquels l'adresse est définie sur 500.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-341">This should contain the all the records where the address is 500.</span></span>  
  
     ![](../core/media/jdeow-xml-output-jde-callbsfn.gif "JDEOW_XML_Output_JDE_CALLBSFN")  
  
     <span data-ttu-id="1b5ce-342">Ces données d’enregistrement retourné doivent correspondre à des données retournées par la requête sur le système JD Edwards OneWorld dans l’atelier 1.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-342">This returned record data should match the data returned by the query against the JD Edwards OneWorld system in Lab 1.</span></span> <span data-ttu-id="1b5ce-343">En comparant les enregistrements que vous avez obtenue dans l’atelier 1, vous pouvez vérifier que le **obtenir** a fonctionné correctement.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-343">By comparing the records you obtained in Lab 1, you can verify that the **Get** method worked properly.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="1b5ce-344">Résumé</span><span class="sxs-lookup"><span data-stu-id="1b5ce-344">Summary</span></span>  
 <span data-ttu-id="1b5ce-345">Au cours de cet atelier, vous avez vérifié que tous les composants permettant d'accéder au système JD Edwards OneWorld étaient correctement installés.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-345">In this lab, you first verified that the prerequisites were set up correctly to access the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-346">Puis vous avez utilisé [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour créer un projet BizTalk contenant une orchestration.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-346">Then you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project containing an orchestration.</span></span> <span data-ttu-id="1b5ce-347">Vous avez configuré l'orchestration BizTalk de manière à ce qu'elle utilise l'adaptateur JD Edwards OneWorld pour extraire des données du système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-347">You configured the BizTalk orchestration to use the JD Edwards OneWorld adapter to get data from the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-348">Pour configurer l'orchestration, vous avez créé des ports d'envoi, des ports de réception et des ports d'envoi/réception.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-348">To configure the orchestration, you created send, receive, and send/receive ports.</span></span> <span data-ttu-id="1b5ce-349">Vous avez lié ces ports à l'adaptateur JD Edwards OneWorld, puis affecté des messages aux ports appropriés.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-349">You bound these ports to the JD Edwards OneWorld adapter, and assigned messages to the appropriate ports.</span></span>  
  
 <span data-ttu-id="1b5ce-350">Une fois le projet BizTalk configuré, vous l'avez créé et déployé à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b5ce-350">After you completed the BizTalk project, you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to build and deploy it.</span></span> <span data-ttu-id="1b5ce-351">Vous avez ensuite configuré la nouvelle application, puis vous l'avez exécutée de manière à ce qu'elle extraie des données du système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-351">You then configured your new application and ran it to get data from the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1b5ce-352">Pour vérifier qu'elle fonctionnait correctement, vous avez comparé le fichier XML de sortie au fichier reçu du système JD Edwards OneWorld au cours de l'atelier 1.</span><span class="sxs-lookup"><span data-stu-id="1b5ce-352">To verify that the application worked correctly, you compared its output XML file to the file that you received from the JD Edwards OneWorld system in Lab 1.</span></span>