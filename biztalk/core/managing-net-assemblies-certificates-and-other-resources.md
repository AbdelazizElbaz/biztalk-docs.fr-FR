---
title: "Gérer les assemblys .NET, certificats et autres ressources | Documents Microsoft"
description: "Liens pour ajouter des fichiers de liaison, les certificats, les assemblys, répertoires virtuels, fichiers, etc. dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efe27a11-19d8-4eb3-9f8c-f4336e4c3d66
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb74762bdf08e6e9e2a79650a26dedb0915ea8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-net-assemblies-certificates-and-other-resources"></a><span data-ttu-id="1c41d-103">Gérer les assemblys .NET, certificats et autres ressources</span><span class="sxs-lookup"><span data-stu-id="1c41d-103">Manage .NET Assemblies, Certificates, and Other Resources</span></span>

## <a name="overview"></a><span data-ttu-id="1c41d-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1c41d-104">Overview</span></span>
<span data-ttu-id="1c41d-105">Cette rubrique fournit des instructions sur l'utilisation de la console Administration de BizTalk Server et de l'outil de ligne de commande BTSTask pour la gestion des types suivants d'artefacts de ressource d'une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1c41d-105">This section provides instructions on using the BizTalk Server Administration console and the BTSTask command-line tool to manage the following types of resource artifacts for a BizTalk application.</span></span> <span data-ttu-id="1c41d-106">Ces artefacts de ressource ne peuvent pas être automatiquement déployés dans une application BizTalk à partir de Visual Studio. Vous devez donc les ajouter manuellement à l'application.</span><span class="sxs-lookup"><span data-stu-id="1c41d-106">These resource artifacts cannot be automatically deployed into a BizTalk application from Visual Studio, so you must add them manually to the application.</span></span> <span data-ttu-id="1c41d-107">Une fois que vous les avez ajoutés à l'application, cependant, vous pouvez les importer, exporter et installer sous la forme d'une unité avec l'application et ses autres artefacts.</span><span class="sxs-lookup"><span data-stu-id="1c41d-107">Once added to an application, however, you can import, export, and install them as a unit with the application and its other artifacts.</span></span>  
  
-   <span data-ttu-id="1c41d-108">**Les fichiers.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-108">**Files.**</span></span> <span data-ttu-id="1c41d-109">Vous pouvez inclure les fichiers ad hoc, tels qu'un fichier Lisezmoi.</span><span class="sxs-lookup"><span data-stu-id="1c41d-109">You can include ad hoc files, such as a Readme file.</span></span> <span data-ttu-id="1c41d-110">Lorsque vous installez l'application, les fichiers sont copiés dans le dossier d'installation.</span><span class="sxs-lookup"><span data-stu-id="1c41d-110">When you install the application, files are copied to the installation folder.</span></span>  
  
-   <span data-ttu-id="1c41d-111">**Certificats.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-111">**Certificates.**</span></span> <span data-ttu-id="1c41d-112">Vous pouvez ajouter un fichier de certificat à une application afin de pouvoir transférer le certificat d'un groupe BizTalk à un autre, au sein d'une application.</span><span class="sxs-lookup"><span data-stu-id="1c41d-112">You can add a certificate file to an application so that you can transport the certificate from one BizTalk group to another, packaged with an application.</span></span> <span data-ttu-id="1c41d-113">Vous attribuez des certificats aux ports d'envoi et emplacements de réception afin de vérifier les identités et d'établir des liaisons sécurisées.</span><span class="sxs-lookup"><span data-stu-id="1c41d-113">You assign certificates to send ports and receive locations to verify identities and to establish secure links.</span></span>  
  
-   <span data-ttu-id="1c41d-114">**Composants COM et COM +.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-114">**COM and COM+ components.**</span></span> <span data-ttu-id="1c41d-115">Vous pouvez inclure des composants COM gérés et COM+ gérés afin de fournir des fonctionnalités supplémentaires à une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1c41d-115">You can include managed COM and managed COM+ components to provide additional functionality in a BizTalk application.</span></span>  
  
