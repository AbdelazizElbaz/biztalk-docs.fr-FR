---
title: "Créer une connexion à SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a03b2c-55b5-49a0-92cc-6f017720d34a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b87b4141c9e14c680d8100a7c505dda0a0093c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-sql-server"></a>Créer une connexion à SQL Server
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Par conséquent, il permet la communication à une base de données SQL Server via une adresse de point de terminaison WCF. Dans WCF, l’adresse de point de terminaison identifie l’emplacement réseau d’un service et est généralement exprimée comme une ressource identificateur URI (Uniform). Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise pour établir une connexion à la base de données SQL Server. Vous devez spécifier un URI de connexion lorsque vous :  
  
-   Créer une fabrique de canaux ou d’un écouteur de canal à l’aide du modèle de canal WCF ou lorsque vous créez un hôte de service ou client WCF à l’aide du modèle de service WCF.  
  
-   Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour une solution BizTalk Server.  
  
-   Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.  
  
 Les rubriques de cette section décrivent comment établir une connexion entre le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] et la base de données SQL Server en vous fournissant :  
  
-   Informations sur les propriétés de connexion et la structure de l’URI de connexion SQL Server.  
  
-   Liens vers des rubriques qui montrent comment spécifier un URI de connexion à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Informations sur la connexion à SQL Server à l’aide de l’authentification Windows.  
  
  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)