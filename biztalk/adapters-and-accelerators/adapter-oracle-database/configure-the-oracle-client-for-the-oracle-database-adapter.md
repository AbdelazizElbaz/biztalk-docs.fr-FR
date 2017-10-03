---
title: "Configurer le Client Oracle pour l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- net service name
- tnsnames.ora
- configuring, the Oracle client
- connect descriptor
- Oracle client, configuring
- Oracle Net Configuration Assistant
- Oracle Net Configuration Assistant, using the
ms.assetid: 2d4c0f20-b3a6-453f-a9b3-65fd5a38c020
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 209d5603a9f8ff8c09185093efb976afb6432d65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-oracle-client-for-the-oracle-database-adapter"></a>Configurer le Client Oracle pour l’adaptateur de base de données Oracle
> [!IMPORTANT]
>  Cette rubrique s’applique uniquement si vous utilisez tnsnames.ora pour se connecter à la base de données Oracle.  
  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] se connecte à la base de données Oracle par le biais du client Oracle installé sur votre ordinateur. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] transmet le nom de service réseau que vous spécifiez dans l’URI de connexion au client Oracle pour établir une connexion à la base de données Oracle. Le nom de service réseau est un alias que le client Oracle utilise pour acquérir des informations de connexion pour le service de base de données Oracle cible.  
  
 Le client Oracle soit résolu nom de service réseau en fonction de la méthode d’affectation de noms qu’il est configuré pour utiliser. Vous utilisez Oracle Net Configuration Assistant pour configurer les méthodes d’affectation de noms à utiliser par le client Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la méthode d’affectation de noms locale pour la connexion à la base de données Oracle. Cette méthode utilise un fichier local, tnsnames.ora, pour résoudre le nom de service réseau.  
  
 L’associe de fichier tnsnames.ora avec des noms de service réseau connecter descripteurs qui contiennent les informations que du client Oracle a besoin pour établir une connexion à un service de base de données Oracle spécifique (instance). Voici un exemple d’entrée à partir de tnsnames.ora.  
  
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
oracledb://ADAPTER  
```  
  
 Pour plus d’informations sur l’utilisation d’Oracle Net Configuration Assistant et tnsnames.ora, consultez Oracle Net Services Guide de l’administrateur de base de données. Contactez l’administrateur de base de données sur les détails de configuration pour votre installation spécifique.  
  
## <a name="see-also"></a>Voir aussi  
[Créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)