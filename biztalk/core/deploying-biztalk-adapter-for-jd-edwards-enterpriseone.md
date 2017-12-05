---
title: Importer des applications JD Edwards EnterpriseOne | Documents Microsoft
description: "Confirmer l’installation, importez le fichier de liaison d’application et examiner les limitations de l’adaptateur JD Edwards EnterpriseOne dans BizTalk Server"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 852f948b-48ba-4ae2-b1eb-7c88c1542a52
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55374c87192c993e26cc11cb496d89074d527868
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a><span data-ttu-id="a4e8e-103">Importez l’application JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="a4e8e-103">Import the JD Edwards EnterpriseOne application</span></span>
  
## <a name="overview"></a><span data-ttu-id="a4e8e-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a4e8e-104">Overview</span></span>
<span data-ttu-id="a4e8e-105">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-105">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4e8e-106">Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-106"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="a4e8e-107">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4e8e-107">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="a4e8e-108">Déployer ou supprimer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys dans une base de données de Configuration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="a4e8e-108">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="a4e8e-109">Installer ou désinstaller des assemblys dans le global assembly cache (GAC)</span><span class="sxs-lookup"><span data-stu-id="a4e8e-109">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="a4e8e-110">Importer ou exporter des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] informations de liaison d’assembly vers et à partir de fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="a4e8e-110">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files</span></span>  
  
<span data-ttu-id="a4e8e-111">Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="a4e8e-111">To use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4e8e-112">L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-112">The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="a4e8e-113">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="a4e8e-114">Vérifiez votre configuration</span><span class="sxs-lookup"><span data-stu-id="a4e8e-114">Confirm your setup</span></span>
<span data-ttu-id="a4e8e-115">Avant d'utiliser le serveur BizTalk pour importer un fichier de liaison, vous devez vérifier les éléments suivants se réalisent :</span><span class="sxs-lookup"><span data-stu-id="a4e8e-115">Before you use the BizTalk Server to import a binding file, you must verify the following:</span></span>  
  
-   <span data-ttu-id="a4e8e-116">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-116">The CLASSPATH is pointing to a specific location for the JD Edwards EnterpriseOne-specific files.</span></span> <span data-ttu-id="a4e8e-117">Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-117">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="a4e8e-118">Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-118">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="a4e8e-119">Les mots de passe du système JD Edwards EnterpriseOne, si cette option a été définie dans la configuration, sont enregistrés en tant que ***** dans le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-119">JD Edwards EnterpriseOne system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="a4e8e-120">Pour plus d’informations, consultez **Limitations** dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-120">For more information, see **Limitations** in this topic.</span></span>

## <a name="clean-the-target-computer"></a><span data-ttu-id="a4e8e-121">Nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="a4e8e-121">Clean the target computer</span></span>
<span data-ttu-id="a4e8e-122">Lors du redéploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur réimportation.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-122">When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.</span></span>  
  
<span data-ttu-id="a4e8e-123">Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-123">Before you import, remove Send ports and Receive locations bound to the orchestration.</span></span> <span data-ttu-id="a4e8e-124">Si Visual Studio n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="a4e8e-124">If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="a4e8e-125">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="a4e8e-125">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="a4e8e-126">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="a4e8e-126">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  

<span data-ttu-id="a4e8e-127">Par exemple, à l'invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="a4e8e-127">For example, from a command prompt run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
## <a name="limitations"></a><span data-ttu-id="a4e8e-128">Limitations</span><span class="sxs-lookup"><span data-stu-id="a4e8e-128">Limitations</span></span>
<span data-ttu-id="a4e8e-129">Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoile (*) dans le fichier de liaison exporté par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-129">The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.</span></span> <span data-ttu-id="a4e8e-130">Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="a4e8e-130">Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).</span></span>  
  
 <span data-ttu-id="a4e8e-131">Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-131">When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports.</span></span> <span data-ttu-id="a4e8e-132">Ceci empêche l'affichage des informations de mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-132">This prevents password information from appearing in clear text.</span></span> <span data-ttu-id="a4e8e-133">La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-133">The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.</span></span>  
  
 <span data-ttu-id="a4e8e-134">Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-134">Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it.</span></span> <span data-ttu-id="a4e8e-135">Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-135">In this case, you must delete the passwords from the binding file after the import operation successfully completes.</span></span>  
  
### <a name="work-around-the-password-limitation"></a><span data-ttu-id="a4e8e-136">Contourner la limitation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="a4e8e-136">Work around the password limitation</span></span>  
  
1.  <span data-ttu-id="a4e8e-137">Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-137">Use Enterprise Single Sign-On instead of using passwords.</span></span> <span data-ttu-id="a4e8e-138">Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-138">Using the SSO option requires no extra work; only an import of the binding file.</span></span>  
  
2.  <span data-ttu-id="a4e8e-139">Vérifiez le système logique et les services de transmission et de réception.</span><span class="sxs-lookup"><span data-stu-id="a4e8e-139">Verify the Logical system and the Transmit and Receive services.</span></span>  


## <a name="next-steps"></a><span data-ttu-id="a4e8e-140">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a4e8e-140">Next steps</span></span>
[<span data-ttu-id="a4e8e-141">Utiliser BizTalk Server des exceptions dans votre orchestration</span><span class="sxs-lookup"><span data-stu-id="a4e8e-141">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling3.md)