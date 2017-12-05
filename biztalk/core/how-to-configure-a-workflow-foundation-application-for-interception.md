---
title: "Comment configurer une Application de Workflow Foundation pour l’Interception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c82e83f-9dbd-4325-9f30-778eba892296
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70afa4ffae47abf5cdd541846831b4054414eff8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-workflow-foundation-application-for-interception"></a><span data-ttu-id="f9d3c-102">Configuration d'une application Foundation pour l'interception</span><span class="sxs-lookup"><span data-stu-id="f9d3c-102">How to Configure a Workflow Foundation Application for Interception</span></span>
<span data-ttu-id="f9d3c-103">Avant de commencer à collecter les données d'activité BAM, vous devez installer le logiciel de l'intercepteur [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] et configurer votre application afin d'utiliser le service de l'intercepteur BAM.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-103">You must install the BAM interceptor software and configure your application to use the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor service before you can begin collecting BAM activity data.</span></span> <span data-ttu-id="f9d3c-104">Vous devez avoir correctement installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ses dépendances et avoir créé au moins un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-104">It is assumed that you have successfully installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies and have created at least one BizTalk group.</span></span>  
  
## <a name="installing-the-bam-eventing-software"></a><span data-ttu-id="f9d3c-105">Installation du logiciel BAM-Événements</span><span class="sxs-lookup"><span data-stu-id="f9d3c-105">Installing the BAM-Eventing Software</span></span>  
 <span data-ttu-id="f9d3c-106">Avant de configurer votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] afin d'utiliser l'intercepteur BAM pour [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], vous devez installer le logiciel BAM-Événements à l'aide du programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9d3c-106">Before you can configure your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application to use the BAM interceptor for [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program.</span></span> <span data-ttu-id="f9d3c-107">Pour plus d’informations sur l’installation du logiciel BAM-événements et l’enregistrement des compteurs de performance, consultez [l’installation du logiciel BAM-événements](../core/installing-the-bam-eventing-software.md).</span><span class="sxs-lookup"><span data-stu-id="f9d3c-107">For more information about installing the BAM-Eventing software and registering the performance counters, see [Installing the BAM-Eventing Software](../core/installing-the-bam-eventing-software.md).</span></span>  
  
## <a name="configuring-a-windows-workflow-foundation-application-for-tracking"></a><span data-ttu-id="f9d3c-108">Configuration d'une application Windows Workflow Foundation pour le suivi</span><span class="sxs-lookup"><span data-stu-id="f9d3c-108">Configuring a Windows Workflow Foundation Application for Tracking</span></span>  
 <span data-ttu-id="f9d3c-109">Vous devez effectuer quatre tâches avant que votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] ne puisse commencer à écrire des informations sur les événements BAM :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-109">Four tasks must be completed before your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application can begin writing BAM event information:</span></span>  
  
-   <span data-ttu-id="f9d3c-110">Vous devez créer un modèle d'observation à l'aide des outils BAM de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis le déployer à l'aide de l'outil de ligne de commande du gestionnaire BAM (bm.exe).</span><span class="sxs-lookup"><span data-stu-id="f9d3c-110">An observation model must be created by using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM tools and then deployed by using the BAM Manager command-line tool (bm.exe).</span></span>  
  
-   <span data-ttu-id="f9d3c-111">Un fichier de configuration de l’intercepteur doit être créé et déployé à l’aide de l’outil en ligne de commande Gestionnaire BAM (bm.exe).</span><span class="sxs-lookup"><span data-stu-id="f9d3c-111">An interceptor configuration file must be created and deployed by using the BAM Manager command line-tool (bm.exe).</span></span>  
  
-   <span data-ttu-id="f9d3c-112">L’utilisateur qui exécute l’application hôte doit être un membre de l’enregistreur d’événements d’activité BAM approprié (bam_\<activité\>_EventWriter) les rôles SQL Server pour autoriser l’application à lire des informations de configuration de l’intercepteur et d’écriture pour les activités BAM.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-112">The user running the host application must be a member of the appropriate BAM activity event writer (bam_\<activity\>_EventWriter) SQL Server roles to enable the application to read the interceptor configuration information and write to the BAM activities.</span></span>  
  
