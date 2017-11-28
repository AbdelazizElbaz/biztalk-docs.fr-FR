---
title: "Comment mettre à jour un mappage à l’aide de la gestion des versions côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b0e377f-92ab-483e-9f3c-222c7b5ac0b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d463823a7038e1ead7e2de323da97eda372db76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-a-map-using-side-by-side-versioning"></a><span data-ttu-id="9d842-102">Comment mettre à jour un mappage à l’aide de la gestion des versions côte à côte</span><span class="sxs-lookup"><span data-stu-id="9d842-102">How to Update a Map Using Side-by-Side Versioning</span></span>
<span data-ttu-id="9d842-103">Certains artefacts BizTalk, tels que des cartes, sont choisis par nom fort qualifié complet (FQSN), dans ce cas les liaisons incluent la version utilisée.</span><span class="sxs-lookup"><span data-stu-id="9d842-103">Some BizTalk artifacts, such as maps, are chosen by fully-qualified strong name (FQSN), in which case the bindings include the version used.</span></span> <span data-ttu-id="9d842-104">Cela permet à deux ou plusieurs mappages de coexister côte à côte dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="9d842-104">This allows two or more maps to coexist side by side in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="9d842-105">Par conséquent, vous pouvez sélectionner un des mappages pour le mappage dans les propriétés d’emplacement de réception entrant ou sortant dans les propriétés de port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="9d842-105">As a result, you can select one of the maps for inbound mapping in the receive location properties or outbound mapping in the send port properties.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9d842-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9d842-106">Prerequisites</span></span>  
 <span data-ttu-id="9d842-107">Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9d842-107">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-add-a-second-map-side-by-side-to-an-existing-map"></a><span data-ttu-id="9d842-108">Pour ajouter une deuxième carte côte à côte pour un mappage existant</span><span class="sxs-lookup"><span data-stu-id="9d842-108">To add a second map side by side to an existing map</span></span>  
  
1.  <span data-ttu-id="9d842-109">Ouvrez Visual Studio et ouvrez le projet contenant le mappage.</span><span class="sxs-lookup"><span data-stu-id="9d842-109">Open Visual Studio, and then open the project containing the map.</span></span>  
  
2.  <span data-ttu-id="9d842-110">Ouvrez le mappage dans l’assembly et modifier un code à la carte.</span><span class="sxs-lookup"><span data-stu-id="9d842-110">Open the map in the assembly, and make a code change to the map.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d842-111">Si vous appelez un mappage à partir d’une orchestration, et la référence de mappage est codé en dur, vous devrez apporter des modifications de code à l’orchestration lui-même.</span><span class="sxs-lookup"><span data-stu-id="9d842-111">If you call a map from an orchestration, and the map reference is hard-coded, you may need to make code changes to the orchestration itself.</span></span>  
  
3.  <span data-ttu-id="9d842-112">Modifier le numéro de version de l’assembly :</span><span class="sxs-lookup"><span data-stu-id="9d842-112">Change the version number of the assembly:</span></span>  
  
    1.  <span data-ttu-id="9d842-113">Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9d842-113">In Solution Explorer, right-click the BizTalk project, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="9d842-114">Dans le **Concepteur de projets**, cliquez sur le **Application** onglet.</span><span class="sxs-lookup"><span data-stu-id="9d842-114">In the **Project Designer**, click the **Application** tab.</span></span>  
  
    3.  <span data-ttu-id="9d842-115">Dans le volet droit, cliquez sur **informations de l’Assembly**.</span><span class="sxs-lookup"><span data-stu-id="9d842-115">In the right pane, click **Assembly Information**.</span></span>  
  
    4.  <span data-ttu-id="9d842-116">Dans le **informations d’Assembly** boîte de dialogue, spécifiez les valeurs pour le **Version de l’Assembly** champ pour modifier le numéro de version d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9d842-116">In the **Assembly Information** dialog box, specify values for the **Assembly Version** field to change the assembly version number.</span></span> <span data-ttu-id="9d842-117">Vous devez modifier uniquement le numéro de version majeure ou mineure.</span><span class="sxs-lookup"><span data-stu-id="9d842-117">You should change only the major or minor version number.</span></span> <span data-ttu-id="9d842-118">Le numéro de version majeure est le premier chiffre de la séquence (***n***.0.0.0).) ; le numéro de version mineure est le deuxième chiffre de la séquence (0. ***n*** . 0.0).</span><span class="sxs-lookup"><span data-stu-id="9d842-118">The major version number is the first digit in the sequence (***n***.0.0.0); the minor version number is the second digit in the sequence (0.***n***.0.0).</span></span>  
  
    5.  <span data-ttu-id="9d842-119">Cliquez sur **OK** pour fermer la **informations d’Assembly** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="9d842-119">Click **OK** to close the **Assembly Information** dialog box.</span></span>  
  
4.  <span data-ttu-id="9d842-120">Compilez l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9d842-120">Compile the assembly.</span></span>  
  
5.  <span data-ttu-id="9d842-121">Déployer l’assembly dans le groupe (et tous les ordinateurs).</span><span class="sxs-lookup"><span data-stu-id="9d842-121">Deploy the assembly to the group (and all computers).</span></span>  
  
