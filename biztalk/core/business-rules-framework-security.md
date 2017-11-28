---
title: "Sécurité de l’infrastructure des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, code samples
- security, business rules
- artifacts, security
- security, artifacts
- business rules, security
ms.assetid: 86582d3a-259e-47f2-9f72-8dbbe0051503
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2c3a38190d242c85b134a791a8c2cd05c208050
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-framework-security"></a><span data-ttu-id="09b5d-102">Sécurité de l'infrastructure des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="09b5d-102">Business Rules Framework Security</span></span>
<span data-ttu-id="09b5d-103">Le Moteur des règles d'entreprise fonctionne dans le contexte de sécurité de l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="09b5d-103">The Business Rule Engine operates in the security context of the hosting application.</span></span> <span data-ttu-id="09b5d-104">L’identité de l’instance du moteur de règles lors de l’exécution est que le contexte de thread qui appelle la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="09b5d-104">The identity of the rule engine instance during execution is that of the thread context that invokes the **Policy.Execute** method.</span></span>  
  
## <a name="default-security-configuration"></a><span data-ttu-id="09b5d-105">Configuration de sécurité par défaut</span><span class="sxs-lookup"><span data-stu-id="09b5d-105">Default security configuration</span></span>  
 <span data-ttu-id="09b5d-106">Lorsque vous installez Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], deux groupes Microsoft Windows sont créés par défaut, un pour les administrateurs et un pour les utilisateurs : « Administrateurs de BizTalk Server » et « Utilisateurs de l’Application BizTalk ».</span><span class="sxs-lookup"><span data-stu-id="09b5d-106">When you install Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], two Microsoft Windows groups are created by default, one for administrators and one for users: "BizTalk Server Administrators" and "BizTalk Application Users."</span></span> <span data-ttu-id="09b5d-107">Ces deux groupes Windows sont membres des rôles SQL BTS_ADMIN_USERS et BTS_HOST_USERS, eux-mêmes membres des rôles SQL RE_ADMIN_USERS et RE_HOST_USERS respectivement.</span><span class="sxs-lookup"><span data-stu-id="09b5d-107">These two Windows groups are members of BTS_ADMIN_USERS and BTS_HOST_USERS SQL Roles which are members of RE_ADMIN_USERS and RE_HOST_USERS SQL Roles respectively.</span></span>  
  
 <span data-ttu-id="09b5d-108">Les rôles SQL par défaut sont créés chaque fois qu’un magasin de règles est créé : BTS_ADMIN_USERS, BTS_HOST_USERS, RE_ADMIN_USERS et RE_HOST_USERS.</span><span class="sxs-lookup"><span data-stu-id="09b5d-108">The default SQL roles are created whenever a rule store is created: BTS_ADMIN_USERS, BTS_HOST_USERS, RE_ADMIN_USERS and RE_HOST_USERS.</span></span>  
  