-   <span data-ttu-id="f9d3c-113">Vous devez modifier le fichier App.config ou l'application pour charger le service de suivi BAM, puis redémarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-113">The App.config file or the application itself must be modified to load the BAM tracking service and then restart the application.</span></span>  
  
 <span data-ttu-id="f9d3c-114">Ce n'est qu'une fois que vous aurez effectué ces tâches correctement que les événements commenceront à apparaître dans la base de données BAM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9d3c-114">Only after these tasks have been successfully completed will events begin appearing in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM database.</span></span>  
  
### <a name="deploying-an-observation-model"></a><span data-ttu-id="f9d3c-115">Déploiement d'un modèle d'observation</span><span class="sxs-lookup"><span data-stu-id="f9d3c-115">Deploying an Observation Model</span></span>  
 <span data-ttu-id="f9d3c-116">Vous devez avoir préalablement déployé un modèle d'observation avant de déployer un fichier de configuration d'intercepteur ou de capturer des activités BAM dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-116">You must have an observation model deployed before you can deploy an interceptor configuration file or capture BAM activities in your application.</span></span>  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a><span data-ttu-id="f9d3c-117">Pour déployer un modèle d'observation à l'aide de bm.exe</span><span class="sxs-lookup"><span data-stu-id="f9d3c-117">To deploy an observation model by using bm.exe</span></span>  
  
