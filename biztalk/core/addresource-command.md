---
title: Commande AddResource | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b09bd8d-5e07-4443-b626-60401a158540
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 875a087fa3afe7515aee2c406cbc47551bea1f4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="addresource-command"></a><span data-ttu-id="fa0d0-102">Commande AddResource</span><span class="sxs-lookup"><span data-stu-id="fa0d0-102">AddResource Command</span></span>
<span data-ttu-id="fa0d0-103">Les rubriques de cette section contiennent des informations d'ordre technique relatives aux paramètres de la commande AddResource.</span><span class="sxs-lookup"><span data-stu-id="fa0d0-103">The topics in this section provide reference information about the parameters of the AddResource command.</span></span> <span data-ttu-id="fa0d0-104">Les paramètres que vous utilisez avec cette commande varient en fonction du type d’artefact que vous souhaitez ajouter.</span><span class="sxs-lookup"><span data-stu-id="fa0d0-104">The parameters that you use with this command vary according to the type of artifact that you want to add.</span></span> <span data-ttu-id="fa0d0-105">Pour obtenir la liste complète des types d’artefacts, utilisez la **ListTypes** de commande, comme décrit dans [commande ListTypes](../core/listtypes-command.md).</span><span class="sxs-lookup"><span data-stu-id="fa0d0-105">To obtain complete lists of artifact types, use the **ListTypes** command, as described in [ListTypes Command](../core/listtypes-command.md).</span></span>  
  
 <span data-ttu-id="fa0d0-106">Pour obtenir de l'aide sur l'ajout d'un type d'artefact particulier, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="fa0d0-106">To get help for adding a particular artifact type, type the following command:</span></span>  
  
 <span data-ttu-id="fa0d0-107">**BTSTask AddResource /Type :**\<*nom de type* \> **/ ?**</span><span class="sxs-lookup"><span data-stu-id="fa0d0-107">**BTSTask AddResource /Type:**\<*type name*\> **/?**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa0d0-108">Si l’objet que vous ajoutez possède un nom de chemin d’accès très long, y compris le nom de fichier, l’opération d’ajout de l’artefact à une application peut échouer.</span><span class="sxs-lookup"><span data-stu-id="fa0d0-108">If the artifact you are adding has a very long path name, including the file name, the operation to add the artifact to an application may fail.</span></span> <span data-ttu-id="fa0d0-109">Un chemin d’accès ne peut pas dépasser 260 caractères.</span><span class="sxs-lookup"><span data-stu-id="fa0d0-109">A path cannot exceed 260 characters.</span></span>  
>   
>  <span data-ttu-id="fa0d0-110">Si une opération d'ajout échoue, toutes les actions lancées pendant cette opération sont annulées à l'exception de l'ajout des assemblys (ils ne sont pas supprimés du Global Assembly Cache s'ils ont été ajoutés par cette commande) et de l'entrée de données (elles ne sont pas supprimées du Registre Windows lorsqu'elles existent).</span><span class="sxs-lookup"><span data-stu-id="fa0d0-110">If an add operation fails, all actions taken during the operation are rolled back, except that assemblies are not removed from the global assembly cache if they were added by this command, and entries are not removed from the Windows registry if any entries were made.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa0d0-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fa0d0-111">In This Section</span></span>  
  
-   [<span data-ttu-id="fa0d0-112">Commande AddResource : assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="fa0d0-112">AddResource Command: BizTalk Assembly</span></span>](../core/addresource-command-biztalk-assembly.md)  
  
-   [<span data-ttu-id="fa0d0-113">Commande AddResource : liaison BizTalk</span><span class="sxs-lookup"><span data-stu-id="fa0d0-113">AddResource Command: BizTalk Binding</span></span>](../core/addresource-command-biztalk-binding.md)  
  
-   [<span data-ttu-id="fa0d0-114">Commande AddResource : assembly .NET</span><span class="sxs-lookup"><span data-stu-id="fa0d0-114">AddResource Command: .NET Assembly</span></span>](../core/addresource-command-net-assembly.md)  
  
-   [<span data-ttu-id="fa0d0-115">Commande AddResource : artefact BAM</span><span class="sxs-lookup"><span data-stu-id="fa0d0-115">AddResource Command: BAM Artifact</span></span>](../core/addresource-command-bam-artifact.md)  
  
-   [<span data-ttu-id="fa0d0-116">Commande AddResource : certificat</span><span class="sxs-lookup"><span data-stu-id="fa0d0-116">AddResource Command: Certificate</span></span>](../core/addresource-command-certificate.md)  
  
-   [<span data-ttu-id="fa0d0-117">Commande AddResource : composant COM</span><span class="sxs-lookup"><span data-stu-id="fa0d0-117">AddResource Command: COM Component</span></span>](../core/addresource-command-com-component.md)  
  
-   [<span data-ttu-id="fa0d0-118">Commande AddResource : fichier</span><span class="sxs-lookup"><span data-stu-id="fa0d0-118">AddResource Command: File</span></span>](../core/addresource-command-file.md)  
  
-   [<span data-ttu-id="fa0d0-119">Commande AddResource : script de prétraitement</span><span class="sxs-lookup"><span data-stu-id="fa0d0-119">AddResource Command: Preprocessing Script</span></span>](../core/addresource-command-preprocessing-script.md)  
  
-   [<span data-ttu-id="fa0d0-120">Commande AddResource : script de post-traitement</span><span class="sxs-lookup"><span data-stu-id="fa0d0-120">AddResource Command: Postprocessing Script</span></span>](../core/addresource-command-postprocessing-script.md)  
  
-   [<span data-ttu-id="fa0d0-121">Commande AddResource : stratégie</span><span class="sxs-lookup"><span data-stu-id="fa0d0-121">AddResource Command: Policy</span></span>](../core/addresource-command-policy.md)  
  
-   [<span data-ttu-id="fa0d0-122">Commande AddResource : répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="fa0d0-122">AddResource Command: Virtual Directory</span></span>](../core/addresource-command-virtual-directory.md)