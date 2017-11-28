---
title: Commande RemoveResource | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e2c6046-43d4-4ac1-a1b1-3795b4e44038
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d091c46ea25cbb2489264316239b6763d841a47e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="removeresource-command"></a><span data-ttu-id="4d25e-102">Commande RemoveResource</span><span class="sxs-lookup"><span data-stu-id="4d25e-102">RemoveResource Command</span></span>
<span data-ttu-id="4d25e-103">Supprime un artefact de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4d25e-103">Removes (deletes) an artifact from the BizTalk Management database.</span></span> <span data-ttu-id="4d25e-104">L'exécution de cette commande ne supprime pas l'artefact du Global Assembly Cache (GAC), du système de fichiers, du magasin de certificats, des services Internet ou du Registre Windows s'il existe à ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="4d25e-104">Running this command does not remove the artifact from the global assembly cache (GAC), file system, certificate store, Internet Information Services, or the Windows registry, if it exists in any of these locations.</span></span> <span data-ttu-id="4d25e-105">Elle ne supprime pas de définition BAM dans la base de données d'importation principale BAM ni de stratégies dans la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="4d25e-105">It does not remove a BAM definition from the BAM Primary Import database nor does it remove policies from the Rule Engine database.</span></span> <span data-ttu-id="4d25e-106">Si vous exécutez cette commande pour supprimer un fichier de liaison, les liaisons ne sont pas modifiées : seul le fichier de liaison est supprimé.</span><span class="sxs-lookup"><span data-stu-id="4d25e-106">If you run this command to remove a binding file, the bindings remain unchanged – only the binding file is removed.</span></span>  
  
 <span data-ttu-id="4d25e-107">Vous pouvez utiliser cette commande pour supprimer les types d'artefact suivants :</span><span class="sxs-lookup"><span data-stu-id="4d25e-107">You can use this command to remove the following artifact types:</span></span>  
  
-   <span data-ttu-id="4d25e-108">Assembly .NET (System.BizTalk:Assembly)</span><span class="sxs-lookup"><span data-stu-id="4d25e-108">.NET assembly (System.BizTalk:Assembly)</span></span>  
  
-   <span data-ttu-id="4d25e-109">Définition BAM (System.BizTalk:Bam)</span><span class="sxs-lookup"><span data-stu-id="4d25e-109">BAM definition (System.BizTalk:Bam)</span></span>  
  
