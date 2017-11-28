---
title: "Comment configurer une Application Windows Communication Foundation pour l’Interception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37f2ccde-aa79-470a-ac31-57e4168dc54a
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 103eb58223ba4acd61d909640bacda76d08efe8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-windows-communication-foundation-application-for-interception"></a><span data-ttu-id="0d153-102">Configuration d'une application Windows Communication Foundation pour l'interception</span><span class="sxs-lookup"><span data-stu-id="0d153-102">How to Configure a Windows Communication Foundation Application for Interception</span></span>
<span data-ttu-id="0d153-103">Avant de commencer à collecter les données d'activité BAM, vous devez installer le logiciel de l'intercepteur BAM et configurer votre application afin d'utiliser le service de l'intercepteur BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d153-103">You must install the BAM interceptor software and configure your application to use the BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] interceptor service before you can begin collecting BAM activity data.</span></span> <span data-ttu-id="0d153-104">Vous devez avoir correctement installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ses dépendances et avoir créé au moins un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0d153-104">It is assumed that you have successfully installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies and have created at least one BizTalk group.</span></span>  
  
## <a name="installing-the-bam-eventing-software"></a><span data-ttu-id="0d153-105">Installation du logiciel BAM-Événements</span><span class="sxs-lookup"><span data-stu-id="0d153-105">Installing the BAM-Eventing Software</span></span>  
 <span data-ttu-id="0d153-106">Avant de configurer votre application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] afin d'utiliser l'intercepteur BAM pour [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], vous devez installer le logiciel BAM-Événements à l'aide du programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d153-106">Before you can configure your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application to use the BAM interceptor for [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program.</span></span> <span data-ttu-id="0d153-107">Pour plus d’informations sur l’installation du logiciel BAM-événements et l’enregistrement des compteurs de performance, consultez [l’installation du logiciel BAM-événements](../core/installing-the-bam-eventing-software.md).</span><span class="sxs-lookup"><span data-stu-id="0d153-107">For more information about installing the BAM-Eventing software and registering the performance counters, see [Installing the BAM-Eventing Software](../core/installing-the-bam-eventing-software.md).</span></span>  
  
## <a name="configuring-a-wcf-application-for-tracking"></a><span data-ttu-id="0d153-108">Configuration d'une application WCF pour le suivi</span><span class="sxs-lookup"><span data-stu-id="0d153-108">Configuring a WCF Application for Tracking</span></span>  
 <span data-ttu-id="0d153-109">Vous devez effectuer quatre tâches avant que votre application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] ne puisse commencer à écrire des informations sur les événements BAM :</span><span class="sxs-lookup"><span data-stu-id="0d153-109">Four tasks must be completed before your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application can begin writing BAM event information:</span></span>  
  
-   <span data-ttu-id="0d153-110">Un modèle d’observation doit être créé à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM des outils et puis déployé à l’aide de l’outil de ligne de commande du gestionnaire BAM (bm.exe).</span><span class="sxs-lookup"><span data-stu-id="0d153-110">An observation model must be created by using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM tools and then deployed by using the BAM Manager command line tool (bm.exe).</span></span>  
  
-   <span data-ttu-id="0d153-111">Vous devez créer un fichier de configuration d'intercepteur et le déployer à l'aide de l'outil de ligne de commande du gestionnaire BAM (bm.exe).</span><span class="sxs-lookup"><span data-stu-id="0d153-111">An interceptor configuration file must be created and deployed by using the BAM Manager command line tool (bm.exe).</span></span>  
  
-   <span data-ttu-id="0d153-112">L’utilisateur qui exécute l’application hôte doit être un membre de l’enregistreur d’événements d’activité BAM approprié (bam_\<activité > _EventWriter) les rôles SQL Server pour permettre à l’application lire des informations de configuration de l’intercepteur et écrire dans l’analyse BAM activités.</span><span class="sxs-lookup"><span data-stu-id="0d153-112">The user running the host application must be a member of the appropriate BAM activity event writer (bam_\<activity>_EventWriter) SQL Server roles to enable the application to read the interceptor configuration information and write to the BAM activities.</span></span>  
  
-   <span data-ttu-id="0d153-113">Vous devez modifier le fichier App.config pour le serveur et l'application cliente pour charger le service de suivi BAM.</span><span class="sxs-lookup"><span data-stu-id="0d153-113">The App.config file for the server and client application must be modified to load the BAM tracking service.</span></span> <span data-ttu-id="0d153-114">Une fois le fichier App.config modifié, vous devez redémarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="0d153-114">After the App.config file has been modified, the application must be restarted.</span></span>  
  
 <span data-ttu-id="0d153-115">Ce n'est qu'une fois que vous aurez effectué ces tâches correctement que les événements commenceront à apparaître dans la base de données BAM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d153-115">Only after these tasks have been successfully completed will events begin appearing in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM database.</span></span>  
  
