---
title: "Création d’une commande avant ou le Script de post-traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts, post-processing
- scripts, pre-processing
- scripts, warnings
- scripts, applications
- applications, scripts
- scripts, deploying
- deploying, scripts
ms.assetid: d5fbaec8-fbfe-4ceb-8ba8-0933baa37a1f
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532c730d5a654512610a37c9dac783fbc6a76d6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-pre--or-post-processing-script"></a><span data-ttu-id="a4c99-102">Création d'un script de pré-traitement ou de post-traitement</span><span class="sxs-lookup"><span data-stu-id="a4c99-102">Creating a Pre- or Post-processing Script</span></span>
<span data-ttu-id="a4c99-103">Vous pouvez créer un script qui effectue des opérations lors du déploiement d'une application, puis définir le moment où ce script doit être exécuté durant le processus.</span><span class="sxs-lookup"><span data-stu-id="a4c99-103">You can create a script to perform actions when an application is deployed, and then define when it will run during the deployment process.</span></span> <span data-ttu-id="a4c99-104">Vous pouvez insérer le code d'installation et le code de nettoyage dans le même script en vous servant des variables d'environnement pour délimiter le code.</span><span class="sxs-lookup"><span data-stu-id="a4c99-104">You can include both installation and cleanup code in the same script, using environment variables to delimit the code.</span></span> <span data-ttu-id="a4c99-105">Il est également possible de passer des arguments en ligne de commande au script.</span><span class="sxs-lookup"><span data-stu-id="a4c99-105">You can also pass command-line arguments into the script.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a4c99-106">Écrivez toujours les scripts destinés à des systèmes de production en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="a4c99-106">You should always write scripts intended for production systems in silent mode.</span></span> <span data-ttu-id="a4c99-107">En effet, lorsque le script est en attente de données, les bases de données BizTalk se verrouillent et ne sont plus accessibles tant que l'utilisateur n'a pas entré les données requises.</span><span class="sxs-lookup"><span data-stu-id="a4c99-107">This is because a script waiting for user input will cause the BizTalk databases to become locked and inaccessible until the input is received.</span></span>  
  
## <a name="specifying-when-a-script-will-run-during-deployment"></a><span data-ttu-id="a4c99-108">Spécification du moment d'exécution d'un script lors du déploiement</span><span class="sxs-lookup"><span data-stu-id="a4c99-108">Specifying when a script will run during deployment</span></span>  
 <span data-ttu-id="a4c99-109">Vous indiquez le moment où le script doit être exécuté lorsque vous ajoutez le script à une application, soit en tant que System.BizTalk:PreProcessingScript (script de pré-traitement), soit en tant que System.BizTalk:PostProcessingScript (script de post-traitement).</span><span class="sxs-lookup"><span data-stu-id="a4c99-109">You specify when a script will run when you add the script to an application by adding it as either a System.BizTalk:PreProcessingScript (pre-processing script) or a System.BizTalk:PostProcessingScript (post-processing script).</span></span>  
  
 <span data-ttu-id="a4c99-110">Les scripts de pré-traitement et de post-traitement s'exécutent comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4c99-110">Pre- and post-processing scripts run as follows:</span></span>  
  
-   <span data-ttu-id="a4c99-111">Les scripts de pré-traitement s'exécutent au début du processus d'importation ou d'installation.</span><span class="sxs-lookup"><span data-stu-id="a4c99-111">Pre-processing scripts run at the beginning of the import or installation process.</span></span>  
  
-   <span data-ttu-id="a4c99-112">Les scripts de post-traitement s'exécutent à la fin du processus d'importation ou d'installation.</span><span class="sxs-lookup"><span data-stu-id="a4c99-112">Post-processing scripts run at the end of the import or installation process.</span></span>  
  
-   <span data-ttu-id="a4c99-113">Lors d'une désinstallation, tous les scripts s'exécutent dans l'ordre inverse à celui dans lequel ils s'exécutent lors d'une installation.</span><span class="sxs-lookup"><span data-stu-id="a4c99-113">During uninstallation, all scripts run in the opposite order that they run during installation.</span></span> <span data-ttu-id="a4c99-114">Par conséquent, les scripts de post-traitement s'exécutent au début du processus de désinstallation et les scripts de pré-traitement, à la fin.</span><span class="sxs-lookup"><span data-stu-id="a4c99-114">Therefore, post-processing scripts run at the beginning of uninstallation and pre-processing scripts at the end of uninstallation.</span></span>  
  
