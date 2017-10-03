---
title: "Comment créer et modifier un groupe d’adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1eef051-2ed7-4e28-8cb9-0145d6c8ed76
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6865de8eb67d9fe1a6ca8d93b7d2e6527ae36364
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-and-modify-an-adapter-group"></a><span data-ttu-id="00d1e-102">Comment créer et modifier un groupe d’adaptateurs</span><span class="sxs-lookup"><span data-stu-id="00d1e-102">How to Create and Modify an Adapter Group</span></span>
<span data-ttu-id="00d1e-103">L'une des nouvelles fonctionnalités de l'authentification unique (SSO) permet de créer et de modifier des groupes d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="00d1e-103">One of the new features of Single Sign-On (SSO) is the ability to create and modify adapter groups.</span></span> <span data-ttu-id="00d1e-104">Comme le nom l'indique, un groupe d'adaptateurs correspond à un regroupement d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="00d1e-104">As the name implies, an adapter group is a collection of adapters.</span></span> <span data-ttu-id="00d1e-105">Vous pouvez utiliser des groupes d’adaptateurs pour organiser les paramètres de sécurité et autres propriétés de vos adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="00d1e-105">You can use adapter groups to organize security settings and other properties for your adapters.</span></span>  
  
### <a name="to-create-and-modify-an-adapter-group"></a><span data-ttu-id="00d1e-106">Pour créer et modifier un groupe d’adaptateurs</span><span class="sxs-lookup"><span data-stu-id="00d1e-106">To create and modify an adapter group</span></span>  
  
1.  <span data-ttu-id="00d1e-107">Créez le groupe d'adaptateurs à l'aide un appel à l'outil ssops.</span><span class="sxs-lookup"><span data-stu-id="00d1e-107">Create the adapter group by using a call to the ssops tool.</span></span>  
  
     <span data-ttu-id="00d1e-108">Dans le fichier XML associé, définissez l'indicateur de groupe comme groupe d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="00d1e-108">In the associated XML file, you must set the group flag as an adapter group.</span></span>  
  
2.  <span data-ttu-id="00d1e-109">Ajoutez un ou plusieurs adaptateurs au groupe d'adaptateurs à l'aide de `ISSOPSAdmin.AddAdapterToAdapterGroup`.</span><span class="sxs-lookup"><span data-stu-id="00d1e-109">Add one or more adapters to the adapter group by using `ISSOPSAdmin.AddAdapterToAdapterGroup`.</span></span>  
  
     <span data-ttu-id="00d1e-110">À ce stade, votre groupe d’adaptateurs est prêt à fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="00d1e-110">At this point, your adapter group is ready to work as intended.</span></span> <span data-ttu-id="00d1e-111">Si nécessaire, affichez la liste complète des adaptateurs associés à l'aide de `ISSOPSAdmin.GetAdaptersForAdapterGroup`.</span><span class="sxs-lookup"><span data-stu-id="00d1e-111">If necessary, you can view the full list of associated adapters by using `ISSOPSAdmin.GetAdaptersForAdapterGroup`.</span></span>  
  
3.  <span data-ttu-id="00d1e-112">Vous pouvez modifier les paramètres de votre groupe d'adaptateurs à l'aide de `ISSOPSAdmin.SetAdapterProperties`.</span><span class="sxs-lookup"><span data-stu-id="00d1e-112">You can modify the settings of your adapter group using `ISSOPSAdmin.SetAdapterProperties`.</span></span>  
  
4.  <span data-ttu-id="00d1e-113">Une fois que vous avez terminé, vous pouvez supprimer l'adaptateur du groupe d'adaptateurs à l'aide de `ISSOPSAdmin.RemoveAdapterFromAdapterGroup`.</span><span class="sxs-lookup"><span data-stu-id="00d1e-113">When you are finished, you can remove the adapter from the adapter group using `ISSOPSAdmin.RemoveAdapterFromAdapterGroup`.</span></span>  
  
5.  <span data-ttu-id="00d1e-114">Enfin, vous pouvez supprimer le groupe d'adaptateurs à l'aide de `ISSOAdmin.DeleteApplication`.</span><span class="sxs-lookup"><span data-stu-id="00d1e-114">Finally, you can delete the adapter group by using `ISSOAdmin.DeleteApplication`.</span></span>  
  
     <span data-ttu-id="00d1e-115">Vous pouvez à la place décider de supprimer le groupe d'adaptateurs à l'aide de la commande `-delete` de l'outil ssops.</span><span class="sxs-lookup"><span data-stu-id="00d1e-115">You may choose instead to delete the adapter group by using the `-delete` command of the ssops tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d1e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00d1e-116">See Also</span></span>  
 [<span data-ttu-id="00d1e-117">Synchronisation des mots de passe</span><span class="sxs-lookup"><span data-stu-id="00d1e-117">Synchronizing Passwords</span></span>](../core/synchronizing-passwords.md)