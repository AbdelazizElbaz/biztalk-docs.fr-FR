---
title: "Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1272b76c-29a1-4912-9c2d-8a4cf43df59d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aa1b709c317438c9614e412496eedb318dea3a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-present-data-from-oracle-e-business-suite-on-a-sharepoint-site"></a><span data-ttu-id="358fe-102">Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site</span><span class="sxs-lookup"><span data-stu-id="358fe-102">Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site</span></span>
<span data-ttu-id="358fe-103">Ce didacticiel fournit des instructions détaillées sur l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec Microsoft Office SharePoint Server pour présenter des données à partir d’Oracle E-Business Suite à un portail SharePoint.</span><span class="sxs-lookup"><span data-stu-id="358fe-103">This tutorial provides detailed instructions on using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with Microsoft Office SharePoint Server to present data from Oracle E-Business Suite on a SharePoint portal.</span></span> <span data-ttu-id="358fe-104">Il montre également comment configurer une application de recherche dans Microsoft Office SharePoint Server qui vous permet d’effectuer une recherche en texte intégral à partir d’un portail SharePoint sur l’artefact d’Oracle E-Business Suite configuré.</span><span class="sxs-lookup"><span data-stu-id="358fe-104">It also demonstrates how to configure a search application in the Microsoft Office SharePoint Server that allows you to do a full-text search from a SharePoint portal on the configured Oracle E-Business Suite artifact.</span></span>  
  
 <span data-ttu-id="358fe-105">Pour illustrer la marche à suivre, imaginez une table interface dans Oracle E-Business Suite qui stocke des informations sur les employés.</span><span class="sxs-lookup"><span data-stu-id="358fe-105">To demonstrate how to do so, consider a sample interface table in Oracle E-Business Suite that stores information about employees.</span></span> <span data-ttu-id="358fe-106">Dans ce didacticiel, une application est créée dans Microsoft Office SharePoint Server récupérer une liste de clients à partir d’Oracle E-Business Suite basée sur une chaîne de recherche à l’aide de :</span><span class="sxs-lookup"><span data-stu-id="358fe-106">In this tutorial, an application is created in Microsoft Office SharePoint Server that retrieve a list of customers from Oracle E-Business Suite based on a search string using:</span></span>  
  
-   <span data-ttu-id="358fe-107">Un composant WebPart de liste de données métier dans Microsoft Office SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="358fe-107">A Business Data List Web Part in Microsoft Office SharePoint Server</span></span>  
  
-   <span data-ttu-id="358fe-108">La fonctionnalité de recherche dans Microsoft Office SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="358fe-108">The search feature in Microsoft Office SharePoint Server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="358fe-109">Avant de poursuivre le didacticiel, assurez-vous que vous avez installé tous les composants requis pour l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="358fe-109">Before proceeding with the tutorial, make sure you have installed all the prerequisites for using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="358fe-110">Pour plus d’informations sur la configuration requise, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation, généralement installé dans C:\Program Files\Microsoft BizTalk adaptateur Pack\Documents.</span><span class="sxs-lookup"><span data-stu-id="358fe-110">For information about the prerequisites, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide, typically installed at C:\Program Files\Microsoft BizTalk Adapter Pack\Documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="358fe-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="358fe-111">In This Section</span></span>  
  
-   [<span data-ttu-id="358fe-112">Étape 1 : Utiliser l’adaptateur Oracle E-Business pour créer et publier un Service WCF</span><span class="sxs-lookup"><span data-stu-id="358fe-112">Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)  
  
-   [<span data-ttu-id="358fe-113">Étape 2 : Créer un fichier de définition d’Application pour les artefacts Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="358fe-113">Step 2: Create an Application Definition File for the Oracle E-Business Suite Artifacts</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)  
  
-   [<span data-ttu-id="358fe-114">Étape 3 : Créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="358fe-114">Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
  
-   [<span data-ttu-id="358fe-115">Étape 4 : Tester votre Application SharePoint</span><span class="sxs-lookup"><span data-stu-id="358fe-115">Step 4: Test Your SharePoint Application</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)