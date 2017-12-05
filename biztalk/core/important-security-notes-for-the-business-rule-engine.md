---
title: "Notes de sécurité importantes pour l’activité du moteur de règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, store administrator
- Business Rule Composer, security
- business rules, security
- Denial of Service attacks
ms.assetid: 8972127a-5569-4b32-bc09-e9265efe9514
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e54a532d33e4f84eb5f1ecea67f957d415344a7c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="important-security-notes-for-the-business-rule-engine"></a><span data-ttu-id="120ba-102">Notes de sécurité importantes pour le moteur de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="120ba-102">Important Security Notes for the Business Rule Engine</span></span>
<span data-ttu-id="120ba-103">Cette rubrique résume les problèmes de sécurité connus dans Microsoft BizTalk Server et les étapes à suivre pour atténuer les risques de sécurité.</span><span class="sxs-lookup"><span data-stu-id="120ba-103">This topic summarizes known security issues in Microsoft BizTalk Server and the steps you must take to mitigate the security risks.</span></span>  
  
## <a name="malicious-schema-input-causing-denial-of-service-attack"></a><span data-ttu-id="120ba-104">Entrée de schéma malveillante causant une attaque par refus de service</span><span class="sxs-lookup"><span data-stu-id="120ba-104">Malicious schema input causing Denial of Service attack</span></span>  
 <span data-ttu-id="120ba-105">Pendant la déclaration de faits, chaque règle est vérifiée en étant comparée à chaque objet qui correspond aux types pris en charge dans une stratégie.</span><span class="sxs-lookup"><span data-stu-id="120ba-105">While asserting facts, each rule is verified against every object that matches the supported types within a policy.</span></span> <span data-ttu-id="120ba-106">Supposons la présence d'une règle dans une stratégie qui utilise l'un des éléments d'un schéma transmis en utilisant un sélecteur.</span><span class="sxs-lookup"><span data-stu-id="120ba-106">Suppose there is a rule in a policy that uses one of the elements in a schema passed by using a selector.</span></span> <span data-ttu-id="120ba-107">Si l'instance de cet élément/attribut correspondant au sélecteur est répétée des milliers de fois, toutes les instances de ce type sont déclarées, entraînant une dégradation des performances et un éventuel refus de service (DoS, Denial of Service).</span><span class="sxs-lookup"><span data-stu-id="120ba-107">Now if the instance if this element/attribute that matches the selector is repeated thousands of times, every such instance is asserted, causing performance degradation and subsequent possible Denial of Service (DoS).</span></span>  
  
 <span data-ttu-id="120ba-108">Pour réduire les risques que ce problème se produise, il faut que vous validiez toutes les entrées ambiguës transmises pendant l'exécution d'une stratégie.</span><span class="sxs-lookup"><span data-stu-id="120ba-108">To mitigate this potential issue, you need to validate all ambiguous input that is passed while executing a policy.</span></span>  
  
## <a name="ruleset-not-validating-objects-before-asserting-the-facts"></a><span data-ttu-id="120ba-109">Ensemble de règles ne validant pas les objets avant de déclarer les faits</span><span class="sxs-lookup"><span data-stu-id="120ba-109">RuleSet not validating objects before asserting the facts</span></span>  
 <span data-ttu-id="120ba-110">N’importe quelle instance de schéma est passé en tant que fait la **RuleSet** n’est pas validé par rapport au schéma avant de déclarer les règles utilisant des sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="120ba-110">Any schema instance passed as a fact to the **RuleSet** is not validated against the schema before asserting any rules using selectors.</span></span> <span data-ttu-id="120ba-111">Vous devez valider toutes les entrées transmises pendant l'exécution d'une stratégie.</span><span class="sxs-lookup"><span data-stu-id="120ba-111">You should validate all input that is passed while executing a policy.</span></span>  
  
