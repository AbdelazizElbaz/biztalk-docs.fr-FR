---
title: "Configurer le client Oracle pour l’adaptateur de E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842b6ecc-5334-4cc0-af10-baa7f692ad23
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ada64bf6f54c95f3d6e1c8f968a506476dbbc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-oracle-client-for-the-e-business-suite-adapter"></a>Configurer le client Oracle pour l’adaptateur de E-Business Suite
> [!IMPORTANT]
>  Cette rubrique s’applique uniquement si vous utilisez tnsnames.ora pour se connecter à la base de données Oracle.  
  
 Pour établir une connexion à la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], l’adaptateur se connecte à la base de données Oracle sous-jacent via le client Oracle installé sur votre ordinateur. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] transmet le nom de service réseau que vous spécifiez dans l’URI de connexion pour le client Oracle pour établir une connexion à Oracle E-Business Suite. Le nom de service réseau est un alias que le client Oracle utilise pour acquérir des informations de connexion pour le service de base de données Oracle cible.  
  
 Le client Oracle soit résolu nom de service réseau en fonction de la méthode d’affectation de noms qu’il est configuré pour utiliser. Vous utilisez Oracle Net Configuration Assistant pour configurer les méthodes d’affectation de noms à utiliser par le client Oracle. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la méthode d’affectation de noms locale pour la connexion à Oracle E-Business Suite. Cette méthode utilise un fichier local, tnsnames.ora, pour résoudre le nom de service réseau.  
  
 Le fichier tnsnames.ora associe les noms de service réseau avec connexion descripteurs qui contiennent les informations que le client Oracle a besoin pour établir une connexion à un service de base de données Oracle spécifique (instance). Voici un exemple d’entrée à partir de tnsnames.ora.  
  
```  
ADAPTER =  
  (DESCRIPTION =  
    (ADDRESS_LIST =  
      (ADDRESS = (PROTOCOL = TCP)(HOST = yourOracleServer)(PORT = 1521))  
    )  
    (CONNECT_DATA =  
      (SERVICE_NAME = yourOracleDatabaseServiceName)  
    )  
  )  
```  
  
 Dans cet exemple d’entrée, la carte est le nom de service réseau. Le descripteur de connexion spécifie les informations d’adresse et le nom du service du service de base de données Oracle associé à l’adaptateur. Vous pouvez utiliser Oracle Net Configuration Assistant pour créer et configurer des noms de service réseau dans tnsnames.ora. Après avoir configuré le nom de service réseau, vous pouvez les spécifier dans l’URI de connexion comme dans l’exemple suivant.  
  
```  
oracleebs://ADAPTER  
```  
  
 Pour plus d’informations sur l’utilisation d’Oracle Net Configuration Assistant et tnsnames.ora, consultez Oracle Net Services Guide de l’administrateur de base de données. Contactez l’administrateur de base de données sur les détails de configuration pour votre installation spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une connexion à Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)