-   <span data-ttu-id="1c41d-116">**Assemblys .NET.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-116">**.NET assemblies.**</span></span> <span data-ttu-id="1c41d-117">Vous pouvez ajouter à une application BizTalk des assemblys .NET qui ne sont pas des assemblys spécifiques à BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1c41d-117">You can include .NET assemblies that are not specifically BizTalk assemblies in a BizTalk application.</span></span> <span data-ttu-id="1c41d-118">(Les assemblys BizTalk sont des assemblys .NET contenant des orchestrations, pipelines, schémas ou mappages BizTalk.)</span><span class="sxs-lookup"><span data-stu-id="1c41d-118">(BizTalk assemblies are .NET assemblies that contain BizTalk orchestrations, pipelines, schemas, or maps.)</span></span>  
  
-   <span data-ttu-id="1c41d-119">**Fichiers de définition BAM.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-119">**BAM definition files.**</span></span> <span data-ttu-id="1c41d-120">Pour faciliter le déploiement de l'analyse BAM, vous pouvez créer une application BizTalk et lui ajouter des définitions d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="1c41d-120">To make BAM deployment easier, you can create a BizTalk application and add BAM definitions to it.</span></span> <span data-ttu-id="1c41d-121">Vous pouvez ensuite utiliser les fonctionnalités de déploiement d'applications BizTalk pour déployer les définitions d'analyse BAM dans différents environnements.</span><span class="sxs-lookup"><span data-stu-id="1c41d-121">You can then use the BizTalk application deployment features to deploy the BAM definitions into different environments.</span></span>  
  
-   <span data-ttu-id="1c41d-122">**Fichiers de liaison.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-122">**Binding files.**</span></span> <span data-ttu-id="1c41d-123">Vous pouvez ajouter des fichiers de liaison à une application afin d'accélérer et de faciliter le déplacement de cette application d'un environnement de déploiement à un autre.</span><span class="sxs-lookup"><span data-stu-id="1c41d-123">You can add binding files to an application to make moving an application from one deployment environment to another quicker and easier.</span></span>  
  
-   <span data-ttu-id="1c41d-124">**Répertoires virtuels.**</span><span class="sxs-lookup"><span data-stu-id="1c41d-124">**Virtual directories.**</span></span> <span data-ttu-id="1c41d-125">Vous pouvez ajouter des répertoires virtuels à votre application, afin qu'ils soient déployés avec celle-ci.</span><span class="sxs-lookup"><span data-stu-id="1c41d-125">You can add virtual directories to your application so that they will be deployed with the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c41d-126">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="1c41d-126">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="1c41d-127">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="1c41d-127">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="1c41d-128">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1c41d-128">Next steps</span></span>
  
-   [<span data-ttu-id="1c41d-129">Ajouter un fichier à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-129">Add a File to an Application</span></span>](../core/how-to-add-a-file-to-an-application.md)  
  
-   [<span data-ttu-id="1c41d-130">Ajouter un certificat à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-130">Add a Certificate to an Application</span></span>](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [<span data-ttu-id="1c41d-131">Ajouter un composant COM à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-131">Add a COM Component to an Application</span></span>](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [<span data-ttu-id="1c41d-132">Ajouter un Assembly .NET à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-132">Add a .NET Assembly to an Application</span></span>](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="1c41d-133">Ajouter un artefact BAM à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-133">Add a BAM Artifact to an Application</span></span>](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [<span data-ttu-id="1c41d-134">Ajouter un fichier de liaison à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-134">Add a Binding File to an Application</span></span>](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
-   [<span data-ttu-id="1c41d-135">Ajouter un répertoire virtuel à une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-135">Add a Virtual Directory to an Application</span></span>](../core/how-to-add-a-virtual-directory-to-an-application.md)  
  
-   [<span data-ttu-id="1c41d-136">Modifier les Options de déploiement d’un Assembly .NET, un composant COM, un fichier ou un artefact BAM</span><span class="sxs-lookup"><span data-stu-id="1c41d-136">Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact</span></span>](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md)  
  
-   [<span data-ttu-id="1c41d-137">Supprimer un Assembly .NET, certificat ou autre artefact de ressource d’une Application</span><span class="sxs-lookup"><span data-stu-id="1c41d-137">Remove a .NET Assembly, Certificate, or Other Resource Artifact from an Application</span></span>](../core/remove-a-net-assembly-certificate-or-resource-artifact-from-an-application.md)