---
title: Fichiers de Configuration des Services BAM le Script de ligne de commande pour la Notification | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa4a460-58f9-439d-af28-0a9cb2288236
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b22607193ed7c345388a6435e2d58c16b8986370
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="bam-command-line-script-for-notification-services-configuration-files"></a><span data-ttu-id="b29f5-102">Script de ligne de commande BAM pour des fichiers de configuration des services de notification</span><span class="sxs-lookup"><span data-stu-id="b29f5-102">BAM Command-Line Script for Notification Services Configuration Files</span></span>
<span data-ttu-id="b29f5-103">Les administrateurs utilisent le script ProcessBamNSFiles.vbs pour personnaliser le comportement de SQL Server Notification Services en matière d'alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="b29f5-103">Administrators use the ProcessBamNSFiles.vbs script to customize the behavior of SQL Server Notification Services for BAM alerts.</span></span> <span data-ttu-id="b29f5-104">Vous pouvez utiliser ce script pour obtenir le fichier de définition d'application des services de notification ainsi que celui de configuration.</span><span class="sxs-lookup"><span data-stu-id="b29f5-104">You can use the script to obtain the Notification Services application definition file (ADF) and Notification Services configuration file.</span></span> <span data-ttu-id="b29f5-105">Vous pouvez modifier ces fichiers, puis vous servir du script pour appliquer les modifications effectuées.</span><span class="sxs-lookup"><span data-stu-id="b29f5-105">These files can be modified and then the script can be used to apply the changes.</span></span>  
  
 <span data-ttu-id="b29f5-106">Ce script doit être exécuté à partir d'une invite de commandes des services de notification et non à partir d'une invite de commandes classique.</span><span class="sxs-lookup"><span data-stu-id="b29f5-106">You run the script from a Notification Services command prompt and not from a typical command prompt.</span></span> <span data-ttu-id="b29f5-107">À partir d'une invite de commandes classique, il ne s'exécute pas correctement.</span><span class="sxs-lookup"><span data-stu-id="b29f5-107">Running the script from a typical command prompt will cause the script to execute incorrectly.</span></span> <span data-ttu-id="b29f5-108">Pour l'exécuter, tous les paramètres sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="b29f5-108">When running the script all parameters are mandatory.</span></span>  
  
## <a name="get-command"></a><span data-ttu-id="b29f5-109">Commande GET</span><span class="sxs-lookup"><span data-stu-id="b29f5-109">Get command</span></span>  
 <span data-ttu-id="b29f5-110">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b29f5-110">**Usage**</span></span>  
  
 <span data-ttu-id="b29f5-111">**cscript ProcessBamNSFiles-Get \<chemin d’accès du fichier de configuration\> \<cheminaccèsadf\>\<serveur d’importation principale\> \<base de données d’importation principale  \>**</span><span class="sxs-lookup"><span data-stu-id="b29f5-111">**cscript ProcessBamNSFiles -Get \<configuration file path\> \<ADF file path\>  \<primary import server\> \<primary import database\>**</span></span>  
  
|<span data-ttu-id="b29f5-112">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b29f5-112">Parameter</span></span>|<span data-ttu-id="b29f5-113"> Description</span><span class="sxs-lookup"><span data-stu-id="b29f5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b29f5-114">chemin d'accès du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b29f5-114">configuration file path</span></span>|<span data-ttu-id="b29f5-115">Indique le nom du fichier de configuration ainsi que son emplacement de stockage.</span><span class="sxs-lookup"><span data-stu-id="b29f5-115">Specifies the name and location in which to store the configuration file.</span></span>|  
|<span data-ttu-id="b29f5-116">chemin d'accès du fichier ADF</span><span class="sxs-lookup"><span data-stu-id="b29f5-116">ADF file path</span></span>|<span data-ttu-id="b29f5-117">Indique le nom du fichier de définition d'application ainsi que son emplacement de stockage.</span><span class="sxs-lookup"><span data-stu-id="b29f5-117">Specifies the name and location in which to store the ADF file.</span></span>|  
|<span data-ttu-id="b29f5-118">serveur d'importation principale</span><span class="sxs-lookup"><span data-stu-id="b29f5-118">primary import server</span></span>|<span data-ttu-id="b29f5-119">Nom de l'ordinateur sur lequel la base de données d'importation principale BAM est stockée.</span><span class="sxs-lookup"><span data-stu-id="b29f5-119">Name of the computer on which the BAM Primary Import database is stored.</span></span>|  
|<span data-ttu-id="b29f5-120">base de données d'importation principale</span><span class="sxs-lookup"><span data-stu-id="b29f5-120">primary import database</span></span>|<span data-ttu-id="b29f5-121">Nom de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="b29f5-121">Name of the BAM Primary Import database.</span></span>|  
  
 <span data-ttu-id="b29f5-122">Récupère les fichiers de configuration et de définition d'application des services de notification dans la base de données d'importation principale BAM et les enregistre sous des chemins d'accès spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b29f5-122">Retrieves the Notification Services configuration and application definition files from the BAM Primary Import database and saves them to specified paths.</span></span>  
  
