---
title: Importer des applications PeopleSoft | Documents Microsoft
description: "Utiliser un fichier de liaison XML à importer vos applications de l’adaptateur PeopleSoft dans BizTalk Server et lire toutes les restrictions lors de l’importation"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f53d1b4-e1df-41ff-b554-1bb1d20b9111
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed076bd238eff5106bb0b2f08449144d922fed4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploy-biztalk-adapter-for-peoplesoft-enterprise"></a><span data-ttu-id="766e8-103">Déployez l’adaptateur BizTalk pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="766e8-103">Deploy BizTalk Adapter for PeopleSoft Enterprise</span></span>
<span data-ttu-id="766e8-104">Cette section fournit des informations sur le déploiement de l'adaptaeur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="766e8-104">This section provides information about deploying BizTalk Adapter for PeopleSoft Enterprise.</span></span>  

## <a name="overview"></a><span data-ttu-id="766e8-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="766e8-105">Overview</span></span>
<span data-ttu-id="766e8-106">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="766e8-106">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="766e8-107">Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="766e8-107"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="766e8-108">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="766e8-108">You use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform these tasks:</span></span>  
  
-   <span data-ttu-id="766e8-109">déploiement ou suppression des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une base de données de configuration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="766e8-109">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="766e8-110">installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;</span><span class="sxs-lookup"><span data-stu-id="766e8-110">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="766e8-111">importation/exportation des informations de liaison des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vers/à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="766e8-111">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files.</span></span>  
  
<span data-ttu-id="766e8-112">Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="766e8-112">To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="766e8-113">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="766e8-113">The Microsoft BizTalk Adapter for PeopleSoft Enterprise only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="766e8-114">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="766e8-114">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="766e8-115">Vérifiez votre configuration</span><span class="sxs-lookup"><span data-stu-id="766e8-115">Confirm your setup</span></span>
<span data-ttu-id="766e8-116">Avant d'importer un fichier de liaison à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="766e8-116">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="766e8-117">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="766e8-117">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="766e8-118">Vérifiez que l’emplacement de ces fichiers est le même sur le nouvel ordinateur, ou modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="766e8-118">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="766e8-119">Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur, ou modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="766e8-119">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="766e8-120">S'ils sont présents dans la configuration, les mots de passe du système PeopleSoft Enterprise sont enregistrés dans le fichier de liaison sous la forme *****.</span><span class="sxs-lookup"><span data-stu-id="766e8-120">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="766e8-121">Consultez **Limitations** dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="766e8-121">See **Limitations** in this topic.</span></span>

> [!NOTE]
>  <span data-ttu-id="766e8-122">Le déploiement remplace la configuration de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="766e8-122">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="766e8-123">Lorsque vous déployez un fichier de liaison et l’assembly sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="766e8-123">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="766e8-124">Pour obtenir des instructions sur l’importation de fichiers de liaison, consultez [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md).</span><span class="sxs-lookup"><span data-stu-id="766e8-124">For step-by-step directions about importing binding files, see [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md).</span></span> 
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="766e8-125">Nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="766e8-125">Clean the target computer</span></span>
<span data-ttu-id="766e8-126">Pour nettoyer l’ordinateur cible pour le déploiement de la nouvelle application, supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="766e8-126">To clean the target computer for deploying the new application, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="766e8-127">Si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="766e8-127">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
<span data-ttu-id="766e8-128">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="766e8-128">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
<span data-ttu-id="766e8-129">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception**</span><span class="sxs-lookup"><span data-stu-id="766e8-129">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
<span data-ttu-id="766e8-130">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="766e8-130">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## <a name="limitations"></a><span data-ttu-id="766e8-131">Limitations</span><span class="sxs-lookup"><span data-stu-id="766e8-131">Limitations</span></span>
<span data-ttu-id="766e8-132">Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (*) dans le fichier de liaison exporté par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format.</span><span class="sxs-lookup"><span data-stu-id="766e8-132">The Transport Adapter password is stored as asterisks (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span>  
  
 <span data-ttu-id="766e8-133">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="766e8-133">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="766e8-134">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="766e8-134">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="766e8-135">Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="766e8-135">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="766e8-136">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="766e8-136">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="766e8-137">Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison à l’issue de l’opération d’importation.</span><span class="sxs-lookup"><span data-stu-id="766e8-137">In this case, you must delete the passwords from the binding file after the import operation finishes.</span></span>  
  

### <a name="work-around-the-password-limitation"></a><span data-ttu-id="766e8-138">Contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="766e8-138">Work around the password limitation</span></span>  

<span data-ttu-id="766e8-139">**Option 1**</span><span class="sxs-lookup"><span data-stu-id="766e8-139">**Option 1**</span></span>   
  
-   <span data-ttu-id="766e8-140">Avant d’importer, mettre à jour le fichier de liaison en remplaçant les astérisques par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="766e8-140">Before you import, update the binding file by replacing the asterisks with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="766e8-141">Cette pratique n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="766e8-141">This practice is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="766e8-142">Avant d’importer, mettre à jour le fileby de liaison en remplaçant les astérisques par des valeurs aléatoires (c'est-à-dire, pas le mot de passe).</span><span class="sxs-lookup"><span data-stu-id="766e8-142">Before you import, update the binding fileby replacing the asterisks with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="766e8-143">Après avoir importé, entrez le mot de passe correct dans la **propriétés du Transport** dans Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="766e8-143">After you import, enter the correct password in the **Transport Properties** in BizTalk Server Administration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="766e8-144">Cette solution de contournement ne peut être utilisée que si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est installé sur l'ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="766e8-144">This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.</span></span>  
  
<span data-ttu-id="766e8-145">**Option 2**</span><span class="sxs-lookup"><span data-stu-id="766e8-145">**Option 2**</span></span>  
  
-   <span data-ttu-id="766e8-146">Utilisez l'authentification unique de l'entreprise (SSO) plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="766e8-146">Use Enterprise Single Sign-On (SSO) instead of using passwords.</span></span> <span data-ttu-id="766e8-147">L'utilisation de l'option SSO nécessite l'importation d'un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="766e8-147">Using the SSO option requires an import of the binding file.</span></span>  
  
- <span data-ttu-id="766e8-148">Vérifiez le système logique et le transmettre et recevoir des services.</span><span class="sxs-lookup"><span data-stu-id="766e8-148">Verify the logical system and the Transmit and Receive services.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="766e8-149">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="766e8-149">Next steps</span></span>
[<span data-ttu-id="766e8-150">Utiliser BizTalk Server des exceptions dans votre orchestration</span><span class="sxs-lookup"><span data-stu-id="766e8-150">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling2.md)