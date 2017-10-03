---
title: "Leçon 8 : Création et déploiement de l’Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 74c9dfbd-8365-4600-8885-a9d9c3490dd5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6f043764dba966d662274d47643e01bec3735a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-8-building-and-deploying-the-assembly"></a><span data-ttu-id="bbb7b-102">Leçon 8 : Création et déploiement de l’Assembly</span><span class="sxs-lookup"><span data-stu-id="bbb7b-102">Lesson 8: Building and Deploying the Assembly</span></span>
<span data-ttu-id="bbb7b-103">Dans cette leçon, vous générez et déployez le projet de pipeline pour générer un assembly qui contient les pipelines que vous avez créé dans les étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-103">In this lesson, you build and deploy the pipeline project to generate an assembly that contains the pipelines you created in the previous steps.</span></span> <span data-ttu-id="bbb7b-104">Cette leçon s’assure aucune erreur de compilation dans le travail que vous avez créé jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-104">This lesson ensures there are no compilation errors in the work you have created so far.</span></span>  
  
 <span data-ttu-id="bbb7b-105">Compiler le projet dans un fichier d’assembly (DLL) et l’enregistrer dans le \< *lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour SWIFT\bin\Development dossier.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-105">You compile the project into an assembly (DLL) file and save it in the \<*drive*>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\bin\Development folder.</span></span>  
  
### <a name="to-build-and-deploy-the-project"></a><span data-ttu-id="bbb7b-106">Pour créer et déployer le projet</span><span class="sxs-lookup"><span data-stu-id="bbb7b-106">To build and deploy the project</span></span>  
  
1.  <span data-ttu-id="bbb7b-107">Dans l’Explorateur de solutions, cliquez sur **SWIFTPipelines**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-107">In Solution Explorer, right-click **SWIFTPipelines**, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bbb7b-108">Pendant le processus de compilation, vous ne devez pas voir les erreurs.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-108">During the compilation process, you should not see any failures.</span></span> <span data-ttu-id="bbb7b-109">Si vous le faites, vérifiez la source de l’erreur, corrigez-la et puis générez à nouveau le projet.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-109">If you do, check the source of the error, correct it and then re-build the project.</span></span> <span data-ttu-id="bbb7b-110">Toutefois, vous voyez un nombre d’avertissements liés aux composants de pipeline A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-110">You may, however, see a number of warnings related to the A4SWIFT pipeline components.</span></span> <span data-ttu-id="bbb7b-111">Vous pouvez corriger la condition qui est à ces avertissements en définissant le **copie locale** propriétés les références de composant de pipeline au **False**.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-111">You can correct the condition leading to these warnings by setting the **Copy Local** properties of the pipeline component references to **False**.</span></span> <span data-ttu-id="bbb7b-112">Pour plus d’informations, consultez « Création d’un projet de pipeline peut générer des avertissements » dans [divers problèmes connus](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).</span><span class="sxs-lookup"><span data-stu-id="bbb7b-112">For more information, see "Building a pipeline project may result in warnings" in [Miscellaneous Known Issues](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).</span></span>  
  
2.  <span data-ttu-id="bbb7b-113">Pour vérifier la création de la SWIFTPipelines.dll de fichiers, à l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à \< *lecteur*: > \labs\SWIFTProject\SWIFTPipelines\bin\Development et assurez-vous que le fichier existe dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-113">To verify the creation of the SWIFTPipelines.dll file, using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to \<*drive*:>\labs\SWIFTProject\SWIFTPipelines\bin\Development, and ensure that the file exists in this folder.</span></span>  
  
3.  <span data-ttu-id="bbb7b-114">Dans l’Explorateur de solutions, cliquez sur **SWIFTPipelines**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-114">In Solution Explorer, right-click **SWIFTPipelines**, and then click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bbb7b-115">Pendant le processus de déploiement, vous ne devez pas voir des erreurs ou des avertissements.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-115">During the deployment process, you should not see any failures or warnings.</span></span> <span data-ttu-id="bbb7b-116">Si vous le faites, vérifiez la source de l’erreur, corrigez-la, puis redéployez le projet.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-116">If you do, check the source of the error, correct it, and then re-deploy the project.</span></span>  
  
4.  <span data-ttu-id="bbb7b-117">Pour le rendre conforme de la réussite du déploiement, dans le **vue** menu de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **l’Explorateur BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-117">To conform deployment success, in the **View** menu of [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **BizTalk Explorer**.</span></span>  
  
5.  <span data-ttu-id="bbb7b-118">Avec le bouton droit **bases de données de Configuration BizTalk**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-118">Right-click **BizTalk Configuration Databases**, and then click **Refresh**.</span></span>  
  
6.  <span data-ttu-id="bbb7b-119">Développez le **assemblys** nœud et vérifiez que l’accélérateur déployé correctement **SWIFTPipelines (1.0.0.0)**.</span><span class="sxs-lookup"><span data-stu-id="bbb7b-119">Expand the **Assemblies** node and confirm that the accelerator successfully deployed **SWIFTPipelines (1.0.0.0)**.</span></span>  
  
 <span data-ttu-id="bbb7b-120">Passez à [Module 4 : création de code XML de réception et Ports d’envoi File plat](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="bbb7b-120">Proceed to [Module 4: Creating XML Receive and Flat File Send Ports](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md).</span></span>