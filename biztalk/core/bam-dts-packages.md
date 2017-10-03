---
title: Les Packages DTS BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DTS packages, BAM
- BAM, DTS packages
ms.assetid: bba70d81-6ddf-4f1f-a1f7-d5a5bf453bae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 105d1b42848b73505d9a82df07693111708ce802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-dts-packages"></a><span data-ttu-id="b9983-102">Lots DTS BAM</span><span class="sxs-lookup"><span data-stu-id="b9983-102">BAM DTS Packages</span></span>
<span data-ttu-id="b9983-103">Un administrateur peut mettre à jour les paramètres des lots DTS BAM suivants :</span><span class="sxs-lookup"><span data-stu-id="b9983-103">An administrator can update parameters for the following BAM DTS packages:</span></span>  
  
-   <span data-ttu-id="b9983-104">Le **CubeUpdate** package de Services DTS (Data Transformation) se trouve toujours sur le même serveur que la base de données de schémas en étoile.</span><span class="sxs-lookup"><span data-stu-id="b9983-104">The **CubeUpdate** Data Transformation Services (DTS) package is always located on the same server as the Star Schema database.</span></span>  
  
-   <span data-ttu-id="b9983-105">Le **DataMaintenance** de package DTS est toujours situé sur le même serveur que la base de données d’importation principale.</span><span class="sxs-lookup"><span data-stu-id="b9983-105">The **DataMaintenance** DTS package is always located on the same server as the Primary Import database.</span></span>  
  
 <span data-ttu-id="b9983-106">Les lots DTS utilisent les paramètres suivants dans le fichier BAMConfiguration.xml.</span><span class="sxs-lookup"><span data-stu-id="b9983-106">The DTS packages use the following parameters in the BAMConfiguration.xml file.</span></span>  
  
|<span data-ttu-id="b9983-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b9983-107">Parameter</span></span>|<span data-ttu-id="b9983-108"> Description</span><span class="sxs-lookup"><span data-stu-id="b9983-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9983-109">ConnectionTimeOut</span><span class="sxs-lookup"><span data-stu-id="b9983-109">ConnectionTimeOut</span></span>|<span data-ttu-id="b9983-110">La valeur du délai avant expiration (en secondes) de la connexion DTS est un entier.</span><span class="sxs-lookup"><span data-stu-id="b9983-110">The DTS connection time out value (in seconds) is an integer.</span></span> <span data-ttu-id="b9983-111">Si ce paramètre est omis, le fichier de configuration se base sur 60 secondes, qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b9983-111">If you omit the ConnectionTimeOut parameter, the configuration file uses 60 seconds, the default value.</span></span>|  
|<span data-ttu-id="b9983-112">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="b9983-112">Encryption</span></span>|<span data-ttu-id="b9983-113">Par défaut, les lots DTS ne chiffrent pas les données pendant qu'ils les transforment (la valeur d'Encryption est 0).</span><span class="sxs-lookup"><span data-stu-id="b9983-113">By default, the DTS packages do not encrypt data while they transform the data (Encryption value is 0).</span></span> <span data-ttu-id="b9983-114">Définissez Encryption sur 1 pour chiffrer les données pendant la transformation.</span><span class="sxs-lookup"><span data-stu-id="b9983-114">Set Encryption to 1 to encrypt the data during transformation.</span></span>|  
|<span data-ttu-id="b9983-115">OwnerPassword</span><span class="sxs-lookup"><span data-stu-id="b9983-115">OwnerPassword</span></span>|<span data-ttu-id="b9983-116">Le mot de passe du propriétaire de lot DTS.</span><span class="sxs-lookup"><span data-stu-id="b9983-116">The password for the DTS package owner.</span></span> <span data-ttu-id="b9983-117">Les propriétaires de lots DTS peuvent les ouvrir et les modifier.</span><span class="sxs-lookup"><span data-stu-id="b9983-117">DTS package owners can open and modify DTS packages.</span></span> <span data-ttu-id="b9983-118">Pour plus d'informations sur les propriétaires de lots DTS, consultez documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b9983-118">For information about DTS package owners, see SQL Server Books Online.</span></span>|  
|<span data-ttu-id="b9983-119">UserPassword</span><span class="sxs-lookup"><span data-stu-id="b9983-119">UserPassword</span></span>|<span data-ttu-id="b9983-120">Le mot de passe de l'utilisateur DTS.</span><span class="sxs-lookup"><span data-stu-id="b9983-120">The password for the DTS user.</span></span> <span data-ttu-id="b9983-121">Les utilisateurs de lots DTS peuvent exécuter des lots DTS.</span><span class="sxs-lookup"><span data-stu-id="b9983-121">DTS package users can run DTS packages.</span></span> <span data-ttu-id="b9983-122">Pour plus d'informations sur les utilisateurs de lots DTS, consultez documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b9983-122">For information about DTS package users, see SQL Server Books Online.</span></span>|  
  
 <span data-ttu-id="b9983-123">Dans le fichier BAMConfiguration.xml, les lots DTS font appel aux conventions d'attribution de noms suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9983-123">The DTS packages use the following naming conventions in the BAMConfiguration.xml file:</span></span>  
  
