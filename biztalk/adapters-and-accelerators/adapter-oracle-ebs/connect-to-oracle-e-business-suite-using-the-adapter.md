---
title: "Se connecter à Oracle E-Business Suite à l’aide de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80ff31d4-be4c-42d7-a321-8f01b40dd71e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c8551c0f09d65d50b87248a6b0dc4030a612fc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-e-business-suite-using-the-adapter"></a>Se connecter à Oracle E-Business Suite à l’aide de l’adaptateur
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] ODP.NET 11.1.0.7 pour se connecter à Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exige que les clients de l’adaptateur fournir une chaîne de connexion, appelée la connexion identificateur URI (Uniform Resource), pour se connecter à Oracle E-Business Suite. En interne, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] se connecte à la base de données Oracle sous-jacent via l’URI. Avec un URI de connexion, les clients de carte peuvent spécifier des paramètres de connexion pour se connecter à un système externe.  

## <a name="connectivity-to-oracle-ebs"></a>Connexion à Oracle eBusiness Suite  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients de l’adaptateur pour se connecter à Oracle E-Business Suite dans le code suivant deux façons :  
  
-   **À l’aide de tnsnames.ora**: l’URI fourni par le client de l’adaptateur de connexion contient uniquement le nom de service réseau spécifié dans le fichier tnsnames.ora. L’adaptateur extrait les paramètres de connexion comme nom de serveur, nom du service et numéro de port de l’entrée de nom de service réseau dans le fichier tnsnames.ora. Pour utiliser cette approche, l’ordinateur qui exécute le client Oracle doit être configuré pour inclure le nom de service réseau pour la base de données Oracle dans le fichier tnsnames.ora.  
  
    > [!IMPORTANT]
    >  En raison d’une limitation du Client Oracle, le **DataSourceName** paramètre (nom de service réseau) dans le [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md) ne peut pas contenir plus de 39 caractères si vous effectuez des opérations dans une transaction. Par conséquent, assurez-vous que la valeur spécifiée pour le **DataSourceName** paramètre est inférieur ou égal à 39 caractères si vous allez effectuer les opérations dans une transaction.  
  
-   **Sans utiliser de tnsnames.ora**: l’URI fourni par les clients de l’adaptateur de connexion contient les paramètres de connexion comme nom de serveur, nom du service et numéro de port. Dans ce cas, le nom de service réseau dans le fichier tnsnames.ora ou le fichier tnsnames.ora réel lui-même, n’a pas besoin d’être présents sur l’ordinateur client. Cela est utile lorsque vous avez un grand nombre d’utilisateurs qui se connectent à la base de données Oracle dans votre organisation, et ajout/la mise à jour des serveurs ne mène pas à ajouter/mettre à jour manuellement les informations de connexion dans le fichier tnsnames.ora sur chaque ordinateur client.  
  
    > [!IMPORTANT]
    >  Ce mode de connectivité n’est pas pris en charge si vous effectuez des opérations dans une transaction. Il s’agit d’une limitation du Client Oracle.  
  
 Pour plus d’informations sur la connexion à Oracle E-Business Suite, consultez [créer une connexion à Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).  
  
 Veillez à que respecter les consignes de sécurité lors de l’établissement d’une connexion avec Oracle E-Business Suite. Consultez [sécuriser votre application Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md).
  
## <a name="enter-client-credentials"></a>Entrez les informations d’identification du client  
 Dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous pouvez fournir des informations d’identification pour se connecter à Oracle E-Business Suite dans les deux emplacements suivants :  
  
-   Sur le **sécurité** onglet dans le **configurer l’adaptateur** boîte de dialogue. Vous pouvez trouver cette boîte de dialogue dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   Dans le **OracleUserName** et **OraclePassword** propriétés de liaison de la **propriétés de liaison** onglet dans le **configurer l’adaptateur** boîte de dialogue. Vous pouvez trouver cette boîte de dialogue dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Dans ce cas, les informations d’identification sont stockées en texte brut dans le fichier de liaison.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose le **ClientCredentialType** liaison de la propriété qui vous permet de spécifier le jeu d’informations d’identification (Oracle E-Business Suite ou base de données Oracle) qui permet de se connecter à Oracle E-Business Suite.  
  
-   Pour vous connecter à l’aide des informations d’identification de base de données Oracle, spécifiez la **ClientCredentialType** de la propriété de liaison **base de données**, puis, dans le **sécurité** onglet, spécifiez le informations d’identification dans la base de données le **nom d’utilisateur** et **mot de passe** zones de texte.  Si vous effectuez des opérations sur les artefacts d’Oracle E-Business Suite (table d’interface, vue de l’interface, simultanées du programme, ensemble de la demande ou Oracle E-Business Suite PL/SQL API), vous devez également fournir les informations d’identification Oracle E-Business Suite dans le **OracleUserName** et **OraclePassword** propriétés de liaison.  
  
-   Pour vous connecter à l’aide des informations d’identification Oracle E-Business Suite, spécifiez la **ClientCredentialType** de la propriété de liaison **EBusiness**, puis spécifiez les informations d’identification Oracle E-Business Suite dans le  **Nom d’utilisateur** et **mot de passe** zones de texte sur le **sécurité** onglet. Vous devez également spécifier les informations d’identification de la base de données Oracle pour le **OracleUserName** et **OraclePassword** propriétés de liaison.  
  
 Pour plus d’informations sur la spécification des informations d’identification du client, consultez [configurer les informations d’identification de connexion d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-sign-in-credentials-for-the-oracle-e-business-suite.md).  
  
## <a name="using-windows-authentication"></a>Avec l’authentification Windows  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge l’authentification Windows lors de la connexion à Oracle E-Business Suite. Avec l’authentification Windows, les clients de l’adaptateur peuvent déterminer l’identité d’un utilisateur selon les informations d’identification d’ouverture de session de Windows et peuvent tirer parti de la sécurité intégrée de l’environnement Windows. Pour plus d’informations sur la connexion à Oracle E-Business Suite à l’aide de l’authentification Windows, consultez [se connecter à Oracle E-Business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md).  
  
## <a name="see-also"></a>Voir aussi  
[Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)