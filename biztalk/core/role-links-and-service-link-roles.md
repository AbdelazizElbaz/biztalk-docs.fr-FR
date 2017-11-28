---
title: "Liens de rôle et le Service de rôles lier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, orchestrations
- service link roles
- role links
- roles, orchestrations
- roles
- roles, about roles
- service link roles, about service link roles
- orchestrations, roles
- role links, about role links
- orchestrations, deleting
ms.assetid: 23b4ca34-a1a5-44d4-a50d-661277681c72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6630b1ad22ba86f3efe8a19409f3b731880c8a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="role-links-and-service-link-roles"></a><span data-ttu-id="18b34-102">Liens de rôle et rôles de lien de service</span><span class="sxs-lookup"><span data-stu-id="18b34-102">Role Links and Service Link Roles</span></span>
<span data-ttu-id="18b34-103">A *rôle* est une collection de types de port qui utilise un service ou implémente un service.</span><span class="sxs-lookup"><span data-stu-id="18b34-103">A *role* is a collection of port types that either uses a service or implements a service.</span></span> <span data-ttu-id="18b34-104">Un rôle représente le type d’interaction qu’un tiers peut avoir avec une ou de nombreuses orchestrations.</span><span class="sxs-lookup"><span data-stu-id="18b34-104">A role represents the type of interaction that a party can have with one or many orchestrations.</span></span> <span data-ttu-id="18b34-105">Les rôles confèrent une flexibilité et une facilité de gestion à mesure que le nombre de tiers augmente.</span><span class="sxs-lookup"><span data-stu-id="18b34-105">Roles provide flexibility and ease of management as the number of parties increase.</span></span> <span data-ttu-id="18b34-106">Par exemple, une orchestration peut revêtir le rôle d'un Expéditeur.</span><span class="sxs-lookup"><span data-stu-id="18b34-106">For example, an orchestration might use the role of a Shipper.</span></span> <span data-ttu-id="18b34-107">Un ou deux tiers sont associés à ce rôle.</span><span class="sxs-lookup"><span data-stu-id="18b34-107">The Shipper would have one or two parties associated with it.</span></span> <span data-ttu-id="18b34-108">Lorsque l'orchestration choisit la société de transport à utiliser pour un élément, elle compare le prix des tiers dans le rôle Expéditeur.</span><span class="sxs-lookup"><span data-stu-id="18b34-108">When the orchestration decides which shipping company to use to ship an item, it compares the prices of the parties in the Shipper role.</span></span>  
  
 <span data-ttu-id="18b34-109">A *type de lien de rôle* est une propriété qui représente la relation entre deux services ou orchestrations.</span><span class="sxs-lookup"><span data-stu-id="18b34-109">A *role link type* is a property that characterizes the relationship between two services or orchestrations.</span></span> <span data-ttu-id="18b34-110">Il définit le rôle joué par chaque service dans la relation et spécifie les types de ports fournis par chaque rôle.</span><span class="sxs-lookup"><span data-stu-id="18b34-110">It defines the part played by each of the services in the relationship and specifies the port types provided by each role.</span></span>  
  
 <span data-ttu-id="18b34-111">Un tiers, ou unité d'organisation, représente une entité, en dehors de BizTalk Server, qui interagit avec une orchestration.</span><span class="sxs-lookup"><span data-stu-id="18b34-111">A party, or organizational unit, represents an entity outside of BizTalk Server that interacts with an orchestration.</span></span> <span data-ttu-id="18b34-112">Dans BizTalk Server, chaque organisation avec laquelle vous échangez des messages est représentée par un tiers.</span><span class="sxs-lookup"><span data-stu-id="18b34-112">In BizTalk Server, each organization with which you exchange messages is represented by a party.</span></span> <span data-ttu-id="18b34-113">Vous pouvez définir de quelle façon le tiers interagira en l'inscrivant dans un rôle.</span><span class="sxs-lookup"><span data-stu-id="18b34-113">You can define how the party interacts by enlisting it in a role.</span></span>  
  
 <span data-ttu-id="18b34-114">Vous pouvez déployer ou supprimer un type de lien de rôle lorsqu'il est associé à une orchestration.</span><span class="sxs-lookup"><span data-stu-id="18b34-114">You can deploy or remove a role link type when it is associated with an orchestration.</span></span>  
  
## <a name="orchestrations-and-roles"></a><span data-ttu-id="18b34-115">Orchestrations et rôles</span><span class="sxs-lookup"><span data-stu-id="18b34-115">Orchestrations and Roles</span></span>  
 <span data-ttu-id="18b34-116">Lorsque vous déployez une orchestration qui utilise un type de lien de rôle, la base de données de configuration enregistre le rôle.</span><span class="sxs-lookup"><span data-stu-id="18b34-116">When you deploy an orchestration that uses a role link type, the Configuration database saves the role.</span></span> <span data-ttu-id="18b34-117">Étant donné qu'un rôle peut être utilisé par plusieurs orchestrations, la base de données de gestion n'enregistre qu'une copie du type de lien de rôle.</span><span class="sxs-lookup"><span data-stu-id="18b34-117">Because a role can be used by more than one orchestration, the Management database saves only one copy of the role link type.</span></span>  
  
 <span data-ttu-id="18b34-118">Si votre projet BizTalk contient deux types de liens de rôle dans des fichiers d'orchestration distincts (.odx) qui portent le même nom et espace de noms, votre projet BizTalk n'est pas compilé.</span><span class="sxs-lookup"><span data-stu-id="18b34-118">If your BizTalk project contains two role link types in separate orchestration (.odx) files that have the same name and namespace, your BizTalk project does not compile.</span></span>  
  
### <a name="orchestration-removals-that-use-roles"></a><span data-ttu-id="18b34-119">Suppressions d'orchestration qui utilisent des rôles</span><span class="sxs-lookup"><span data-stu-id="18b34-119">Orchestration Removals that use Roles</span></span>  
 <span data-ttu-id="18b34-120">Étant donné qu'un type de lien de rôle peut être utilisé par plusieurs orchestrations, lorsque vous annulez le déploiement d'un assembly qui contient une orchestration utilisant un rôle, la base de données de gestion ne supprime le rôle que si aucune autre orchestration ne l'utilise.</span><span class="sxs-lookup"><span data-stu-id="18b34-120">Because a role link type can be used by more than one orchestration, when you undeploy an assembly that contains an orchestration that uses a role, the Management database removes the role only if no other orchestrations are using the role.</span></span>  
  
 <span data-ttu-id="18b34-121">Par ailleurs, la base de données de gestion ne supprime un rôle que si aucun tiers n'est inscrit auprès de lui.</span><span class="sxs-lookup"><span data-stu-id="18b34-121">Additionally, the Management database removes a role only if there are no parties enlisted with it.</span></span> <span data-ttu-id="18b34-122">De même que vous ne pouvez pas remplacer un rôle auprès duquel des tiers sont inscrits, vous ne pouvez pas non plus en supprimer.</span><span class="sxs-lookup"><span data-stu-id="18b34-122">Just as you cannot overwrite a role that has parties enlisted with it, you cannot remove a role that has parties enlisted with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b34-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18b34-123">See Also</span></span>  
 <span data-ttu-id="18b34-124">[À l’aide de liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="18b34-124">[Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="18b34-125">Artefacts</span><span class="sxs-lookup"><span data-stu-id="18b34-125">Artifacts</span></span>](../core/artifacts.md)