## <a name="expected-behaviors-of-the-business-rule-composer-when-rulestore-security-is-on"></a><span data-ttu-id="120ba-112">Comportements attendus de l'Éditeur des règles d'entreprise lorsque la sécurité RuleStore est activée</span><span class="sxs-lookup"><span data-stu-id="120ba-112">Expected behaviors of the Business Rule Composer when RuleStore security is on</span></span>  
 <span data-ttu-id="120ba-113">Vous pouvez activer la fonctionnalité de sécurité des rôles pour le magasin de règles en appelant le **EnableAuthorization** méthode de la **RuleStore** classe.</span><span class="sxs-lookup"><span data-stu-id="120ba-113">You can enable the role-based security feature for the rule store by calling the **EnableAuthorization** method of the **RuleStore** class.</span></span> <span data-ttu-id="120ba-114">Lorsque ce composant de sécurité est activé, les comportements attendus dans l'Éditeur des règles d'entreprise sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="120ba-114">When this security feature is enabled, the expected behaviors in the Business Rule Composer are as follows:</span></span>  
  
-   <span data-ttu-id="120ba-115">Le modèle objet filtre les ensembles de règles et les vocabulaires pour lesquels l'utilisateur n'a pas d'accès en lecture.</span><span class="sxs-lookup"><span data-stu-id="120ba-115">The object model filters out rule sets and vocabularies to which the user does not have read access.</span></span> <span data-ttu-id="120ba-116">Ils n'apparaissent donc pas dans l'Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="120ba-116">Therefore, they do not appear in the Business Rule Composer.</span></span>  
  
-   <span data-ttu-id="120ba-117">Si l'utilisateur n'a pas d'accès en écriture à une stratégie ou un vocabulaire, toute tentative d'enregistrement provoque l'émission d'une exception.</span><span class="sxs-lookup"><span data-stu-id="120ba-117">If the user does not have write access to a policy or a vocabulary, any save attempt causes an exception to be thrown.</span></span>  
  
## <a name="user-types-for-rule-store-administrator"></a><span data-ttu-id="120ba-118">Types d'utilisateurs pour l'administrateur du magasin de règles</span><span class="sxs-lookup"><span data-stu-id="120ba-118">User types for rule store administrator</span></span>  
 <span data-ttu-id="120ba-119">L'administrateur du magasin de règles dispose du privilège de définir un groupe d'autorisations pour les artefacts enregistrés dans le magasin de règles.</span><span class="sxs-lookup"><span data-stu-id="120ba-119">The rule store administrator has the privilege to define an authorization group for artifacts saved in the rule store.</span></span> <span data-ttu-id="120ba-120">Notez cependant les différences suivantes entre deux types d'utilisateurs auxquels l'administrateur du magasin de règles peut appartenir :</span><span class="sxs-lookup"><span data-stu-id="120ba-120">However, note the following differences between two types of user to which the rule store administrator can belong:</span></span>  
  
-   <span data-ttu-id="120ba-121">Lorsque l'administrateur du magasin de règles est un utilisateur Windows, autrement dit s'il utilise l'authentification Windows pour se connecter au magasin de règles, il peut définir un groupe d'autorisations dont l'utilisateur est un groupe Windows ou un utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="120ba-121">When the rule store administrator is a Windows user, which means using Windows authentication to connect the rule store, the rule store administrator can define an authorization group whose user is a Windows group or a Windows user.</span></span>  
  
-   <span data-ttu-id="120ba-122">Lorsque l'administrateur du magasin de règles est un utilisateur SQL, autrement dit s'il utilise l'authentification SQL pour se connecter au magasin de règles, il ne peut pas définir de groupe d'autorisations dont l'utilisateur est un groupe Windows, mais peut en définir un dont l'utilisateur est un utilisateur Windows.</span><span class="sxs-lookup"><span data-stu-id="120ba-122">When the rule store administrator is a SQL user, which means using SQL authentication to connect the rule store, the rule store administrator cannot define an authorization group whose user is a Windows group, but can define an authorization group whose user is a Windows user.</span></span>  
  