### <a name="deploying-an-observation-model"></a><span data-ttu-id="0d153-116">Déploiement d'un modèle d'observation</span><span class="sxs-lookup"><span data-stu-id="0d153-116">Deploying an Observation Model</span></span>  
 <span data-ttu-id="0d153-117">Vous devez avoir préalablement déployé un modèle d'observation avant de déployer un fichier de configuration d'intercepteur ou de capturer des activités BAM dans votre application.</span><span class="sxs-lookup"><span data-stu-id="0d153-117">You must have an observation model deployed before you can deploy an interceptor configuration file or capture BAM activities in your application.</span></span>  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a><span data-ttu-id="0d153-118">Pour déployer un modèle d'observation à l'aide de bm.exe</span><span class="sxs-lookup"><span data-stu-id="0d153-118">To deploy an observation model by using bm.exe</span></span>  
  
1.  <span data-ttu-id="0d153-119">Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="0d153-119">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2.  <span data-ttu-id="0d153-120">Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d153-120">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0d153-121">Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le modèle d'observation à déployer.</span><span class="sxs-lookup"><span data-stu-id="0d153-121">Use the change directory command to move to the directory containing the observation model to deploy.</span></span> <span data-ttu-id="0d153-122">Par exemple, **cd c:\businessprocess\Orders**.</span><span class="sxs-lookup"><span data-stu-id="0d153-122">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4.  <span data-ttu-id="0d153-123">Déployer le modèle d’observation à l’aide de bm.exe :</span><span class="sxs-lookup"><span data-stu-id="0d153-123">Deploy the observation model using bm.exe:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="0d153-124">Tracking\bm.exe déployer-all - Definitionfile :\<*definitionfile.xml*></span><span class="sxs-lookup"><span data-stu-id="0d153-124">Tracking\bm.exe deploy-all -Definitionfile:\<*definitionfile.xml*></span></span>  
  
     <span data-ttu-id="0d153-125">Veillez à remplacer \< *definitionfile.xml*> avec le nom du fichier de modèle d’observation à déployer.</span><span class="sxs-lookup"><span data-stu-id="0d153-125">Make sure you replace \<*definitionfile.xml*> with the name of the observation model file you want to deploy.</span></span> <span data-ttu-id="0d153-126">Pour plus d’options, consultez [les commandes de gestion de l’intercepteur](../core/interceptor-management-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0d153-126">For more options see [Interceptor Management Commands](../core/interceptor-management-commands.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-127">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0d153-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="0d153-128">Type **Exit** et appuyez sur ENTRÉE pour fermer l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="0d153-128">Type **Exit** and then press ENTER to close the command prompt.</span></span>  
  
### <a name="deploying-an-interceptor-configuration-file"></a><span data-ttu-id="0d153-129">Déploiement d'un fichier de configuration d'intercepteur</span><span class="sxs-lookup"><span data-stu-id="0d153-129">Deploying an Interceptor Configuration File</span></span>  
 <span data-ttu-id="0d153-130">Vous devez déployer un fichier de configuration d'intercepteur pour que votre application puisse capturer des activités BAM.</span><span class="sxs-lookup"><span data-stu-id="0d153-130">You must deploy an interceptor configuration file before your application will be able to capture BAM activities.</span></span>  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a><span data-ttu-id="0d153-131">Pour déployer un fichier de configuration d'intercepteur à l'aide de bm.exe</span><span class="sxs-lookup"><span data-stu-id="0d153-131">To deploy an interceptor configuration file by using bm.exe</span></span>  
  
1.  <span data-ttu-id="0d153-132">Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="0d153-132">Click **Start** and then click **Run** to open the Windows command prompt.</span></span>  
  
2.  <span data-ttu-id="0d153-133">Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d153-133">Type **cmd** in the **Open** field, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0d153-134">Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le fichier de configuration d'intercepteur à déployer.</span><span class="sxs-lookup"><span data-stu-id="0d153-134">Use the change directory command to move to the directory containing the interceptor configuration file to deploy.</span></span> <span data-ttu-id="0d153-135">Par exemple, **cd c:\businessprocess\Orders**.</span><span class="sxs-lookup"><span data-stu-id="0d153-135">For example, **cd c:\businessprocess\Orders**.</span></span>  
  
4.  <span data-ttu-id="0d153-136">Déployez le fichier de configuration d'intercepteur à l'aide de bm.exe :</span><span class="sxs-lookup"><span data-stu-id="0d153-136">Deploy the interceptor configuration file by using bm.exe:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="0d153-137">Tracking\bm.exe déployer-intercepteur - Filename :\<*icfile.xml*></span><span class="sxs-lookup"><span data-stu-id="0d153-137">Tracking\bm.exe deploy-interceptor -Filename:\<*icfile.xml*></span></span>  
  
     <span data-ttu-id="0d153-138">Veillez à remplacer \< *icfile.xml*> par le nom du fichier de configuration de l’intercepteur à déployer.</span><span class="sxs-lookup"><span data-stu-id="0d153-138">Make sure you replace \<*icfile.xml*> with the name of the interceptor configuration file you want to deploy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-139">Vous pouvez utiliser la **-Force : True** indicateur pour remplacer les sources d’événements existantes avec le même nom que ceux figurant dans votre fichier de configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="0d153-139">You can use the **-Force:True** flag to override existing event sources with the same name(s) as those in your interceptor configuration file.</span></span> <span data-ttu-id="0d153-140">Si vous le faites, assurez-vous que vous sauvegardez la configuration existante à l’aide de la **get-interceptor** commande.</span><span class="sxs-lookup"><span data-stu-id="0d153-140">If you do so, make sure you back up the existing configuration by using the **get-interceptor** command.</span></span> <span data-ttu-id="0d153-141">L'utilisation de l'indicateur -Force:True pourrait supprimer des configurations d'intercepteur qui font référence aux sources d'événements remplacées.</span><span class="sxs-lookup"><span data-stu-id="0d153-141">Using the -Force:True flag could delete any interceptor configurations that reference the event sources being overwritten.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-142">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0d153-142">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="0d153-143">Type **Exit** et appuyez sur ENTRÉE pour fermer l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="0d153-143">Type **Exit** and then press ENTER to close the command prompt.</span></span>  
  
 <span data-ttu-id="0d153-144">Si vous avez déjà déployé votre application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], la nouvelle configuration ne sera chargée qu'au prochain intervalle d'interrogation.</span><span class="sxs-lookup"><span data-stu-id="0d153-144">If you have already deployed your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, the new configuration will not be loaded until the next polling interval.</span></span> <span data-ttu-id="0d153-145">Toutefois, si vous configurez et redémarrez votre application, la configuration est immédiatement récupérée.</span><span class="sxs-lookup"><span data-stu-id="0d153-145">However, if you configure your application and restart it, the configuration will be picked up immediately.</span></span>  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a><span data-ttu-id="0d153-146">Ajout de l'utilisateur au rôle approprié de l'activité BAM</span><span class="sxs-lookup"><span data-stu-id="0d153-146">Adding the User to the Appropriate BAM Activity Role</span></span>  
 <span data-ttu-id="0d153-147">L'infrastructure de l'intercepteur BAM utilise les rôles SQL Server par activité pour contrôler l'accès aux activités et aux informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d153-147">The BAM Interceptor Framework uses per-activity SQL Server roles to control access to activities and configuration information.</span></span> <span data-ttu-id="0d153-148">Vous devez ajouter le compte d'utilisateur exécutant votre application WCF au(x) rôle(s) approprié(s) de l'activité BAM dans la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="0d153-148">You must add the user account running your WCF application to the appropriate BAM activity role(s) in the BAMPrimaryImport database.</span></span>  
  
