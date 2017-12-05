---
title: "Des Applications associées SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, designing applications
- applications [SSO], application types
- SSO, application types
- SSO, application properties
- applications [SSO], properties
- applications [SSO]
- SSO, applications
- applications [SSO], designing
ms.assetid: 002ecf7e-4d52-425a-9498-0e7bd6545047
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1621973fed0c7a87538e3ed18161f05c4c9cf9e6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sso-affiliate-applications"></a>Applications associées SSO
Les applications associées à l'authentification unique de l'entreprise (SSO) constituent des entités logiques représentant un système ou un sous-système tel qu'un hôte, un système principal ou une application sectorielle à laquelle vous êtes connecté via l'authentification unique de l'entreprise. Une application associée peut représenter un système principal, tel qu'un macroordinateur (grand système) ou un ordinateur fonctionnant sous UNIX. Elle peut également constituer une application SAP ou une sous-classe du système, telle que les sous-systèmes « Avantages » ou « Bulletin de paie ».  
  
 Quand un administrateur SSO ou un administrateur d'applications associées à SSO définit une application associée, il doit également déterminer qui va administrer celle-ci (administrateur de l'application), qui en seront les utilisateurs (utilisateurs de l'application) et quels paramètres seront utilisés par le système SSO pour en authentifier les utilisateurs (ID utilisateur, mots de passe, codes confidentiels, etc.). Pour plus d’informations sur les administrateurs et utilisateurs de l’application, consultez [groupes utilisateur SSO](../core/sso-user-groups.md).  
  
## <a name="affiliate-application-types"></a>Types d'applications associées  
 L'authentification unique de l'entreprise définit différents types d'applications. Ces derniers prennent en charge différents types de mappages entre le compte Windows et le compte du système non-Windows.  
  
 Les applications peuvent être de type :  
  
 **Individuels** applications individuelles prennent en charge les associations entre le compte Windows et le compte non-Windows. Dans un type d'application individuelle, un compte Windows est mappé à un seul et unique compte non-Windows. Le mappage peut être utilisé dans les deux sens, soit à partir d'un compte Windows vers un compte non-Windows, soit à partir d'un compte non-Windows vers un compte Windows, ou les deux, selon les indicateurs définis pour cette application.  Par conséquent, les applications individuelles peuvent être utilisées pour l'authentification unique initiée par Windows ou par l'hôte, ou encore par les deux.   
  
 **Groupe** des applications de groupe prennent en charge les mappages entre un groupe Windows et un compte non-Windows unique. Le compte Utilisateurs d'applications sert à définir le groupe Windows à utiliser pour cette application de groupe. Un seul mappage peut être défini pour une application de groupe. Il doit mapper le groupe Windows à un compte non-Windows unique qui sera utilisé par tous les membres de ce groupe Windows pour accéder au système non-Windows. Les applications de groupe ne peuvent être utilisées que pour l'authentification unique initiée par Windows.  
  
 **Groupe hôte** applications groupe d’hôtes sont exactement le contraire des applications de groupe. Elles prennent en charge les mappages entre un groupe défini de comptes non-Windows et un compte unique Windows.  Pour cette application, le compte unique Windows utilisé par les comptes non-Windows est défini par le compte des utilisateurs de l'application. Le groupe des comptes non-Windows qui dispose d'une autorisation d'accès à cette application est défini par la création d'un mappage pour chaque compte non-Windows. Les applications de groupe d'hôtes ne peuvent être utilisées que pour l'authentification unique initiée par l'hôte.  
  
## <a name="designing-an-affiliate-application"></a>Conception d'une application associée  
 Avant la création d'une application associée, l'administrateur d'applications associées à SSO ou l'administrateur SSO doit prendre les décisions suivantes :  
  
1.  **Ce que représente cette application associée ?** Vous devez connaître les applications non-Windows que l'application associée va représenter dans le système SSO. Par exemple :  
  
     Nom de l’application : APP1  
  
     Description : Les applications du service de paie stub d'  
  
     Contact :administrator@companyname.com  
  
2.  **Qui va administrer cette application associée ?** Vous devez déterminer les administrateurs de cette application associée. Ceux-ci forment le groupe des administrateurs Windows pour cette application associée. Par exemple, Domain\APP1AdminGroup  
  
3.  **Qui utilisera cette application associée ?** Vous devez déterminer les utilisateurs finaux de cette application associée. Ces utilisateurs représentent le groupe des utilisateurs Windows pour cette application associée, par exemple, Domain\DomainUsers. Dans le cas de l'application pour les bulletins de paie, vous pouvez souhaiter que tous les utilisateurs puissent accéder à leurs informations de bulletin de paie : vous pouvez donc spécifier le groupe des utilisateurs du domaine comme groupe d'utilisateurs de cette application.  
  
4.  **Les informations d’identification est l’utilisation d’application associée pour authentifier ses utilisateurs ?** Différentes applications utilisent des informations d'identification différentes pour authentifier les utilisateurs. Par exemple, certaines applications peuvent utiliser des ID, des mots de passe, des codes confidentiels ou une combinaison de tous ces éléments. Vous devez également déterminer si le système doit masquer les informations d'identification que l'utilisateur va fournir.  
  
5.  **Allez-vous utiliser des mappages individuels ou un mappage de groupe pour cette application associée ?** Est-ce que chaque utilisateur Windows possède un compte dans le système principal ou le système principal possède-t-il un compte pour tous les utilisateurs Windows ? Dans le cas du système « Bulletin de paie », étant donné que chaque utilisateur possède son propre compte pour accéder à ses propres informations de paie, vous devez utiliser des mappages individuels.  
  
 Après avoir créé une application associée, il est impossible de modifier les propriétés suivantes :  
  
-   Nom de l’application associée  
  
-   Champs liés à l'application associée  
  
-   Type de l'application associée (groupe d'hôtes, individuelle ou magasin de configuration)  
  
