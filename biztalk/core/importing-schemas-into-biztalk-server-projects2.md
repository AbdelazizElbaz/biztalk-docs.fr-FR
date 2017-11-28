---
title: "Importer des schémas de JD Edwards EnterpriseOne dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acd61cc8ab63d6859a8e10afb76f93c2f8cb2150
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a><span data-ttu-id="de5bc-102">Importation de schémas dans des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="de5bc-102">Importing Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="de5bc-103">Cette section décrit la navigation sur un serveur JD Edwards EnterpriseOne et l'importation des schémas dans un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de5bc-103">This section discusses browsing a JD Edwards EnterpriseOne server and importing the schemas into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de5bc-104">Vous devez vérifier que vous avez défini le fichier arglist.</span><span class="sxs-lookup"><span data-stu-id="de5bc-104">You must ensure that you set the arglist.</span></span> <span data-ttu-id="de5bc-105">Vous devez mettre à jour le fichier jdearglist.txt avant de générer les schémas dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="de5bc-105">You must update jdearglist.txt before you generate the schemas in the orchestration.</span></span> <span data-ttu-id="de5bc-106">Pour plus d’informations, consultez [gestion des valeurs de chaîne](../core/handling-string-values2.md).</span><span class="sxs-lookup"><span data-stu-id="de5bc-106">For more information, see [Handling String Values](../core/handling-string-values2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de5bc-107">Chaque fois que vous modifiez le fichier jdearglist, vous devez régénérer les schémas pour cet objet métier.</span><span class="sxs-lookup"><span data-stu-id="de5bc-107">Each time that you change the jdearglist, you must regenerate the schemas for that business object.</span></span>  
  
 <span data-ttu-id="de5bc-108">Après la création du port JD Edwards EnterpriseOne, vous pouvez explorer JD Edwards EnterpriseOne en lançant l'Assistant Adaptateur Microsoft à partir d'un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de5bc-108">After creating the JD Edwards EnterpriseOne port, you can browse JD Edwards EnterpriseOne by launching the Microsoft Adapter Wizard from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
## <a name="import-schemas-into-visual-studio"></a><span data-ttu-id="de5bc-109">Importer des schémas dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de5bc-109">Import schemas into Visual Studio</span></span>
  
1.  <span data-ttu-id="de5bc-110">Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de5bc-110">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="de5bc-111">Cliquez sur le nom de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="de5bc-111">Right-click the name of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="de5bc-112">Cliquez sur **ajouter** pour ouvrir le **Assistant Ajout d’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="de5bc-112">Click **Add** to open the **Add Adapter Wizard**.</span></span>  
  
4.  <span data-ttu-id="de5bc-113">Sur le **sélectionner un adaptateur** page, sélectionnez le nom de la carte pour laquelle vous souhaitez importer des schémas (par exemple, **JDEEnterpriseOne**).</span><span class="sxs-lookup"><span data-stu-id="de5bc-113">On the **Select Adapter** page, select the name of the adapter for which you want to import schemas (for example, **JDEEnterpriseOne**).</span></span>  
  
5.  <span data-ttu-id="de5bc-114">Dans le **SQL Server** , sélectionnez un serveur SQL server.</span><span class="sxs-lookup"><span data-stu-id="de5bc-114">In the **SQL Server** box, select a SQL server.</span></span>  
  
6.  <span data-ttu-id="de5bc-115">Dans le **base de données** , sélectionnez une base de données.</span><span class="sxs-lookup"><span data-stu-id="de5bc-115">In the **Database** box, select a database.</span></span>  
  
     <span data-ttu-id="de5bc-116">La base de données par défaut est la même que votre serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="de5bc-116">The default database is the same one as your SQL server.</span></span>  
  
7.  <span data-ttu-id="de5bc-117">Dans le **Port** zone, sélectionnez un serveur SQL server, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="de5bc-117">In the **Port** box, select a SQL server, and then click **Next**.</span></span>  
  
     <span data-ttu-id="de5bc-118">Le système JD Edwards EnterpriseOne apparaît dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="de5bc-118">The JD Edwards EnterpriseOne system displays in the browser.</span></span>  
  
8.  <span data-ttu-id="de5bc-119">Continuez avec la procédure suivante ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="de5bc-119">Continue with the next procedure below.</span></span>  
  
 <span data-ttu-id="de5bc-120">L'Assistant Ajout d'adaptateur affiche une arborescence des systèmes définis.</span><span class="sxs-lookup"><span data-stu-id="de5bc-120">The Add Adapter Wizard displays a tree of all of the defined systems.</span></span> <span data-ttu-id="de5bc-121">JD Edwards EnterpriseOne inclut plusieurs modules.</span><span class="sxs-lookup"><span data-stu-id="de5bc-121">JD Edwards EnterpriseOne has many modules.</span></span> <span data-ttu-id="de5bc-122">Les modules sont regroupés selon les trois premiers caractères de leur nom.</span><span class="sxs-lookup"><span data-stu-id="de5bc-122">The modules are grouped together according to the first three characters of their name.</span></span>  
  