### <a name="configuring-the-windows-communication-foundation-application-to-load-the-bam-tracking-service"></a><span data-ttu-id="0d153-149">Configuration de l'application Windows Communication Foundation pour charger le service de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="0d153-149">Configuring the Windows Communication Foundation Application to Load the BAM Tracking Service</span></span>  
 <span data-ttu-id="0d153-150">Pour configurer l'application de manière qu'elle charge le service de suivi BAM, ajoutez quelques lignes au fichier App.config du serveur ou de l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="0d153-150">You configure your application to load the BAM tracking service by adding a few lines to the App.config file for your server or client application.</span></span>  
  
 <span data-ttu-id="0d153-151">Pour activer le suivi BAM sur votre serveur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] ou application cliente, vous devez modifier le fichier de configuration App.config en incluant un nouveau comportement de point de terminaison et une extension de comportement, et en ajoutant un attribut de configuration de comportement.</span><span class="sxs-lookup"><span data-stu-id="0d153-151">To enable BAM tracking in your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] server or client application, you will need to modify the App.config configuration file to include an additional endpoint behavior and behavior extension and add a behavior configuration attribute.</span></span> <span data-ttu-id="0d153-152">Les formats du service et des modèles client sont similaires.</span><span class="sxs-lookup"><span data-stu-id="0d153-152">The formats of the service and client templates are similar.</span></span>  
  
 <span data-ttu-id="0d153-153">Lorsque vous configurez l'application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], notez les points suivants.</span><span class="sxs-lookup"><span data-stu-id="0d153-153">When configuring the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, note the following.</span></span> <span data-ttu-id="0d153-154">Si plusieurs comportements de point de terminaison BAM sont définis dans le fichier App.config pour la même application (même client ou service), l'analyse BAM effectue les actions suivantes.</span><span class="sxs-lookup"><span data-stu-id="0d153-154">If there is more than one BAM endpoint behaviors defined in the App.config for the same application, that is, the same client or service, BAM will take the following actions.</span></span>  
  
