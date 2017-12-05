---
title: "Limitation des attaques de déni de Service des attaques par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPSec, message protection
- messages, size
- security, configuring
- Authentication Required property
- security, Internet Information Services (IIS) Lockdown Tool
- security, Denial of Service attacks
- discretionary access control lists (DACLs)
- IPSec, data protection
- Internet Information Services (IIS) Lockdown Tool
- Denial of Service attacks
ms.assetid: f39c0d0a-b890-4c48-874d-5cafbc71473c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a02e3eddcd43acf67e8e928e1a8f172c0019c616
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mitigating-denial-of-service-attacks"></a>Limitation des attaques de déni de Service des attaques par
Il est recommandé d'utiliser les techniques de prévention suivantes pour protéger les services et les serveurs BizTalk contre les attaques par déni de service. Vous devez choisir les techniques adaptées à votre environnement.  
  
-   **Utilisez la propriété authentification requise dans le port de réception.** Par défaut, BizTalk envoie les messages qu'il reçoit vers la base de données MessageBox, même ceux provenant d'un tiers inconnu ou non résolu (invité). Pour réduire le risque d’une personne malveillante envoyer un grand nombre de messages à BizTalk Server et inonde (remplisse) la base de données MessageBox, vous pouvez utiliser la **authentification requise** propriété du port de réception pour recevoir uniquement messages qui proviennent de tiers que BizTalk Server connus. Vous pouvez soit abandonner les messages envoyés par un tiers inconnu, soit les suspendre. Pour plus d’informations sur la **authentification requise** propriété, consultez [authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md). Outre la **authentification requise** propriété, vous devez envisager l’utilisation d’un mécanisme externe tel que le filtrage de port de pare-feu ou de blocage pour vous protéger contre les attaques par déni de Service d’adresses IP.  
  
-   **Limiter la taille des messages reçus par BizTalk.** Par exemple, lorsque vous utilisez l’adaptateur de réception SOAP, vous pouvez éviter de recevoir des messages très volumineux en définissant l’attribut maxRequestLength dans le \<httpRuntime\> élément à une taille acceptable. Le \<httpRuntime\> élément est défini dans le fichier Machine.config, situé dans le \< *lecteur*\>:\\<*Windows répertoire*\>\Microsoft.NET\Framework\vX.X.XXXXX\CONFIG active. Pour plus d’informations sur \<httpRuntime\> élément, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkId=60948](http://go.microsoft.com/fwlink/?LinkId=60948).  
  
-   **Utilisation des listes DACL fort pour les emplacements de réception.** Il est recommandé d'utiliser des listes de contrôle d'accès discrétionnaire renforcées dans les emplacements de dépôt des emplacements de réception. Par exemple, vous devez utiliser des listes de contrôle d'accès discrétionnaire renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.  
  
-   **Utilisez IPSec.** Si vous n'utilisez aucun pare-feu logiciel ou matériel, utilisez le protocole IPSec (Internet Protocol security) pour protéger les messages et les données lorsque BizTalk Server les transfère entre deux serveurs. Pour plus d’informations sur IPSec, consultez le Center Download Microsoft à [http://go.microsoft.com/fwlink/?LinkId=60949](http://go.microsoft.com/fwlink/?LinkId=60949).  
  
## <a name="see-also"></a>Voir aussi  
 [Identifier les menaces potentielles](../core/identifying-potential-threats.md)   
 [Planification de la sécurité](../core/planning-for-security.md)