-   Compte d'administration identique au groupe des administrateurs d'applications associées (si vous sélectionnez cette propriété, le groupe des administrateurs d'applications associées est utilisé comme compte d'administrateurs de l'application pour cette application associée).  
  
## <a name="affiliate-application-properties"></a>Propriétés des applications associées  
 Le tableau suivant répertorie les propriétés dont vous avez besoin pour définir chaque application associée que vous créez.  
  
|Propriété| Description|  
|--------------|-----------------|  
|Nom de l'application|Nom de l'application associée. Une fois l'application associée créée, cette propriété ne peut plus être modifiée|  
| Description|Brève description de l'application associée|  
|Contact|Contact principal auquel les utilisateurs peuvent recourir pour cette application associée (il peut s'agir d'une adresse de messagerie).|  
|appUserAccount|Groupe Windows contenant les comptes d'utilisateur des utilisateurs finaux qui utiliseront l'application associée|  
|appAdminAccount|Groupe Windows contenant les comptes d'administrateur qui gèreront cette application associée. **Remarque :** vous n’avez pas besoin de définir cette propriété si vous définissez adminAccountSame sur Oui.|  
  
|Indicateur d'application| Description|  
|----------------------|-----------------|  
|enableApp|État de l'application associée.|  
|groupApp|Détermine si cette application utilise un mappage de groupe (Oui) ou des mappages individuels (Non).<br /><br /> Une fois l'application créée, cette propriété ne peut plus être modifiée.|  
|configStoreApp|Détermine si cette application associée est une application de type Magasin de configuration (Oui).<br /><br /> Une fois l'application créée, cette propriété ne peut plus être modifiée.|  
|hostInitiatedSSO|Cette case à cocher doit être activée s'il s'agit d'une application SSO initiée par l'hôte. Valeur par défaut est non.|  
|windowsInitiatedSSO|Cette case à cocher doit être activée s'il s'agit d'une application SSO initiée par Windows. La valeur par défaut est Oui.|  
|validatePassword|Cette option s'applique uniquement aux applications SSO initiées par l'hôte. Quand l'application tente d'extraire les informations d'identification, elle doit fournir le mot de passe inscrit dans la base de données SSO dont les services SSO se servent pour la validation. La valeur par défaut est Oui.|  
|disableCredCache|Le serveur d’authentification unique stocke les informations d’identification dans un cache pour accélérer l’accès. Valeur par défaut est non.|  
|allowTickets|Indiquer si le système de l'authentification unique utilise des tickets pour cette application associée.<br /><br /> **Sécurité** vous devez être un administrateur SSO peut définir cet indicateur.|  
|validateTickets|Indiquer si le système de l'authentification unique valide les tickets lors de leur échange.<br /><br /> **Sécurité** vous devez être un administrateur SSO peut définir cet indicateur.|  
|appTicketTimeOut|Spécifier un délai d'attente du ticket propre à l'application associée. Cela ne peut être défini que lors de la mise à jour d'une application associée et non lors de sa création.<br /><br /> Si la création de tickets est activée pour cette application et que cette propriété n’est pas le cas, le délai d’attente spécifié au niveau du système d’authentification unique (Global) niveau est utilisé.<br /><br /> **Sécurité** vous devez être un administrateur SSO peut définir cet indicateur.|  
|timeoutTickets|Déterminer si les tickets disposent d'un délai d'utilisation limité. La valeur par défaut est Oui.<br /><br /> **Sécurité** sauf s’il est nécessaire, ne désactivez pas les délais d’attente du ticket (n°).<br /><br /> **Sécurité** vous devez être un administrateur SSO peut définir cet indicateur.|  
|allowLocalAccounts|Détermine si l'utilisation des comptes et des groupes locaux est autorisée dans le système de l'authentification unique. Dans les scénarios impliquant un seul ordinateur, vous pouvez uniquement configurer cet indicateur sur Oui.|  
|adminAccountSame|Détermine si le groupe des administrateurs d'applications associées à SSO doit être utilisé comme groupe d'administrateurs de l'application.<br /><br /> Une fois l'application créée, cette propriété ne peut plus être modifiée.<br /><br /> **Sécurité** vous devez être un administrateur SSO ou administrateur d’applications associées pour définir cet indicateur.|  
  
|Champs de l'application| Description| Description|  
|------------------------|-----------------|-----------------|  
|Champ [0]|\<*informations d’identification*\>: / Unmasked masqués|Détermine le type d'informations d'identification (ID utilisateur, mot de passe, carte à puce) que les utilisateurs finaux doivent fournir pour se connecter à l'application associée, et si ces informations sont masquées (caractères saisis par l'utilisateur non affichés à l'écran) ou non.<br /><br /> Vous pouvez entrer autant de champs qu'il y a d'informations d'identification pour cette application associée. Cependant, le premier champ est obligatoirement l'ID utilisateur.<br /><br /> Une fois l'application créée, cette propriété ne peut plus être modifiée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)