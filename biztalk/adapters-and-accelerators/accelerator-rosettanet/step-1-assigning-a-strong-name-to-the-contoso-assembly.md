---
title: "Étape 1 : Attribution d’un nom fort à l’Assembly Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, assigning strong-names
- strong-named assemblies
ms.assetid: c8ec4593-5a4d-47ab-8799-7b2cd3d15ffc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7124561b9f842a7cc980c7a54230cd122ae32856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-assigning-a-strong-name-to-the-contoso-assembly"></a><span data-ttu-id="ee9d5-102">Étape 1 : Attribution d’un nom fort à l’Assembly Contoso</span><span class="sxs-lookup"><span data-stu-id="ee9d5-102">Step 1: Assigning a Strong Name to the Contoso Assembly</span></span>
<span data-ttu-id="ee9d5-103">Au cours de cette étape, vous allez créer un nom fort et l'affecter à votre assembly BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-103">In this step, you create and assign a strong name for your BizTalk assembly.</span></span> <span data-ttu-id="ee9d5-104">Un nom fort affecte une signature numérique et une paire de clés unique à un assembly pour garantir son unicité.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-104">A strong name guarantees the uniqueness of an assembly by assigning a digital signature and a unique key pair.</span></span> <span data-ttu-id="ee9d5-105">Par ailleurs, il est possible de vérifier l'intégrité d'un nom pour s'assurer que le contenu de l'assembly n'a pas changé depuis sa dernière génération.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-105">Additionally, a strong name provides an integrity check to guarantee that the content of the assembly has not changed since you last built it.</span></span>  
  
### <a name="to-create-a-strong-name-assembly-key-file"></a><span data-ttu-id="ee9d5-106">Pour créer un fichier de clé d'assembly de nom fort</span><span class="sxs-lookup"><span data-stu-id="ee9d5-106">To create a strong name assembly key file</span></span>  
  
1.  <span data-ttu-id="ee9d5-107">Démarrez une **invite de commandes Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-107">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="ee9d5-108">À l'invite de commandes, passez à l'emplacement de la solution Contoso.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-108">At the command prompt, move to the location of the Contoso solution.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee9d5-109">Par défaut, l’emplacement de la solution Contoso est  *\<lecteur >*: \Documents and Settings\\*\<nom d’utilisateur >*documents\Visual Studio \<version > \Projects.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-109">By default, the location of the Contoso solution is *\<drive>*:\Documents and Settings\\*\<user name>*\My Documents\Visual Studio \<version>\Projects.</span></span>  
  
3.  <span data-ttu-id="ee9d5-110">À l'invite de commandes, tapez **sn -k FabConPriceAvail.snk**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-110">At the command prompt, type **sn -k FabConPriceAvail.snk**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="ee9d5-111">À l'invite de commandes, tapez **Exit**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-111">At the command prompt, type **Exit**, and then press **Enter**.</span></span>  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a><span data-ttu-id="ee9d5-112">Pour affecter un nom fort à votre assembly</span><span class="sxs-lookup"><span data-stu-id="ee9d5-112">To assign a strong name to your assembly</span></span>  
  
1.  <span data-ttu-id="ee9d5-113">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **ContosoPriceAndAvailability** , puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-113">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ee9d5-114">Dans Pages de propriétés, cliquez sur **Signature** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-114">In the Property Pages, click **Signing** in the left pane.</span></span>  
  
3.  <span data-ttu-id="ee9d5-115">Dans le volet droit, sélectionnez **Signer l'assembly**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-115">In the right pane, select **Sign the assembly**.</span></span>  
  
4.  <span data-ttu-id="ee9d5-116">Cliquez sur **Parcourir** dans le champ Choisir un fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-116">Click **Browse** in the Choose the strong name key file field.</span></span>  
  
5.  <span data-ttu-id="ee9d5-117">Recherchez le dossier de votre projet, sélectionnez le fichier **FabConPriceAvail.snk** créé précédemment, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-117">Locate your project folder, select the **FabConPriceAvail.snk** file you created earlier, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="ee9d5-118">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-118">Click **OK** to save the changes.</span></span>  
  
7.  <span data-ttu-id="ee9d5-119">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **ContosoPriceAndAvailability** , puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-119">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, and then click **Build**.</span></span> <span data-ttu-id="ee9d5-120">Une fois la génération réussie, cliquez à nouveau avec le bouton droit sur le projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="ee9d5-120">After the build has succeeded, right-click the project again, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee9d5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee9d5-121">See Also</span></span>  
 [<span data-ttu-id="ee9d5-122">Étape 2 : Création de Ports pour le prix 3A2 de Contoso et le scénario de requête/réponse de disponibilité</span><span class="sxs-lookup"><span data-stu-id="ee9d5-122">Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario</span></span>](step-2-create-ports-for-contoso-3a2-price-and-availability-query.md)