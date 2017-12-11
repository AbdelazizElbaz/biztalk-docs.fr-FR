---
title: Les erreurs courantes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fe48a8e-def0-4a00-aa7f-9a49ae555351
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b882c44e69489114a2dd8084df71d6414df0cb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="common-errors"></a><span data-ttu-id="ce2eb-102">Erreurs fréquentes</span><span class="sxs-lookup"><span data-stu-id="ce2eb-102">Common Errors</span></span>
<span data-ttu-id="ce2eb-103">Cette rubrique répertorie les messages d'erreur courants que vous pouvez rencontrer lors de la création de mappages à l'aide du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-103">This topic lists out common error messages you may encounter while creating maps using BizTalk Mapper.</span></span>  
  
## <a name="you-receive-error-event-id-324-when-parsing-dates"></a><span data-ttu-id="ce2eb-104">L'ID d'événement d'erreur 324 s'affiche lors de l'analyse de dates</span><span class="sxs-lookup"><span data-stu-id="ce2eb-104">You receive error event ID 324 when parsing dates</span></span>  
  
### <a name="problem"></a><span data-ttu-id="ce2eb-105">Problème</span><span class="sxs-lookup"><span data-stu-id="ce2eb-105">Problem</span></span>  
 <span data-ttu-id="ce2eb-106">Lorsque vous utilisez la base de données **extracteur de valeur** fonctoid dans un mappage pour extraire un champ de date, votre document peut échouer la validation par rapport à la définition de document sortant.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-106">When you use the Database **Value Extractor** functoid in a map to extract a date field, your document may fail validation against the outbound document definition.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ce2eb-107">le journal des événements peut connecter une erreur de validation similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-107"> may log a validation error similar to the following in the event log:</span></span>  
  
 <span data-ttu-id="ce2eb-108">Source d’événement : BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ce2eb-108">Event Source: BizTalk Server</span></span>  
  
 <span data-ttu-id="ce2eb-109">Catégorie d’événement : Le traitement des documents</span><span class="sxs-lookup"><span data-stu-id="ce2eb-109">Event Category: Document Processing</span></span>  
  
 <span data-ttu-id="ce2eb-110">ID d’événement : 324</span><span class="sxs-lookup"><span data-stu-id="ce2eb-110">Event ID: 324</span></span>  
  
 <span data-ttu-id="ce2eb-111">Description :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-111">Description:</span></span>  
  
 <span data-ttu-id="ce2eb-112">Une erreur s'est produite dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-112">An error occurred in BizTalk Server.</span></span>  
  
 <span data-ttu-id="ce2eb-113">Détails :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-113">Details:</span></span>  
  
 -----------------------------\-  
  
 <span data-ttu-id="ce2eb-114">Le document XML n’a pas pour la raison suivante : erreur d’analyse de ' 10/12/1995 ' comme type de données de date.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-114">The XML document has failed validation for the following reason: Error parsing '10/12/1995' as date datatype.</span></span>  
  
 <span data-ttu-id="ce2eb-115">ID de la file d’attente suspendue : « {A1127909-CA36-4359-B672-7CBA8B60BDAF} »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-115">Suspended Queue ID: "{A1127909-CA36-4359-B672-7CBA8B60BDAF}"</span></span>  
  
### <a name="cause"></a><span data-ttu-id="ce2eb-116">Cause</span><span class="sxs-lookup"><span data-stu-id="ce2eb-116">Cause</span></span>  
 <span data-ttu-id="ce2eb-117">Le format de date (tel que renvoyé par la source de données) n'est pas conforme au format ISO 8601, le format requis par XML.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-117">The date format (as it is returned from the data source) is not in ISO 8601 format, which is the format required by XML.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ce2eb-118">Résolution</span><span class="sxs-lookup"><span data-stu-id="ce2eb-118">Resolution</span></span>  
 <span data-ttu-id="ce2eb-119">Pour résoudre ce problème, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-119">To resolve this issue, do one of the following:</span></span>  
  
-   <span data-ttu-id="ce2eb-120">Modifiez la définition du document sortant afin d'utiliser un type de données chaîne au lieu d'un type de données date.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-120">Edit your outbound document definition to use a string datatype instead of a date datatype.</span></span>  
  
