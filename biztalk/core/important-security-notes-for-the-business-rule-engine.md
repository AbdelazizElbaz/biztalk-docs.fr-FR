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
# <a name="important-security-notes-for-the-business-rule-engine"></a>Notes de sécurité importantes pour le moteur de règles d’entreprise
Cette rubrique résume les problèmes de sécurité connus dans Microsoft BizTalk Server et les étapes à suivre pour atténuer les risques de sécurité.  
  
## <a name="malicious-schema-input-causing-denial-of-service-attack"></a>Entrée de schéma malveillante causant une attaque par refus de service  
 Pendant la déclaration de faits, chaque règle est vérifiée en étant comparée à chaque objet qui correspond aux types pris en charge dans une stratégie. Supposons la présence d'une règle dans une stratégie qui utilise l'un des éléments d'un schéma transmis en utilisant un sélecteur. Si l'instance de cet élément/attribut correspondant au sélecteur est répétée des milliers de fois, toutes les instances de ce type sont déclarées, entraînant une dégradation des performances et un éventuel refus de service (DoS, Denial of Service).  
  
 Pour réduire les risques que ce problème se produise, il faut que vous validiez toutes les entrées ambiguës transmises pendant l'exécution d'une stratégie.  
  
## <a name="ruleset-not-validating-objects-before-asserting-the-facts"></a>Ensemble de règles ne validant pas les objets avant de déclarer les faits  
 N’importe quelle instance de schéma est passé en tant que fait la **RuleSet** n’est pas validé par rapport au schéma avant de déclarer les règles utilisant des sélecteurs. Vous devez valider toutes les entrées transmises pendant l'exécution d'une stratégie.  
  
## <a name="expected-behaviors-of-the-business-rule-composer-when-rulestore-security-is-on"></a>Comportements attendus de l'Éditeur des règles d'entreprise lorsque la sécurité RuleStore est activée  
 Vous pouvez activer la fonctionnalité de sécurité des rôles pour le magasin de règles en appelant le **EnableAuthorization** méthode de la **RuleStore** classe. Lorsque ce composant de sécurité est activé, les comportements attendus dans l'Éditeur des règles d'entreprise sont les suivants :  
  
-   Le modèle objet filtre les ensembles de règles et les vocabulaires pour lesquels l'utilisateur n'a pas d'accès en lecture. Ils n'apparaissent donc pas dans l'Éditeur des règles d'entreprise.  
  
-   Si l'utilisateur n'a pas d'accès en écriture à une stratégie ou un vocabulaire, toute tentative d'enregistrement provoque l'émission d'une exception.  
  
## <a name="user-types-for-rule-store-administrator"></a>Types d'utilisateurs pour l'administrateur du magasin de règles  
 L'administrateur du magasin de règles dispose du privilège de définir un groupe d'autorisations pour les artefacts enregistrés dans le magasin de règles. Notez cependant les différences suivantes entre deux types d'utilisateurs auxquels l'administrateur du magasin de règles peut appartenir :  
  
-   Lorsque l'administrateur du magasin de règles est un utilisateur Windows, autrement dit s'il utilise l'authentification Windows pour se connecter au magasin de règles, il peut définir un groupe d'autorisations dont l'utilisateur est un groupe Windows ou un utilisateur Windows.  
  
-   Lorsque l'administrateur du magasin de règles est un utilisateur SQL, autrement dit s'il utilise l'authentification SQL pour se connecter au magasin de règles, il ne peut pas définir de groupe d'autorisations dont l'utilisateur est un groupe Windows, mais peut en définir un dont l'utilisateur est un utilisateur Windows.  
  
## <a name="user-cannot-associate-an-authorization-group-with-an-artifact-without-sufficient-rights"></a>Un utilisateur ne peut associer un groupe d'autorisations à un artefact s'il ne dispose pas des droits nécessaires  
 Un créateur d'artefact qui n'est ni un utilisateur dbo SQL, ni un membre de RE_ADMIN_USERS, et qui ne dispose pas non plus de l'autorisation MODIFY_DELETE pour un artefact, ne peut pas associer de nouveau groupe d'autorisations à l'artefact. Le scénario suivant est un exemple de ce comportement :  
  
1.  Le créateur de l'ensemble de règles n'est pas dbo, ne fait pas partie du groupe RE_ADMIN_USERS et ne dispose pas de l'autorisation MODIFY_DELETE une fois que l'ensemble de règles est créé.  
  
2.  Le créateur crée un ensemble de règles.  
  
3.  Un membre du groupe RE_ADMIN_USERS crée une autorisation AG1 dotée d'une autorisation MODIFY_DELETE pour l'utilisateur2.  
  
4.  Le créateur associe AG1 à l'ensemble de règles.  
  
5.  Activation de l'autorisation du magasin de règles.  
  
6.  Un membre du groupe RE_ADMIN_USERS crée une autorisation AG2 dotée d'une autorisation READ_EXECUTE pour l'utilisateur2.  
  
7.  Le créateur associe AG2 à l'ensemble de règles. Bien que le créateur ne dispose pas des autorisations nécessaires pour cela, aucun message d'erreur n'apparaît.  
  
8.  La tentative de l'utilisateur2 de lire l'ensemble de règles échoue.