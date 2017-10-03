---
title: "Se connecter à la base de données Oracle à l’aide de l’authentification Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73b42a1b-1105-4278-bf8a-62cf0cffb08f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1b1dd0a6e11a1755bb69782f88f1a5a4b8b0067
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-oracle-database-using-windows-authentication"></a>Se connecter à la base de données Oracle à l’aide de l’authentification Windows
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] permet aux clients de carte à utiliser l’authentification Windows pour établir une connexion avec la base de données Oracle. Pour utiliser l’authentification Windows, les clients de l’adaptateur doivent spécifier « / » pour le nom d’utilisateur et de ne pas renseigner le mot de passe. Pour plus d’informations sur la connexion à la base de données Oracle à l’aide de l’authentification Windows, consultez [se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).  
  
 Pour activer la carte aux clients d’utiliser l’authentification Windows pour se connecter à une base de données Oracle, vous devez effectuer les tâches suivantes sur l’ordinateur exécutant la base de données Oracle.  
  
1.  Assurez-vous que le `sqlnet.ora` fichier sur le client et le serveur, disponible sous `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, a l’entrée suivante :  
  
    ```  
    SQLNET.AUTHENTICATION_SERVICES= (NTS)  
    ```  
  
2.  Connectez-vous à la base de données Oracle en tant que SYSDBA.  
  
3.  Créer l’utilisateur Windows en tant qu’un utilisateur externe dans la base de données Oracle. Notez que le nom d’utilisateur doit être en majuscules.  
  
    ```  
    CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME>” IDENTIFIED EXTERNALLY;  
    ```  
  
4.  Accorder les privilèges nécessaires pour l’utilisateur.  
  
    ```  
    GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME>”;  
    ```  
  
5.  Pour activer l’utilisateur nouvellement créé, la journalisation à l’aide de l’authentification Windows, pour accéder aux artefacts de base de données Oracle, vous pouvez modifier le schéma de l’utilisateur vers le schéma SCOTT. Vous pouvez ajouter la commande SQL suivante au script d’ouverture de session qui modifie le schéma par défaut de l’utilisateur à SCOTT lorsque l’utilisateur ouvre une session.  
  
    ```  
    alter session set current_schema=SCOTT;  
    ```  
  
6.  Même si vous avez modifié le schéma de l’utilisateur pour le schéma SCOTT, vous serez toujours pas être en mesure de voir les artefacts de base de données Oracle lors de la navigation et la génération de métadonnées à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Il s’agit, car l’utilisateur nouvellement créé n’a pas d’autorisations pour le schéma SCOTT. Assurez-vous que vous avez fourni des autorisations pour le schéma SCOTT à l’utilisateur nouvellement créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le Client Oracle pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)   
[Créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)