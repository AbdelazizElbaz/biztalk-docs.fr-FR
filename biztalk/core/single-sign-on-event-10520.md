---
title: "Single Sign-On : Événement 10520 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91662072-d87c-4290-8afb-2143143ee858
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9349452d99518f210237c5e8dd0f945d1f92aa46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10520"></a>Single Sign-On : Événement 10520
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10520|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_NO_SECRETS|  
|Texte du message|Aucun secret n'a été trouvé dans le Registre du serveur de secret principal. Utilisez les outils de configuration pour générer ou restaurer un secret principal.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'aucun secret n'a été trouvé dans le Registre du serveur de secret principal. Les secrets principaux de l'authentification unique sont stockés sous forme chiffrée dans le Registre du serveur de secret principal SSO. Deux secrets sont généralement conservés dans le Registre : le secret principal actuel et le secret principal précédent. Les secrets sont identifiés à l'aide d'un GUID (ID de secret principal). Si le secret principal spécifié est introuvable dans le Registre suite à une demande, ce code d'erreur est renvoyé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez une ou plusieurs des opérations suivantes :  
  
-   Vérifiez que le nom du serveur de secret principal est correct et tel que prévu.  
  
-   S'il est correct, vérifiez que le secret principal figure dans le Registre de ce serveur de secret principal. Le secret principal est situé sous HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS (cette clé est présente uniquement sur le serveur de secret principal SSO).  
  
-   Si cette clé est manquante, le secret principal n'est pas présent. Une ou plusieurs clés doivent figurer sous SSOSS sous forme de GUID qui contiennent les clés chiffrées. Si celles-ci ne sont pas présentes, le secret principal ne l'est pas non plus. Les secrets principaux sont identifiés à l'aide de GUID (ID de secret principal), aussi ceux-ci (s'ils sont présents) doivent correspondre à l'ID du secret principal demandé. Si les clés présentes sous forme de GUID ne correspondent pas à l'ID de secret principal demandé, il y a une confusion entre le secret principal dans le Registre et celui utilisé pour chiffrer les données dans la base de données SSO (SSODB). Dans ce cas, il peut être nécessaire de restaurer un autre secret principal. Il se peut également que la base de données SSODB ait été restaurée à partir d'une sauvegarde de niveau inférieur. Si le secret principal n'est pas présent, il peut être restauré à partir d'une sauvegarde à l'aide des outils de configuration de l'authentification unique (ligne de commande ou console MMC) ou un nouveau secret peut être généré. Notez qu'habituellement, vous générez un nouveau secret principal s'il s'agit d'une nouvelle installation et s'il n'y a pas de données chiffrées existantes dans la base de données SSO. Le secret principal est généré la première fois lors de la configuration initiale.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Serveur de secret principal](../core/master-secret-server.md)  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)  
  
-   [Configuration de l’authentification unique](../core/configuring-sso.md)