|<span data-ttu-id="09b5d-109">Groupes Windows par défaut</span><span class="sxs-lookup"><span data-stu-id="09b5d-109">Default Windows groups</span></span>|<span data-ttu-id="09b5d-110">Rôles SQL</span><span class="sxs-lookup"><span data-stu-id="09b5d-110">SQL roles</span></span>|  
|----------------------------|---------------|  
|<span data-ttu-id="09b5d-111">Administrateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="09b5d-111">BizTalk Server Administrators</span></span>|<span data-ttu-id="09b5d-112">RE_ADMIN_USERS</span><span class="sxs-lookup"><span data-stu-id="09b5d-112">RE_ADMIN_USERS</span></span>|  
|<span data-ttu-id="09b5d-113">Utilisateurs d'applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="09b5d-113">BizTalk Application Users</span></span>|<span data-ttu-id="09b5d-114">RE_HOST_USERS</span><span class="sxs-lookup"><span data-stu-id="09b5d-114">RE_HOST_USERS</span></span>|  
  
 <span data-ttu-id="09b5d-115">Seuls les utilisateurs du rôle RE_ADMIN_USERS sont en mesure d'exécuter les procédures stockées qui mettent à jour les tables de configuration de déploiement et de protection de l'accès aux entités.</span><span class="sxs-lookup"><span data-stu-id="09b5d-115">Only users in the RE_ADMIN_USERS role can execute the stored procedures that update the deployment and entity access protection configuration tables.</span></span> <span data-ttu-id="09b5d-116">Cela signifie que le déploiement, l'annulation de déploiement et la configuration de la protection sont du ressort unique des administrateurs du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="09b5d-116">This means that the deployment, undeployment, and protection configuration are all done only by rule engine administrators.</span></span> <span data-ttu-id="09b5d-117">Les utilisateurs du rôle RE_HOST_USERS peuvent exécuter les autres procédures stockées dans le magasin de règles SQL.</span><span class="sxs-lookup"><span data-stu-id="09b5d-117">Users in the RE_HOST_USERS role can execute the other stored procedures in the SQL rule store.</span></span>  
  
 <span data-ttu-id="09b5d-118">Quel que soit l'ordre d'installation du moteur de règles, le processus de configuration de ce dernier accorde au rôle SQL RE_HOST_USERS l'adhésion au compte Service de mise à jour du moteur des règles s'il ne dispose pas déjà d'un accès à la base de données.</span><span class="sxs-lookup"><span data-stu-id="09b5d-118">Regardless of the order of installation of the rule engine, the rule engine configuration process grants the Rule Engine Update Service account membership to the RE_HOST_USERS SQL role, if it does not already have database access.</span></span> <span data-ttu-id="09b5d-119">Mais si le moteur de règles est installé après la première installation BizTalk, le groupe d'utilisateurs spécifique à l'hôte BizTalk n'est pas ajouté au rôle SQL BTS_HOST_USERS dans la base de données Moteur des règles, car la création d'hôtes est déjà terminée.</span><span class="sxs-lookup"><span data-stu-id="09b5d-119">However, if the rule engine is installed after the initial BizTalk installation the BizTalk, host-specific users group is not added to the BTS_HOST_USERS SQL role in the Rule Engine database because host creation has already been completed.</span></span> <span data-ttu-id="09b5d-120">Vous devez effectuer cette étape manuellement.</span><span class="sxs-lookup"><span data-stu-id="09b5d-120">You need to perform this step manually.</span></span>  
  
