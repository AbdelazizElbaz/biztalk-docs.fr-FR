---
title: "Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3044cdea-e9b2-4cc2-b66e-799da1dfc07e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74addb5a69e8f17319a7019167eac1415a3a88d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-3-hosting-the-echo-adapter-in-iis"></a><span data-ttu-id="5ccdb-102">Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS</span><span class="sxs-lookup"><span data-stu-id="5ccdb-102">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>
<span data-ttu-id="5ccdb-103">Ce didacticiel fournit des instructions détaillées de hébergeant l’adaptateur Echo développés dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="5ccdb-103">This tutorial provides step-by-step instructions for hosting the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="5ccdb-104">Plus spécifiquement, les étapes montrent comment vous pouvez héberger l’adaptateur dans Internet Information Services (IIS) à l’aide de la [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ccdb-104">More specifically, the steps show how you can host the adapter in Internet Information Services (IIS) by using the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span></span> <span data-ttu-id="5ccdb-105">Vous également utiliser la fonctionnalité de catalogue de données métiers dans SharePoint pour appeler l’opération EchoGreetings de l’adaptateur hébergé par IIS et afficher les résultats dans un composant WebPart.</span><span class="sxs-lookup"><span data-stu-id="5ccdb-105">You will also use the Business Data Catalog feature in SharePoint to call the EchoGreetings operation of the IIS-hosted adapter, and then display the results in a Web Part.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="5ccdb-106">L’adaptateur d’écho, le code de test et le script d’installation sont inclus dans les fichiers d’installation de BizTalk à `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` ou `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span><span class="sxs-lookup"><span data-stu-id="5ccdb-106">The Echo Adapter, test code, and installation script are included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span> 
  
## <a name="in-this-section"></a><span data-ttu-id="5ccdb-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ccdb-107">In This Section</span></span>  
  
-   [<span data-ttu-id="5ccdb-108">Étape 1 : Utiliser l’Assistant développement d’adaptateurs pour créer le projet Web</span><span class="sxs-lookup"><span data-stu-id="5ccdb-108">Step 1: Use the Adapter Service Development Wizard to Create the Web Project</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)  
  
-   [<span data-ttu-id="5ccdb-109">Étape 2 : Déployer le projet Web</span><span class="sxs-lookup"><span data-stu-id="5ccdb-109">Step 2: Deploy the Web Project</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)  
  
-   [<span data-ttu-id="5ccdb-110">Étape 3 : Créer un fichier de définition d’Application</span><span class="sxs-lookup"><span data-stu-id="5ccdb-110">Step 3: Create an Application Definition File</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)  
  
-   [<span data-ttu-id="5ccdb-111">Étape 4 : Créer une Application Sharepoint pour accéder à la carte</span><span class="sxs-lookup"><span data-stu-id="5ccdb-111">Step 4: Create a Sharepoint Application to Access the Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="5ccdb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ccdb-112">See Also</span></span>  
 <span data-ttu-id="5ccdb-113">[Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="5ccdb-113">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
  [<span data-ttu-id="5ccdb-114">Didacticiels de kit de développement logiciel l’adaptateur WCF LOB</span><span class="sxs-lookup"><span data-stu-id="5ccdb-114">WCF LOB Adapter SDK Tutorials</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)