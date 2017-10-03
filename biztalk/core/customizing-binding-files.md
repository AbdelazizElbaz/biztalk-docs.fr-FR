---
title: Personnalisation des fichiers de liaison | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, binding files
- binding files
- binding files, about binding files
- binding files, customizing
ms.assetid: 4714e6c2-4912-43aa-ba5a-0be06916a30a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1534be96255084b963ed3883a1370af00f73b605
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-binding-files"></a><span data-ttu-id="5c13e-102">Personnalisation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="5c13e-102">Customizing Binding Files</span></span>
<span data-ttu-id="5c13e-103">Les fichiers de liaison sont des fichiers XML décrivant les artefacts d'une base de données de gestion BizTalk et les relations entre artefacts.</span><span class="sxs-lookup"><span data-stu-id="5c13e-103">Binding files are XML files that describe artifacts in a BizTalk Management database and the relationship between these artifacts.</span></span> <span data-ttu-id="5c13e-104">Ils permettent d'exporter des informations de configuration d'une base de données de configuration BizTalk pour les importer dans une autre base de données de configuration BizTalk. </span><span class="sxs-lookup"><span data-stu-id="5c13e-104">Binding files are useful for exporting configuration information from one BizTalk configuration database and importing this information into another BizTalk configuration database.</span></span> <span data-ttu-id="5c13e-105">Ainsi, un développeur peut concevoir une solution BizTalk et ses artefacts associés dans un environnement de développement, puis exporter les artefacts dans un fichier de liaison afin, ensuite, de les importer dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="5c13e-105">For example, a developer may design a BizTalk solution and its related artifacts in a development environment, then export these artifacts to a binding file and finally, import these artifacts into a production environment.</span></span> <span data-ttu-id="5c13e-106">Le fichier de liaison peut également servir à mettre à jour une configuration existante.</span><span class="sxs-lookup"><span data-stu-id="5c13e-106">You can also use a binding file to update an existing configuration.</span></span> <span data-ttu-id="5c13e-107">Il vous est ainsi possible, par l'intermédiaire d'un fichier de liaison, d'appliquer les modifications apportées à une configuration dans un environnement de développement à votre environnement de production.</span><span class="sxs-lookup"><span data-stu-id="5c13e-107">For example you can apply configuration changes made in a development environment to your production environment with a binding file.</span></span> <span data-ttu-id="5c13e-108">Cette rubrique présente la mise à jour d'une configuration existante avec un fichier de liaison, la structure d'un fichier de liaison, ainsi que les propriétés de configuration propres aux adaptateurs qu'il est possible de définir dans un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="5c13e-108">This topic discusses considerations when updating an existing configuration with a binding file, the structure of a binding file, and adapter specific configuration properties that can be set in a binding file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c13e-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5c13e-109">In This Section</span></span>  
  
-   [<span data-ttu-id="5c13e-110">Mise à jour d’une Configuration existante avec un fichier de liaison</span><span class="sxs-lookup"><span data-stu-id="5c13e-110">Updating an Existing Configuration with a Binding File</span></span>](../core/updating-an-existing-configuration-with-a-binding-file.md)  
  
-   [<span data-ttu-id="5c13e-111">Structure d’un fichier de liaison</span><span class="sxs-lookup"><span data-stu-id="5c13e-111">Structure of a Binding File</span></span>](../core/structure-of-a-binding-file.md)  
  
-   [<span data-ttu-id="5c13e-112">Propriétés de configuration des adaptateurs BizTalk intégrés</span><span class="sxs-lookup"><span data-stu-id="5c13e-112">Configuration Properties for Integrated BizTalk Adapters</span></span>](../core/configuration-properties-for-integrated-biztalk-adapters.md)