---
title: "Sécurité entre le serveur SQL Server et l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b0fd11-6753-4f52-9be7-3b6fa330fb8b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8673aee316a8a2ef83011ab3dd85016a99df1162
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-sql-server-and-the-adapter"></a>Sécurité entre le serveur SQL Server et de la carte
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est compatible avec les méthodes standards, telles que l’authentification unique et IPSEC permettent de sécuriser les échanges de données avec le serveur de base de données. Les échanges de données non sécurisée peuvent exposer des données pour les acteurs non autorisés. Pour plus d’informations sur les problèmes de sécurité avec SQL Server, consultez [considérations de sécurité pour SQL Server](http://go.microsoft.com/fwlink/p/?LinkId=196954) dans la documentation de SQL.  
  
 Vous pouvez améliorer la sécurité des échanges de données à l’aide de sécurité du protocole Internet (IPsec). IPsec est une infrastructure de normes ouvertes pour la protection des communications sur des réseaux IP (Internet Protocol). Avec IPSec, toutes les données échangent entre le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] et SQL server sur le réseau est chiffré, ce qui complique les acteurs non autorisés à utiliser les données. Pour plus d’informations sur IPsec et à l’aide d’IPsec avec les produits Microsoft, consultez l’article Microsoft TechNet [IPsec](http://go.microsoft.com/fwlink/p/?LinkId=196955).  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge l’authentification unique et la sécurité intégrée pour l’authentification sur les connexions qu’il établit avec la base de données. Avec l’authentification unique, les informations d’identification sont chiffrées et stockées dans le Registre. Le système utilise ces informations d’identification pour déterminer l’accès au lieu de demander l’utilisateur à entrer les où ils peuvent être détectés par les acteurs non autorisés. La sécurité intégrée utilise les informations d’identification de l’utilisateur connecté pour accéder au serveur SQL. Cela évite également aux utilisateurs d’entrer des informations d’identification. L’administrateur de base de données doit configurer SQL pour accepter les informations d’identification des utilisateurs pour la sécurité intégrée fonctionner correctement.  
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)