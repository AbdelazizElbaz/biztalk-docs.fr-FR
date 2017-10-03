---
title: "Exemple d’Architecture : BizTalk Server de Base | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- IPSec
- BizTalk Server, examples
- security, examples
- security, architecture
- IPSec, about IPSec
- BizTalk Server, architecture
- architecture, security
ms.assetid: 7ccc1ef3-670f-423f-b6ca-3d56b9bbeabf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea815c0165f58c28cea8ce7cae35fd6ed7437323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-base-biztalk-server"></a>Exemple d'architecture : BizTalk Server de base
Cette rubrique présente un exemple d'architecture de base. Elle décrit les composants indépendants d'un adaptateur dans un déploiement BizTalk Server. Il est recommandé que tout déploiement BizTalk Server dispose au moins de trois composants.  
  
 La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server de base. Ces composants sont présents dans toutes les architectures BizTalk Server spécifiques aux adaptateurs que nous avons abordées dans les sections précédentes.  
  
 **Figure 1 architecture de Base composants**  
  
 ![Composants de l’architecture de base](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")  
  
 Cet exemple d'architecture contient les éléments présentés dans les sections suivantes.  
  
## <a name="perimeter-networkinternet"></a>Network―internet de périmètre  
  
-   Ce réseau de périmètre (également appelé DMZ, zone démilitarisée et sous-réseau filtré) contient des serveurs qui fournissent des services Internet. Ce domaine ne comprend pas de serveurs BizTalk Server, d'emplacements de réception BizTalk ni de serveurs d'authentification unique de l'entreprise (SSO).  
  
## <a name="perimeter-networkintranet"></a>Réseau de périmètre ― intranet  
 Ce réseau de périmètre contient des serveurs qui fournissent des services intranet. Il fournit également une couche de sécurité supplémentaire entre votre intranet (par exemple, un réseau d'entreprise) et les serveurs exécutant l'application. À l'instar du réseau de périmètre Internet, le réseau de périmètre intranet ne contient pas de serveurs BizTalk Server, d'emplacements de réception BizTalk ni de serveurs d'authentification unique de l'entreprise.  
  
## <a name="e-business-domain"></a>Domaine E-Business  
 Ce domaine contient toutes les infrastructures et applications utilisées par votre implémentation BizTalk Server. Les serveurs de ce domaine sont les suivants :  
  
-   **BizTalk Server.** ce serveur dispose de l'installation du moteur d'exécution de BizTalk Server ainsi que des instances de plusieurs hôtes BizTalk. Le nombre de serveurs BizTalk Server présents dans un environnement dépend du type d'hôtes qu'ils exécutent et des exigences en matière de performances. Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.  
  
-   **Serveur de secret principal.** ce serveur correspond au serveur de secret principal de l'authentification unique de l'entreprise. Il contient le secret principal (clé de chiffrement) que le système SSO utilise pour chiffrer les données dans la base de données SSO.  
  
-   **SQL Server.** ce serveur contient les bases de données BizTalk.  
  
    > [!IMPORTANT]
    >  Pour bénéficier d'une protection par basculement, il est recommandé de mettre en cluster chaque base de données BizTalk. Pour plus d’informations sur le clustering de basculement Microsoft SQL Server, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216).  
  
    > [!NOTE]
    >  Selon vos exigences en matière de performances, vous devrez peut-être répartir les bases de données BizTalk sur plusieurs ordinateurs exécutant SQL Server.  
  
-   **Contrôleur de domaine.** ce serveur héberge le domaine Active Directory E-Business. Il contient les informations relatives aux groupes et comptes individuels qui requièrent l'accès à BizTalk Server.  
  
-   **Outils d’administration.** Un des serveurs présents dans ce domaine héberge les outils d'administration : la console Administration de BizTalk et l'utilitaire d'administration de l'authentification unique de l'entreprise (SSO).  
  
## <a name="firewalls-and-domains"></a>Pare-feu et domaines  
 Dans la figure 1, le serveur Forefront Threat Management Gateway (TMG) 2010 agit en tant que pare-feu logiciel pour aider à protéger et à contenir chacun de ces domaines. En outre, le domaine E-Business a son propre contrôleur de domaine, et ce domaine n'en approuve aucun autre. Pour plus d’informations sur la façon de configurer un pare-feu pour les domaines et approbations, consultez le site Web de support technique et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).  
  
 L'exemple d'architecture dispose de deux pare-feu :  
  
-   **Pare-feu 1.** Ce pare-feu dispose de trois interfaces réseau : il achemine le trafic à partir d'Internet, de l'intranet et des réseaux de périmètre.  
  
-   **Pare-feu 2.** Ce pare-feu dispose de deux interfaces réseau : il achemine le trafic à partir des réseaux de périmètre (Internet et intranet) et du domaine E-Business.  
  
 Les ordinateurs situés dans les réseaux de périmètre ne sont pas membres d'un domaine et ne communiquent pas entre eux.  
  
## <a name="ipsec"></a>IPsec  
 Il est recommandé d'utiliser la sécurité du protocole Internet (IPSec) pour sécuriser les communications entre les serveurs présents dans le domaine E-Business. Les règles IPsec sont les suivantes :  
  
-   Autoriser le trafic authentifié entre un serveur BizTalk Server et le contrôleur de domaine.  
  
-   Autoriser le trafic authentifié entre un serveur BizTalk Server et le serveur hébergeant les outils d'administration.  
  
-   Autoriser le trafic authentifié entre un serveur BizTalk Server et le serveur de secret principal.  
  
-   Autoriser le trafic authentifié entre un serveur BizTalk Server et un serveur SQL Server.  
  
-   Autoriser le trafic authentifié entre le serveur de secret principal et le contrôleur de domaine.  
  
-   Autoriser le trafic authentifié entre le serveur de secret principal et un serveur BizTalk Server (hôtes isolé, de traitement, In-process et de suivi).  
  
-   Autoriser le trafic authentifié entre le serveur de secret principal et un serveur SQL Server (bases de données SSO).  
  
-   Autoriser le trafic authentifié entre le contrôleur de domaine et tous les serveurs du domaine.  
  
-   Autoriser le trafic authentifié entre le serveur hébergeant les outils d'administration et tous les serveurs du domaine.  
  
 Si d'autres applications du domaine ne requièrent pas l'accès à un serveur BizTalk Server, SQL Server, de secret principal ou à un serveur hébergeant les outils d'administration, il est conseillé de bloquer le trafic entre ces applications et les serveurs appropriés.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la sécurité](../core/planning-for-security.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)