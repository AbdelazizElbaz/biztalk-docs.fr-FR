---
title: Importer l’adaptateur BizTalk pour JD Edwards OneWorld | Documents Microsoft
description: Importez le fichier de liaison d’application et passer en revue les limitations de l’adaptateur JD Edwards OneWorld dans BizTalk Server
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f308d2fe-39dd-4008-94ed-292c4c26fe06
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4a452d61b3bdb5f5d0fee9e0916811645938d70
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a><span data-ttu-id="8a0f9-103">Importez l’application JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="8a0f9-103">Import the JD Edwards EnterpriseOne application</span></span>
  
## <a name="overview"></a><span data-ttu-id="8a0f9-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8a0f9-104">Overview</span></span>
<span data-ttu-id="8a0f9-105">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-105">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="8a0f9-106">BizTalk Server exporte la configuration des ports d'envoi/emplacements de réception dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-106">BizTalk Server exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="8a0f9-107">Vous pouvez utiliser BizTalk Server pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a0f9-107">You can use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="8a0f9-108">déploiement ou suppression des assemblys BizTalk Server dans une base de données de configuration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="8a0f9-108">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="8a0f9-109">Installer ou désinstaller des assemblys dans le global assembly cache (GAC)</span><span class="sxs-lookup"><span data-stu-id="8a0f9-109">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="8a0f9-110">importation/exportation des informations de liaison des assemblys BizTalk Server vers/à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-110">Import or export BizTalk Server assembly binding information to and from binding files</span></span>  

<span data-ttu-id="8a0f9-111">Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="8a0f9-111">To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a0f9-112">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-112">The Microsoft BizTalk Adapter for JD Edwards OneWorld only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="8a0f9-113">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="8a0f9-114">Vérifiez votre configuration</span><span class="sxs-lookup"><span data-stu-id="8a0f9-114">Confirm your setup</span></span>
<span data-ttu-id="8a0f9-115">Avant d’utiliser le serveur BizTalk pour importer un fichier de liaison, vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8a0f9-115">Before you use the BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="8a0f9-116">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-116">The CLASSPATH is pointing to a specific location for the JD Edwards-specific files.</span></span> <span data-ttu-id="8a0f9-117">Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-117">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="8a0f9-118">Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-118">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="8a0f9-119">S'ils sont présents dans la configuration, les mots de passe du système JD Edwards sont enregistrés dans le fichier de liaison sous la forme \*\*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-119">JD Edwards system passwords, if present in the configuration, are saved as \*\*\*\*\* in the binding file.</span></span> <span data-ttu-id="8a0f9-120">Consultez **Limitations** dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-120">See **Limitations** in this topic.</span></span>

  
> [!NOTE]
>  <span data-ttu-id="8a0f9-121">Déploiement remplace la configuration de l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-121">Deployment overwrites Receive Location configuration.</span></span> <span data-ttu-id="8a0f9-122">Lors du déploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur importation.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-122">When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="8a0f9-123">Nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="8a0f9-123">Clean the target computer</span></span>
<span data-ttu-id="8a0f9-124">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-124">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="8a0f9-125">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-125">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
<span data-ttu-id="8a0f9-126">Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-126">Before you import, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="8a0f9-127">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="8a0f9-127">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8a0f9-128">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="8a0f9-128">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8a0f9-129">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="8a0f9-129">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
<span data-ttu-id="8a0f9-130">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="8a0f9-130">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="limitations"></a><span data-ttu-id="8a0f9-131">Limitations</span><span class="sxs-lookup"><span data-stu-id="8a0f9-131">Limitations</span></span>
<span data-ttu-id="8a0f9-132">Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par l’Assistant Déploiement BizTalk et est transmis à la gestion composant dans le même format.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-132">The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format.</span></span> <span data-ttu-id="8a0f9-133">Avant d'importer le fichier de liaison, vous devez le modifier en remplaçant les astérisques par des valeurs alphanumériques aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="8a0f9-133">Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password).</span></span> <span data-ttu-id="8a0f9-134">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-134">Then enter the correct password using the **Transport Properties** page after importing the binding file.</span></span>  
  
 <span data-ttu-id="8a0f9-135">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-135">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="8a0f9-136">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-136">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="8a0f9-137">La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-137">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="8a0f9-138">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-138">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="8a0f9-139">Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-139">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a0f9-140">Lors de l’importation d’un fichier .msi dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application contenant des informations de liaison pour un adaptateur d’entreprise, vous pouvez recevoir un message d’erreur d’importation.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-140">When importing an .msi file into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message.</span></span> <span data-ttu-id="8a0f9-141">Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [ http://support.microsoft.com/kb/923733/en-us ](http://support.microsoft.com/kb/923733/en-us).</span><span class="sxs-lookup"><span data-stu-id="8a0f9-141">A supported hotfix is available from Microsoft along with a full description of the error at [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).</span></span>  
  
### <a name="work-around-the-password-limitation"></a><span data-ttu-id="8a0f9-142">Contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="8a0f9-142">Work around the password limitation</span></span>  

<span data-ttu-id="8a0f9-143">**Option 1**</span><span class="sxs-lookup"><span data-stu-id="8a0f9-143">**Option 1**</span></span>  

- <span data-ttu-id="8a0f9-144">Avant d’importer, mettre à jour le fichier de liaison en remplaçant les astérisques par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-144">Before you import, update the binding file by replacing the asterisks with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="8a0f9-145">Cette opération n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-145">This is not recommended for security reasons.</span></span>  
  
- <span data-ttu-id="8a0f9-146">Avant d’importer, mettre à jour le fichier de liaison en remplaçant les astérisques par des valeurs aléatoires (c'est-à-dire, pas le mot de passe).</span><span class="sxs-lookup"><span data-stu-id="8a0f9-146">Before you import, update the binding file by replacing the asterisks with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="8a0f9-147">Après avoir importé, entrez le mot de passe correct à l’aide de la **propriétés du Transport**.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-147">After you import, enter the correct password using the **Transport Properties**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8a0f9-148">Cette solution de contournement peut être utilisée uniquement si Microsoft Visual Studio est installé sur l’ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-148">This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.</span></span>  
  
<span data-ttu-id="8a0f9-149">**Option 2**</span><span class="sxs-lookup"><span data-stu-id="8a0f9-149">**Option 2**</span></span>  
  
1.  <span data-ttu-id="8a0f9-150">Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-150">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="8a0f9-151">Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-151">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="8a0f9-152">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="8a0f9-152">Verify the Logical system and the Transmit and Receive services.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="8a0f9-153">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8a0f9-153">Next steps</span></span>
[<span data-ttu-id="8a0f9-154">Utiliser BizTalk Server des exceptions dans votre orchestration</span><span class="sxs-lookup"><span data-stu-id="8a0f9-154">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling1.md)