-   <span data-ttu-id="0d153-155">Si les chaînes de connexion diffèrent, l'analyse BAM génère une exception.</span><span class="sxs-lookup"><span data-stu-id="0d153-155">If the connection strings differ, BAM will raise and exception.</span></span>  
  
-   <span data-ttu-id="0d153-156">Si seul l'intervalle d'interrogation diffère, l'analyse BAM en sélectionne un et continue.</span><span class="sxs-lookup"><span data-stu-id="0d153-156">If only the polling interval differs, BAM will select one and move on.</span></span> <span data-ttu-id="0d153-157">Au moment de la conception, il n'est pas possible de déterminer celui qui sera sélectionné.</span><span class="sxs-lookup"><span data-stu-id="0d153-157">It is not possible at design time to determine which one will be selected.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d153-158">Si les chaînes de connexion sont identiques, c'est-à-dire qu'elles font référence au même ordinateur, le traitement BAM est normal.</span><span class="sxs-lookup"><span data-stu-id="0d153-158">If the connection strings are the same, meaning that they reference the same computer, BAM processing will proceed normally.</span></span>  
  
 <span data-ttu-id="0d153-159">L'exemple suivant de modèle App.config est configuré pour une application serveur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d153-159">The following sample App.config template is configured for a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] server application.</span></span> <span data-ttu-id="0d153-160">Il définit un point de terminaison qui utilise un comportement personnalisé « bamEndpointBehavior » configuré pour utiliser l'intercepteur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d153-160">It defines an endpoint that uses a custom behavior "bamEndpointBehavior" that is configured to use the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] interceptor.</span></span>  
  
```  
<system.serviceModel>  
  <services>  
    <service name="Service.CreditCardAuthorization">  
      <!-- The endpoint will use the "bamEndpointBehavior" -->   
      <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    </service>  
  </services>  
  <bindings>  
    <wsDualHttpBinding>  
      <binding name="wsDualHttpBinding_ICreditCardAuthorization" transactionFlow="true" />  
    </wsDualHttpBinding>  
  </bindings>  
  <behaviors>  
    <endpointBehaviors>  
      <!-- Define a new behavior named "bamEndpointBehavior" -->  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <extensions>  
    <behaviorExtensions>  
      <!-- Define a new enpoint behavior extension using WCF interceptor -->  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
  </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0d153-161">Vous devez légèrement modifier ce modèle avant de l'utiliser dans votre propre fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="0d153-161">You will need to make small changes to this template before using it in your own App.config file.</span></span>  
  
##### <a name="to-use-this-template-in-your-wcf-service-appconfig-file"></a><span data-ttu-id="0d153-162">Pour utiliser ce modèle dans votre fichier App.config du service WCF</span><span class="sxs-lookup"><span data-stu-id="0d153-162">To use this template in your WCF service App.config file</span></span>  
  
1.  <span data-ttu-id="0d153-163">Ouvrez le fichier App.config associé à votre application.</span><span class="sxs-lookup"><span data-stu-id="0d153-163">Open the App.config file associated with your application.</span></span> <span data-ttu-id="0d153-164">Vous pouvez utiliser Notepad.exe ou un autre éditeur de texte pour cette tâche.</span><span class="sxs-lookup"><span data-stu-id="0d153-164">You can use Notepad.exe or another text editor for this task.</span></span>  
  
2.  <span data-ttu-id="0d153-165">Ajoutez l'extension de comportement [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior à l'élément `extensions` à l'aide du code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="0d153-165">Add the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior behavior extension to the `extensions` element by using the following XML:</span></span>  
  
    ```  
    <behaviorExtensions>  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-166">Vous pouvez adapter le nom de l'extension de comportement, « BamEndpointBehaviorExtension », à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="0d153-166">The behavior extension is named "BamEndpointBehaviorExtension" and can be changed as needed to suit your environment.</span></span>  
  
