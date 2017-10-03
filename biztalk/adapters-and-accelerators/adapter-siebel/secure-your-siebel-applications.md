---
title: "Sécuriser vos applications Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security and protection
- data protection
ms.assetid: 8977cbd3-0025-48d4-8203-8e9e72ea7d26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3b597120de91b6a09fdc26b90a2cb357cdc7dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-siebel-applications"></a>Sécuriser vos applications Siebel
Le système Siebel contient souvent des informations sensibles telles que les détails du compte client. Les applications qui utilisent le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission. Sécurité et protection des données sont généralement considérées dans les termes suivants :  
  
-   *Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.  
  
-   *Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.  
  
-   *La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.  
  
-   *L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.  
  
 Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. L’adaptateur utilise ces informations d’identification d’ouverture de connexions au système Siebel. Ces informations d’identification peuvent être fournies dans la connexion URI ; Toutefois, étant donné que le nom d’utilisateur et un mot de passe sont texte clair, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit d’autres méthodes que vous pouvez utiliser pour fournir ces informations d’identification de manière plus sécurisée.  
  
 Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Sécurité entre le système Siebel et de la carte](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
-   [Sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
-   [Programmation sécurisée avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md)
  
-   [Meilleures pratiques pour sécuriser l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)