---
title: Identifier les menaces potentielles | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- planning, security
- security, potential threats
- security, planning
ms.assetid: 1d70a0c1-6daf-47bb-af15-a4b35a7bafc2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d20f17ee3d1c4d1291de27ae73d18fed3e604fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="identifying-potential-threats"></a>Identifier les menaces potentielles
Vous pouvez utiliser le modèle STRIDE pour identifier des menaces potentielles pour votre déploiement de BizTalk Server. STRIDE est un acronyme formé à partir des catégories suivantes : *S*urpation d’identité, *T*ion des données, *R*épudiation, *I* divulgation d’informations, *D*éni de service et élévation de privilèges. Cette section fournit des exemples de menaces potentielles pour un environnement BizTalk Server, ainsi que les mécanismes pour les atténuer.  
  
 **Usurpation d’identité**  
  
-   Si vous enregistrez des mots de passe dans les fichiers de liaison, puis que vous enregistrez ces derniers, des utilisateurs non autorisés peuvent les lire et les utiliser pour se connecter aux serveurs BizTalk Server, et endommager ceux-ci. Vous ne devez pas enregistrer de mot de passe dans des fichiers de liaison, et vous devez utiliser des listes de contrôle d'accès discrétionnaire (DACL) pour limiter l'accès aux fichiers pouvant contenir des données sensibles.  
  
 **Falsification des données**  
  
-   Des utilisateurs malveillants peuvent intercepter des messages de partenaires à destination de BizTalk Server, et en modifier le contenu. Vous pouvez utiliser des signatures numériques pour empêcher les utilisateurs malveillants de falsifier des messages en transit.  
  
 **Répudiation**  
  
-   Vous devez assurer le suivi des messages que BizTalk envoie et reçoit. Vous pouvez utiliser des signatures numériques pour prouver que les messages échangés entre vous et vos partenaires proviennent de sources fiables.  
  
 **Divulgation d’informations**  
  
-   Des utilisateurs malveillants peuvent lire des communications en texte clair entre les serveurs BizTalk Server et Microsoft SQL Server™. Vous pouvez utiliser le protocole IPSec (Internet Protocol security) ou SSL (Secure Sockets Layer) pour sécuriser la communication entre les serveurs. Vous pouvez utiliser des pare-feu pour limiter l'accès à chaque serveur. Vous pouvez utiliser le chiffrement pour garantir la confidentialité des messages en transit.  
  
-   Des utilisateurs non autorisés peuvent accéder à des informations sur les partages et répertoires réseau. Vous pouvez utiliser des listes de contrôle d'accès discrétionnaire (DACL) renforcées pour limiter l'accès aux comptes qui utilisent les ressources.  
  
-   L'administrateur Windows d'un ordinateur exécutant une instance d'hôte BizTalk peut mener différents types d'attaques (par exemple, une divulgation d'informations ou un déni de service). Cependant, dans la plupart des cas, vous pouvez limiter ces attaques à l'hôte pris pour cible.  
  
 **Déni de service**  
  
-   Un utilisateur malveillant peut envoyer un grand nombre de messages vers BizTalk Server, ce qui peut empêcher BizTalk de recevoir des messages valides. Pour plus d’informations sur les techniques de prévention de cette menace, consultez [atténuation des attaques par déni de Service](../core/mitigating-denial-of-service-attacks.md).  
  
 **Élévation de privilèges**  
  
-   Les menaces d'élévation de privilèges se produisent généralement lorsqu'un code non approuvé est exécuté dans un environnement approuvé, ou lorsqu'un utilisateur malveillant exploite les défauts d'un logiciel ou d'une configuration. Vous devez vous assurer que les assemblys et les autres composants déployés dans votre environnement sont approuvés. Pour réduire les risques d'une attaque d'élévations de privilèges, vous devez utiliser des comptes dotés d'autorisations minimales, qui ne se chevauchent pas, et vous devez éviter d'utiliser les comptes d'administration pour les services et les opérations d'exécution. Vous devez également réduire le nombre de composants, d'applications et de services exécutés dans l'environnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Limitation des attaques de déni de Service des attaques par](../core/mitigating-denial-of-service-attacks.md)   
 [Recommandations de sécurité pour un déploiement BizTalk Server](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [Planification de la sécurité](../core/planning-for-security.md)