---
title: "Se connecter à la base de données Oracle à l’aide de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection string
- uniform resource identifier
- Oracle database, connecting to
- URI
- connection URI
ms.assetid: 5d5598e5-aba0-4c73-8e97-9156475b93c4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01b04a615d0b0b8cd83b9ed7516cd096b2c85a54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-database-using-the-adapter"></a>Se connecter à la base de données Oracle à l’aide de l’adaptateur
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] ODP.NET 11.1.0.7 pour se connecter à la base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exige que les clients de l’adaptateur fournir une chaîne de connexion, appelée la connexion identificateur URI (Uniform Resource), pour se connecter à la base de données Oracle. En interne, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] mappe l’URI vers une chaîne de connexion de base de données pour se connecter à la base de données Oracle. Avec un URI de connexion, les clients de carte peuvent spécifier des paramètres de connexion pour se connecter à un système externe.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux clients de l’adaptateur pour se connecter à la base de données Oracle dans les éléments suivants de deux manières :  
  
-   **À l’aide de tnsnames.ora**: l’URI fourni par le client de l’adaptateur de connexion contient uniquement le nom de service réseau spécifié dans le fichier tnsnames.ora. L’adaptateur extrait les paramètres de connexion comme nom de serveur, nom du service et numéro de port de l’entrée de nom de service réseau dans le fichier tnsnames.ora. Pour utiliser cette approche, l’ordinateur qui exécute le client Oracle doit être configuré pour inclure le nom de service réseau pour la base de données Oracle dans le fichier tnsnames.ora.  
  
    > [!IMPORTANT]
    >  En raison d’une limitation du Client Oracle, le **DataSourceName** paramètre (nom de service réseau) dans le [configurer l’URI de connexion pour la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-connection-uri-for-the-oracle-database-adapter.md) ne peut pas contenir plus de 39 caractères si vous effectuez les opérations dans une transaction. Par conséquent, assurez-vous que la valeur spécifiée pour le **DataSourceName** paramètre est inférieur ou égal à 39 caractères si vous allez effectuer les opérations dans une transaction.  
  
-   **Sans utiliser de tnsnames.ora**: l’URI fourni par les clients de l’adaptateur de connexion contient les paramètres de connexion comme nom de serveur, nom du service et numéro de port. Dans ce cas, le nom de service réseau dans le fichier tnsnames.ora ou le fichier tnsnames.ora réel lui-même, n’a pas besoin d’être présents sur l’ordinateur client. Cela est utile lorsque vous avez un grand nombre d’utilisateurs qui se connectent à la base de données Oracle dans votre organisation, et ajout/la mise à jour des serveurs ne mène pas à ajouter/mettre à jour manuellement les informations de connexion dans le fichier tnsnames.ora sur chaque ordinateur client.  
  
    > [!IMPORTANT]
    >  Ce mode de connectivité n’est pas pris en charge si vous effectuez des opérations dans une transaction. Il s’agit d’une limitation du Client Oracle.  
  
 Pour plus d’informations sur la connexion à la base de données Oracle, consultez [créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md).  
  
 Veillez à que respecter les consignes de sécurité lors de l’établissement d’une connexion avec la base de données Oracle. Pour plus d’informations sur les règles de sécurité, consultez [sécuriser vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md).  
  
## <a name="windows-authentication"></a>Authentification Windows  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge l’authentification Windows lors de la connexion à la base de données Oracle. Avec l’authentification Windows, les clients de l’adaptateur peuvent déterminer l’identité d’un utilisateur selon les informations d’identification d’ouverture de session de Windows et peuvent tirer parti de la sécurité intégrée de l’environnement Windows. Pour plus d’informations sur la connexion à la base de données Oracle à l’aide de l’authentification Windows, consultez [se connecter à la base de données Oracle à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)