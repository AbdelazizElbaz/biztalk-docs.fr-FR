---
title: "Sécurité entre Oracle E-Business Suite et de la carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f5f8ed-48d5-4420-9fdb-0a6860b95ac4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ceac01c8d495374470bf2a78912908338611180
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-oracle-e-business-suite-and-the-adapter"></a>Sécurité entre Oracle E-Business Suite et de la carte
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne fournit aucune prise en charge pour aider à sécuriser la communication entre elle et la base de données Oracle. Vous devez fournir un mécanisme de sécurité pour garantir des niveaux d’autorisation, d’authentification, de confidentialité des données et de l’intégrité des données pour les échanges de données entre l’adaptateur et la base de données Oracle.  
  
 Un mécanisme possible pour aider à fournir davantage de sécurité sur le réseau est la sécurité du protocole Internet (IPsec). IPsec est une infrastructure de normes ouvertes pour la protection des communications sur des réseaux IP (Internet Protocol). Pour plus d’informations sur IPsec et à l’aide d’IPsec avec les produits Microsoft, consultez l’article Microsoft TechNet « IPsec » à [http://go.microsoft.com/fwlink/?LinkID=196851](http://go.microsoft.com/fwlink/?LinkID=196851).  
  
 Toutefois, en l’absence de mécanismes de sécurité tels que IPsec, l’administrateur doit configurer le chiffrement de données natif Oracle et l’intégrité pour assurer les échanges de données sécurisée entre le client de carte et Oracle E-Business Suite.  
  
 Vous devez fournir les informations d’identification de mot de passe de nom utilisateur pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise ces informations d’identification pour authentifier l’utilisateur sur la base de données Oracle lorsqu’il ouvre une connexion. Ces informations d’identification fournissent un niveau d’autorisation sur la base de données Oracle pour la connexion.  
  
> [!NOTE]
>  Les informations d’identification utilisées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour établir une connexion sur la base de données Oracle ne fournissent pas d’authentification au niveau du message ou au niveau du transport ou autorisation pour les données transitent par le réseau. Ils sont uniquement utilisés pour ouvrir une connexion et d’authentifier l’utilisateur à la base de données Oracle.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] fournit un certain nombre de méthodes par le biais duquel vous pouvez fournir ces informations d’identification. Pour plus d’informations sur la façon de fournir des informations d’identification Oracle dans les solutions BizTalk en toute sécurité, consultez [sécurité avec l’adaptateur Oracle E-Business Suite et BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md). Pour plus d’informations sur la façon de fournir des informations d’identification de la base de données Oracle dans les solutions de programmation en toute sécurité, consultez [considérations de sécurité pour les adaptateurs](../../core/security-considerations-for-adapters.md).  
  
## <a name="managing-audit-logs"></a>Gestion des journaux d’Audit  
 Journaux d’audit permettent de stocker des informations sur les actions effectuées par les différents clients sur votre logiciel d’entreprise et permet de surveillance de l’utilisation et le suivi du problème. Toutefois, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne fournissant pas de méthode pour gérer les journaux d’audit pour les actions effectuées par les clients de la carte dans Oracle E-Business Suite. Cela peut constituer une menace de sécurité que les clients de l’adaptateur peuvent désolidariser par les actions effectuées par ces derniers dans Oracle E-Business Suite. Pour résoudre ce problème, vous devez activer le traçage dans Oracle pour se connecter les actions effectuées par les clients de la carte dans Oracle E-Business Suite. Pour plus d’informations sur la façon dont vous pouvez configurer Oracle les pistes d’audit, consultez le livre blanc « Oracle – Oracle E-Business Suite processus » [http://go.microsoft.com/fwlink/?LinkId=136388](http://go.microsoft.com/fwlink/?LinkId=136388).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications Oracle eBusiness Suite](secure-your-oracle-ebs-applications.md)  
 [Meilleures pratiques pour sécuriser l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)