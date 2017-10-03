---
title: "Comment mettre à jour un Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f456c8f-247a-4d5c-b5af-41e88968779c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 163b06706652b1f65b9a76e3feea8911a2ca4c88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-an-assembly"></a><span data-ttu-id="2bf5b-102">Comment mettre à jour un Assembly</span><span class="sxs-lookup"><span data-stu-id="2bf5b-102">How to Update an Assembly</span></span>
<span data-ttu-id="2bf5b-103">Cette rubrique décrit comment mettre à jour la version d’un assembly et l’application qu’un assembly est déployé à l’aide de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-103">This topic describes how to update the version of an assembly and the application that an assembly is deployed to using Visual Studio 2010.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2bf5b-104">Si vous mettez à jour un assembly avec une version plus récente, il n'est pas nécessaire de redémarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-104">If you are updating an assembly with a new version, you do not need to restart the application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2bf5b-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2bf5b-105">Prerequisites</span></span>  
 <span data-ttu-id="2bf5b-106">Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-106">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="updating-an-assembly"></a><span data-ttu-id="2bf5b-107">Mise à jour d’un Assembly</span><span class="sxs-lookup"><span data-stu-id="2bf5b-107">Updating an Assembly</span></span>  
  
#### <a name="to-increment-the-version-number-of-an-assembly"></a><span data-ttu-id="2bf5b-108">Pour incrémenter le numéro de version d’un assembly</span><span class="sxs-lookup"><span data-stu-id="2bf5b-108">To increment the version number of an assembly</span></span>  
  
1.  <span data-ttu-id="2bf5b-109">Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-109">In Solution Explorer, right-click the BizTalk project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2bf5b-110">Dans le **Concepteur de projets**, cliquez sur le **Application** onglet.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-110">In the **Project Designer**, click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="2bf5b-111">Dans le volet droit, cliquez sur **informations de l’Assembly**.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-111">In the right pane, click **Assembly Information**.</span></span>  
  
4.  <span data-ttu-id="2bf5b-112">Dans le **informations d’Assembly** boîte de dialogue, spécifiez les valeurs pour le **Version de l’Assembly** champ pour augmenter le numéro de version d’assembly.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-112">In the **Assembly Information** dialog box, specify values for the **Assembly Version** field to increase the assembly version number.</span></span> <span data-ttu-id="2bf5b-113">Vous ne devez augmenter que le numéro de version majeure ou mineure.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-113">You should increase only the major or minor version number.</span></span> <span data-ttu-id="2bf5b-114">Le numéro de version majeure est le premier chiffre de la séquence (***n***.0.0.0).) ; le numéro de version mineure est le deuxième chiffre de la séquence (0.*** n ***. 0.0).</span><span class="sxs-lookup"><span data-stu-id="2bf5b-114">The major version number is the first digit in the sequence (***n***.0.0.0); the minor version number is the second digit in the sequence (0.***n***.0.0).</span></span> <span data-ttu-id="2bf5b-115">BizTalk Server ne reconnaît pas une modification de numéro de version plus loin dans la séquence, telles que 0.0. *** n ***.0 ou 0.0.0.*** n***.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-115">BizTalk Server will not recognize a version number change that is later in the sequence, such as 0.0.***n***.0 or 0.0.0.***n***.</span></span>  
  
5.  <span data-ttu-id="2bf5b-116">Cliquez sur **OK** pour fermer la **informations d’Assembly** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-116">Click **OK** to close the **Assembly Information** dialog box.</span></span>  
  
6.  <span data-ttu-id="2bf5b-117">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-117">Save the project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2bf5b-118">Utilisez le Concepteur de pipeline et le Modèle objet de l'Explorateur BizTalk pour éviter tout conflit de schémas lors de l'incrémentation des versions d'assembly.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-118">Use the Pipeline Designer and BizTalk Explorer Object Model to avoid schema collisions when incrementing assembly versions.</span></span>  
  
#### <a name="to-change-the-application-that-an-assembly-is-deployed-to"></a><span data-ttu-id="2bf5b-119">Pour modifier l’application déployée dans un assembly</span><span class="sxs-lookup"><span data-stu-id="2bf5b-119">To change the application that an assembly is deployed to</span></span>  
  
1.  <span data-ttu-id="2bf5b-120">Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-120">In Solution Explorer, right-click the BizTalk project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2bf5b-121">Dans le **Concepteur de projets**, cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-121">In the **Project Designer**, click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="2bf5b-122">Dans le volet droit, spécifiez le nom de l’application dans le **nom de l’Application** champ.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-122">In the right pane, specify the application name in the **Application Name** field.</span></span>  
  
4.  <span data-ttu-id="2bf5b-123">Vérifiez que le **installer dans le Global Assembly Cache** est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-123">Ensure that the **Install to Global Assembly Cache** property is set to **True**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2bf5b-124">Lorsque vous déployez la solution, les assemblys sont déployés dans la nouvelle application et installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="2bf5b-124">When you deploy the solution, the assemblies will be deployed into the new application and installed in the GAC.</span></span>