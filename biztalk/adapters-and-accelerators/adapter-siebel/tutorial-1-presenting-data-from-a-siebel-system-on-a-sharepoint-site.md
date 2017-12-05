---
title: "Didacticiel 1 : Présentation des données à partir d’un système Siebel sur un Site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dd06f75-75d1-4fad-8f34-51c97c7790e3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd82dc1f8328645e59aa8c7b0fc668cbe2509ab6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site"></a><span data-ttu-id="59458-102">Didacticiel 1 : Présentation des données à partir d’un système Siebel sur un Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="59458-102">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>
<span data-ttu-id="59458-103">Ce didacticiel fournit des instructions détaillées sur l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Microsoft Office SharePoint Server pour présenter les données d’entreprise à partir d’un système Siebel sur un portail SharePoint.</span><span class="sxs-lookup"><span data-stu-id="59458-103">This tutorial provides detailed instructions on using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft Office SharePoint Server to present business data from a Siebel system on a SharePoint portal.</span></span> <span data-ttu-id="59458-104">Pour illustrer l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Office SharePoint Server, nous créons une application dans Office SharePoint Server pour récupérer la liste des comptes clients à partir du référentiel de Siebel avec la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59458-104">To demonstrate how to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Office SharePoint Server, we create an application in Office SharePoint Server to retrieve a list of customer accounts from the Siebel repository using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
 <span data-ttu-id="59458-105">Pour extraire ces informations à partir du système Siebel, l’exemple appelle la méthode de requête sur le **compte** des composants d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="59458-105">To extract this information from the Siebel system, the example invokes the Query method on the **Account** business components.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59458-106">Avant de poursuivre le didacticiel, assurez-vous que vous avez installé tous les composants requis pour l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="59458-106">Before proceeding with the tutorial, make sure you have installed all the prerequisites for using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Office SharePoint Server.</span></span> <span data-ttu-id="59458-107">Pour plus d’informations sur la configuration requise, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation, généralement installé sur \<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span><span class="sxs-lookup"><span data-stu-id="59458-107">For more information about the prerequisites, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide, typically installed at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59458-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="59458-108">In This Section</span></span>  
  
-   [<span data-ttu-id="59458-109">Étape 1 : Publier les opérations des composants métier Siebel sous forme de service WCF</span><span class="sxs-lookup"><span data-stu-id="59458-109">Step 1: Publish the Siebel Business Component Operations as a WCF Service</span></span>](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)  
  
-   [<span data-ttu-id="59458-110">Étape 2 : Créer un fichier de définition d’application pour les opérations des composants métier Siebel</span><span class="sxs-lookup"><span data-stu-id="59458-110">Step 2: Create an Application Definition File for Siebel Business Component Operations</span></span>](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)  
  
-   [<span data-ttu-id="59458-111">Étape 3 : Créer une application SharePoint pour récupérer les données à partir de Siebel</span><span class="sxs-lookup"><span data-stu-id="59458-111">Step 3: Create a SharePoint Application to Retrieve Data from Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)  
  
-  [<span data-ttu-id="59458-112">Étape 4 : Tester votre application SharePoint</span><span class="sxs-lookup"><span data-stu-id="59458-112">Step 4: Test Your SharePoint Application</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="59458-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59458-113">See Also</span></span>  
 [<span data-ttu-id="59458-114">Didacticiels pour l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="59458-114">Siebel Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)