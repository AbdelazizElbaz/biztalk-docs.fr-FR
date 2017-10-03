---
title: "Comment activer le suivi de l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4da99e74-a41d-4ab1-a07d-e3bee6187216
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9cf7cddd25f3f01b6203c050a4391e16cedc989
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-tracing-in-bam"></a><span data-ttu-id="54ef8-102">Activation du suivi dans BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-102">How to Enable Tracing in BAM</span></span>
<span data-ttu-id="54ef8-103">Vous pouvez activer le suivi dans BAM afin de faciliter la résolution des problèmes susceptibles de survenir dans les cinq composants BAM suivants :</span><span class="sxs-lookup"><span data-stu-id="54ef8-103">You can enable tracing in BAM to help troubleshoot problems within the following five BAM components:</span></span>  
  
-   <span data-ttu-id="54ef8-104">utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-104">BAM Management utility</span></span>  
  
-   <span data-ttu-id="54ef8-105">Bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-105">BAM event bus</span></span>  
  
-   <span data-ttu-id="54ef8-106">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-106">BAM portal</span></span>  
  
-   <span data-ttu-id="54ef8-107">La génération d’alertes BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-107">BAM alerting</span></span>  
  
-   <span data-ttu-id="54ef8-108">Intercepteur WCF BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-108">BAM WCF Interceptor</span></span>  
  
## <a name="enabling-tracing-for-the-bam-management-utility"></a><span data-ttu-id="54ef8-109">Activation du suivi pour l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-109">Enabling Tracing for the BAM Management Utility</span></span>  
 <span data-ttu-id="54ef8-110">En activant le suivi de cet utilitaire, vous pouvez récupérer des informations sur les échecs de déploiement.</span><span class="sxs-lookup"><span data-stu-id="54ef8-110">You can obtain information about deployment failures by enabling tracing for the BAM Management utility.</span></span> <span data-ttu-id="54ef8-111">Pour cela, de deux manières.</span><span class="sxs-lookup"><span data-stu-id="54ef8-111">You can do this in two ways.</span></span> <span data-ttu-id="54ef8-112">activer le suivi depuis la ligne de commande pour certaines commandes BM.exe, ou modifier le fichier de configuration de l'utilitaire de gestion de l'analyse BAM afin d'activer le suivi, pour toutes les commandes BM.exe.</span><span class="sxs-lookup"><span data-stu-id="54ef8-112">You can enable tracing via the command line for specific BM.exe commands, or you can modify the BAM Management utility configuration file to enable tracing for all BM.exe commands.</span></span>  
  
### <a name="using-the-command-line"></a><span data-ttu-id="54ef8-113">Utilisation de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="54ef8-113">Using the Command Line</span></span>  
 <span data-ttu-id="54ef8-114">Le suivi de ligne de commande BM.exe est activé à l’aide de la **-Trace : sur &#124; off** basculer.</span><span class="sxs-lookup"><span data-stu-id="54ef8-114">BM.exe command line tracing is activated using the **-Trace:on&#124;off** switch.</span></span> <span data-ttu-id="54ef8-115">L'utilisation de l'option Trace remplace les paramètres du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="54ef8-115">Using the Trace switch overrides the settings in the configuration file.</span></span>  
  
 <span data-ttu-id="54ef8-116">L'option est utilisée conjointement avec toute commande BM.exe classique.</span><span class="sxs-lookup"><span data-stu-id="54ef8-116">The switch is used in conjunction with any normal BM.exe command.</span></span>  
  
 <span data-ttu-id="54ef8-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="54ef8-117">For example:</span></span>  
  
 <span data-ttu-id="54ef8-118">**BM.exe déployer-all - DefinitionFile:PO.xml – Trace : sur**</span><span class="sxs-lookup"><span data-stu-id="54ef8-118">**bm.exe deploy-all -DefinitionFile:PO.xml –Trace:On**</span></span>  
  