1.  <span data-ttu-id="f9d3c-118">Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-118">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2.  <span data-ttu-id="f9d3c-119">Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-119">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f9d3c-120">Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le modèle d'observation à déployer.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-120">Use the change directory command to move to the directory containing the observation model to deploy.</span></span> <span data-ttu-id="f9d3c-121">Par exemple, **cd c:\businessprocess\Orders**.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-121">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4.  <span data-ttu-id="f9d3c-122">Déployez le modèle d'observation à l'aide de bm.exe :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-122">Deploy the observation model by using bm.exe:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="f9d3c-123">Tracking\BM.exe déployer-all - definitionfile :\<*definitionfile.xml*\></span><span class="sxs-lookup"><span data-stu-id="f9d3c-123">Tracking\BM.exe deploy-all -definitionfile:\<*definitionfile.xml*\></span></span>  
  
     <span data-ttu-id="f9d3c-124">Veillez à remplacer \< *definitionfile.xml* \> avec le nom du fichier d’observation à déployer.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-124">Make sure you replace \<*definitionfile.xml*\> with the name of the observation file you want to deploy.</span></span> <span data-ttu-id="f9d3c-125">Pour plus d’options, consultez [les commandes de gestion de l’intercepteur](../core/interceptor-management-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f9d3c-125">For more options see [Interceptor Management Commands](../core/interceptor-management-commands.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d3c-126">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="f9d3c-127">Type **Exit**, puis appuyez sur ENTRÉE pour fermer l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-127">Type **Exit**, and then press ENTER to close the command prompt.</span></span>  
  
### <a name="deploying-an-interceptor-configuration-file"></a><span data-ttu-id="f9d3c-128">Déploiement d'un fichier de configuration d'intercepteur</span><span class="sxs-lookup"><span data-stu-id="f9d3c-128">Deploying an Interceptor Configuration File</span></span>  
 <span data-ttu-id="f9d3c-129">Vous devez déployer un fichier de configuration de l’intercepteur avant que votre application peut capturer des activités BAM.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-129">You must deploy an interceptor configuration file before your application can capture BAM activities.</span></span>  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a><span data-ttu-id="f9d3c-130">Pour déployer un fichier de configuration d'intercepteur à l'aide de bm.exe</span><span class="sxs-lookup"><span data-stu-id="f9d3c-130">To deploy an interceptor configuration file by using bm.exe</span></span>  
  
1.  <span data-ttu-id="f9d3c-131">Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-131">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2.  <span data-ttu-id="f9d3c-132">Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-132">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f9d3c-133">Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le fichier de configuration d'intercepteur à déployer.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-133">Use the change directory command to move to the directory containing the interceptor configuration file to deploy.</span></span> <span data-ttu-id="f9d3c-134">Par exemple, **cd c:\businessprocess\Orders**.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-134">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4.  <span data-ttu-id="f9d3c-135">Déployez le fichier de configuration d'intercepteur à l'aide de bm.exe :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-135">Deploy the interceptor configuration file by using bm.exe:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="f9d3c-136">Tracking\BM.exe déployer-intercepteur - filename :\<*icfile.xml*\></span><span class="sxs-lookup"><span data-stu-id="f9d3c-136">Tracking\BM.exe deploy-interceptor -filename:\<*icfile.xml*\></span></span>  
  
     <span data-ttu-id="f9d3c-137">Veillez à remplacer \< *icfile.xml* \> avec le nom du fichier de configuration de l’intercepteur à déployer.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-137">Make sure you replace \<*icfile.xml*\> with the name of the interceptor configuration file you want to deploy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d3c-138">Vous pouvez utiliser la **-Force : True** indicateur pour remplacer les sources d’événements existantes avec le même nom que ceux figurant dans votre fichier de configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-138">You can use the **-Force:True** flag to override existing event sources with the same name(s) as those in your interceptor configuration file.</span></span> <span data-ttu-id="f9d3c-139">Si vous le faites, assurez-vous que vous sauvegardez la configuration existante à l’aide de la **get-interceptor** commande.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-139">If you do so, make sure you back up the existing configuration by using the **get-interceptor** command.</span></span> <span data-ttu-id="f9d3c-140">L'utilisation de l'indicateur -Force:True pourrait supprimer des configurations d'intercepteur qui font référence aux sources d'événements remplacées.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-140">Using the -Force:True flag could delete any interceptor configurations that reference the event sources being overwritten.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d3c-141">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-141">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="f9d3c-142">Type **Exit**, puis appuyez sur ENTRÉE pour fermer l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-142">Type **Exit**, and then press ENTER to close the command prompt.</span></span>  
  
 <span data-ttu-id="f9d3c-143">Si vous avez déjà déployé votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], la nouvelle configuration ne sera chargée qu'au prochain intervalle d'interrogation.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-143">If you have already deployed your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application, the new configuration will not be loaded until the next polling interval.</span></span> <span data-ttu-id="f9d3c-144">Toutefois, si vous configurez et redémarrez votre application, la configuration est immédiatement récupérée.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-144">However, if you configure your application and restart it, the configuration will be picked up immediately.</span></span>  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a><span data-ttu-id="f9d3c-145">Ajout de l'utilisateur au rôle approprié de l'activité BAM</span><span class="sxs-lookup"><span data-stu-id="f9d3c-145">Adding the User to the Appropriate BAM Activity Role</span></span>  
 <span data-ttu-id="f9d3c-146">L'infrastructure de l'intercepteur BAM utilise les rôles SQL Server par activité pour contrôler l'accès aux activités et aux informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-146">The BAM Interceptor Framework uses per-activity SQL Server roles to control access to activities and configuration information.</span></span> <span data-ttu-id="f9d3c-147">Vous devez ajouter le compte d'utilisateur exécutant votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] au(x) rôle(s) approprié(s) de l'activité BAM dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-147">You must add the user account running your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application to the appropriate BAM activity role(s) in the BAM Primary Import database.</span></span>  
  
### <a name="configuring-the-application-to-load-the-bam-tracking-service"></a><span data-ttu-id="f9d3c-148">Configuration de l'application pour charger le service de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="f9d3c-148">Configuring the Application to Load the BAM Tracking Service</span></span>  
 <span data-ttu-id="f9d3c-149">Il existe trois scénarios de chargement du service de suivi BAM dans votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-149">There are three scenarios for loading the BAM tracking service in your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application:</span></span>  
  
