---
title: "Sécurité entre la base de données Oracle et de la carte | Documents Microsoft"
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
- credentials, supplying user name password
- authentication
- IPsec
ms.assetid: 09d40a05-3678-4002-9e08-2f97c2d5c686
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb27f87bceaba6039588ddcad6b5dcb2d3ce79ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-oracle-database-and-the-adapter"></a>Sécurité entre la base de données Oracle et de la carte
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne fournit aucune prise en charge pour aider à sécuriser la communication entre elle et la base de données Oracle. Vous devez fournir un mécanisme de sécurité pour garantir des niveaux d’autorisation, d’authentification, de confidentialité des données et de l’intégrité des données pour les échanges de données entre l’adaptateur et la base de données Oracle.  
  
 Un mécanisme possible pour aider à fournir davantage de sécurité sur le réseau est la sécurité du protocole Internet (IPsec). IPsec est une infrastructure de normes ouvertes pour la protection des communications sur des réseaux IP (Internet Protocol). Pour plus d’informations sur IPsec et à l’aide d’IPsec avec les produits Microsoft, consultez l’article Microsoft TechNet « IPsec » à [http://go.microsoft.com/fwlink/?LinkId=196851](http://go.microsoft.com/fwlink/?LinkId=196851).  
  
 Toutefois, en l’absence de mécanismes de sécurité tels que IPsec, l’administrateur doit configurer le chiffrement de données natif Oracle et l’intégrité pour assurer les échanges de données sécurisée entre le client de carte et de la base de données Oracle. Pour plus d’informations sur la configuration de chiffrement de données Oracle natif et l’intégrité, consultez [http://go.microsoft.com/fwlink/p/?LinkId=140032](http://go.microsoft.com/fwlink/p/?LinkId=140032).  
  
 Vous devez fournir les informations d’identification de mot de passe de nom utilisateur pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise ces informations d’identification pour authentifier l’utilisateur sur la base de données Oracle lorsqu’il ouvre une connexion. Ces informations d’identification fournissent un niveau d’autorisation sur la base de données Oracle pour la connexion.  
  
> [!NOTE]
>  Les informations d’identification utilisées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour établir une connexion sur la base de données Oracle ne fournissent pas d’authentification au niveau du message ou au niveau du transport ou autorisation pour les données transitent par le réseau. Ils sont uniquement utilisés pour ouvrir une connexion et d’authentifier l’utilisateur à la base de données Oracle.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fournit un certain nombre de méthodes par le biais duquel vous pouvez fournir ces informations d’identification. Pour plus d’informations sur la façon de fournir des informations d’identification Oracle dans les solutions BizTalk en toute sécurité, consultez [sécurité avec l’adaptateur de base de données Oracle et Biztalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md). Pour plus d’informations sur la façon de fournir des informations d’identification de la base de données Oracle dans les solutions de programmation en toute sécurité, consultez [sécurisée avec l’adaptateur de base de données Oracle de programmation](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md).  
  
## <a name="managing-audit-logs"></a>Gestion des journaux d’Audit  
 Journaux d’audit permettent de stocker des informations sur les actions effectuées par les différents clients sur votre logiciel d’entreprise et permet de surveillance de l’utilisation et le suivi du problème. Toutefois, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne fournissant pas de méthode pour gérer les journaux d’audit pour les actions effectuées par les clients de la carte sur la base de données Oracle. Cela peut constituer une menace de sécurité que les clients de l’adaptateur peuvent désolidariser par les actions effectuées par ces derniers sur la base de données Oracle. Pour résoudre ce problème, vous devez activer le traçage dans Oracle pour se connecter les actions effectuées par les clients de la carte sur la base de données Oracle.  
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)   
[Meilleures pratiques](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)