### <a name="using-the-configuration-file"></a><span data-ttu-id="54ef8-119">Utilisation du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="54ef8-119">Using the Configuration File</span></span>  
 <span data-ttu-id="54ef8-120">Vous pouvez activer le suivi en modifiant le fichier de configuration BM.exe.config situé dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span><span class="sxs-lookup"><span data-stu-id="54ef8-120">You can enable tracing by modifying the BM.exe.config configuration file located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking folder.</span></span> <span data-ttu-id="54ef8-121">Ce fichier contient un **system.diagnostics** section qui contient les éléments de suivi.</span><span class="sxs-lookup"><span data-stu-id="54ef8-121">This file contains a **system.diagnostics** section which contains the tracing elements.</span></span> <span data-ttu-id="54ef8-122">Supprimez les commentaires pour activer le suivi.</span><span class="sxs-lookup"><span data-stu-id="54ef8-122">Remove the comment to enable tracing.</span></span> <span data-ttu-id="54ef8-123">Par défaut, le suivi est désactivé.</span><span class="sxs-lookup"><span data-stu-id="54ef8-123">By default, tracing is not enabled.</span></span>  
  
 `<system.diagnostics>`  
  
 `<!-- To turn on BAM tracing, remove this comment or use the "-trace:on" command-line switch`  
  
 `<switches>`  
  
 `<add name="bm" value="1" />`  
  
 `<add name="Microsoft.BizTalk.Bam.Management" value="1" />`  
  
 `</switches>`  
  
 `-->`  
  
## <a name="enabling-tracing-for-the-bam-event-bus"></a><span data-ttu-id="54ef8-124">Activation du suivi pour le bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-124">Enabling Tracing for the BAM Event Bus</span></span>  
 <span data-ttu-id="54ef8-125">L'activation du suivi pour le bus d'événements BAM peut vous permettre de diagnostiquer deux catégories d'erreurs de stockage de base de données :</span><span class="sxs-lookup"><span data-stu-id="54ef8-125">Enabling tracing for the BAM event bus can help you diagnose two classes of database storage errors:</span></span>  
  
-   <span data-ttu-id="54ef8-126">les erreurs issues d'événements du service BizTalk Server lors de l'utilisation de l'Éditeur de modèle de suivi ;</span><span class="sxs-lookup"><span data-stu-id="54ef8-126">Storage errors originating from events from the BizTalk Server service when using the Tracking Profile Editor.</span></span>  
  
-   <span data-ttu-id="54ef8-127">les erreurs générées lors de l'utilisation des API de flux d'événements mis en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="54ef8-127">Storage errors generated when using the buffered event stream APIs.</span></span>  
  
 <span data-ttu-id="54ef8-128">Pour activer le suivi pour le bus d'événements BAM, modifiez ou ajoutez la section suivante du fichier BTSNTSvc.exe.config situé dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54ef8-128">To enable tracing for the BAM event bus, edit or add the following section of the BTSNTSvc.exe.config file located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] folder.</span></span>  
  
 `<system.diagnostics>`  
  
 `<switches>`  
  
 `<add name="Microsoft.BizTalk.Bam.EventBus" value="1" />`  
  
 `</switches>`  
  
 `<trace autoflush="true" indentsize="4">`  
  
 `<listeners>`  
  
 `<add name="Text" type="System.Diagnostics.TextWriterTraceListener" initializeData="c:\tdds.log"/>`  
  
 `</listeners>`  
  
 `</trace>`  
  
 `</system.diagnostics>`  
  
#### <a name="to-enable-tracing-for-the-bam-event-bus"></a><span data-ttu-id="54ef8-129">Pour activer le suivi pour le bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-129">To enable tracing for the BAM Event bus</span></span>  
  
1.  <span data-ttu-id="54ef8-130">Modifiez le fichier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config.</span><span class="sxs-lookup"><span data-stu-id="54ef8-130">Edit the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config file.</span></span>  
  
2.  <span data-ttu-id="54ef8-131">Recherchez le \<system.diagnostics > et  \< /System.Diagnostics > balise.</span><span class="sxs-lookup"><span data-stu-id="54ef8-131">Locate the \<system.diagnostics> and \</system.diagnostics> tag.</span></span> <span data-ttu-id="54ef8-132">Si vous ne les trouvez pas dans le fichier, copiez le code indiqué plus haut et collez-le dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="54ef8-132">If they are not present in the file, copy the code listed above and paste it into the configuration file.</span></span>  
  
3.  <span data-ttu-id="54ef8-133">Supprimez les marques de commentaires que les diagnostics système section en plaçant le délimiteur de commentaire de fin ('-->') d’après le \</System.Diagnostics > balise avant le \<system.diagnostics > balise.</span><span class="sxs-lookup"><span data-stu-id="54ef8-133">Uncomment the Uncomment the system diagnostics section by moving the end comment delimiter ('-->') from after the \</system.diagnostics> tag to before the \<system.diagnostics> tag.</span></span>  
  