-   <span data-ttu-id="a4c99-115">Si une installation échoue, les scripts sont appelés dans l'ordre inverse, en suivant l'action d'annulation appropriée.</span><span class="sxs-lookup"><span data-stu-id="a4c99-115">If an installation fails, scripts are called in reverse order with the appropriate rollback action.</span></span>  
  
 <span data-ttu-id="a4c99-116">Une fois appelé, un script de pré-traitement ou post-traitement détermine quel état de déploiement (installer, importer, supprimer, désinstaller, annulation de l’importation ou installer rollback) il s’exécute en vérifiant les variables d’environnement BTAD_ChangeRequestAction, BTAD_InstallMode, et BTAD_HostClass, comme décrit dans [état du déploiement de l’environnement Variables indiquer](../core/how-environment-variables-indicate-deployment-state.md).</span><span class="sxs-lookup"><span data-stu-id="a4c99-116">Once invoked, a pre- or post-processing script determines which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running in by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode, and BTAD_HostClass, as described in [How Environment Variables Indicate Deployment State](../core/how-environment-variables-indicate-deployment-state.md).</span></span> <span data-ttu-id="a4c99-117">Pour plus d’informations de référence sur les variables, consultez [Variables d’environnement de Script et de post-traitement](../core/pre-and-post-processing-script-environment-variables.md).</span><span class="sxs-lookup"><span data-stu-id="a4c99-117">For reference information about the variables, see [Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md).</span></span>  
  
 <span data-ttu-id="a4c99-118">Pour obtenir des instructions sur l’ajout d’un script à une application, consultez [Ajout antérieur à la version ou un Script de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="a4c99-118">For instructions on adding a script to an application, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4c99-119">Si vous souhaitez insérer des arguments en ligne de commande à un script, comme mentionné plus loin dans cette rubrique, vous devez utiliser la commande AddResource lorsque vous ajoutez le script.</span><span class="sxs-lookup"><span data-stu-id="a4c99-119">If you want to include command-line arguments in a script, as discussed later in this topic, you must use the AddResource command to add the script.</span></span>  
  
## <a name="supported-script-file-extensions"></a><span data-ttu-id="a4c99-120">Extensions de fichier de script prises en charge</span><span class="sxs-lookup"><span data-stu-id="a4c99-120">Supported script file extensions</span></span>  
 <span data-ttu-id="a4c99-121">Les extensions de fichier de script suivantes sont prises en charge : .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf et .wsh.</span><span class="sxs-lookup"><span data-stu-id="a4c99-121">The following script file extensions are supported: .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf, and .wsh.</span></span> <span data-ttu-id="a4c99-122">Cet ensemble d'extensions est défini dans la variable d'environnement PATHEXT.</span><span class="sxs-lookup"><span data-stu-id="a4c99-122">This set of extensions is defined in the PATHEXT environment variable.</span></span>  
  
## <a name="logging-errors"></a><span data-ttu-id="a4c99-123">Consignation des erreurs</span><span class="sxs-lookup"><span data-stu-id="a4c99-123">Logging errors</span></span>  
 <span data-ttu-id="a4c99-124">Il est recommandé de configurer chaque script de sorte qu'il consigne les erreurs dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a4c99-124">As a best practice, you should configure each script to log errors to a file.</span></span> <span data-ttu-id="a4c99-125">En effet, Windows Installer ne consigne pas les erreurs éventuellement générées dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="a4c99-125">This is because Windows Installer does not log errors generated in the scripts.</span></span> <span data-ttu-id="a4c99-126">Une fois le script exécuté, vérifiez que les fichiers journaux ne contiennent pas d'erreurs nécessitant votre intervention.</span><span class="sxs-lookup"><span data-stu-id="a4c99-126">You should check these logs after the script runs for any errors that need to be addressed.</span></span>  
  
 <span data-ttu-id="a4c99-127">Pour pouvoir déterminer plus facilement le moment où l'erreur s'est produite, vous pouvez inclure la date et l'heure dans le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="a4c99-127">To help you determine when the error occurred, you can include the date and time in the log file.</span></span>  
  
 <span data-ttu-id="a4c99-128">Utilisez le code suivant pour spécifier un fichier journal et y consigner les erreurs.</span><span class="sxs-lookup"><span data-stu-id="a4c99-128">Use the following code to specify a log file and then log an error to it.</span></span>  
  
 `Set LogFile=<full path of log file>`  
  
 `…`  
  
 `echo %DATE% %TIME% <text> >> %LogFile%`  
  
 <span data-ttu-id="a4c99-129">Dans l'exemple suivant, une entrée est créée dans le fichier journal spécifié lorsque le jeton de clé publique n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="a4c99-129">In the following example, when the public key token is not defined, an entry is made in the specified log file.</span></span> <span data-ttu-id="a4c99-130">Dans ce fichier journal, la date et l'heure sont écrits sur la même ligne, comme indiqué dans la ligne de code « Public key should be set in script » ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a4c99-130">In the log file, the date and time is written in the same line as the text, "Public key should be set in script."</span></span>  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 <span data-ttu-id="a4c99-131">Vous pouvez ajouter la ligne `exit /b 1` à un script afin qu'un code d'erreur soit généré pour Windows Installer. Cet ajout entraîne l'annulation de l'exécution de Windows Installer. </span><span class="sxs-lookup"><span data-stu-id="a4c99-131">You can also add the line `exit /b 1` to a script to generate an error code for Windows Installer, which will cause it to roll back.</span></span>  
  
 <span data-ttu-id="a4c99-132">Dans l'exemple suivant, le script signale une erreur à Windows Installer si le jeton de clé publique n'a pas été défini.</span><span class="sxs-lookup"><span data-stu-id="a4c99-132">In the following example, if the public key token has not been defined, the script will return an error to Windows Installer, and the installer will roll back.</span></span>  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 `exit /b 1`  
  
## <a name="including-installation-and-cleanup-code-in-the-same-script"></a><span data-ttu-id="a4c99-133">Insertion du code d'installation et du code de nettoyage dans le même script</span><span class="sxs-lookup"><span data-stu-id="a4c99-133">Including installation and cleanup code in the same script</span></span>  
 <span data-ttu-id="a4c99-134">Étant donné que les scripts s'exécutent dans l'ordre inverse selon qu'il s'agit d'une installation ou d'une désinstallation, vous pouvez inclure un code d'installation et un code de nettoyage dans le même script, dans une instruction conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="a4c99-134">Because scripts run in the opposite order during installation and uninstallation, you can include installation and cleanup code in the same script, inside a conditional statement.</span></span> <span data-ttu-id="a4c99-135">Par exemple, vous pouvez placer le code d'installation dans une instruction conditionnelle qui vérifie le mode d'installation comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4c99-135">For example, you can place the installation code within a conditional statement that checks for the installation mode, as follows:</span></span>  
  
```  
  
%BTAD_ChangeRequestAction%=Update AND %BTAD_InstallMode%=Install  
  
```  
  
 <span data-ttu-id="a4c99-136">Vous pouvez qualifier le code de nettoyage dans une instruction conditionnelle qui vérifie le mode d'installation comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4c99-136">You can qualify cleanup code within a conditional statement that checks for the installation mode, as follows:</span></span>  
  
```  
  
%BTAD_ChangeRequestAction%=Delete AND %BTAD_InstallMode%=Uninstall  
  
```  
  
## <a name="passing-in-command-line-arguments"></a><span data-ttu-id="a4c99-137">Passage d'arguments en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a4c99-137">Passing in command-line arguments</span></span>  
 <span data-ttu-id="a4c99-138">Pour passer des arguments en ligne de commande au script, spécifiez le paramètre décrit ci-après lorsque vous ajoutez le script à l'application à l'aide de la commande BTSTask AddResource.</span><span class="sxs-lookup"><span data-stu-id="a4c99-138">You can pass command-line arguments into the script by specifying the following parameter when you use the BTSTask AddResource command to add the script to the application.</span></span> <span data-ttu-id="a4c99-139">Cela fait, les arguments sont passés au script lorsque ce dernier est invoqué.</span><span class="sxs-lookup"><span data-stu-id="a4c99-139">When you do this, the arguments are passed to the script when the script is invoked.</span></span>  
  
 <span data-ttu-id="a4c99-140">**/Property:args =**»*liste d’arguments*»</span><span class="sxs-lookup"><span data-stu-id="a4c99-140">**/Property:Args=**"*argument list*"</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4c99-141">Lorsque vous avez plusieurs scripts de pré-traitement et de post-traitement dans une application, ils sont exécutés sans respecter d'ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="a4c99-141">If you have multiple pre- or post-processing scripts in and application, they are run in no particular order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4c99-142">N'utilisez pas de commandes BTSTask dans les scripts, surtout dans les scripts qui s'exécutent lors de l'importation car ces scripts ne sont pas inscrits dans la même transaction qu'une importation.</span><span class="sxs-lookup"><span data-stu-id="a4c99-142">You should not use BTSTask commands in scripts, especially those that run during import, because scripts are not enlisted in the same transaction as an import.</span></span>  
  
 <span data-ttu-id="a4c99-143">Pour obtenir des instructions sur l’utilisation de la commande AddResource pour ajouter un script à une application, consultez [commande AddResource : scripts de pré-traitement](../core/addresource-command-preprocessing-script.md).</span><span class="sxs-lookup"><span data-stu-id="a4c99-143">For instructions on using the AddResource command to add a script to an application, see [AddResource Command: Preprocessing Script](../core/addresource-command-preprocessing-script.md).</span></span> <span data-ttu-id="a4c99-144">Consultez également [commande AddResource : scripts de post-traitement](../core/addresource-command-postprocessing-script.md)</span><span class="sxs-lookup"><span data-stu-id="a4c99-144">Also see [AddResource Command: Postprocessing Script](../core/addresource-command-postprocessing-script.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c99-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4c99-145">See Also</span></span>  
 <span data-ttu-id="a4c99-146">[À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="a4c99-146">[Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span></span>  
 [<span data-ttu-id="a4c99-147">Modèle (exemple de déploiement d’Application)</span><span class="sxs-lookup"><span data-stu-id="a4c99-147">Template (Application Deployment Sample)</span></span>](../core/template-application-deployment-sample.md)