## <a name="update-command"></a><span data-ttu-id="b29f5-123">Commande UPDATE</span><span class="sxs-lookup"><span data-stu-id="b29f5-123">Update command</span></span>  
 <span data-ttu-id="b29f5-124">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b29f5-124">**Usage**</span></span>  
  
 <span data-ttu-id="b29f5-125">**cscript ProcessBamNSFiles-mise à jour \<configfilepath\> \<cheminfichieradf\>\<cheminaccèsadf server\> \<bdimportationprincipale  \>**</span><span class="sxs-lookup"><span data-stu-id="b29f5-125">**cscript ProcessBamNSFiles -Update \<configfilepath\> \<adffilepath\>  \<primaryimport server\> \<primary import db\>**</span></span>  
  
|<span data-ttu-id="b29f5-126">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b29f5-126">Parameter</span></span>|<span data-ttu-id="b29f5-127"> Description</span><span class="sxs-lookup"><span data-stu-id="b29f5-127">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b29f5-128">chemin d'accès du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b29f5-128">configuration file path</span></span>|<span data-ttu-id="b29f5-129">Indique le nom et l'emplacement du fichier à utiliser pour mettre à jour les informations de configuration des services de notification.</span><span class="sxs-lookup"><span data-stu-id="b29f5-129">Specifies the name and location from which to update the Notification Services configuration information.</span></span>|  
|<span data-ttu-id="b29f5-130">chemin d'accès du fichier ADF</span><span class="sxs-lookup"><span data-stu-id="b29f5-130">ADF file path</span></span>|<span data-ttu-id="b29f5-131">Indique le nom et l'emplacement du fichier à utiliser pour mettre à jour les informations de définition d'application.</span><span class="sxs-lookup"><span data-stu-id="b29f5-131">Specifies the name and location from which to update the ADF information.</span></span>|  
|<span data-ttu-id="b29f5-132">serveur d'importation principale</span><span class="sxs-lookup"><span data-stu-id="b29f5-132">primary import server</span></span>|<span data-ttu-id="b29f5-133">Nom de l'ordinateur sur lequel la base de données d'importation principale BAM est stockée.</span><span class="sxs-lookup"><span data-stu-id="b29f5-133">Name of the computer on which the BAM Primary Import database is stored.</span></span>|  
|<span data-ttu-id="b29f5-134">base de données d'importation principale</span><span class="sxs-lookup"><span data-stu-id="b29f5-134">primary import database</span></span>|<span data-ttu-id="b29f5-135">Nom de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="b29f5-135">Name of the BAM Primary Import database.</span></span>|  
  
 <span data-ttu-id="b29f5-136">Appelle les services de notification et met à jour les paramètres à l'aide des informations fournies par les fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b29f5-136">Calls Notification Services and updates the settings with the information in the specified files.</span></span> <span data-ttu-id="b29f5-137">Les fichiers de configuration et de définition d'application sont stockés dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="b29f5-137">The configuration and ADF files are stored in the BAM Primary Import database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29f5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b29f5-138">See Also</span></span>  
 [<span data-ttu-id="b29f5-139">Outils en ligne de commande BAM</span><span class="sxs-lookup"><span data-stu-id="b29f5-139">BAM Command-Line Tools</span></span>](../core/bam-command-line-tools.md)