## <a name="user-cannot-associate-an-authorization-group-with-an-artifact-without-sufficient-rights"></a><span data-ttu-id="120ba-123">Un utilisateur ne peut associer un groupe d'autorisations à un artefact s'il ne dispose pas des droits nécessaires</span><span class="sxs-lookup"><span data-stu-id="120ba-123">User cannot associate an authorization group with an artifact without sufficient rights</span></span>  
 <span data-ttu-id="120ba-124">Un créateur d'artefact qui n'est ni un utilisateur dbo SQL, ni un membre de RE_ADMIN_USERS, et qui ne dispose pas non plus de l'autorisation MODIFY_DELETE pour un artefact, ne peut pas associer de nouveau groupe d'autorisations à l'artefact.</span><span class="sxs-lookup"><span data-stu-id="120ba-124">An artifact creator that is neither a SQL dbo user nor a member of RE_ADMIN_USERS, and does not have MODIFY_DELETE permission to an artifact, cannot associate a new authorization group with the artifact.</span></span> <span data-ttu-id="120ba-125">Le scénario suivant est un exemple de ce comportement :</span><span class="sxs-lookup"><span data-stu-id="120ba-125">The following scenario is an example of this behavior:</span></span>  
  
1.  <span data-ttu-id="120ba-126">Le créateur de l'ensemble de règles n'est pas dbo, ne fait pas partie du groupe RE_ADMIN_USERS et ne dispose pas de l'autorisation MODIFY_DELETE une fois que l'ensemble de règles est créé.</span><span class="sxs-lookup"><span data-stu-id="120ba-126">Rule set creator is not dbo, is not in the RE_ADMIN_USERS group, and does not have MODIFY_DELETE permission after the rule set is created.</span></span>  
  
2.  <span data-ttu-id="120ba-127">Le créateur crée un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="120ba-127">Creator creates a rule set.</span></span>  
  
3.  <span data-ttu-id="120ba-128">Un membre du groupe RE_ADMIN_USERS crée une autorisation AG1 dotée d'une autorisation MODIFY_DELETE pour l'utilisateur2.</span><span class="sxs-lookup"><span data-stu-id="120ba-128">Member of the RE_ADMIN_USERS group creates authorization AG1 with MODIFY_DELETE permission to User2.</span></span>  
  
4.  <span data-ttu-id="120ba-129">Le créateur associe AG1 à l'ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="120ba-129">Creator associates AG1 with the rule set.</span></span>  
  
5.  <span data-ttu-id="120ba-130">Activation de l'autorisation du magasin de règles.</span><span class="sxs-lookup"><span data-stu-id="120ba-130">Enable the rule store authorization.</span></span>  
  
6.  <span data-ttu-id="120ba-131">Un membre du groupe RE_ADMIN_USERS crée une autorisation AG2 dotée d'une autorisation READ_EXECUTE pour l'utilisateur2.</span><span class="sxs-lookup"><span data-stu-id="120ba-131">Member of the RE_ADMIN_USERS group creates authorization AG2 with READ_EXECUTE permission to User2.</span></span>  
  
7.  <span data-ttu-id="120ba-132">Le créateur associe AG2 à l'ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="120ba-132">Creator associates AG2 with the rule set.</span></span> <span data-ttu-id="120ba-133">Bien que le créateur ne dispose pas des autorisations nécessaires pour cela, aucun message d'erreur n'apparaît.</span><span class="sxs-lookup"><span data-stu-id="120ba-133">Although the creator does not have sufficient right to do so, no error message appears.</span></span>  
  
8.  <span data-ttu-id="120ba-134">La tentative de l'utilisateur2 de lire l'ensemble de règles échoue.</span><span class="sxs-lookup"><span data-stu-id="120ba-134">Attempt to read the rule set by User2 fails.</span></span>