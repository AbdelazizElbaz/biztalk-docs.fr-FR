---
title: "Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0937dfd9-4a94-4d65-a42c-3c5019eefde2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed71a893ef029e6524b7e71f68626c32f207f91e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="connect-to-oracle-e-business-suite-using-windows-authentication"></a>Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients de carte à utiliser l’authentification Windows pour établir une connexion avec Oracle E-Business Suite. Pour utiliser l’authentification Windows des clients de l’adaptateur doivent spécifier une « / » pour le nom d’utilisateur et laissez le mot de passe vide. Pour plus d’informations sur la connexion à Oracle E-Business Suite à l’aide de l’authentification Windows, consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir  
 Pour utiliser l’authentification Windows, vous devez procédez comme suit :  
  
-   Si le **ClientCredentialType** est définie sur **base de données**, spécifiez « / » pour le nom d’utilisateur et laissez le mot de passe vide pour vous connecter à Oracle E-Business Suite.  
  
-   Si le **ClientCredentialType** est définie sur **EBusiness**, spécifiez les informations d’identification Oracle E-Business Suite pour vous connecter. En outre, vous devez spécifier « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.  

## <a name="enable-windows-authentication"></a>Activer l’authentification Windows  
 Pour activer la carte aux clients d’utiliser l’authentification Windows pour se connecter à une base de données Oracle, vous devez effectuer les tâches suivantes sur l’ordinateur exécutant la base de données Oracle.  
  
1.  Assurez-vous que le `sqlnet.ora` fichier sur le client et le serveur, disponible sous `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, a l’entrée suivante :  
  
    ```  
    SQLNET.AUTHENTICATION_SERVICES= (NTS)  
    ```  
  
2.  Connectez-vous à la base de données Oracle en tant que SYSDBA.  
  
3.  Créer l’utilisateur Windows en tant qu’un utilisateur externe dans la base de données Oracle. Notez que le nom d’utilisateur doit être en majuscules.  
  
    ```  
    CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
    ```  
  
4.  Accorder les privilèges nécessaires pour l’utilisateur.  
  
    ```  
    GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
    ```  
  
5.  Les artefacts d’Oracle E-Business Suite sont disponibles sous le schéma d’applications. Pour activer l’utilisateur nouvellement créé, la journalisation à l’aide de l’authentification Windows, pour accéder aux artefacts Oracle E-Business Suite, schéma de l’utilisateur doit être remplacé par le schéma d’applications. Vous pouvez ajouter la commande SQL suivante au script d’ouverture de session qui modifie le schéma par défaut de l’utilisateur aux applications lorsque l’utilisateur ouvre une session.  
  
    ```  
    alter session set current_schema=APPS;  
    ```  
  
6.  Même si vous avez modifié le schéma de l’utilisateur au schéma d’applications, vous serez toujours pas être en mesure de voir les artefacts d’Oracle E-Business Suite lors de la navigation et la génération de métadonnées à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Il s’agit, car l’utilisateur nouvellement créé n’a pas d’autorisations pour le schéma d’applications. Assurez-vous que vous avez fourni les autorisations pour le schéma d’applications pour l’utilisateur nouvellement créé.  
  
## <a name="see-also"></a>Voir aussi  
[Configurer le client Oracle pour l’adaptateur de E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)   
[Créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)  
 [Créer une connexion à Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)