---
title: "Comment utiliser l’Assistant mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35b96cea-ead7-43de-8411-62d2c7d6620e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6b016eb0599924d4927868b6a19d3b57389e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-mapping-wizard"></a><span data-ttu-id="fe99a-102">Utilisation de l'Assistant Mappage</span><span class="sxs-lookup"><span data-stu-id="fe99a-102">How to Use the Mapping Wizard</span></span>
<span data-ttu-id="fe99a-103">Cette version de l'authentification unique de l'entreprise inclut l'Assistant Mappage, lequel vous permet de créer facilement des mappages pour les applications associées.</span><span class="sxs-lookup"><span data-stu-id="fe99a-103">This version of Enterprise Single Sign-On includes the Mapping Wizard, which allows you to easily create mappings for affiliate applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe99a-104">L'Assistant Mappage n'est utilisable que si l'ID utilisateur externe UserID a pour base le compte de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="fe99a-104">You can only use the Mapping Wizard if the External UserID is based on the Windows domain account.</span></span>  
  
### <a name="to-start-the-mapping-wizard"></a><span data-ttu-id="fe99a-105">Pour démarrer l'Assistant Mappage</span><span class="sxs-lookup"><span data-stu-id="fe99a-105">To start the Mapping Wizard</span></span>  
  
1.  <span data-ttu-id="fe99a-106">Ouvrez l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="fe99a-106">Open Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="fe99a-107">Dans le volet d’étendue, cliquez sur **Applications associées**.</span><span class="sxs-lookup"><span data-stu-id="fe99a-107">In the scope pane, click **Affiliate Applications**.</span></span>  
  
3.  <span data-ttu-id="fe99a-108">Cliquez avec le bouton droit sur l'application associée appropriée.</span><span class="sxs-lookup"><span data-stu-id="fe99a-108">Right click the appropriate affiliate application.</span></span>  
  
4.  <span data-ttu-id="fe99a-109">Cliquez sur **créer des mappages**.</span><span class="sxs-lookup"><span data-stu-id="fe99a-109">Click **Create Mappings**.</span></span> <span data-ttu-id="fe99a-110">L'Assistant Mappage s'affiche.</span><span class="sxs-lookup"><span data-stu-id="fe99a-110">The Mapping Wizard appears.</span></span>  
  
5.  <span data-ttu-id="fe99a-111">**Bienvenue dans l’Assistant mappage**</span><span class="sxs-lookup"><span data-stu-id="fe99a-111">**Welcome to the Mapping Wizard**</span></span>  
  
    -   <span data-ttu-id="fe99a-112">Vérifiez qu’il s’agit de l’application associée correcte, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="fe99a-112">Verify that this is the correct affiliate application, and click **Next**.</span></span>  
  
6.  <span data-ttu-id="fe99a-113">**Option du fichier de mappage** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-113">**Mappings File Option** page</span></span>  
  
    -   <span data-ttu-id="fe99a-114">L'authentification unique de l'entreprise (ENTSSO) gère les mappages au moyen d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="fe99a-114">ENTSSO manages mappings through an XML file.</span></span> <span data-ttu-id="fe99a-115">Vous pouvez décider de créer un fichier ou d'en utiliser un existant.</span><span class="sxs-lookup"><span data-stu-id="fe99a-115">You can choose to create a new file or use an existing one.</span></span>  
  
7.  <span data-ttu-id="fe99a-116">**Emplacement des fichiers** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-116">**Files Location** page</span></span>  
  
    -   <span data-ttu-id="fe99a-117">Sélectionnez les fichiers à utiliser.</span><span class="sxs-lookup"><span data-stu-id="fe99a-117">Select the files to be used.</span></span>  
  
    -   <span data-ttu-id="fe99a-118">Vous devez cliquer sur **Validate** pour valider les fichiers avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="fe99a-118">You must click **Validate** to validate the files before proceeding.</span></span> <span data-ttu-id="fe99a-119">L’état de validation s’affiche dans le **état** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="fe99a-119">The validation status appears in the **Status** window.</span></span>  
  
8.  <span data-ttu-id="fe99a-120">**Comptes** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-120">**Accounts** page</span></span>  
  
    -   <span data-ttu-id="fe99a-121">Choisissez un ou plusieurs comptes pour générer les fichiers de mappage, puis cliquez sur **Validate**.</span><span class="sxs-lookup"><span data-stu-id="fe99a-121">Choose one or more accounts to generate the new mappings file, and click **Validate**.</span></span>  
  
