---
title: "Sécuriser vos applications SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b182593-fcca-4ebc-a2fd-7684b84cfb15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d631bc3ad87e9a8ec8ac51850b7dbe1eb244c140
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-sql-applications"></a>Sécuriser vos applications SQL
## <a name="overview"></a>Vue d'ensemble
Bases de données SQL Server contiennent souvent des informations sensibles telles que les détails du compte client. Les applications qui utilisent le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission. Sécurité et protection des données sont généralement considérées dans les termes suivants :  
  
-   *Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.  
  
-   *Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.  
  
-   *La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.  
  
-   *L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.  
  
 Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. L’adaptateur utilise ces informations d’identification d’ouverture de connexions dans le système SQL. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’autorise pas les informations d’identification doivent être fournis dans l’URI de connexion. Cela empêche les informations d’identification à partir de la mise en route exposées par inadvertance. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fournit deux autres méthodes pour fournir ces informations d’identification de manière plus sécurisée :  
  
 Sécurité intégrée. Dans ce cas, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] informations d’identification. Vous devez configurer le serveur SQL server pour accepter ces informations d’identification pour cette méthode fonctionne.  
  
 Enterprise Single Sign-on (SSO). Pour plus d’informations sur l’utilisation de l’authentification unique, consultez [sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) .  
  
 Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Sécurité entre le serveur SQL Server et de la carte](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)
  
-   [Sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) 
  
-   [Programmation sécurisée avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)
  
-   [Meilleures pratiques](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)