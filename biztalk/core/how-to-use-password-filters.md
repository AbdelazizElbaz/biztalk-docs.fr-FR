---
title: Comment utiliser le mot de passe des filtres | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb429f8b-c301-45a3-8a4f-bbe6f2c566a3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ad35e2c3bec5b2ece69911b8de8c7fd13c9b790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-password-filters"></a><span data-ttu-id="bf322-102">Utilisation des filtres de mot de passe</span><span class="sxs-lookup"><span data-stu-id="bf322-102">How to Use Password Filters</span></span>
<span data-ttu-id="bf322-103">La fonctionnalité de synchronisation de mot de passe de l'authentification unique de l'entreprise synchronise les mots de passe entre Microsoft Windows Active Directory et les systèmes non Windows.</span><span class="sxs-lookup"><span data-stu-id="bf322-103">The ENTSSO Password Synchronization feature synchronizes passwords between Microsoft Windows Active Directory and non-Windows systems.</span></span> <span data-ttu-id="bf322-104">De nombreux systèmes externes utilisent toutefois des stratégies de mot de passe différentes de celles applicables dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="bf322-104">However, many external systems have password policy requirements which differ from those in Active Directory.</span></span> <span data-ttu-id="bf322-105">Par exemple, un système IBM peut exiger un mot de passe en majuscules et limité à 8 caractères. L'authentification unique de l'entreprise est donc contrainte d'utiliser le « plus petit dénominateur commun » entre les deux systèmes, ce qui limite la sécurité des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="bf322-105">(For example, an IBM system may require a password to be upper case and limited to 8 characters.) This forces ENTSSO to use the “lowest common denominator” between the two systems, limiting password security.</span></span>  
  
 <span data-ttu-id="bf322-106">La fonctionnalité de filtre de mot de passe de l'authentification unique de l'entreprise permet de résoudre cette limitation.</span><span class="sxs-lookup"><span data-stu-id="bf322-106">The ENTSSO Password Filter feature addresses this limitation.</span></span> <span data-ttu-id="bf322-107">Un filtre de mot de passe est un simple adaptateur de synchronisation de mot de passe avec des propriétés supplémentaires définies.</span><span class="sxs-lookup"><span data-stu-id="bf322-107">A Password Filter is merely a Password Sync Adapter with additional properties defined.</span></span> <span data-ttu-id="bf322-108">Celles-ci (longueur maximale ou minimale, restrictions de casse et de caractères, etc.) permettent de filtrer les mots de passe pour garantir leur conformité aux critères du système externe.</span><span class="sxs-lookup"><span data-stu-id="bf322-108">These additional properties (such as maximum or minimum length, case, and character restrictions) serve to filter the passwords so that they meet the criteria of the external system.</span></span>  
  
 <span data-ttu-id="bf322-109">Lorsque vous créez un filtre de mot de passe, le groupe Administrateurs spécifié est automatiquement utilisé comme compte d'administrateur de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="bf322-109">Note that when you create a Password Filter, the Administrator group specified is automatically used as the SSO Administrators account.</span></span> <span data-ttu-id="bf322-110">Si vous modifiez le groupe Administrateurs de l'authentification unique, vous devez vous assurer que le filtre de mot de passe est également mis à jour avec le nouveau compte d'administrateur de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="bf322-110">If you change the SSO Administrator group, you will need to make sure the Password Filter is also updated with the new SSO Administrators account.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf322-111">Comme pour les autres éléments du système d'authentification unique de l'entreprise, les filtres de mot de passe contiennent des informations sensibles et doivent être exposés le moins possible.</span><span class="sxs-lookup"><span data-stu-id="bf322-111">As with all elements of the ENTSSO system, Password Filters contain highly sensitive information and should be exposed to the minimum number of people possible.</span></span>  
  
### <a name="to-create-a-password-filter"></a><span data-ttu-id="bf322-112">Pour créer un filtre de mot de passe</span><span class="sxs-lookup"><span data-stu-id="bf322-112">To Create a Password Filter</span></span>  
  
1.  <span data-ttu-id="bf322-113">Dans le **Console de gestion de l’authentification unique**, avec le bouton droit le **gestion de mot de passe** nœud, puis cliquez sur **créer un filtre**.</span><span class="sxs-lookup"><span data-stu-id="bf322-113">In the **SSO Management Console**, right-click the **Password Management** node, and then click **Create Filter**.</span></span>  
  
     <span data-ttu-id="bf322-114">Le **Assistant Filtre de mot de passe** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bf322-114">The **Password Filter Wizard** appears.</span></span>  
  
2.  <span data-ttu-id="bf322-115">Suivez les instructions de l'Assistant pour créer le filtre de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="bf322-115">Follow the directions on the Wizard to create the Password Filter.</span></span>  
  
### <a name="to-assign-an-affiliate-application-to-a-password-filter"></a><span data-ttu-id="bf322-116">Pour assigner une application associée à un filtre de mot de passe</span><span class="sxs-lookup"><span data-stu-id="bf322-116">To Assign an Affiliate Application to a Password Filter</span></span>  
  
1.  <span data-ttu-id="bf322-117">Cliquez sur le filtre approprié, puis cliquez sur **affecter**...</span><span class="sxs-lookup"><span data-stu-id="bf322-117">Right-click the appropriate filter, and then click **Assign**….</span></span>  
  
2.  <span data-ttu-id="bf322-118">Sélectionnez la **Application associée**.</span><span class="sxs-lookup"><span data-stu-id="bf322-118">Select the appropriate **Affiliate Application**.</span></span>