-   <span data-ttu-id="ce2eb-121">Créer un personnalisé [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)] **Script** fonctoid qui convertira la sortie de la base de données **extracteur de valeur** fonctoid dans le format ISO 8601.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-121">Create a custom [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)]**Script** functoid that will convert the output of the Database **Value Extractor** functoid into the ISO 8601 format.</span></span>  
  
 <span data-ttu-id="ce2eb-122">Pour plus d’informations, consultez l’article [278737](http://support.microsoft.com/kb/278737/en-us).</span><span class="sxs-lookup"><span data-stu-id="ce2eb-122">For more information, see KB article [278737](http://support.microsoft.com/kb/278737/en-us).</span></span>  
  
## <a name="you-receive-internal-compiler-error-0xc0000005-at-address-53624fd6-when-compiling-the-maps"></a><span data-ttu-id="ce2eb-123">L'erreur interne du compilateur (0xc0000005 à l'adresse 53624FD6) s'affiche lors de la compilation des mappages</span><span class="sxs-lookup"><span data-stu-id="ce2eb-123">You receive Internal Compiler Error (0xc0000005 at address 53624FD6) when compiling the maps</span></span>  
  
### <a name="problem"></a><span data-ttu-id="ce2eb-124">Problème</span><span class="sxs-lookup"><span data-stu-id="ce2eb-124">Problem</span></span>  
 <span data-ttu-id="ce2eb-125">Lors de la compilation d'un seul projet BizTalk comprenant des schémas, mappages ou orchestrations de grande taille, le compilateur peut générer une erreur similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-125">When you compile a single BizTalk project that consists of large schemas, maps, or orchestrations, the compiler may generate an error similar to the following:</span></span>  
  
 <span data-ttu-id="ce2eb-126">Erreur interne du compilateur (0xc0000005 à l’adresse 53624FD6) : en est probablement 'CODEGEN'.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-126">Internal Compiler Error (0xc0000005 at address 53624FD6): likely culprit is 'CODEGEN'.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="ce2eb-127">Cause</span><span class="sxs-lookup"><span data-stu-id="ce2eb-127">Cause</span></span>  
 <span data-ttu-id="ce2eb-128">Le compilateur [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] limite à 16 Mo la taille totale de l'ensemble des chaînes d'un seul projet.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-128">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler has a 16-megabyte limitation on the total size of all strings in a single project.</span></span> <span data-ttu-id="ce2eb-129">Lors de la compilation des projets BizTalk, le compilateur sérialise les schémas, les mappages et les orchestrations pour créer les assemblys, ce qui accroît la taille totale des chaînes parfois au-delà de la limite autorisée.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-129">While compiling BizTalk projects, the compiler serializes schemas, maps, and orchestrations for creating the assemblies, and this increases the total size of all strings, which may exceed the limitation.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ce2eb-130">Résolution</span><span class="sxs-lookup"><span data-stu-id="ce2eb-130">Resolution</span></span>  
 <span data-ttu-id="ce2eb-131">Pour résoudre ce problème, vous pouvez diviser les schémas ou les mappages en plusieurs projets BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-131">To resolve this issue, you can separate schemas or maps into different BizTalk projects.</span></span>  
  
## <a name="you-receive-errors-about-the-type-name-of-a-biztalk-artifact"></a><span data-ttu-id="ce2eb-132">Des erreurs concernant le nom du type d'un artefact BizTalk s'affichent</span><span class="sxs-lookup"><span data-stu-id="ce2eb-132">You receive errors about the Type Name of a BizTalk artifact</span></span>  
  
### <a name="problem"></a><span data-ttu-id="ce2eb-133">Problème</span><span class="sxs-lookup"><span data-stu-id="ce2eb-133">Problem</span></span>  
 <span data-ttu-id="ce2eb-134">Dans un projet BizTalk, créer un mappage avec le nom de fichier **System.btm** ou **Microsoft.btm**.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-134">In a BizTalk project, create a map with filename **System.btm** or **Microsoft.btm**.</span></span> <span data-ttu-id="ce2eb-135">Lors de la création du projet, le Mappeur BizTalk génère une erreur similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-135">When you build the project, the BizTalk Mapper generates an error similar to any of the following:</span></span>  
  
-   <span data-ttu-id="ce2eb-136">« Le nom du type 'SerializableAttribute' n'existe pas... »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-136">“The typename ‘SerializableAttribute’ does not exist…”</span></span>  
  
-   <span data-ttu-id="ce2eb-137">« Le nom du type 'NonSerializableAttribute' n'existe pas... »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-137">“The typename ‘NonSerializableAttribute’ does not exist…”</span></span>  
  
-   <span data-ttu-id="ce2eb-138">« Le nom du type 'SerializableAttributeAttribute' n'existe pas... »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-138">“The typename ‘SerializableAttributeAttribute’ does not exist…”</span></span>  
  
-   <span data-ttu-id="ce2eb-139">« Le nom du type 'XLANs' n'existe pas... »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-139">“The typename ‘XLANs’ does not exist…”</span></span>  
  
### <a name="cause"></a><span data-ttu-id="ce2eb-140">Cause</span><span class="sxs-lookup"><span data-stu-id="ce2eb-140">Cause</span></span>  
 <span data-ttu-id="ce2eb-141">Le **nom de Type** dans les **propriétés** grille ne devrait pas les espaces de noms .NET réservé, tel que **système**, **Microsoft**, etc.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-141">The **Type Name** in the **Properties** grid should not have any reserved .NET namespaces, such as **System**, **Microsoft**, etc.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ce2eb-142">Résolution</span><span class="sxs-lookup"><span data-stu-id="ce2eb-142">Resolution</span></span>  
 <span data-ttu-id="ce2eb-143">Pour résoudre ce problème, suivez l'une des solutions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-143">To resolve this issue, you can follow any of these workarounds:</span></span>  
  
-   <span data-ttu-id="ce2eb-144">Modifiez le nom du mappage par une chaîne n'étant pas un mot réservé .NET.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-144">Modify the name of the map to any string which is not a .NET reserved word.</span></span> <span data-ttu-id="ce2eb-145">Par défaut, le système de projet BizTalk crée le **nom de Type** à partir du nom de l’artefact correspondant.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-145">By default, the BizTalk project system creates the **Type Name** from the name of the respective artifact.</span></span>  
  
     <span data-ttu-id="ce2eb-146">Pour, par exemple : création d’un mappage avec le nom **Map1.btm** définit le **nom de Type** valeur de propriété à **Map1**.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-146">For e.g.: Creating a new map with name **Map1.btm** sets the **Type Name** property value to **Map1**.</span></span> <span data-ttu-id="ce2eb-147">Toutefois, renommer un BizTalk existant artefact ne modifie pas le **nom de Type**.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-147">However, renaming an existing BizTalk artifact does not change the **Type Name**.</span></span>  
  
-   <span data-ttu-id="ce2eb-148">Vérifiez que le nom de fichier de chaque artefact du projet BizTalk ne correspond à aucun espace de noms réservé .NET.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-148">Ensure the filename of any of the artifacts in the BizTalk project is not a .NET reserved namespace.</span></span>  
  
## <a name="you-receive-errors-about-the-file-name-of-a-biztalk-artifact"></a><span data-ttu-id="ce2eb-149">Des erreurs concernant le nom de fichier d'un artefact BizTalk s'affichent</span><span class="sxs-lookup"><span data-stu-id="ce2eb-149">You receive errors about the File Name of a BizTalk artifact</span></span>  
  
### <a name="problem"></a><span data-ttu-id="ce2eb-150">Problème</span><span class="sxs-lookup"><span data-stu-id="ce2eb-150">Problem</span></span>  
 <span data-ttu-id="ce2eb-151">Lors de la création d'un projet BizTalk, le Mappeur BizTalk génère une erreur similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-151">When you build a BizTalk project, the BizTalk Mapper generates an error similar to any of the following:</span></span>  
  
-   <span data-ttu-id="ce2eb-152">« Le fichier \<nom de fichier\> a des valeurs en double pour les propriétés du nom de type et espace de noms. »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-152">“The File \<filename\> has duplicate values for namespace and type name properties.”</span></span>  
  
-   <span data-ttu-id="ce2eb-153">« L’espace de noms \<nom\> contient déjà une définition pour '_'. »</span><span class="sxs-lookup"><span data-stu-id="ce2eb-153">“The namespace \<name\> already contains a definition for ‘_’.”</span></span>  
  
### <a name="cause"></a><span data-ttu-id="ce2eb-154">Cause</span><span class="sxs-lookup"><span data-stu-id="ce2eb-154">Cause</span></span>  
 <span data-ttu-id="ce2eb-155">Dans le projet BizTalk, vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-155">In the BizTalk project, check for the following:</span></span>  
  
-   <span data-ttu-id="ce2eb-156">Plusieurs artefacts possèdent le même nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-156">Multiple artifacts have the same filename.</span></span> <span data-ttu-id="ce2eb-157">Pour, par exemple, **Map1.xsd** et**Map1.btm**.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-157">For e.g., **Map1.xsd** and**Map1.btm**.</span></span>  
  
-   <span data-ttu-id="ce2eb-158">Le nom de fichier comprend uniquement des caractères spéciaux (**~**, **!**,  **@** , etc.).</span><span class="sxs-lookup"><span data-stu-id="ce2eb-158">The filename comprises of only special characters (**~**, **!**, **@**, etc.).</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ce2eb-159">Résolution</span><span class="sxs-lookup"><span data-stu-id="ce2eb-159">Resolution</span></span>  
 <span data-ttu-id="ce2eb-160">Pour résoudre ce problème, suivez l'une des solutions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce2eb-160">To resolve this issue, you can follow any of these workarounds:</span></span>  
  
-   <span data-ttu-id="ce2eb-161">Renommez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-161">Rename the files.</span></span> <span data-ttu-id="ce2eb-162">Vérifiez que les noms de fichiers de tous les artefacts du projet BizTalk sont uniques.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-162">Ensure the filenames for all artifacts in the BizTalk project are unique.</span></span>  
  
-   <span data-ttu-id="ce2eb-163">Vérifiez que le nom de type de chaque artefact du projet BizTalk est unique.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-163">Ensure Type Name for all artifacts in the BizTalk project are unique.</span></span>  
  
## <a name="building-any-c-workflow-project-with-biztalk-mapper-shows-a-warning-regarding-version-conflict-for-envdtedll"></a><span data-ttu-id="ce2eb-164">La création d'un projet de workflow C# à l'aide du Mappeur BizTalk affiche un avertissement relatif à un conflit de version pour EnvDTE.dll</span><span class="sxs-lookup"><span data-stu-id="ce2eb-164">Building any C# workflow project with BizTalk Mapper shows a warning regarding version conflict for EnvDTE.dll</span></span>  
  
### <a name="problem"></a><span data-ttu-id="ce2eb-165">Problème</span><span class="sxs-lookup"><span data-stu-id="ce2eb-165">Problem</span></span>  
 <span data-ttu-id="ce2eb-166">La création d'un projet de workflow C# avec l'activité du Mappeur BizTalk affiche toujours l'avertissement suivant relatif à un conflit de version pour EnvDTE.dll.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-166">Building any C# workflow project with BizTalk Mapper acitivity always shows the following warning about version conflict for EnvDTE.dll.</span></span>  
  
 <span data-ttu-id="ce2eb-167">Impossible de résoudre le conflit entre « EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a » et « EnvDTE, Version=7.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a ».</span><span class="sxs-lookup"><span data-stu-id="ce2eb-167">No way to resolve conflict between "EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" and "EnvDTE, Version=7.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a".</span></span> <span data-ttu-id="ce2eb-168">Choix arbitraire de « EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a ».</span><span class="sxs-lookup"><span data-stu-id="ce2eb-168">Choosing "EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" arbitrarily.</span></span>  <span data-ttu-id="ce2eb-169">Envisagez le remappage via app.config de l'assembly « EnvDTE, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a » de la version « 7.0.3300.0 » [] vers la version « 8.0.0.0 » [C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll] pour résoudre le conflit et supprimer l'avertissement.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-169">Consider app.config remapping of assembly "EnvDTE, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" from Version "7.0.3300.0" [] to Version "8.0.0.0" [C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll] to solve conflict and get rid of warning.</span></span> <span data-ttu-id="ce2eb-170">C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9) : avertissement MSB3247 : des conflits entre différentes versions du même assembly dépendant ont été.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-170">C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9): warning MSB3247: Found conflicts between different versions of the same dependent assembly.</span></span>  
  
 <span data-ttu-id="ce2eb-171">WorkflowConsoleApplication3 -> C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe</span><span class="sxs-lookup"><span data-stu-id="ce2eb-171">WorkflowConsoleApplication3 -> C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe</span></span>  
  
### <a name="cause"></a><span data-ttu-id="ce2eb-172">Cause</span><span class="sxs-lookup"><span data-stu-id="ce2eb-172">Cause</span></span>  
 <span data-ttu-id="ce2eb-173">Ceci se produit en raison du fichier Microsoft.BizTalk.Mapper.OM.dll auquel l'activité du Mappeur fait référence.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-173">This happens because of the Microsoft.BizTalk.Mapper.OM.dll which the Mapper activity references.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ce2eb-174">Résolution</span><span class="sxs-lookup"><span data-stu-id="ce2eb-174">Resolution</span></span>  
 <span data-ttu-id="ce2eb-175">Ignorez l'avertissement.</span><span class="sxs-lookup"><span data-stu-id="ce2eb-175">Ignore the warning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2eb-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce2eb-176">See Also</span></span>  
 [<span data-ttu-id="ce2eb-177">Résolution des problèmes de mappages</span><span class="sxs-lookup"><span data-stu-id="ce2eb-177">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)