4.  <span data-ttu-id="54ef8-134">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="54ef8-134">Save the file.</span></span>  
  
## <a name="enabling-tracing-for-the-bam-portal"></a><span data-ttu-id="54ef8-135">Activation du suivi pour le portail BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-135">Enabling Tracing for the BAM Portal</span></span>  
 <span data-ttu-id="54ef8-136">L'activation du suivi pour le portail BAM vous permet de résoudre les problèmes de connectivité.</span><span class="sxs-lookup"><span data-stu-id="54ef8-136">Enabling tracing for the BAM portal allows you to troubleshoot connectivity issues.</span></span>  
  
 <span data-ttu-id="54ef8-137">Le portail BAM est une application ASP.NET qui suit le protocole standard de suivi.</span><span class="sxs-lookup"><span data-stu-id="54ef8-137">The BAM portal is an ASP.NET application, and follows the standard protocol for tracing.</span></span> <span data-ttu-id="54ef8-138">Dans le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, fichier, il existe une section intitulée \<trace > que vous pouvez activer.</span><span class="sxs-lookup"><span data-stu-id="54ef8-138">Within the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config file, there is a section called \<trace> which you can enable.</span></span>  
  
#### <a name="to-enable-tracing-for-the-bam-portal"></a><span data-ttu-id="54ef8-139">Pour activer le suivi pour le portail BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-139">To enable tracing for the BAM portal</span></span>  
  
1.  <span data-ttu-id="54ef8-140">Modifiez le fichier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config.</span><span class="sxs-lookup"><span data-stu-id="54ef8-140">Edit the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config file.</span></span>  
  
2.  <span data-ttu-id="54ef8-141">Recherchez le \<system.diagnostics > et  \< /System.Diagnostics > balises.</span><span class="sxs-lookup"><span data-stu-id="54ef8-141">Locate the \<system.diagnostics> and \</system.diagnostics> tags.</span></span>  
  
3.  <span data-ttu-id="54ef8-142">Supprimez les commentaires de la section des diagnostics système par déplacement délimiteur de commentaire de fin ('-->') d’après le \</System.Diagnostics > balise avant le \<system.diagnostics > balise.</span><span class="sxs-lookup"><span data-stu-id="54ef8-142">Uncomment the system diagnostics section by moving end comment delimiter ('-->') from after the \</system.diagnostics> tag to before the \<system.diagnostics> tag.</span></span>  
  
4.  <span data-ttu-id="54ef8-143">Modifiez l'attribut initializeData afin d'indiquer l'emplacement d'écriture du journal des suivis.</span><span class="sxs-lookup"><span data-stu-id="54ef8-143">Modify the initializeData attribute to specify the location to write the tracing log.</span></span>  
  
5.  <span data-ttu-id="54ef8-144">Recherchez \<system.web > balise.</span><span class="sxs-lookup"><span data-stu-id="54ef8-144">Locate \<system.web> tag.</span></span>  
  
6.  <span data-ttu-id="54ef8-145">Dans la section system.web, repérez la balise de suivi et supprimez les marques de commentaires de la commande trace en plaçant le délimiteur ('-->'), placé après la balise de suivi, devant la balise.</span><span class="sxs-lookup"><span data-stu-id="54ef8-145">In the system.web section locate the trace tag and uncomment the trace command by moving the delimiter ('-->') from after the trace tag to before it.</span></span>  
  
7.  <span data-ttu-id="54ef8-146">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="54ef8-146">Save the file.</span></span>  
  
 `<!--`  
  
 `TRACING: To turn tracing on:`  
  
 `1) Uncomment this tag and specify a file path for trace output`  
  
 `2) Uncomment the <trace tag> under <system.web>`  
  
 `The trace will be saved to the file pointed to by "initializeData" below.`  
  
 `Ensure that the target directory exists (C:\temp by default).`  
  
 `Make sure that the IIS worker process user account (usually Network Service or ASPNET)`  
  
 `and the BAM Portal user have write permissions for the trace log file directory (C:\temp below).`  
  
 `To turn tracing on, you will need to uncomment the <trace> tag under <system.web>`  
  
 `<system.diagnostics>`  
  
 `<trace autoflush="true" indentsize="2">`  
  
 `<listeners>`  
  
 `<add name="BAMPortalListener"`  
  
 `type="System.Diagnostics.TextWriterTraceListener"`  
  
 `initializeData="C:\temp\BAMPortalTrace.log" />`  
  
 `</listeners>`  
  
 `</trace>`  
  
 `</system.diagnostics>`  
  
 `-->`  
  
 `<!--`  
  
 `TRACING: To turn tracing on:`  
  
 `1) Uncomment this tag`  
  
 `2) Uncomment the <system.diagnostics> tag above and specify a file path for trace output`  
  
 `<trace enabled="true"`  
  
 `requestLimit="40"`  
  
 `pageOutput="false"`  
  
 `traceMode="SortByTime"`  
  
 `localOnly="true"`  
  
 `writeToDiagnosticsTrace="true" />`  
  
 `-->`  
  
