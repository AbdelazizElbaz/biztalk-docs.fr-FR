---
title: "Leçon 2 : Création d’un Assembly BizTalk avec nom fort pour le projet SWIFTSchemas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, creating strong-names
- strong-named assemblies
ms.assetid: 2aacbf38-8b1d-46ea-89ae-5207327bedc1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8ff979c7b6915f53ebc7144cf0774ab1ffb779a
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-2-creating-a-strong-named-biztalk-assembly-for-the-swiftschemas-project"></a><span data-ttu-id="cfb72-102">Leçon 2 : Création d’un Assembly BizTalk avec nom fort pour le projet SWIFTSchemas</span><span class="sxs-lookup"><span data-stu-id="cfb72-102">Lesson 2: Creating a Strong-Named BizTalk Assembly for the SWIFTSchemas Project</span></span>
<span data-ttu-id="cfb72-103">Dans cette leçon, vous créez un nom fort sur lequel les assemblys BizTalk sont compilés et déployés.</span><span class="sxs-lookup"><span data-stu-id="cfb72-103">In this lesson, you create a strong name upon which the BizTalk assemblies are compiled and deployed.</span></span> <span data-ttu-id="cfb72-104">Un assembly avec nom fort présente plusieurs avantages de sécurité :</span><span class="sxs-lookup"><span data-stu-id="cfb72-104">A strong-named assembly provides several security benefits:</span></span>  
  
-   <span data-ttu-id="cfb72-105">Un nom fort garantit l’unicité de l’assembly en assignant une signature numérique et une paire de clés unique.</span><span class="sxs-lookup"><span data-stu-id="cfb72-105">A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair.</span></span>  
  
-   <span data-ttu-id="cfb72-106">Un nom fort protège le lignage de l’assembly en veillant à ce que personne d’autre ne peut générer une version ultérieure de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="cfb72-106">A strong name protects the lineage of the assembly by ensuring that no one else can generate a subsequent version of the assembly.</span></span>  
  
-   <span data-ttu-id="cfb72-107">Un nom fort fournit un contrôle d’intégrité fort pour garantir que le contenu de l’assembly n’a pas changé depuis la dernière génération.</span><span class="sxs-lookup"><span data-stu-id="cfb72-107">A strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since the last build.</span></span>  
  
 <span data-ttu-id="cfb72-108">Vous pouvez générer un fichier de clé à l’aide de l’outil strong name (sn.exe) fourni avec [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] ou [!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cfb72-108">You can generate a key file by using the strong name tool (sn.exe) that comes with [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] or the [!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)].</span></span>  
  
### <a name="to-create-a-strong-named-biztalk-assembly"></a><span data-ttu-id="cfb72-109">Pour créer un assembly avec nom fort de BizTalk</span><span class="sxs-lookup"><span data-stu-id="cfb72-109">To create a strong-named BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="cfb72-110">Démarrez l’invite de commandes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfb72-110">Start Visual Studio command prompt.</span></span>  
  
2.  <span data-ttu-id="cfb72-111">À l’invite de commandes Visual Studio, accédez à la \< *lecteur*\>: \labs dossier.</span><span class="sxs-lookup"><span data-stu-id="cfb72-111">At the Visual Studio command prompt, browse to the \<*drive*\>:\labs folder.</span></span>  
  
3.  <span data-ttu-id="cfb72-112">À l’invite de commandes, tapez **sn – k swift.snk**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="cfb72-112">At the command prompt, type **sn –k swift.snk**, and then press ENTER.</span></span> <span data-ttu-id="cfb72-113">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="cfb72-113">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfb72-114">Si le message approprié n’apparaît pas, utilisez Visual Studio pour résoudre les problèmes de votre assembly.</span><span class="sxs-lookup"><span data-stu-id="cfb72-114">If the correct message does not appear, use Visual Studio to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="cfb72-115">Dans l’Explorateur de solutions, cliquez sur le **SWIFTSchemas** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cfb72-115">In Solution Explorer, right-click the **SWIFTSchemas** project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="cfb72-116">Dans la boîte de dialogue Pages de propriétés SWIFTSchemas, vérifiez que **propriétés communes** est développé, puis sélectionnez **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="cfb72-116">In the SWIFTSchemas Property Pages dialog box, ensure that **Common Properties** is expanded, and then select **Assembly**.</span></span>  
  
6.  <span data-ttu-id="cfb72-117">Défilement vers le bas les propriétés de l’assembly dans le volet droit et dans le **nom fort** , cliquez sur la zone à droite de **fichier de clé d’Assembly**.</span><span class="sxs-lookup"><span data-stu-id="cfb72-117">Scroll down the assembly properties in the right pane, and in the **Strong name** section, click the box to the right of **Assembly Key File**.</span></span> <span data-ttu-id="cfb72-118">Cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="cfb72-118">Click the ellipsis button.</span></span>  
  
7.  <span data-ttu-id="cfb72-119">Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à  **\< *lecteur*:\>\labs**.</span><span class="sxs-lookup"><span data-stu-id="cfb72-119">In the Assembly Key File dialog box, browse to **\<*drive*:\>\labs**.</span></span>  
  
8.  <span data-ttu-id="cfb72-120">Sélectionnez le **swift.snk** de fichiers en tant que le fichier de clé, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="cfb72-120">Select the **swift.snk** file as the key file, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="cfb72-121">Dans la boîte de dialogue Pages de propriétés SWIFTSchemas, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cfb72-121">In the SWIFTSchemas Property Pages dialog box, click **OK**.</span></span>  
  
10. <span data-ttu-id="cfb72-122">Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="cfb72-122">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="cfb72-123">Passez à [leçon 3 : ajout de schémas SWIFT à un projet](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md).</span><span class="sxs-lookup"><span data-stu-id="cfb72-123">Proceed to [Lesson 3: Adding SWIFT Schemas to a Project](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-swift-schemas-to-a-project.md).</span></span>