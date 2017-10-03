---
title: Architecture de programmation de synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679edbf1-fb08-4472-b366-3e1d361b20e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb68af3624b19a5a5385902d6a0131cfe28acb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="password-sync-programming-architecture"></a>Architecture de programmation de synchronisation de mot de passe
Un adaptateur de synchronisation de mot de passe utilise un modèle d’extraction pour interagir avec le reste du système Enterprise Single Sign-On : autrement dit, l’adaptateur reçoit activement les modifications de mot de passe à partir du service d’entreprise Sign-On (ENTSSO) ainsi que le système non-Windows. De même, l'adaptateur transmet les modifications de mot de passe reçues d'un système à l'autre. Avec ce modèle, votre adaptateur interagit avec trois composants architecturaux : l’architecture ENTSSO, le composant d’assistance de la synchronisation de mot de passe (PS) et un système non-Windows spécifié.  
  
## <a name="enterprise-single-sign-on-architecture"></a>Architecture de l'authentification unique de l'entreprise  
 ENTSSO est le service qui met en œuvre la technologie d'authentification unique de l'entreprise et s'exécute en tant que service local sur le même système que votre adaptateur. La communication entre l'adaptateur et ENTSSO est donc toujours locale. En revanche, chaque adaptateur de synchronisation de mot de passe s'exécute dans un processus séparé du service ENTSSO.  
  
 ENTSSO utilise le magasin de configuration pour stocker les informations de configuration des adaptateurs. Le compte des utilisateurs de l'application d'une application de magasin de configuration correspond au compte d'accès. Lorsqu'un adaptateur appelle ENTSSO, ENTSSO vérifie s'il se trouve dans le compte d'accès configuré à son intention. Le compte d'accès doit être un compte de groupe (local ou de domaine).  
  
 ENTSSO stockant des informations à propos d'un adaptateur, celui-ci peut s'identifier auprès d'ENTSSO par son nom d'adaptateur. Le nom d'adaptateur correspond au nom de l'application du magasin de configuration et à l'identificateur de magasin de configuration utilisé pour stocker les propriétés de l'adaptateur. Il suffit aux adaptateurs de connaître leur nom d'adaptateur pour accéder aux informations de configuration et s'identifier correctement auprès du système ENTSSO à l'exécution.  
  
## <a name="password-sync-helper"></a>Programme d'aide à la synchronisation des mots de passe  
 Le Programme d'aide à la synchronisation des mots de passe est un composant COM fourni par ENTSSO. Il s'exécute de façon in-process avec l'adaptateur de synchronisation de mot de passe et expose ISSOPSWrapper. Votre adaptateur peut appeler l'une ou l'autre interface pour communiquer avec le service ENTSSO. Le Programme d'aide à la synchronisation des mots de passe transmet les communications vers et à partir d'ENTSSO à l'aide d'un LRPC (Lightweight Remote Procedure Call) chiffré. Bien que les communications aient principalement pour objet la mise à jour de mots de passe, vous pouvez aussi utiliser les interfaces pour transmettre d'autres types de notifications entre l'adaptateur et ENTSSO. Le Programme d'aide à la synchronisation des mots de passe étant exécuté en tant que valeur singleton par processus, plusieurs adaptateurs peuvent appeler le même objet de Programme d'aide à la synchronisation des mots de passe à partir du même processus d'adaptateur. Pour plus d’informations sur l’utilisation d’assistance de PS par programme, consultez [synchronisation des mots de passe](../core/synchronizing-passwords.md).  
  
## <a name="non-windows-system"></a>Système non-Windows  
 Le système non-Windows est l'ordinateur distant avec lequel votre adaptateur interagit. C'est vous qui décidez de la manière dont vous voulez interagir avec le système non-Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateurs de synchronisation de mot de passe](../core/password-sync-adapters.md)