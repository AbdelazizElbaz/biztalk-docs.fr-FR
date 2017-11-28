---
title: Importer des liaisons pour TIBCO EMS | Documents Microsoft
description: "Déployer votre adaptateur BizTalk pour les applications de TIBCO Enterprise Message Service à l’aide de la fonctionnalité d’importation des liaisons dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69dae448-4ec6-4a56-a628-bb447bc21b62
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e020ccc111c3f1a7ae11ae0b2b434d36e8a5db28
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deploy-tibco-ems-ports-and-assemblies"></a><span data-ttu-id="cc892-103">Déployer des assemblys et des ports de TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="cc892-103">Deploy TIBCO EMS ports and assemblies</span></span>

## <a name="overview"></a><span data-ttu-id="cc892-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="cc892-104">Overview</span></span>
<span data-ttu-id="cc892-105">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="cc892-105">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cc892-106">configuration de l’emplacement de réception/ports d’envoi exporte dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="cc892-106"> exports send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="cc892-107">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc892-107">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="cc892-108">déploiement ou suppression des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une base de données de configuration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="cc892-108">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database.</span></span>  
  
-   <span data-ttu-id="cc892-109">installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;</span><span class="sxs-lookup"><span data-stu-id="cc892-109">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
-   <span data-ttu-id="cc892-110">importation/exportation des informations de liaison des assemblys BizTalk vers/à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="cc892-110">Import or export BizTalk assembly binding information to and from binding files.</span></span>  
  
 <span data-ttu-id="cc892-111">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="cc892-111">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc892-112">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="cc892-112">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="cc892-113">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="cc892-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="cc892-114">Vérifiez votre configuration</span><span class="sxs-lookup"><span data-stu-id="cc892-114">Confirm your setup</span></span>
<span data-ttu-id="cc892-115">Avant d'importer un fichier de liaison à l'aide de BizTalk Server, vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cc892-115">Before you use BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="cc892-116">Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="cc892-116">The folders for the responses must exist and be identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="cc892-117">S'ils sont inclus dans la configuration, les mots de passe du système TIBCO Enterprise Message Service doivent être enregistrés dans le fichier de liaison sous la forme *****.</span><span class="sxs-lookup"><span data-stu-id="cc892-117">TIBCO Enterprise Message Service system passwords, if present in the configuration, must be saved as ***** in the binding file.</span></span> <span data-ttu-id="cc892-118">Consultez **Limitations** dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cc892-118">See **Limitations** in this topic.</span></span>


## <a name="clean-the-target-computer"></a><span data-ttu-id="cc892-119">Nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="cc892-119">Clean the target computer</span></span>
<span data-ttu-id="cc892-120">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="cc892-120">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="cc892-121">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="cc892-121">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  

<span data-ttu-id="cc892-122">Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="cc892-122">Before you import, remove any send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="cc892-123">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="cc892-123">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
`\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs`  
  
`\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs`
  

<span data-ttu-id="cc892-124">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="cc892-124">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name>
```

## <a name="limitations"></a><span data-ttu-id="cc892-125">Limitations</span><span class="sxs-lookup"><span data-stu-id="cc892-125">Limitations</span></span>
<span data-ttu-id="cc892-126">Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoiles (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par BizTalk Server et la transmet au composant de gestion dans le même format.</span><span class="sxs-lookup"><span data-stu-id="cc892-126">The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format.</span></span> <span data-ttu-id="cc892-127">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="cc892-127">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="cc892-128">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="cc892-128">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
 <span data-ttu-id="cc892-129">Il s'agit d'une limitation connue.</span><span class="sxs-lookup"><span data-stu-id="cc892-129">This is a known limitation.</span></span> <span data-ttu-id="cc892-130">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="cc892-130">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="cc892-131">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="cc892-131">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="cc892-132">Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="cc892-132">The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span> <span data-ttu-id="cc892-133">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="cc892-133">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="cc892-134">Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison une fois l’opération d’importation terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="cc892-134">In this case, you must delete the passwords from the binding file after the import operation successfully finishes.</span></span>  
  
 
### <a name="password-limitation-workaround"></a><span data-ttu-id="cc892-135">Contournement de la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="cc892-135">Password Limitation Workaround</span></span>  
 <span data-ttu-id="cc892-136">Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc892-136">To work around this password limitation, you can use one of the following methods:</span></span>  
  
-   <span data-ttu-id="cc892-137">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.</span><span class="sxs-lookup"><span data-stu-id="cc892-137">Edit the binding file before importing by replacing the stars with plain text.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="cc892-138">Cette opération n'est pas recommandée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="cc892-138">This is not recommended for security reasons.</span></span>  
  
-   <span data-ttu-id="cc892-139">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="cc892-139">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span> <span data-ttu-id="cc892-140">Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="cc892-140">Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cc892-141">Cette solution de contournement ne peut être utilisée que si Visual Studio est installé sur l'ordinateur cible ou en développant un outil personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cc892-141">This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.</span></span>  
  
-   <span data-ttu-id="cc892-142">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="cc892-142">Verify the Logical system and the Transmit and Receive services.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="cc892-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cc892-143">Next steps</span></span>
[<span data-ttu-id="cc892-144">Utiliser BizTalk Server des exceptions dans votre orchestration</span><span class="sxs-lookup"><span data-stu-id="cc892-144">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling5.md)