## <a name="artifact-level-security"></a><span data-ttu-id="09b5d-121">Sécurité au niveau des artefacts</span><span class="sxs-lookup"><span data-stu-id="09b5d-121">Artifact level security</span></span>  
 <span data-ttu-id="09b5d-122">En plus de la configuration de la sécurité par défaut, le moteur des règles d'entreprise peut également assurer la sécurité au niveau stratégie et vocabulaire des artefacts.</span><span class="sxs-lookup"><span data-stu-id="09b5d-122">In addition to the default security configuration, the Business Rule Engine can also provide security at the artifact—policy and vocabulary level.</span></span>  
  
 <span data-ttu-id="09b5d-123">Chaque version de stratégie ou de vocabulaire est associée à un ou plusieurs groupes d'autorisations.</span><span class="sxs-lookup"><span data-stu-id="09b5d-123">Each policy or vocabulary version has one or more authorization groups associated with it.</span></span> <span data-ttu-id="09b5d-124">Un groupe d'autorisations est une liste nommée d'utilisateurs Microsoft Windows, d'utilisateurs SQL, de rôles SQL et de groupes Windows, dont chaque type a un niveau d'accès particulier.</span><span class="sxs-lookup"><span data-stu-id="09b5d-124">An Authorization group is a named list of Microsoft Windows users, SQL users, SQL roles, and Windows groups, with a particular access level on each type.</span></span>  
  
 <span data-ttu-id="09b5d-125">Lorsqu'une politique ou une stratégie est créée dans le magasin de règles, seuls l'utilisateur qui en est à l'origine et l'administrateur du moteur de règles ont un accès lecture/exécution et modification/suppression par défaut.</span><span class="sxs-lookup"><span data-stu-id="09b5d-125">When a new policy or vocabulary is created in the rule store, only the user who created it and the rule engine administrator have both read/execute and modify/delete access by default.</span></span> <span data-ttu-id="09b5d-126">L'administrateur du moteur de règles peut configurer les utilisateurs (les processus opèrent en fonction des informations d'identification utilisateur) qui auront le niveau ou les droits d'accès nécessaires pour effectuer diverses opérations : lecture/exécution, modification/suppression, autorisation maximale, interdiction.</span><span class="sxs-lookup"><span data-stu-id="09b5d-126">The rule engine administrator can configure which users (processes operate under user credentials) have the access level, or rights, to perform different operations—read/execute, modify/delete, full permission, or no permission.</span></span>  
  
 <span data-ttu-id="09b5d-127">La sécurité spécifique aux artefacts n'est pas activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="09b5d-127">Artifact specific security is not enabled by default.</span></span> <span data-ttu-id="09b5d-128">La définition de la sécurité au niveau des artefacts n'est actuellement pas possible via l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="09b5d-128">Setting artifact level security is not currently available through the user interface.</span></span> <span data-ttu-id="09b5d-129">Cela dit, cette définition peut s'effectuer de façon programmée à l'aide des informations d'identification administrateur du Moteur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="09b5d-129">However, it can be set programmatically with the Business Rule Engine administrator credential.</span></span> <span data-ttu-id="09b5d-130">Le fragment de code suivant montre comment créer une autorisation et associer le groupe à un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="09b5d-130">The following code fragment shows how to create a new authorization and associate the group to a rule set.</span></span>  
  
```  
RuleSet rs;  
string RSName;     
  
// Create new user  
AuthorizationGroupEntry newuser = new AuthorizationGroupEntry(UserName, UID);  
AuthorizationGroupEntryCollection AGEC = new AuthorizationGroupEntryCollection();  
AGEC.Add(newuser);  
  
// Define new authorization group collection  
AuthorizationGroupCollection AGC = new AuthorizationGroupCollection();  
  
// Create new authorization group  
AuthorizationGroup AG = new AuthorizationGroup(GroupName, AccessPermit, AGEC);  
  
//add the authorization group to the authorization group collection  
AGC.Add(AG);  
  
//saving the authorization group collection to the rule store  
m_sqlRS.SaveAuthorizationGroups(AGC);  
  
rs = m_sqlRS.GetRuleSet(rsInfo[0]);                 
RSName = rs.Name;  
  
// Associate authorization group to the ruleset  
m_sqlRS.SetRuleSetAuthorizations(RSName, AGC);  
  
// Get ruleset by name from SQL rule store  
RuleSetInfoCollection rsInfo = m_sqlRS.GetRuleSets("myRuleSet", RuleStore.Filter.All);  
```  
  
> [!NOTE]
>  <span data-ttu-id="09b5d-131">L'utilisation du niveau 1 de sécurité des artefacts est susceptible de réduire les performances, la stratégie devant effectuer une recherche dans la base de données à chaque exécution afin d'évaluer le niveau d'accès de l'application avant de retourner une instance du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="09b5d-131">The use of artifact level l security can diminish performance, because the policy will have to do a database lookup on each execution to evaluate the application's access level before returning an instance of the rule engine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b5d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09b5d-132">See Also</span></span>  
 [<span data-ttu-id="09b5d-133">Notes de sécurité importantes pour le moteur de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="09b5d-133">Important Security Notes for the Business Rule Engine</span></span>](../core/important-security-notes-for-the-business-rule-engine.md)