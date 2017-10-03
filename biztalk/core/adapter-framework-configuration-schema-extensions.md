---
title: "Extensions de schéma de Configuration Framework adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27c9727f-5f97-41ee-a0b8-45d90427b0af
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cc50bcd592e104be0ffc82573c8ad9f4227858c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-framework-configuration-schema-extensions"></a><span data-ttu-id="e5bb1-102">Extensions de schéma de Configuration Framework adaptateur</span><span class="sxs-lookup"><span data-stu-id="e5bb1-102">Adapter Framework Configuration Schema Extensions</span></span>
<span data-ttu-id="e5bb1-103">L'infrastructure d'adaptateurs BizTalk prend en charge la génération dynamique des interfaces utilisateurs basées sur une définition XSD.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-103">The BizTalk Adapter Framework supports the dynamic generation of user interfaces based on an XSD definition.</span></span> <span data-ttu-id="e5bb1-104">L'adaptateur fournit le XSD requis et l'infrastructure d'adaptateurs crée une page de propriétés dans laquelle l'utilisateur peut entrer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-104">The adapter supplies the required XSD and the Adapter Framework creates a property page that allows the user to enter values.</span></span>  
  
 <span data-ttu-id="e5bb1-105">Pour créer des interfaces utilisateur personnalisées, l'infrastructure d'adaptateurs BizTalk fournit plusieurs extensions.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-105">To create custom user interfaces, the Adapter Framework provides several extensions.</span></span> <span data-ttu-id="e5bb1-106">Pour utiliser ces extensions, importez le schéma de l'infrastructure d'adaptateurs (BiztalkAdapterFramework.xsd).</span><span class="sxs-lookup"><span data-stu-id="e5bb1-106">To use these extensions, you must import the Adapter Framework schema (BizTalkAdapterFramework.xsd).</span></span> <span data-ttu-id="e5bb1-107">Cette importation vous permet d'accéder à des décorations et types spécifiques et de les utiliser dans le schéma de configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-107">By importing the schema, you can access and use the decorations and specialized types in the adapter configuration schema.</span></span>  
  
 <span data-ttu-id="e5bb1-108">Utilisez les balises d'ornement et les types intégrés présentés dans cette section pour personnaliser la grille de propriétés d'un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e5bb1-108">Use the decoration tags and built-in types discussed in this section to customize the property grid for an adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5bb1-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e5bb1-109">In This Section</span></span>  
  
-   [<span data-ttu-id="e5bb1-110">L’activation des Extensions Configuration infrastructure d’adaptateurs</span><span class="sxs-lookup"><span data-stu-id="e5bb1-110">Enabling Adapter Framework Configuration Extensions</span></span>](../core/enabling-adapter-framework-configuration-extensions.md)  
  
-   [<span data-ttu-id="e5bb1-111">Balises d’ornement adaptateur Framework Configuration schéma</span><span class="sxs-lookup"><span data-stu-id="e5bb1-111">Adapter Framework Configuration Schema Decoration Tags</span></span>](../core/adapter-framework-configuration-schema-decoration-tags.md)  
  
-   [<span data-ttu-id="e5bb1-112">Exemples de schémas de Configuration personnalisée pour les adaptateurs</span><span class="sxs-lookup"><span data-stu-id="e5bb1-112">Examples of Custom Configuration Schemas for Adapters</span></span>](../core/examples-of-custom-configuration-schemas-for-adapters.md)