3.  <span data-ttu-id="0d153-167">Ajoutez un nouveau comportement de point de terminaison qui utilise la nouvelle extension de comportement à l'élément `behaviors`, à l'aide du code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="0d153-167">Add a new endpoint behavior that uses the new behavior extension to the `behaviors` element by using the following XML.</span></span> <span data-ttu-id="0d153-168">L'extension de comportement fournit une chaîne de connexion et un intervalle d'interrogation en secondes.</span><span class="sxs-lookup"><span data-stu-id="0d153-168">The behavior extension provides a connection string and polling interval in seconds.</span></span>  
  
    ```  
    <endpointBehaviors>  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
    ```  
  
     <span data-ttu-id="0d153-169">Remplacez la source de données par le nom de l'ordinateur hébergeant la base de données BamPrimaryImport dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="0d153-169">Replace the Data Source with the name of the computer hosting the BamPrimaryImport database in your environment.</span></span> <span data-ttu-id="0d153-170">Adaptez l'intervalle d'interrogation aux conditions requises ; un nombre élevé signifie que l'intercepteur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] mettra plus longtemps à détecter les modifications de configuration.</span><span class="sxs-lookup"><span data-stu-id="0d153-170">Change the polling interval to suit your requirements; a higher number means that the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] interceptor will take longer to detect configuration changes.</span></span> <span data-ttu-id="0d153-171">Si vous avez modifié le nom de l'extension de comportement, utilisez-le pour remplacer « BamEndpointBehaviorExtension ».</span><span class="sxs-lookup"><span data-stu-id="0d153-171">If you changed the name of the behavior extension, use it to replace "BamEndpointBehaviorExtension".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-172">Vous pouvez adapter le nom du comportement, « bamEndpointBehavior », à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="0d153-172">The behavior name is "bamEndpointBehavior" and can be changed to suit your environment.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-173">Évitez d'utiliser une combinaison de nom d'utilisateur/mot de passe en texte clair lorsque vous spécifiez l'élément `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="0d153-173">Avoid using a cleartext username/password combination when specifying `ConnectionString`.</span></span> <span data-ttu-id="0d153-174">Cela pourrait compromettre votre serveur de bases de données.</span><span class="sxs-lookup"><span data-stu-id="0d153-174">Doing so may compromise your database server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-175">Vous devez spécifier un `PollingIntervalSec` supérieur ou égal à 5 (secondes).</span><span class="sxs-lookup"><span data-stu-id="0d153-175">You must specify an `PollingIntervalSec` greater than or equal to 5 (seconds).</span></span> <span data-ttu-id="0d153-176">Si vous spécifiez une valeur inférieure ou omettez l'élément `PollingIntervalSec`, une erreur est générée et l'interception n'est pas configurée.</span><span class="sxs-lookup"><span data-stu-id="0d153-176">If you specify a lower value or omit the `PollingIntervalSec` element, an error will be raised and interception will not be configured.</span></span>  
  
4.  <span data-ttu-id="0d153-177">Ajoutez l'attribut `behaviorConfiguration` au point de terminaison que vous allez suivre et nommez le nouveau comportement :</span><span class="sxs-lookup"><span data-stu-id="0d153-177">Add the `behaviorConfiguration` attribute to the endpoint you will be tracking and provide the name of the new behavior:</span></span>  
  
    ```  
    <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0d153-178">Si vous avez utilisé un autre nom de comportement, indiquez-le à la place.</span><span class="sxs-lookup"><span data-stu-id="0d153-178">If you used a different behavior name, supply it instead.</span></span>  
  
     <span data-ttu-id="0d153-179">Vous pouvez appliquer la configuration du comportement à plusieurs points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0d153-179">You can apply the behavior configuration to multiple endpoints.</span></span>  
  
5.  <span data-ttu-id="0d153-180">Enregistrez le fichier App.config modifié et redémarrez votre application.</span><span class="sxs-lookup"><span data-stu-id="0d153-180">Save the modified App.config file and restart your application.</span></span>