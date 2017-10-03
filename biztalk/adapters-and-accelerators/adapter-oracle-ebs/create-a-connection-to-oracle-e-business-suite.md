---
title: "Créer une connexion à Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeeab604-155e-4806-b77a-45319a3f8cc0
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ffdfdc8810024e331598211529f3a594e0169f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-oracle-e-business-suite"></a>Créer une connexion à Oracle E-Business Suite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Par conséquent, il permet la communication pour Oracle E-Business Suite via une adresse de point de terminaison WCF. Dans WCF, l’adresse de point de terminaison identifie l’emplacement réseau d’un service et est généralement exprimée comme une ressource identificateur URI (Uniform). Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise pour établir une connexion à Oracle E-Business Suite. Vous devez spécifier un URI de connexion lorsque vous :  
  
-   Créer une fabrique de canaux ou d’un écouteur de canal à l’aide du modèle de canal WCF ou lorsque vous créez un hôte de service ou client WCF à l’aide du modèle de service WCF.  
  
-   Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour une solution BizTalk Server.  
  
-   Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF ou l’interface de service WCF pour une solution de modèle de service WCF.  

## <a name="ways-to-connect-to-oracle"></a>Modes de connexion à Oracle  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge deux manières d’établir une connexion à la base de données Oracle :  
  
-   **À l’aide de tnsnames.ora**. Dans cette approche, l’URI fourni par le client de l’adaptateur de connexion contient uniquement le nom de service réseau entré dans le fichier tnsnames.ora. L’adaptateur extrait les paramètres de connexion, telles que le nom du serveur, nom du service, numéro de port et ainsi de suite, à partir de l’entrée de nom de service réseau dans le fichier. Pour utiliser cette approche, l’ordinateur qui exécute le client Oracle doit être configuré pour inclure le nom de service réseau pour la base de données Oracle dans le fichier tnsnames.ora.  
  
    > [!IMPORTANT]
    >  En raison d’une limitation du Client Oracle, le **DataSourceName** paramètre (nom de service réseau) dans le [créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md) ne peut pas contenir plus de 39 caractères si vous êtes exécution d’opérations dans une transaction. Par conséquent, si vous effectuez des opérations dans une transaction, assurez-vous que le **DataSourceName** valeur du paramètre est inférieur ou égal à 39 caractères.  
  
-   **Sans utiliser de tnsnames.ora**. Dans cette approche, les clients de l’adaptateur permet d’entrer les paramètres de connexion directement dans l’URI de connexion. Cela ne nécessite pas le nom de service réseau d’être présents dans le fichier tnsnames.ora sur l’ordinateur client. Cette approche ne nécessite pas le fichier tnsnames.ora se trouvent sur l’ordinateur client.  
  
    > [!IMPORTANT]
    >  Ce mode de connectivité n’est pas pris en charge si vous effectuez des opérations dans une transaction. Il s’agit d’une limitation du Client Oracle.  

## <a name="in-this-section"></a>Contenu de cette section    
 Les rubriques suivantes décrivent comment établir une connexion entre le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et Oracle E-Business Suite :  
  
-   [Configurer le client Oracle pour l’adaptateur de E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md): informations sur l’utilisation de tnsnames.ora à cconfiguring le client Oracle (obligatoire uniquement si le tnsnames.ora pour établir la connexion)  
  
-   [Créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md): plus d’informations sur les propriétés de connexion et de la structure de l’URI de connexion Oracle E-Business Suite
  
-   [Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md): plus d’informations sur la connexion à Oracle à l’aide de l’authentification Windows
  