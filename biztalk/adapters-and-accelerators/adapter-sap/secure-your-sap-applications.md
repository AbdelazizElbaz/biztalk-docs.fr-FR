---
title: "Sécuriser vos applications SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security and protection
ms.assetid: 9f0fb2a2-d6e2-4561-8472-c0bf682a4798
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f5fe75acf7b033d0f957c7742f52ba521bdde7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-sap-applications"></a>Sécuriser vos applications SAP
Le système SAP peut contenir des informations sensibles telles que les détails du compte client. Les applications qui utilisent le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission. Sécurité et protection des données sont généralement considérées dans les termes suivants :  
  
-   *Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.  
  
-   *Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.  
  
-   *La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.  
  
-   *L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.  
  
 Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Sécurité entre le système SAP et de l’adaptateur](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)
  
-   [Sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)
  
-   [Programmation sécurisée avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md)
  
-   [Meilleures pratiques pour sécuriser l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)