## <a name="modifying-a-map-to-reflect-updated-version-numbers"></a><span data-ttu-id="9d842-122">Modification d’un mappage afin de refléter mis à jour les numéros de Version</span><span class="sxs-lookup"><span data-stu-id="9d842-122">Modifying a Map to Reflect Updated Version Numbers</span></span>  
 <span data-ttu-id="9d842-123">Assemblys .NET peuvent être appelés à partir d’un mappage à l’aide du fonctoid script.</span><span class="sxs-lookup"><span data-stu-id="9d842-123">.NET assemblies can be invoked from within a map by using the Scripting functoid.</span></span> <span data-ttu-id="9d842-124">Cela apporte une grande flexibilité et permet au développeur de résoudre de nombreux problèmes relatifs au mappage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9d842-124">This provides a great deal of flexibility and enables the developer to solve many different custom mapping problems.</span></span> <span data-ttu-id="9d842-125">En outre, une seule contrainte est imposée pour le mappage : il doit, de manière interne, faire référence au nom du type d'assembly ainsi qu'au numéro de version complet de l'assembly invoqué.</span><span class="sxs-lookup"><span data-stu-id="9d842-125">It also imposes a unique constraint on the map—it must internally reference not only the assembly type name but also the full assembly version number being invoked.</span></span> <span data-ttu-id="9d842-126">Cela signifie que, si le numéro de version de l'assembly appelé par le mappage change, tous les liens qui font référence à cet assembly sont rompus.</span><span class="sxs-lookup"><span data-stu-id="9d842-126">As a consequence, if the version number of the assembly called by the map changes, all of the links that reference the assembly will break.</span></span>  
  
 <span data-ttu-id="9d842-127">Pour éviter ce problème, nous recommandons que si les assemblys sont requis pour être appelée à partir d’une carte, un assembly particulier est créé pour contenir uniquement des fonctionnalités de carte et que le numéro de version de cet assembly est fixe.</span><span class="sxs-lookup"><span data-stu-id="9d842-127">To avoid this issue we recommend that if assemblies are required to be called from a map, a specific assembly is created to hold only map functionality and that the assembly version number of this assembly is fixed.</span></span> <span data-ttu-id="9d842-128">Ainsi, la version d'assembly des autres fonctions d'assistance peut être mise à jour sans supprimer les mappages.</span><span class="sxs-lookup"><span data-stu-id="9d842-128">In this way, other helper functions can have the assembly version updated without breaking the maps.</span></span>  
  
 <span data-ttu-id="9d842-129">Si un assembly référencé dans un mappage est modifié après le développement des mappages, pensez à mettre à jour le fichier de mappage hors de l'Éditeur de mappage pour répercuter les numéros de version mis à jour.</span><span class="sxs-lookup"><span data-stu-id="9d842-129">If an assembly referenced from a map is changed after map development then consider updating the map file outside of the Map Editor to reflect the updated version numbers.</span></span>  
  
#### <a name="to-modify-a-map-file-to-reflect-updated-version-numbers"></a><span data-ttu-id="9d842-130">Pour modifier un fichier de mappage pour refléter les numéros de version de mise à jour</span><span class="sxs-lookup"><span data-stu-id="9d842-130">To modify a map file to reflect updated version numbers</span></span>  
  
1.  <span data-ttu-id="9d842-131">À l’aide de la **Démarrer** menu, ouvrir **bloc-notes**.</span><span class="sxs-lookup"><span data-stu-id="9d842-131">Using the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="9d842-132">Dans **bloc-notes**, dans le **fichier** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9d842-132">In **Notepad**, on the **File** menu, click **Open**.</span></span> <span data-ttu-id="9d842-133">Dans le **ouvrir** boîte de dialogue, sélectionnez le fichier de mappage que vous souhaitez modifier, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9d842-133">In the **Open** dialog box, select the map file you want to modify, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="9d842-134">Dans le menu **Edition** , cliquez sur **Rechercher**.</span><span class="sxs-lookup"><span data-stu-id="9d842-134">On the **Edit** menu, click **Find**.</span></span> <span data-ttu-id="9d842-135">Dans le **trouver** boîte de dialogue, entrez **Assembly =**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="9d842-135">In the **Find** dialog box, enter **Assembly=**, and then click **Find Next**.</span></span>  
  
4.  <span data-ttu-id="9d842-136">S'il existe une référence de script à un assembly externe, le Bloc-notes doit rechercher un élément XML tel que :</span><span class="sxs-lookup"><span data-stu-id="9d842-136">If there is a script reference to an external assembly, Notepad should find an XML element like the following:</span></span>  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=  
    <token>  
    " Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
5.  <span data-ttu-id="9d842-137">Mettez à jour le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="9d842-137">Update the version number.</span></span> <span data-ttu-id="9d842-138">S’il existe plusieurs instances, utilisez **remplacer** sur la **modifier** menu.</span><span class="sxs-lookup"><span data-stu-id="9d842-138">If there are multiple instances, use **Replace** on the **Edit** menu.</span></span>  
  
6.  <span data-ttu-id="9d842-139">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="9d842-139">Save the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d842-140">Vous pouvez maintenant ouvrir le mappage à l'aide de l'Éditeur de mappage.</span><span class="sxs-lookup"><span data-stu-id="9d842-140">You can now open the map using the Map Editor.</span></span>