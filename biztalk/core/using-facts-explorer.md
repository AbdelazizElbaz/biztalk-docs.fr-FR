---
title: "À l’aide de l’Explorateur de faits | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, Facts Explorer
- business rules, vocabularies
- business rules, schemas
- business rules, databases
- business rules, .NET classes
- Facts Explorer [Business Rule Composer]
ms.assetid: ee125eb1-d5b9-4121-8a25-fcb7a640570e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4c84b01625bb1566d02c1679bfadd0100b7b406
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-facts-explorer"></a><span data-ttu-id="0c82b-102">À l’aide de l’Explorateur de faits</span><span class="sxs-lookup"><span data-stu-id="0c82b-102">Using Facts Explorer</span></span>
<span data-ttu-id="0c82b-103">L’Explorateur de faits contient quatre onglets : **vocabulaires**, **schémas XML**, **bases de données**, et **Classes .NET**.</span><span class="sxs-lookup"><span data-stu-id="0c82b-103">The Facts Explorer contains four tabs: **Vocabularies**, **XML Schemas**, **Databases**, and **.NET Classes**.</span></span>  
  
## <a name="vocabularies-tab"></a><span data-ttu-id="0c82b-104">Onglet Vocabulaires</span><span class="sxs-lookup"><span data-stu-id="0c82b-104">Vocabularies tab</span></span>  
 <span data-ttu-id="0c82b-105">Utilisez le **vocabulaires** onglet dans l’Explorateur de faits pour gérer les définitions et les versions de vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="0c82b-105">Use the **Vocabularies** tab in the Facts Explorer to manage vocabulary versions and definitions.</span></span>  
  
 <span data-ttu-id="0c82b-106">Utilisez le menu contextuel pour accéder aux options ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0c82b-106">Use the shortcut menu to access the following options.</span></span>  
  
|<span data-ttu-id="0c82b-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="0c82b-107">Use this</span></span>|<span data-ttu-id="0c82b-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="0c82b-108">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="0c82b-109">**Ajouter un nouveau vocabulaire**</span><span class="sxs-lookup"><span data-stu-id="0c82b-109">**Add New Vocabulary**</span></span>|<span data-ttu-id="0c82b-110">Créer un vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="0c82b-110">Create a new vocabulary.</span></span>|  
|<span data-ttu-id="0c82b-111">**Ajouter une nouvelle Version**</span><span class="sxs-lookup"><span data-stu-id="0c82b-111">**Add New Version**</span></span>|<span data-ttu-id="0c82b-112">Créer une version vide du vocabulaire sélectionné.</span><span class="sxs-lookup"><span data-stu-id="0c82b-112">Create a new empty version of the selected vocabulary.</span></span> <span data-ttu-id="0c82b-113">Vous pouvez copier des définitions provenant d'autres versions et les coller dans la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="0c82b-113">You can copy definitions from other versions and paste them into the new version.</span></span>|  
|<span data-ttu-id="0c82b-114">**Coller une Version de vocabulaire**</span><span class="sxs-lookup"><span data-stu-id="0c82b-114">**Paste Vocabulary Version**</span></span>|<span data-ttu-id="0c82b-115">Dans le vocabulaire sélectionné, coller, en tant que nouvelle version, le contenu d'une version de vocabulaire préalablement copiée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-115">Paste the contents of a previously copied vocabulary version as a new version in the selected vocabulary.</span></span>|  
|<span data-ttu-id="0c82b-116">**Delete**</span><span class="sxs-lookup"><span data-stu-id="0c82b-116">**Delete**</span></span>|<span data-ttu-id="0c82b-117">Supprimer le vocabulaire sélectionné ainsi que toutes ses versions.</span><span class="sxs-lookup"><span data-stu-id="0c82b-117">Delete the selected vocabulary and all its versions.</span></span>|  
|<span data-ttu-id="0c82b-118">**Ajouter une nouvelle définition**</span><span class="sxs-lookup"><span data-stu-id="0c82b-118">**Add New Definition**</span></span>|<span data-ttu-id="0c82b-119">Lancer l'Assistant Définition de vocabulaire pour créer une définition dans la version de vocabulaire sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-119">Launch the Vocabulary Definition Wizard to create a new definition in the selected vocabulary version.</span></span>|  
|<span data-ttu-id="0c82b-120">**Enregistrer**</span><span class="sxs-lookup"><span data-stu-id="0c82b-120">**Save**</span></span>|<span data-ttu-id="0c82b-121">Enregistrer toutes les modifications effectuées dans la version sélectionnée et dans ses définitions.</span><span class="sxs-lookup"><span data-stu-id="0c82b-121">Save the changes made to the selected version and its definitions.</span></span>|  
|<span data-ttu-id="0c82b-122">**Publier**</span><span class="sxs-lookup"><span data-stu-id="0c82b-122">**Publish**</span></span>|<span data-ttu-id="0c82b-123">Publier la version de vocabulaire sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-123">Publish the selected vocabulary version.</span></span> <span data-ttu-id="0c82b-124">Notez que vous ne pouvez pas directement modifier une version publiée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-124">Note that you cannot directly modify a published version.</span></span> <span data-ttu-id="0c82b-125">Vous pouvez copier et coller dans une nouvelle version du vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="0c82b-125">You can copy and paste it to a new version of the vocabulary.</span></span>|  
|<span data-ttu-id="0c82b-126">**Recharger**</span><span class="sxs-lookup"><span data-stu-id="0c82b-126">**Reload**</span></span>|<span data-ttu-id="0c82b-127">Recharger la version de vocabulaire sélectionnée et ses définitions, en choisissant d'ignorer ou non les modifications effectuées dans cette version et de rétablir le contenu à partir du magasin de règles.</span><span class="sxs-lookup"><span data-stu-id="0c82b-127">Reload the selected vocabulary version and its definitions, with the option to discard any current changes made in that version and restore the contents from the rule store.</span></span>|  
|<span data-ttu-id="0c82b-128">**Modifier**</span><span class="sxs-lookup"><span data-stu-id="0c82b-128">**Modify**</span></span>|<span data-ttu-id="0c82b-129">Lancer l'Assistant Définition de vocabulaire pour modifier la définition sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-129">Launch the Vocabulary Definition Wizard to change the selected definition.</span></span> <span data-ttu-id="0c82b-130">Notez que vous ne pouvez pas modifier une définition qui fait partie d'une version publiée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-130">Note that you cannot modify a definition that is part of a published vocabulary version.</span></span>|  
|<span data-ttu-id="0c82b-131">**Atteindre le fait source**</span><span class="sxs-lookup"><span data-stu-id="0c82b-131">**Go to source fact**</span></span>|<span data-ttu-id="0c82b-132">À partir d'un assembly .NET, d'un schéma XML ou d'une table de base de données, accéder au fait source correspondant à la définition sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0c82b-132">For the selected definition, go to the corresponding source fact in a .NET assembly, XML schema, or database table.</span></span>|  
  
