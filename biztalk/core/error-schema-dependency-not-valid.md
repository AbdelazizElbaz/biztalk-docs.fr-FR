---
title: "Erreur : dépendance de schéma non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.schemaDependencyNotValid
ms.assetid: 431278f0-6cd1-4b3f-8d87-16af4991d354
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36326608f191b520c41cb42890aec029c432fd30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-dependency-not-valid"></a><span data-ttu-id="555d9-102">Erreur : dépendance de schéma non valide</span><span class="sxs-lookup"><span data-stu-id="555d9-102">Error - Schema Dependency Not Valid</span></span>
<span data-ttu-id="555d9-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="555d9-103">**Error Code**</span></span>  
  
 <span data-ttu-id="555d9-104">BEC2009</span><span class="sxs-lookup"><span data-stu-id="555d9-104">BEC2009</span></span>  
  
 <span data-ttu-id="555d9-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="555d9-105">**Explanation**</span></span>  
  
 <span data-ttu-id="555d9-106">Tous les schémas dépendants, notamment ceux qui sont importés, inclus ou redéfinis dans le schéma actuel, doivent être ajoutés au projet BizTalk ou doivent exister dans un assembly référencé par ce projet.</span><span class="sxs-lookup"><span data-stu-id="555d9-106">All dependent schemas, such as those that are imported, included, or redefined in the current schema, must be added to this BizTalk project or exist in an assembly referenced by this project.</span></span> <span data-ttu-id="555d9-107">Schémas **importer**, **incluent**, et **redéfinir** directives qui spécifient les schémas sur un site Web distant doivent être ajoutés à ce projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="555d9-107">Even schema **import**, **include**, and **redefine** directives that specify schemas on a remote Web site must be added to this BizTalk project.</span></span>  
  
 <span data-ttu-id="555d9-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="555d9-108">**User Action**</span></span>  
  
 <span data-ttu-id="555d9-109">Utilisez le **ajouter un élément existant** commande sur le **fichier** menu et le menu contextuel du projet Microsoft® BizTalk® Server ajouter tous les schémas dont dépend ce schéma au projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="555d9-109">Use the **Add Existing Item** command on the **File** menu and the shortcut menu for the Microsoft® BizTalk® Server project to add all schemas upon which this schema depends to the BizTalk project.</span></span> <span data-ttu-id="555d9-110">Vous devrez peut-être télécharger certains de ces schémas, à partir d'un site Web, sur votre disque dur local avant de pouvoir les ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="555d9-110">You may need to download such schemas from a Web site to your local hard disk before adding them to the BizTalk project.</span></span>