-   <span data-ttu-id="de5bc-123">Le premier niveau de la hiérarchie correspond à la liste des préfixes à trois caractères des noms de module.</span><span class="sxs-lookup"><span data-stu-id="de5bc-123">The first level of the hierarchy is the list of all three-character prefixes for the module names.</span></span>  
  
-   <span data-ttu-id="de5bc-124">Le second niveau inclut les modules qui partagent le même préfixe à trois caractères.</span><span class="sxs-lookup"><span data-stu-id="de5bc-124">The second level lists all the modules that share the same three-character prefix.</span></span>  
  
-   <span data-ttu-id="de5bc-125">Le dernier niveau répertorie les fonctions commerciales appartenant à un module.</span><span class="sxs-lookup"><span data-stu-id="de5bc-125">The last level lists the business functions belonging to a module.</span></span> <span data-ttu-id="de5bc-126">Lorsque vous développez l'icône des services, vous pouvez afficher ses opérations.</span><span class="sxs-lookup"><span data-stu-id="de5bc-126">When you expand the services icon, you can view its operations.</span></span>  
  
 <span data-ttu-id="de5bc-127">Le développement d'une opération affiche les arguments d'entrée/de sortie.</span><span class="sxs-lookup"><span data-stu-id="de5bc-127">Expanding an operation displays the input/output arguments.</span></span> <span data-ttu-id="de5bc-128">Vous pouvez développer les arguments d'entrée/de sortie pour afficher les types de données des arguments.</span><span class="sxs-lookup"><span data-stu-id="de5bc-128">You can expand the input/output arguments to view the data types of the arguments.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de5bc-129">Si les définitions d'objet serveur sont modifiées, vous devez régénérer le schéma afin d'actualiser les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="de5bc-129">If the server object definitions change, you must regenerate the schema to refresh the data it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de5bc-130">Si vous modifiez le fichier jdearglist.txt après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="de5bc-130">If you change jdearglist.txt after generating your schema, you must regenerate the schema to refresh the data it contains.</span></span> <span data-ttu-id="de5bc-131">Pour plus d’informations sur le fichier jdearglist.txt, consultez [gestion des valeurs de chaîne](../core/handling-string-values2.md).</span><span class="sxs-lookup"><span data-stu-id="de5bc-131">For more information on jdearglist.txt, see [Handling String Values](../core/handling-string-values2.md).</span></span>  
  
## <a name="select-the-schemas"></a><span data-ttu-id="de5bc-132">Sélectionner les schémas</span><span class="sxs-lookup"><span data-stu-id="de5bc-132">Select the schemas</span></span>  
  
1.  <span data-ttu-id="de5bc-133">Dans le **sélectionner les Services à importer** page, développez le nœud de niveau supérieur de la **des objets métier** nœud ou la **Services professionnels** nœud.</span><span class="sxs-lookup"><span data-stu-id="de5bc-133">In the **Select Services to Import** page, expand the top level node of the **Business Objects** node or the **Business Services** node.</span></span>  
  
2.  <span data-ttu-id="de5bc-134">Activez la case à cocher en regard des éléments que vous souhaitez importer, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="de5bc-134">Select the check box next to the items that you want to import, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="de5bc-135">Les schémas générés pour les éléments JD Edwards EnterpriseOne sélectionnés sont importés dans votre projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de5bc-135">Schemas generated for the selected JD Edwards EnterpriseOne items are imported into your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de5bc-136">Lors de l’utilisation de carnet d’adresses (N0100041) le nom du champ est **cActionCode**.</span><span class="sxs-lookup"><span data-stu-id="de5bc-136">When using AddressBook (N0100041) the field name is **cActionCode**.</span></span> <span data-ttu-id="de5bc-137">L'action fait partie du fichier XML lui-même.</span><span class="sxs-lookup"><span data-stu-id="de5bc-137">The action is part of the XML file itself.</span></span> <span data-ttu-id="de5bc-138">Les codes suivants sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="de5bc-138">The codes are:</span></span>  
  
-   <span data-ttu-id="de5bc-139">A pour ajouter ;</span><span class="sxs-lookup"><span data-stu-id="de5bc-139">A for Add</span></span>  
  
-   <span data-ttu-id="de5bc-140">C pour modifier ;</span><span class="sxs-lookup"><span data-stu-id="de5bc-140">C for Change</span></span>  
  
-   <span data-ttu-id="de5bc-141">D pour supprimer ;</span><span class="sxs-lookup"><span data-stu-id="de5bc-141">D for Delete</span></span>  
  
-   <span data-ttu-id="de5bc-142">I pour demande.</span><span class="sxs-lookup"><span data-stu-id="de5bc-142">I for Inquiry</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="de5bc-143">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="de5bc-143">Next step</span></span>
[<span data-ttu-id="de5bc-144">Utiliser des propriétés de contexte de message</span><span class="sxs-lookup"><span data-stu-id="de5bc-144">Use Message Context Properties</span></span>](../core/using-message-context-properties1.md)