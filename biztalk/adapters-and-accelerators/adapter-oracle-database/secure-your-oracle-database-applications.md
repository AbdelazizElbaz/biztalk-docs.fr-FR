---
title: "Sécuriser vos applications de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter, security
- authorization
- data protection
- adapter, data protection
- authentication
- security
ms.assetid: c5f18b0a-1c8e-44c6-ba7e-470fa186f636
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8601463c02e32221c369023f05ed2fd3731bb4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-oracle-database-applications"></a>Sécuriser vos applications de base de données Oracle
## <a name="data-protection-and-security-overview"></a>Présentation de sécurité et protection des données
Une base de données contient souvent des informations sensibles telles que les détails du compte client. Les applications qui utilisent le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission. Sécurité et protection des données sont généralement considérées dans les termes suivants :  
  
-   *Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.  
  
-   *Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.  
  
-   *La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.  
  
-   *L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.  
  
 Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. L’adaptateur utilise ces informations d’identification d’ouverture de connexions à la base de données Oracle. Ces informations d’identification peuvent être fournies dans la connexion URI ; Toutefois, étant donné que le nom d’utilisateur et un mot de passe sont texte clair, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fournit d’autres méthodes que vous pouvez utiliser pour fournir ces informations d’identification de manière plus sécurisée.  
  
 Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Sécurité entre la base de données Oracle et de la carte](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [Sécurité avec l’adaptateur de base de données Oracle et BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [Programmation sécurisée avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [Meilleures pratiques](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)