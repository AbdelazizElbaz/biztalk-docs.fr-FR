---
title: "Considérations sur l’installation de BizTalk Server sur un Cluster2 de serveur Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configure Your Server Wizard
- installing, Windows Server cluster
- BizTalk Server Configuration Wizard
- Windows Server cluster, warnings
- high availability, Windows Server cluster
- clustering, Windows Server cluster
- domain groups
- Windows Server cluster, Configure Your Server Wizard
- Network DTC access
- MSDTC
ms.assetid: 4daea7c6-7d26-440c-a2a0-fa018a25b2b3
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38bd34862efb0cd73e66a2c694abd26b823766db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-installing-biztalk-server-on-a-windows-server-cluster"></a>Considérations relatives à l'installation de BizTalk Server sur un cluster de serveurs Windows Server
Vous devez tenir compte de plusieurs éléments importants lors de l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un cluster de serveurs Windows Server. Cette rubrique répertorie ces éléments.  
  
## <a name="a-non-clustered-biztalk-host-instance-should-not-be-run-on-a-windows-server-cluster-where-the-enterprise-sso-service-is-clustered"></a>Une instance d'hôte BizTalk qui ne fait pas partie d'un cluster ne devrait pas s'exécuter sur un cluster Windows Server sur lequel le service d'authentification unique de l'entreprise est mis en cluster.  
 Il est conseillé de mettre en cluster le serveur de secret principal du système d'authentification unique de l'entreprise selon un modèle actif/passif afin de le doter de la haute disponibilité. Si une instance d'hôte BizTalk qui ne fait pas partie d'un cluster et une instance d'hôte mise en cluster du service d'authentification unique de l'entreprise s'exécutent sur le même nœud en cluster, l'instance d'hôte BizTalk échoue si le service d'authentification unique de l'entreprise mis en cluster est déplacé vers un autre nœud du cluster. Les hôtes BizTalk conservent une dépendance sur une instance service d'authentification unique de l'entreprise qui s'exécute localement. Par conséquent, si le service SSO est configuré en tant que ressource en cluster, tous les hôtes BizTalk en cours d’exécution sur les nœuds de cluster doit être configurés en tant que ressource en cluster dans le même groupe de clusters.  
  
## <a name="configure-the-microsoft-distributed-transaction-coordinator-msdtc-as-a-clustered-resource-before-installing-biztalk-server-on-a-cluster"></a>Configurez le service MSDTC (Microsoft Distributed Transaction Coordinator) en tant que ressource mise en cluster avant d'installer BizTalk Server sur un cluster.  
 Si vous envisagez d'installer BizTalk Server sur un cluster de serveurs Windows Server, vous devez d'abord mettre en cluster le service MSDTC.  
  
 Pour mettre en cluster MSDTC sur un cluster de basculement Windows Server 2008, suivez les étapes décrites dans [liste de vérification : création d’un MS DTC Resource dans un Cluster de basculement Windows Server 2008](http://go.microsoft.com/fwlink/?LinkID=129677)  
  
## <a name="network-dtc-access-must-be-enabled-on-all-biztalk-servers-and-on-the-sql-server-before-installing-or-configuring-biztalk-server"></a>Activez l'accès DTC réseau sur tous les serveurs BizTalk et sur le serveur SQL Server avant d'installer ou de configurer BizTalk Server.  
 Pour activer l’accès DTC réseau sur chaque nœud de cluster ainsi que sur le serveur SQL Server qui hébergera les bases de données BizTalk Server, suivez les étapes décrites dans [comment activer MSDTC sur un serveur Web](http://go.microsoft.com/fwlink/?LinkId=189701) (http://go.microsoft.com/fwlink/?LinkId=189701). L'accès DTC réseau doit être activé pour répondre aux besoins de prise en charge transactionnelle [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il est recommandé de redémarrer chaque serveur après avoir effectué toutes les opérations décrites par cet article de la Base de connaissances Microsoft.  
  
## <a name="you-must-manually-create-domain-groups-in-active-directory-before-you-configure-biztalk-server"></a>Créez manuellement des groupes de domaine dans Active Directory avant de configurer BizTalk Server.  
 Si vous installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur plusieurs ordinateurs, vous devez indiquer des groupes de domaine et des comptes d'utilisateur dans l'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous utilisez des groupes de domaine pour configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez créer manuellement les groupes avant de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].