-   <span data-ttu-id="f9d3c-150">Si votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] utilise déjà la classe WorkflowRuntime pour charger une section de configuration [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], vous pouvez ajouter les informations du service de suivi BAM à la section existante.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-150">If your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application already uses WorkflowRuntime to load a [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] configuration section, you can added BAM tracking service information to the existing section.</span></span>  
  
-   <span data-ttu-id="f9d3c-151">Si votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] n'utilise pas la classe WorkflowRuntime pour charger une section de configuration [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], vous devez ajouter du code pour charger une section personnalisée de votre fichier de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-151">If your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application does not use WorkflowRuntime to load a [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] configuration section, you will have to add code to load a custom section from your application configuration file.</span></span> <span data-ttu-id="f9d3c-152">Vous devez créer la section et lui ajouter les informations du service de suivi BAM.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-152">You will have to create the section and add the BAM tracking service information to it.</span></span>  
  
-   <span data-ttu-id="f9d3c-153">Si vous préférez coder la configuration en dur, vous pouvez utiliser l'API [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] pour charger le service de suivi par programme sans fichier de configuration ou charger la configuration depuis une source personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-153">If you prefer to hard-code the configuration, you can use the [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] API to programmatically load the tracking service without a configuration file, or to load the configuration from a custom source.</span></span>  
  
 <span data-ttu-id="f9d3c-154">Lorsque vous configurez l'application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-154">When configuring the [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application, note the following considerations:</span></span>  
  
-   <span data-ttu-id="f9d3c-155">L'intercepteur [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] ne prend en charge qu'une instance BamTrackingService par instance WorkflowRuntime.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-155">The [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] interceptor supports only one BamTrackingService per one WorkflowRuntime.</span></span>  
  
-   <span data-ttu-id="f9d3c-156">L'intercepteur [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] prend en charge plusieurs instances BamTrackingService par domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-156">The [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] interceptor supports multiple BamTrackingService instances per application domain.</span></span>  
  
    -   <span data-ttu-id="f9d3c-157">Un nombre N d'instances BamTrackingService est pris en charge pour un nombre N d'instances WorkflowRuntime.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-157">N number of BamTrackingService is supported for N number of WorkflowRuntime.</span></span>  
  
-   <span data-ttu-id="f9d3c-158">L'intercepteur génère une exception si des chaînes de connexion différentes sont utilisées pour séparer les instances BamTrackingService dans le même domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-158">The interceptor raises an exception if different connection strings are used for separate BamTrackingService instances in the same application domain.</span></span>  
  
-   <span data-ttu-id="f9d3c-159">L'intercepteur obtient la valeur d'intervalle d'interrogation de la configuration d'intercepteur auprès de la première instance BamTrackingService qui démarre.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-159">The interceptor obtains the IC polling interval value from the first BamTrackingService instance that starts.</span></span>  
  
