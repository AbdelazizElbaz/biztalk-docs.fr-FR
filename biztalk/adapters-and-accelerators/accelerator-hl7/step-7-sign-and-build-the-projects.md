---
title: "Étape 7 : Signer et générer des projets | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, projects
- projects, building
- projects, signing
ms.assetid: b66e4dc1-4ec6-4ec0-a69a-419b116b19c1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70f77e536da4eb6589823529644e0c4ab7c95cfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-sign-and-build-the-projects"></a><span data-ttu-id="5f168-102">Étape 7 : Signer et générer des projets</span><span class="sxs-lookup"><span data-stu-id="5f168-102">Step 7: Sign and Build the Projects</span></span>
<span data-ttu-id="5f168-103">Dans cette étape, vous affectez un nom fort et générez le projet pour générer un assembly qui contient les ressources (le schéma) que vous avez créé dans [étape 6 : valider les schémas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="5f168-103">In this step, you assign a strong name and build the project to generate an assembly that contains the resources (the schema) that you created in [Step 6: Validate the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).</span></span> <span data-ttu-id="5f168-104">Cela garantit également qu’il n’y a aucune erreur de compilation dans le travail que vous avez terminé jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="5f168-104">This also ensures that there are no compile errors in the work you have completed so far.</span></span>  
  
### <a name="to-sign-the-btahl7-project"></a><span data-ttu-id="5f168-105">Pour signer le projet BTAHL7</span><span class="sxs-lookup"><span data-stu-id="5f168-105">To sign the BTAHL7 Project</span></span>  
  
1.  <span data-ttu-id="5f168-106">Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5f168-106">In Solution Explorer, right-click **BTAHL7 Project**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5f168-107">Dans la boîte de dialogue Pages de propriétés de projet BTAHL7, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="5f168-107">In the BTAHL7 Project Property Pages dialog box, click **Assembly**.</span></span>  
  
3.  <span data-ttu-id="5f168-108">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="5f168-108">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
4.  <span data-ttu-id="5f168-109">Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à  **\<* lecteur*> : \Tutorial\BTAHL7V22Common\key.snk** (tel que créé dans [étape 3 : assigner un nom fort à l’Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)), puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="5f168-109">In the Assembly Key File dialog box, browse to **\<*drive*>:\Tutorial\BTAHL7V22Common\key.snk** (as created in [Step 3: Assign a Strong Name to the Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)), and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="5f168-110">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="5f168-110">Click **OK** to save changes.</span></span>  
  
### <a name="to-build-the-btahl7-project"></a><span data-ttu-id="5f168-111">Pour générer le projet BTAHL7</span><span class="sxs-lookup"><span data-stu-id="5f168-111">To build the BTAHL7 Project</span></span>  
  
-   <span data-ttu-id="5f168-112">Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="5f168-112">In Solution Explorer, right-click **BTAHL7 Project**, and then click **Deploy**.</span></span> [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]<span data-ttu-id="5f168-113">Compile l’assembly dans un fichier DLL et l’enregistre dans le \< *lecteur*> : \Tutorial\BTAHL7V22Common\Bin\Development dossier.</span><span class="sxs-lookup"><span data-stu-id="5f168-113"> compiles the assembly into a DLL file and saves it in the \<*drive*>:\Tutorial\BTAHL7V22Common\Bin\Development folder.</span></span>  
  
 <span data-ttu-id="5f168-114">Passez à [étape 8 : créer une carte avec le Mappeur BizTalk](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md).</span><span class="sxs-lookup"><span data-stu-id="5f168-114">Proceed to [Step 8: Create a Map with BizTalk Mapper](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f168-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f168-115">See Also</span></span>  
 [<span data-ttu-id="5f168-116">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="5f168-116">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)