## <a name="bam-alerting"></a><span data-ttu-id="54ef8-147">Alertes BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-147">BAM Alerting</span></span>  
 <span data-ttu-id="54ef8-148">L'activation du suivi pour les alertes BAM vous permet de résoudre les erreurs de notification d'alertes.</span><span class="sxs-lookup"><span data-stu-id="54ef8-148">Enabling tracing for BAM alerting helps you troubleshoot alert delivery failures.</span></span>  
  
 <span data-ttu-id="54ef8-149">La fonction d'alertes BAM repose sur l'infrastructure des services de notification de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54ef8-149">BAM alerting is built on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services infrastructure.</span></span> <span data-ttu-id="54ef8-150">Pour activer le suivi des alertes BAM, consultez Résolution des problèmes de rubriques sur les Services de Notification [http://go.microsoft.com/fwlink/?LinkId=79416](http://go.microsoft.com/fwlink/?LinkId=79416).</span><span class="sxs-lookup"><span data-stu-id="54ef8-150">To enable tracing on BAM alerting, see the Notification Services troubleshooting topics at [http://go.microsoft.com/fwlink/?LinkId=79416](http://go.microsoft.com/fwlink/?LinkId=79416).</span></span>  
  
## <a name="bam-interceptors"></a><span data-ttu-id="54ef8-151">Intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-151">BAM Interceptors</span></span>  
 <span data-ttu-id="54ef8-152">Pour activer le suivi de bout en bout des intercepteurs BAM, modifiez le fichier de configuration de l'application : le fichier Web.config pour les applications hébergées sur le Web, ou le fichier Appname.config pour les applications auto-hébergées.</span><span class="sxs-lookup"><span data-stu-id="54ef8-152">To enable end-to-end tracing of the BAM interceptors, you modify the application’s configuration file—either Web.config for Web-hosted applications, or Appname.config for self-hosted applications.</span></span> <span data-ttu-id="54ef8-153">L'exemple suivant illustre la modification du fichier :</span><span class="sxs-lookup"><span data-stu-id="54ef8-153">The following is an example of how you can modify the file:</span></span>  
  
