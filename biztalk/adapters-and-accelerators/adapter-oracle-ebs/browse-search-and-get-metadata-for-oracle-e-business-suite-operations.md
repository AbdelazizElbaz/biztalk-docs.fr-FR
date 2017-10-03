---
title: "Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05a0656c-84d0-4f25-9571-90a9df587b8c
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a26b13ddef6efe9214e7d889d5d8e02d2f1505cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-metadata-for-oracle-e-business-suite-operations"></a>Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite
Cette section fournit des informations sur l’utilisation de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] et [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. À l’aide de ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants, vous pouvez :  
  
-   Rechercher des opérations récupérer des métadonnées.  
  
-   Rechercher des opérations récupérer des métadonnées.  
  
-   Ajouter des schémas de message pour les opérations sélectionnées et les fichiers de configuration de liaison pour le port un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] de projet lorsque vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
-   Ajouter une classe de client WCF ou un contrat de service WCF (interface) pour les opérations sélectionnées et un fichier de configuration (app.config) à un projet de programmation non-BizTalk en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## <a name="how-is-the-metadata-categorized"></a>Quelle est la catégorie de métadonnées ?  
 Le [!INCLUDE[consumeadapterservshort_md](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] offre trois vues différentes des artefacts disponibles dans le serveur Oracle E-Business Suite, vous vous connectez à :**vue basée sur l’Application**, **vue artefact**et le **basée sur un schéma de vue**. Pourquoi devez-vous trois modes différents pour le même ensemble d’artefacts ? Le tableau suivant répertorie les raisons pour lesquelles vous devez utilisent une vue spécifique.  
  
|Affichage|Lorsque vous l’utilisez|  
|----------|------------------------|  
|**Vue basée sur l’application**|Cette vue est classée par les noms d’applications Oracle E-Business Suite. Utilisez cette vue lorsque vous savez quelle application contienne les artefacts que vous souhaitez utiliser.|  
|**Vue basée sur un artefact**|Cette vue est classée par les artefacts d’Oracle E-Business Suite. Utilisez cette vue lorsque vous savez quels artefact Oracle E-Business Suite, vous souhaitez utiliser, mais vous n’êtes pas sûr quelle application auquel appartient l’artefact. À l’aide de cette vue, vous pouvez rechercher un artefact spécifique pour toutes les applications d’Oracle E-Business Suite.<br /><br /> La vue basée sur un artefact répertorie également les artefacts dans la base de données Oracle sous-jacentes telles que les API PL-SQL, les tables, vues, fonctions et procédures. Ces artefacts sont également dans des sous-catégories basés sur le schéma qu'auquel ils appartiennent. Par conséquent, une autre utilisation de la vue basée sur un artefact consiste à utiliser des artefacts qui appartiennent à votre schéma, ainsi que les artefacts qui appartiennent à d’autres schémas. Cette vue vous permet également de rechercher des artefacts dans tous les schémas.|  
|**Vue schéma**|Cette vue est classée par les schémas disponibles dans la base de données Oracle. Utilisez cette vue lorsque vous savez quel schéma a les artefacts que vous souhaitez utiliser. Dans cette vue, les artefacts que classé API PL-SQL, des procédures, fonctions, tables et vues.|  
  
 Pour plus d’informations sur la façon dont sont classés les artefacts d’Oracle E-Business Suite, consultez [se connecter à Oracle E-Business Suite dans Visual Studio à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md) organisant les artefacts dans une autre raison clée modes d’affichage est la facilité pour rechercher les artefacts. Pour plus d’informations sur la façon dont vous pouvez rechercher des artefacts, consultez [recherche pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md).  
  
> [!IMPORTANT]
>  Les nœuds s’affichent en fonction de l’URI que vous spécifiez lors de l’établissement d’une connexion de connexion. Si vous spécifiez des informations d’identification qui n’ont pas d’autorisations sur les artefacts d’Oracle E-Business Suite, vous ne pouvez pas utiliser les artefacts dans le **vue basée sur l’Application**. En outre, le **vue basée sur un artefact** ne répertorie pas les artefacts appartenant à Oracle E-Business Suite.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)