9. <span data-ttu-id="fe99a-122">**Nom d’utilisateur externe** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-122">**External User Name** page</span></span>  
  
    -   <span data-ttu-id="fe99a-123">Définissez la méthode de création du nom d'utilisateur externe à partir du compte d'utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="fe99a-123">Define how the external user name is generated from the Windows user account.</span></span> <span data-ttu-id="fe99a-124">Lorsque vous apportez des sélections dans les zones, vous pouvez voir comment les noms apparaissent dans le **exemple** boîte.</span><span class="sxs-lookup"><span data-stu-id="fe99a-124">As you make selections in the boxes, you can see how the names will appear in the **Example** box.</span></span>  
  
10. <span data-ttu-id="fe99a-125">**Générer** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-125">**Generate** page</span></span>  
  
    -   <span data-ttu-id="fe99a-126">Cliquez sur **Démarrer** pour générer le fichier de mappage.</span><span class="sxs-lookup"><span data-stu-id="fe99a-126">Click **Start** to generate the mappings file.</span></span> <span data-ttu-id="fe99a-127">(Dans la page suivante, vous aurez l'occasion d'afficher et de modifier le fichier selon le besoin avant que les mappages ne soient créés.) Les résultats sont affichés dans les trois fenêtres ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fe99a-127">(You will have an opportunity on the next page to view or edit the file as necessary before mappings are created.) Results are displayed in the three windows below.</span></span>  
  
    -   <span data-ttu-id="fe99a-128">Le **nombre** de mappages dans les comptes sélectionnés est une approximation car les comptes peuvent être imbriqués dans d’autres comptes.</span><span class="sxs-lookup"><span data-stu-id="fe99a-128">The **Number** of mappings in selected accounts is an approximation, because accounts may be nested in other accounts.</span></span>  
  
    -   <span data-ttu-id="fe99a-129">Cliquez sur **afficher le fichier journal** pour examiner les erreurs ou avertissements qui se sont produites.</span><span class="sxs-lookup"><span data-stu-id="fe99a-129">Click **View Log File** to examine any errors or warnings that might have occurred.</span></span>  
  
11. <span data-ttu-id="fe99a-130">**Options** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-130">**Options** page</span></span>  
  
    -   <span data-ttu-id="fe99a-131">Le fichier a été créé.</span><span class="sxs-lookup"><span data-stu-id="fe99a-131">Your file has been created.</span></span> <span data-ttu-id="fe99a-132">Cliquez sur **afficher/modifier le fichier de mappage** si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="fe99a-132">Click **View/Edit Mappings File** if desired.</span></span>  
  
    -   <span data-ttu-id="fe99a-133">Cliquez sur **activer les mappages** si vous souhaitez que les mappages d’être activé automatiquement.</span><span class="sxs-lookup"><span data-stu-id="fe99a-133">Click **Enable mappings** if you want the mappings to be automatically enabled.</span></span> <span data-ttu-id="fe99a-134">(Si vous ne cliquez pas sur cette option, vous devrez les activer manuellement.)</span><span class="sxs-lookup"><span data-stu-id="fe99a-134">(If you do not click this, you will have to enable them manually.)</span></span>  
  
    -   <span data-ttu-id="fe99a-135">Cliquez sur **définir le mot de passe** pour définir automatiquement le mot de passe pour ces mappages.</span><span class="sxs-lookup"><span data-stu-id="fe99a-135">Click **Set Password** to automatically set the password for these mappings.</span></span>  
  
12. <span data-ttu-id="fe99a-136">**Créer** page</span><span class="sxs-lookup"><span data-stu-id="fe99a-136">**Create** page</span></span>  
  
    -   <span data-ttu-id="fe99a-137">Avant de créer les mappages, cliquez sur **afficher le fichier de mappage** si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="fe99a-137">Before creating the mappings, click **View Mappings File** if desired.</span></span>  
  
    -   <span data-ttu-id="fe99a-138">Lorsque vous êtes prêt, cliquez sur **Démarrer** pour effectuer l’opération de mappage.</span><span class="sxs-lookup"><span data-stu-id="fe99a-138">When you are ready, click **Start** to perform the mapping operation.</span></span> <span data-ttu-id="fe99a-139">L'état est affiché dans les trois zones ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="fe99a-139">Your status is displayed in the three boxes below.</span></span>  
  
    -   <span data-ttu-id="fe99a-140">Cliquez sur **afficher le fichier journal** pour examiner les erreurs ou avertissements qui se sont produites.</span><span class="sxs-lookup"><span data-stu-id="fe99a-140">Click **View Log File** to examine any errors or warnings that might have occurred.</span></span>  
  
13. <span data-ttu-id="fe99a-141">**Fin de l’écran de l’Assistant mappage**</span><span class="sxs-lookup"><span data-stu-id="fe99a-141">**Completing the Mapping Wizard screen**</span></span>  
  
14. <span data-ttu-id="fe99a-142">Sélectionnez les options souhaitées, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="fe99a-142">Select any options desired, and then click **Finish**.</span></span>