-   <span data-ttu-id="f9d3c-160">L'intercepteur arrête le thread d'interrogation de la configuration d'intercepteur lorsque la dernière instance BamTrackingService dans le domaine d'application est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-160">The interceptor stops the IC polling thread when last BamTrackingService in application domain is stopped</span></span>  
  
 <span data-ttu-id="f9d3c-161">Pour plus d’informations sur la classe WorkflowRuntime et le chargement des informations de configuration, consultez [http://go.microsoft.com/fwlink/?LinkId=83314](http://go.microsoft.com/fwlink/?LinkId=83314).</span><span class="sxs-lookup"><span data-stu-id="f9d3c-161">For more information on WorkflowRuntime and loading configuration information, see [http://go.microsoft.com/fwlink/?LinkId=83314](http://go.microsoft.com/fwlink/?LinkId=83314).</span></span>  
  
##### <a name="to-configure-the-appconfig-file-for-the-bam-tracking-service"></a><span data-ttu-id="f9d3c-162">Pour configurer le fichier App.config pour le service de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="f9d3c-162">To configure the App.config file for the BAM tracking service</span></span>  
  
1.  <span data-ttu-id="f9d3c-163">Ouvrez le fichier App.config associé à votre application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-163">Open the App.config file associated with your application.</span></span> <span data-ttu-id="f9d3c-164">Vous pouvez utiliser Notepad.exe ou un autre éditeur de texte pour cette tâche.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-164">You can use Notepad.exe or another text editor for this task.</span></span>  
  
2.  <span data-ttu-id="f9d3c-165">Ajoutez le service de suivi BAM en insérant les informations de configuration suivantes dans le fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-165">Add the BAM Tracking service by inserting the following configuration information into the App.config file.</span></span> <span data-ttu-id="f9d3c-166">Il doit être positionné de sorte à être un enfant de l'élément `configuration`.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-166">It should be positioned so that it is a child of the `configuration` element.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d3c-167">L'élément de section doit correspondre au nom utilisé par votre code d'application lors de l'utilisation de la classe WorkflowRuntime.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-167">The section element should correspond to the name used by your application code when using the WorkflowRuntime class.</span></span>  
  
    ```  
    <!-- The element name must match the one expected by WorkflowRuntime in your WF application -->  
    <WorkflowServiceContainer>  
      <Services>  
        <add type="Microsoft.BizTalk.Bam.Interceptors.Workflow.BamTrackingService, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  
       ConnectionString="Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"   
          PollingIntervalSec="5"/>  
        </Services>  
    </WorkflowServiceContainer>  
    ```  
  
3.  <span data-ttu-id="f9d3c-168">Modifier la **ConnectionString** attribut pour correspondre à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-168">Modify the **ConnectionString** attribute to match your environment.</span></span>  
  
4.  <span data-ttu-id="f9d3c-169">Redémarrez votre application.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-169">Restart your application.</span></span>  
  
##### <a name="to-modify-your-application-to-load-a-custom-configuration-section"></a><span data-ttu-id="f9d3c-170">Pour modifier votre application afin de charger une section de configuration personnalisée</span><span class="sxs-lookup"><span data-stu-id="f9d3c-170">To modify your application to load a custom configuration section</span></span>  
  
1.  <span data-ttu-id="f9d3c-171">Ouvrez votre projet Windows Workflow Foundation dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-171">Open your Windows Workflow Foundation project in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f9d3c-172">Ajoutez une nouvelle instance BamTrackingService avec les paramètres appropriés à l'instance de la classe WorkflowRuntime de l'application :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-172">Add a new instance of BamTrackingService with appropriate parameters to the application's instance of WorkflowRuntime:</span></span>  
  
    ```  
    // !! Replace "WorkflowServiceContainer" with the section name  
    // you used in your App.config file.  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime("WorkflowServiceContainer");  
    ```  
  
3.  <span data-ttu-id="f9d3c-173">Recompilez et déployez l'application modifiée.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-173">Recompile and deploy the modified application.</span></span>  
  
##### <a name="to-modify-your-application-to-programmatically-load-the-bam-tracking-service"></a><span data-ttu-id="f9d3c-174">Pour modifier votre application afin de charger par programme le service de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="f9d3c-174">To modify your application to programmatically load the BAM tracking service</span></span>  
  
1.  <span data-ttu-id="f9d3c-175">Ouvrez votre projet Windows Workflow Foundation dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-175">Open your Windows Workflow Foundation project in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f9d3c-176">Ajoutez une nouvelle instance BamTrackingService avec les paramètres appropriés à l'instance de la classe WorkflowRuntime de l'application :</span><span class="sxs-lookup"><span data-stu-id="f9d3c-176">Add a new instance of BamTrackingService with appropriate parameters to the application's instance of WorkflowRuntime:</span></span>  
  
    ```  
    string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"  
    int pollingInterval = 5;  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
    workflowRuntime.AddService(new BamTrackingService(connectionString, pollingInterval));  
    ```  
  
     <span data-ttu-id="f9d3c-177">Vous pouvez ajouter ou supprimer des paramètres en fonction de votre environnement spécifique.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-177">You can add or remove parameters based on your specific environment.</span></span>  
  
3.  <span data-ttu-id="f9d3c-178">Recompilez et déployez l'application modifiée.</span><span class="sxs-lookup"><span data-stu-id="f9d3c-178">Recompile and deploy the modified application.</span></span>