-   <span data-ttu-id="4d25e-110">Assembly BizTalk (System.BizTalk:BizTalkAssembly)</span><span class="sxs-lookup"><span data-stu-id="4d25e-110">BizTalk assembly (System.BizTalk:BizTalkAssembly</span></span>  
  
-   <span data-ttu-id="4d25e-111">Fichier de liaison BizTalk (System.BizTalk:BizTalkBinding)</span><span class="sxs-lookup"><span data-stu-id="4d25e-111">BizTalk binding file (System.BizTalk:BizTalkBinding)</span></span>  
  
-   <span data-ttu-id="4d25e-112">Certificat de sécurité (System.BizTalk:Certificate)</span><span class="sxs-lookup"><span data-stu-id="4d25e-112">Security certificate (System.BizTalk:Certificate)</span></span>  
  
-   <span data-ttu-id="4d25e-113">Composant COM (System.BizTalk:Com)</span><span class="sxs-lookup"><span data-stu-id="4d25e-113">COM component (System.BizTalk:Com)</span></span>  
  
-   <span data-ttu-id="4d25e-114">Fichier ad hoc (System.BizTalk:File)</span><span class="sxs-lookup"><span data-stu-id="4d25e-114">Ad hoc file (System.BizTalk:File)</span></span>  
  
-   <span data-ttu-id="4d25e-115">Script de post-traitement (System.BizTalk:PostProcessingScript)</span><span class="sxs-lookup"><span data-stu-id="4d25e-115">Postprocessing script (System.BizTalk:PostProcessingScript)</span></span>  
  
-   <span data-ttu-id="4d25e-116">Script de post-traitement (System.BizTalk:PreProcessingScript)</span><span class="sxs-lookup"><span data-stu-id="4d25e-116">Preprocessing script (System.BizTalk:PreProcessingScript)</span></span>  
  
-   <span data-ttu-id="4d25e-117">Stratégie ou règle (System.BizTalk:Rules)</span><span class="sxs-lookup"><span data-stu-id="4d25e-117">Policy or rule (System.BizTalk:Rules)</span></span>  
  
-   <span data-ttu-id="4d25e-118">Répertoire virtuel (System.BizTalk:WebDirectory)</span><span class="sxs-lookup"><span data-stu-id="4d25e-118">Virtual directory (System.BizTalk:WebDirectory)</span></span>  
  
 <span data-ttu-id="4d25e-119">L'opération de suppression échoue dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="4d25e-119">The remove operation will fail in the following cases:</span></span>  
  
-   <span data-ttu-id="4d25e-120">tentative de suppression d'un assembly BizTalk auquel un autre assembly fait référence ;</span><span class="sxs-lookup"><span data-stu-id="4d25e-120">You attempt to remove a BizTalk assembly to which another assembly has a reference.</span></span>  
  
-   <span data-ttu-id="4d25e-121">tentative de suppression d'un assembly BizTalk comprenant un pipeline déjà utilisé par un port d'envoi ou de réception ;</span><span class="sxs-lookup"><span data-stu-id="4d25e-121">You attempt to remove a BizTalk assembly that includes a pipeline that is used by a send or receive port.</span></span>  
  
-   <span data-ttu-id="4d25e-122">tentative de suppression d'un assembly BizTalk comprenant un mappage déjà utilisé par un port d'envoi ;</span><span class="sxs-lookup"><span data-stu-id="4d25e-122">You attempt to remove a BizTalk assembly that includes a map used by a send port.</span></span>  
  
-   <span data-ttu-id="4d25e-123">tentative de suppression d'un assembly BizTalk comprenant une orchestration dont l'état n'est pas « Désinscrit » ou dont une instance a été interrompue.</span><span class="sxs-lookup"><span data-stu-id="4d25e-123">You attempt to remove a BizTalk assembly that includes an orchestration that is not in an unenlisted state or that has a suspended instance.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="4d25e-124">Utilisation</span><span class="sxs-lookup"><span data-stu-id="4d25e-124">Usage</span></span>  
 <span data-ttu-id="4d25e-125">**« ApplicationName » BTSTask RemoveResource :** *valeur* **ApplicationName :** *valeur* [**/Server :**  *valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="4d25e-125">**BTSTask RemoveResource /ApplicationName:** *value* **/Luid:** *value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="4d25e-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4d25e-126">Parameters</span></span>  
  
|<span data-ttu-id="4d25e-127">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4d25e-127">Parameter</span></span>|<span data-ttu-id="4d25e-128">Requis</span><span class="sxs-lookup"><span data-stu-id="4d25e-128">Required</span></span>|<span data-ttu-id="4d25e-129"> Description</span><span class="sxs-lookup"><span data-stu-id="4d25e-129">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="4d25e-130">**/ ApplicationName** (ou **/A**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="4d25e-130">**/ApplicationName** (or **/A**, see Remarks)</span></span>|<span data-ttu-id="4d25e-131">Oui</span><span class="sxs-lookup"><span data-stu-id="4d25e-131">Yes</span></span>|<span data-ttu-id="4d25e-132">Nom de l'application BizTalk contenant l'artefact de ressource à supprimer.</span><span class="sxs-lookup"><span data-stu-id="4d25e-132">Name of the BizTalk application containing the resource artifact to delete.</span></span> <span data-ttu-id="4d25e-133">Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).</span><span class="sxs-lookup"><span data-stu-id="4d25e-133">If the name includes spaces, you must enclose it with double quotation marks (").</span></span>|  
|<span data-ttu-id="4d25e-134">**/ Luid** (ou **/l**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="4d25e-134">**/Luid** (or **/L**, see Remarks)</span></span>|<span data-ttu-id="4d25e-135">Oui</span><span class="sxs-lookup"><span data-stu-id="4d25e-135">Yes</span></span>|<span data-ttu-id="4d25e-136">Identificateur unique local (LUID) de l'artefact.</span><span class="sxs-lookup"><span data-stu-id="4d25e-136">Locally unique identifier (LUID) of the artifact.</span></span> <span data-ttu-id="4d25e-137">Vous pouvez obtenir l’identificateur LUID à l’aide de la [commande ListApp](../core/listapp-command.md).</span><span class="sxs-lookup"><span data-stu-id="4d25e-137">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
|<span data-ttu-id="4d25e-138">**/ Serveur** (ou **/S**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="4d25e-138">**/Server** (or **/S**, see Remarks)</span></span>|<span data-ttu-id="4d25e-139">Non</span><span class="sxs-lookup"><span data-stu-id="4d25e-139">No</span></span>|<span data-ttu-id="4d25e-140">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.</span><span class="sxs-lookup"><span data-stu-id="4d25e-140">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="4d25e-141">Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="4d25e-141">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="4d25e-142">Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).</span><span class="sxs-lookup"><span data-stu-id="4d25e-142">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="4d25e-143">Exemples :</span><span class="sxs-lookup"><span data-stu-id="4d25e-143">Examples:</span></span><br /><br /> <span data-ttu-id="4d25e-144">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="4d25e-144">Server=MyServer</span></span><br /><br /> <span data-ttu-id="4d25e-145">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="4d25e-145">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="4d25e-146">Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4d25e-146">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
|<span data-ttu-id="4d25e-147">**/ Base de données** (ou **/D**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="4d25e-147">**/Database** (or **/D**, see Remarks)</span></span>|<span data-ttu-id="4d25e-148">Non</span><span class="sxs-lookup"><span data-stu-id="4d25e-148">No</span></span>|<span data-ttu-id="4d25e-149">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4d25e-149">Name of the BizTalk Management database.</span></span> <span data-ttu-id="4d25e-150">Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4d25e-150">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="4d25e-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d25e-151">Sample</span></span>  
 <span data-ttu-id="4d25e-152">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**</span><span class="sxs-lookup"><span data-stu-id="4d25e-152">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d25e-153">Notes</span><span class="sxs-lookup"><span data-stu-id="4d25e-153">Remarks</span></span>  
 <span data-ttu-id="4d25e-154">Les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="4d25e-154">Parameters are not case-sensitive.</span></span> <span data-ttu-id="4d25e-155">Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="4d25e-155">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d25e-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d25e-156">See Also</span></span>  
 <span data-ttu-id="4d25e-157">[Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4d25e-157">[BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) </span></span>  
 [<span data-ttu-id="4d25e-158">Comment supprimer un artefact d’une Application</span><span class="sxs-lookup"><span data-stu-id="4d25e-158">How to Remove an Artifact from an Application</span></span>](../core/how-to-remove-an-artifact-from-an-application.md)