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
# <a name="business-rules-framework-security"></a>Sécurité de l'infrastructure des règles d'entreprise
Le Moteur des règles d'entreprise fonctionne dans le contexte de sécurité de l'application hôte. L’identité de l’instance du moteur de règles lors de l’exécution est que le contexte de thread qui appelle la **Policy.Execute** (méthode).  
  
## <a name="default-security-configuration"></a>Configuration de sécurité par défaut  
 Lorsque vous installez Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], deux groupes Microsoft Windows sont créés par défaut, un pour les administrateurs et un pour les utilisateurs : « Administrateurs de BizTalk Server » et « Utilisateurs de l’Application BizTalk ». Ces deux groupes Windows sont membres des rôles SQL BTS_ADMIN_USERS et BTS_HOST_USERS, eux-mêmes membres des rôles SQL RE_ADMIN_USERS et RE_HOST_USERS respectivement.  
  
 Les rôles SQL par défaut sont créés chaque fois qu’un magasin de règles est créé : BTS_ADMIN_USERS, BTS_HOST_USERS, RE_ADMIN_USERS et RE_HOST_USERS.  
  
|Groupes Windows par défaut|Rôles SQL|  
|----------------------------|---------------|  
|Administrateurs BizTalk Server|RE_ADMIN_USERS|  
|Utilisateurs d'applications BizTalk|RE_HOST_USERS|  
  
 Seuls les utilisateurs du rôle RE_ADMIN_USERS sont en mesure d'exécuter les procédures stockées qui mettent à jour les tables de configuration de déploiement et de protection de l'accès aux entités. Cela signifie que le déploiement, l'annulation de déploiement et la configuration de la protection sont du ressort unique des administrateurs du moteur de règles. Les utilisateurs du rôle RE_HOST_USERS peuvent exécuter les autres procédures stockées dans le magasin de règles SQL.  
  
 Quel que soit l'ordre d'installation du moteur de règles, le processus de configuration de ce dernier accorde au rôle SQL RE_HOST_USERS l'adhésion au compte Service de mise à jour du moteur des règles s'il ne dispose pas déjà d'un accès à la base de données. Mais si le moteur de règles est installé après la première installation BizTalk, le groupe d'utilisateurs spécifique à l'hôte BizTalk n'est pas ajouté au rôle SQL BTS_HOST_USERS dans la base de données Moteur des règles, car la création d'hôtes est déjà terminée. Vous devez effectuer cette étape manuellement.  
  
## <a name="artifact-level-security"></a>Sécurité au niveau des artefacts  
 En plus de la configuration de la sécurité par défaut, le moteur des règles d'entreprise peut également assurer la sécurité au niveau stratégie et vocabulaire des artefacts.  
  
 Chaque version de stratégie ou de vocabulaire est associée à un ou plusieurs groupes d'autorisations. Un groupe d'autorisations est une liste nommée d'utilisateurs Microsoft Windows, d'utilisateurs SQL, de rôles SQL et de groupes Windows, dont chaque type a un niveau d'accès particulier.  
  
 Lorsqu'une politique ou une stratégie est créée dans le magasin de règles, seuls l'utilisateur qui en est à l'origine et l'administrateur du moteur de règles ont un accès lecture/exécution et modification/suppression par défaut. L'administrateur du moteur de règles peut configurer les utilisateurs (les processus opèrent en fonction des informations d'identification utilisateur) qui auront le niveau ou les droits d'accès nécessaires pour effectuer diverses opérations : lecture/exécution, modification/suppression, autorisation maximale, interdiction.  
  
 La sécurité spécifique aux artefacts n'est pas activée par défaut. La définition de la sécurité au niveau des artefacts n'est actuellement pas possible via l'interface utilisateur. Cela dit, cette définition peut s'effectuer de façon programmée à l'aide des informations d'identification administrateur du Moteur des règles d'entreprise. Le fragment de code suivant montre comment créer une autorisation et associer le groupe à un ensemble de règles.  
  
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
>  L'utilisation du niveau 1 de sécurité des artefacts est susceptible de réduire les performances, la stratégie devant effectuer une recherche dans la base de données à chaque exécution afin d'évaluer le niveau d'accès de l'application avant de retourner une instance du moteur de règles.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes de sécurité importantes pour le moteur de règles d’entreprise](../core/important-security-notes-for-the-business-rule-engine.md)