## <a name="xml-schemas-tab"></a><span data-ttu-id="0c82b-133">Onglet Schémas XML</span><span class="sxs-lookup"><span data-stu-id="0c82b-133">XML Schemas tab</span></span>  
 <span data-ttu-id="0c82b-134">Cet onglet permet de rechercher les définitions d'éléments et attributs XML dans des schémas XSD.</span><span class="sxs-lookup"><span data-stu-id="0c82b-134">Browse through XSD schemas for the definitions of XML elements and attributes.</span></span> <span data-ttu-id="0c82b-135">Vous pouvez faire glisser des éléments vers des versions de vocabulaire non publiées sur le **vocabulaire** onglet pour créer des définitions, ou vous pouvez faire glisser des éléments à l’éditeur de Conditions ou d’Actions pour définir des prédicats, des actions et des arguments.</span><span class="sxs-lookup"><span data-stu-id="0c82b-135">You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.</span></span>  
  
|<span data-ttu-id="0c82b-136">Utiliser</span><span class="sxs-lookup"><span data-stu-id="0c82b-136">Use this</span></span>|<span data-ttu-id="0c82b-137">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="0c82b-137">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="0c82b-138">**Sélectionnez le nœud racine**</span><span class="sxs-lookup"><span data-stu-id="0c82b-138">**Select Root Node**</span></span>|<span data-ttu-id="0c82b-139">Sélectionner un nœud racine à télécharger à partir d'un schéma XML qui contient plusieurs nœuds racines.</span><span class="sxs-lookup"><span data-stu-id="0c82b-139">Select a root node to load from an XML schema that contains multiple root notes.</span></span>|  
  
## <a name="databases-tab"></a><span data-ttu-id="0c82b-140">Onglet Bases de données</span><span class="sxs-lookup"><span data-stu-id="0c82b-140">Databases tab</span></span>  
 <span data-ttu-id="0c82b-141">Cet onglet permet de rechercher les définitions de base de données et de table dans les serveurs de base de données.</span><span class="sxs-lookup"><span data-stu-id="0c82b-141">Browse through database servers for databases and table definitions.</span></span> <span data-ttu-id="0c82b-142">Vous pouvez faire glisser des éléments vers des versions de vocabulaire non publiées sur le **vocabulaire** onglet pour créer des définitions, ou vous pouvez faire glisser des éléments à l’éditeur de Conditions ou d’Actions pour définir des prédicats, des actions et des arguments.</span><span class="sxs-lookup"><span data-stu-id="0c82b-142">You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.</span></span>  
  
## <a name="net-classes-tab"></a><span data-ttu-id="0c82b-143">Onglet Classes .NET</span><span class="sxs-lookup"><span data-stu-id="0c82b-143">.NET Classes tab</span></span>  
 <span data-ttu-id="0c82b-144">Cet onglet permet de rechercher des définitions de classes .NET publiques dans des assemblys .NET.</span><span class="sxs-lookup"><span data-stu-id="0c82b-144">Browse through .NET assemblies for public .NET class definitions.</span></span> <span data-ttu-id="0c82b-145">Vous pouvez faire glisser des éléments vers des versions de vocabulaire non publiées sur le **vocabulaire** onglet pour créer des définitions, ou vous pouvez faire glisser des éléments à l’éditeur de Conditions ou d’Actions pour définir des prédicats, des actions et des arguments.</span><span class="sxs-lookup"><span data-stu-id="0c82b-145">You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.</span></span>  
  
|<span data-ttu-id="0c82b-146">Utiliser</span><span class="sxs-lookup"><span data-stu-id="0c82b-146">Use this</span></span>|<span data-ttu-id="0c82b-147">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="0c82b-147">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="0c82b-148">**Parcourir**</span><span class="sxs-lookup"><span data-stu-id="0c82b-148">**Browse**</span></span>|<span data-ttu-id="0c82b-149">Charger un assembly .NET à partir du global assembly cache</span><span class="sxs-lookup"><span data-stu-id="0c82b-149">Load a .NET assembly from the global assembly cache</span></span>|  
|<span data-ttu-id="0c82b-150">**Supprimer**</span><span class="sxs-lookup"><span data-stu-id="0c82b-150">**Remove**</span></span>|<span data-ttu-id="0c82b-151">Supprimer un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="0c82b-151">Remove a .NET assembly</span></span>|