-   <span data-ttu-id="b9983-124">**CubeUpdate** de package DTS</span><span class="sxs-lookup"><span data-stu-id="b9983-124">**CubeUpdate** DTS package</span></span>  
  
     <span data-ttu-id="b9983-125">**bam_AN_\<** </span><span class="sxs-lookup"><span data-stu-id="b9983-125">**bam_AN_\<** </span></span>  
     <span data-ttu-id="b9983-126">***Nom du cube* >**, où NomCube est le nom du cube.</span><span class="sxs-lookup"><span data-stu-id="b9983-126">***CubeName* >**, where CubeName is the name of the cube.</span></span> <span data-ttu-id="b9983-127">Le classeur BAM génère le nom de cube à partir du nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="b9983-127">The BAM workbook generates the cube name from the view name.</span></span> <span data-ttu-id="b9983-128">Si vous modifiez le nom du cube dans le document XML de configuration BAM, le nouveau nom en résultant est utilisé dans le nom du lot DTS.</span><span class="sxs-lookup"><span data-stu-id="b9983-128">If you modify the cube name in the BAM configuration XML document, the new cube name is used in the DTS package name.</span></span>  
  
-   <span data-ttu-id="b9983-129">**DataMaintenance** de package DTS</span><span class="sxs-lookup"><span data-stu-id="b9983-129">**DataMaintenance** DTS package</span></span>  
  
     <span data-ttu-id="b9983-130">**bam_DM_\<** </span><span class="sxs-lookup"><span data-stu-id="b9983-130">**bam_DM_\<** </span></span>  
     <span data-ttu-id="b9983-131">***ActivityName* >**, où Nomactivité est le nom de l’activité.</span><span class="sxs-lookup"><span data-stu-id="b9983-131">***ActivityName* >**, where ActivityName is the name of the activity.</span></span>  
  
 <span data-ttu-id="b9983-132">Pour regrouper l'agrégation planifiée, vous devez exécuter le lot DTS CubeUpdate.</span><span class="sxs-lookup"><span data-stu-id="b9983-132">You run the CubeUpdate DTS package to aggregate the scheduled aggregation.</span></span> <span data-ttu-id="b9983-133">Dans la section suivante, vous pouvez spécifier la fenêtre de temps destinée à l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="b9983-133">In the next section, you can specify the time window for real-time data aggregation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9983-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9983-134">See Also</span></span>  
 <span data-ttu-id="b9983-135">[Schéma de Configuration BAM](../core/bam-configuration-schema.md) </span><span class="sxs-lookup"><span data-stu-id="b9983-135">[BAM Configuration Schema](../core/bam-configuration-schema.md) </span></span>  
 <span data-ttu-id="b9983-136">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="b9983-136">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="b9983-137">La gestion BAM</span><span class="sxs-lookup"><span data-stu-id="b9983-137">Managing BAM</span></span>](../core/managing-bam.md)