```  
<system.diagnostics>  
  </sources>  
    <source name="Microsoft BizTalk Bam Interceptors" switchValue="All">  
      <listeners>  
  
        <add name="myListener"  
             type="System.Diagnostics.TextWriterTraceListener"  
             initializeData="TextWriterOutput.log" />  
      </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="54ef8-154">Les intercepteurs BAM de Windows Workflow Foundation et Windows Communication Foundation sont écrits dans la source nommée « Microsoft BizTalk Bam Interceptors ».</span><span class="sxs-lookup"><span data-stu-id="54ef8-154">BAM Interceptor for Windows Workflow Foundation and Windows Communication Foundation are written to the source named "Microsoft BizTalk Bam Interceptors".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54ef8-155">La chaîne de la source distingue les majuscules et les minuscules et doit donc apparaître exactement comme indiqué.</span><span class="sxs-lookup"><span data-stu-id="54ef8-155">The source string is case-sensitive and must appear exactly as shown.</span></span> <span data-ttu-id="54ef8-156">Dans le cas contraire, vous ne pourrez pas recevoir les informations de suivi des intercepteurs BAM.</span><span class="sxs-lookup"><span data-stu-id="54ef8-156">If your string is different than the one shown, you will not receive trace information for the BAM interceptors.</span></span>  
  
 <span data-ttu-id="54ef8-157">La définition du paramètre switchValue permet de contrôler le niveau de suivi.</span><span class="sxs-lookup"><span data-stu-id="54ef8-157">You control the tracing level by setting switchValue.</span></span> <span data-ttu-id="54ef8-158">Le tableau suivant récapitule les différents niveaux de suivi disponibles.</span><span class="sxs-lookup"><span data-stu-id="54ef8-158">The available tracing levels are summarized in the following table.</span></span>  
  
|<span data-ttu-id="54ef8-159">Niveau de suivi</span><span class="sxs-lookup"><span data-stu-id="54ef8-159">Trace Level</span></span>|<span data-ttu-id="54ef8-160"> Description</span><span class="sxs-lookup"><span data-stu-id="54ef8-160">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="54ef8-161">Critique</span><span class="sxs-lookup"><span data-stu-id="54ef8-161">Critical</span></span>|<span data-ttu-id="54ef8-162">Consigne les entrées Fail-Fast et Event Log, ainsi que les informations de corrélation de suivi.</span><span class="sxs-lookup"><span data-stu-id="54ef8-162">Logs Fail-Fast and Event Log entries, and trace correlation information.</span></span>|  
|<span data-ttu-id="54ef8-163">Erreur</span><span class="sxs-lookup"><span data-stu-id="54ef8-163">Error</span></span>|<span data-ttu-id="54ef8-164">Consigne toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="54ef8-164">Logs all exceptions.</span></span>|  
|<span data-ttu-id="54ef8-165">Avertissement</span><span class="sxs-lookup"><span data-stu-id="54ef8-165">Warning</span></span>|<span data-ttu-id="54ef8-166">Condition susceptible de générer une erreur ou une erreur critique.</span><span class="sxs-lookup"><span data-stu-id="54ef8-166">A condition exists that may subsequently result in an error or critical failure.</span></span>|  
|<span data-ttu-id="54ef8-167">Informations</span><span class="sxs-lookup"><span data-stu-id="54ef8-167">Information</span></span>|<span data-ttu-id="54ef8-168">Des messages utiles au contrôle et au diagnostic de l'état du système, à l'évaluation des performances ou au profil sont générés.</span><span class="sxs-lookup"><span data-stu-id="54ef8-168">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="54ef8-169">Utilisez-les pour la planification de capacité et la gestion des performances.</span><span class="sxs-lookup"><span data-stu-id="54ef8-169">You can utilize such information for capacity planning and performance management.</span></span>|  
|<span data-ttu-id="54ef8-170">Commentaires</span><span class="sxs-lookup"><span data-stu-id="54ef8-170">Verbose</span></span>|<span data-ttu-id="54ef8-171">Suivi de niveau débogage pour le traitement et le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="54ef8-171">Debug-level tracing for both user code and servicing.</span></span>|  
|<span data-ttu-id="54ef8-172">Tous</span><span class="sxs-lookup"><span data-stu-id="54ef8-172">All</span></span>|<span data-ttu-id="54ef8-173">Tous les messages.</span><span class="sxs-lookup"><span data-stu-id="54ef8-173">All messages.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="54ef8-174">Le suivi peut nuire aux performances.</span><span class="sxs-lookup"><span data-stu-id="54ef8-174">Tracing can have an adverse affect on performance.</span></span> <span data-ttu-id="54ef8-175">Ne l'activez donc que dans le cadre de résolution de problèmes.</span><span class="sxs-lookup"><span data-stu-id="54ef8-175">Only enable tracing when you are performing troubleshooting activities.</span></span>  
  
### <a name="viewing-the-wcf-trace-file"></a><span data-ttu-id="54ef8-176">Affichage du fichier de suivi WCF</span><span class="sxs-lookup"><span data-stu-id="54ef8-176">Viewing the WCF Trace File</span></span>  
 <span data-ttu-id="54ef8-177">Utilisez l'outil WCF Service Trace Viewer pour analyser le suivi WCF.</span><span class="sxs-lookup"><span data-stu-id="54ef8-177">To analyze the WCF trace you use the WCF Service Trace Viewer Tool.</span></span> <span data-ttu-id="54ef8-178">Pour plus d’informations sur l’outil Service Trace Viewer, consultez [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).</span><span class="sxs-lookup"><span data-stu-id="54ef8-178">For more information about the Service Trace Viewer Tool, see [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ef8-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54ef8-179">See Also</span></span>  
 [<span data-ttu-id="54ef8-180">La gestion BAM</span><span class="sxs-lookup"><span data-stu-id="54ef8-180">Managing BAM</span></span>](../core/managing-bam.md)