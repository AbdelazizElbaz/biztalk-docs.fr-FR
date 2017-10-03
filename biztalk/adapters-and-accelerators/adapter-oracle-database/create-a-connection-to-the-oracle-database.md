---
title: "Créer une connexion à la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: adapter, connecting to the Oracle Database
ms.assetid: 95f7905a-abad-4841-85c4-62cf0cc1e044
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f9a42994f0cde9df19e3b80e16fcbafbb2d8d5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-the-oracle-database"></a>Créer une connexion à la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Par conséquent, il permet la communication à une base de données Oracle via une adresse de point de terminaison WCF. Dans WCF, l’adresse de point de terminaison est généralement exprimée comme une ressource identificateur URI (Uniform), qui identifie l’emplacement réseau du service. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise pour établir une connexion à la base de données Oracle.  
  
 Vous devez spécifier un URI de connexion lorsque vous :  
  
-   Créer une fabrique de canaux ou d’un écouteur de canal à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal ou lorsque vous créez un hôte de service ou client WCF à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de service.  
  
-   Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou l’interface de service WCF pour un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de service.  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge deux manières d’établir une connexion à la base de données Oracle :  
  
-   **À l’aide de tnsnames.ora**. Dans cette approche, l’URI fourni par le client de l’adaptateur de connexion contient uniquement le nom de service réseau spécifié dans le fichier tnsnames.ora. L’adaptateur extrait les paramètres de connexion telles que le nom du serveur, nom du service, numéro de port, etc. à partir de l’entrée de nom de service réseau dans le fichier. Pour utiliser cette approche, l’ordinateur qui exécute le client Oracle doit être configuré pour inclure le nom de service réseau pour la base de données Oracle dans le fichier tnsnames.ora.  
  
    > [!IMPORTANT]
    >  En raison d’une limitation du Client Oracle, le **DataSourceName** paramètre (nom de service réseau) dans le [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md) ne peut pas contenir plus de 39 caractères si vous effectuez opérations dans une transaction. Par conséquent, assurez-vous que la valeur spécifiée pour le **DataSourceName** paramètre est inférieur ou égal à 39 caractères si vous allez effectuer les opérations dans une transaction.  
  
-   **Sans utiliser de tnsnames.ora**. Dans cette approche, les clients de l’adaptateur spécifient les paramètres de connexion directement dans l’URI de connexion. Cela ne nécessite pas le nom de service réseau d’être présents dans le fichier tnsnames.ora sur l’ordinateur client. Cette approche ne nécessite pas le fichier tnsname.ora doit se trouver sur l’ordinateur client.  
  
    > [!IMPORTANT]
    >  Ce mode de connectivité n’est pas pris en charge si vous effectuez des opérations dans une transaction. Il s’agit d’une limitation du Client Oracle.  
  
 Les rubriques de cette section décrivent comment établir une connexion entre le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] et la base de données Oracle en vous fournissant :  
  
-   Informations sur la configuration du client Oracle.  
  
-   Informations sur les propriétés de connexion et la structure de l’URI de connexion Oracle.  
  
-   Liens vers des rubriques qui montrent comment établir une connexion à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   Informations sur la connexion à la base de données Oracle à l’aide de l’authentification Windows.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configurer le Client Oracle pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)  
  
-   [Créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)  
  
-   [Se connecter à la base de données Oracle à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)