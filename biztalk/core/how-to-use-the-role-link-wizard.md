---
title: "Comment utiliser l’Assistant lien de rôle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- links [roles]
- Role Link Wizard [Orchestration Designer]
- roles, links
- Orchestration Designer, Role Link Wizard
- role links, Role Link Wizard [Orchestration Designer]
- links [roles], about links
ms.assetid: ddc33d87-c08d-4193-9483-4644ef302853
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d31abcc8fcc2bfaf1ebd641e1e52ad08d1c9c9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-role-link-wizard"></a><span data-ttu-id="62ab0-102">Comment utiliser l’Assistant lien de rôle</span><span class="sxs-lookup"><span data-stu-id="62ab0-102">How to Use the Role Link Wizard</span></span>
<span data-ttu-id="62ab0-103">L'Assistant Lien de rôle vous permet de créer un nouveau lien de rôle ou d'en modifier un existant.</span><span class="sxs-lookup"><span data-stu-id="62ab0-103">The Role Link Wizard enables you to create a new role link or modify an existing one.</span></span> <span data-ttu-id="62ab0-104">Vous pouvez utiliser cet Assistant pour définir ou afficher le nom, le type et la restriction d'accès du lien de rôle ainsi que le rôle d'implémentation et le rôle d'utilisation qui composent le type de lien de rôle.</span><span class="sxs-lookup"><span data-stu-id="62ab0-104">You can use it to set or view the name, type, and access restriction of the role link, as well as the implements role and the uses role that compose the role link type.</span></span> <span data-ttu-id="62ab0-105">Pour comprendre comment fonctionnent les liens de rôle, consultez [à l’aide des liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="62ab0-105">To understand how role links work, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="62ab0-106">**Nom de lien de rôle**: le nom de lien de rôle est renseigné automatiquement et est le nom actuel d’un lien de rôle existant que vous configurez, ou un nom généré automatiquement si vous créez un lien de rôle.</span><span class="sxs-lookup"><span data-stu-id="62ab0-106">**Role link name**: The role link name is filled in for you and is either the current name of an existing role link that you are configuring, or an automatically generated name if you are creating a new role link.</span></span> <span data-ttu-id="62ab0-107">Dans les deux cas, vous pouvez le modifier.</span><span class="sxs-lookup"><span data-stu-id="62ab0-107">In either case you can modify the name.</span></span>  
  
 <span data-ttu-id="62ab0-108">**Type de lien de rôle**: vous pouvez sélectionner un type de lien de rôle existant ou créez-en un.</span><span class="sxs-lookup"><span data-stu-id="62ab0-108">**Role link type**: You can select an existing role link type, or create a new one.</span></span> <span data-ttu-id="62ab0-109">Que vous configuriez un type de lien de rôle nouveau ou existant, vous pouvez spécifier comment votre orchestration participe au service.</span><span class="sxs-lookup"><span data-stu-id="62ab0-109">Whether you are configuring a new or existing role link type, you can specify how your orchestration participates in the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62ab0-110">Nous vous recommandons de créer le type de lien de rôle et le type de port associé avant de créer le lien de rôle afin de pouvoir utiliser un type existant pour sa définition.</span><span class="sxs-lookup"><span data-stu-id="62ab0-110">We recommend that you create the role link type and associated port type prior to create the role link so that you can use an existing role link type for defining your role link.</span></span> <span data-ttu-id="62ab0-111">Pour plus d’informations, consultez [comment créer des liens de rôle dans les Orchestrations](../core/how-to-create-role-links-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="62ab0-111">For more information, see [How to Create Role Links in Orchestrations](../core/how-to-create-role-links-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="62ab0-112">**Utilisation du lien de rôle**: Si vous créez un lien de rôle de type, à la fois l’implémente et utilise les rôles sont créés automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="62ab0-112">**Role link usage**: If you create a new role link type, both the implements and uses roles are automatically created for you.</span></span> <span data-ttu-id="62ab0-113">Vous pouvez sélectionner le rôle qui reflète la manière dont votre orchestration participe au service.</span><span class="sxs-lookup"><span data-stu-id="62ab0-113">You can select the role that reflects how your orchestration participates in the service.</span></span> <span data-ttu-id="62ab0-114">Une fois que vous avez complété toutes les étapes de l'Assistant, vous pouvez renommer les identificateurs de rôles ou supprimer un rôle afin de mieux vous adapter à votre implémentation.</span><span class="sxs-lookup"><span data-stu-id="62ab0-114">After you have completed the steps in the wizard, you can rename the role identifiers or remove a role to better match your implementation.</span></span> <span data-ttu-id="62ab0-115">Un type de lien de rôle doit contenir l'un des types de rôles ou l'un de chaque type de rôle.</span><span class="sxs-lookup"><span data-stu-id="62ab0-115">A role link type must contain one of either role type or one of each role type.</span></span> <span data-ttu-id="62ab0-116">Lorsque vous cliquez sur **OK**, les rôles non configurés sont créés correspondant à chaque nom.</span><span class="sxs-lookup"><span data-stu-id="62ab0-116">When you click **OK**, unconfigured roles are created corresponding to each name.</span></span> <span data-ttu-id="62ab0-117">Vous pouvez également sélectionner des types de ports pour les rôles dans la fenêtre Types.</span><span class="sxs-lookup"><span data-stu-id="62ab0-117">You can also select port types for the roles in the Types window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62ab0-118">Si vous appelez l'Assistant Configuration du port pour créer un type de port pour votre type de lien de rôle et que vous souhaitez sélectionner un type de port précédemment défini, assurez-vous que les restrictions d'accès du type de port n'entrent pas en conflit avec les restrictions d'accès du type de lien de rôle.</span><span class="sxs-lookup"><span data-stu-id="62ab0-118">If you invoke the Port Configuration Wizard to create a port type for your role link type, and want to select a previously defined port type, ensure that the access restrictions of the port type do not conflict with the access restrictions of the role link type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ab0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62ab0-119">See Also</span></span>  
 [<span data-ttu-id="62ab0-120">À l’aide de liens de rôle dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="62ab0-120">Using Role Links in Orchestrations</span></span>](../core/using-role-links-in-orchestrations.md)