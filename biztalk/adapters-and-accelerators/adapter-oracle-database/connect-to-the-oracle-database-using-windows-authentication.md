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
# <a name="connect-to-the-oracle-database-using-windows-authentication"></a><span data-ttu-id="59e08-102">Se connecter à la base de données Oracle à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="59e08-102">Connect to the Oracle Database Using Windows Authentication</span></span>
<span data-ttu-id="59e08-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] permet aux clients de carte à utiliser l’authentification Windows pour établir une connexion avec la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="59e08-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables adapter clients to use Windows Authentication to establish a connection with the Oracle database.</span></span> <span data-ttu-id="59e08-104">Pour utiliser l’authentification Windows, les clients de l’adaptateur doivent spécifier « / » pour le nom d’utilisateur et de ne pas renseigner le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="59e08-104">To use Windows Authentication, the adapter clients must specify “/” for user name and leave the password blank.</span></span> <span data-ttu-id="59e08-105">Pour plus d’informations sur la connexion à la base de données Oracle à l’aide de l’authentification Windows, consultez [se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).</span><span class="sxs-lookup"><span data-stu-id="59e08-105">For more information about connecting to the Oracle database using Windows Authentication, see [Connect to Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).</span></span>  
  
 <span data-ttu-id="59e08-106">Pour activer la carte aux clients d’utiliser l’authentification Windows pour se connecter à une base de données Oracle, vous devez effectuer les tâches suivantes sur l’ordinateur exécutant la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="59e08-106">To enable adapter clients to use Windows Authentication to connect to an Oracle database, you must perform the following tasks on the computer running the Oracle database.</span></span>  
  
1.  <span data-ttu-id="59e08-107">Assurez-vous que le `sqlnet.ora` fichier sur le client et le serveur, disponible sous `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, a l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="59e08-107">Make sure that the `sqlnet.ora` file on both the client and the server, available under `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, has the following entry:</span></span>  
  
    ```  
    SQLNET.AUTHENTICATION_SERVICES= (NTS)  
    ```  
  
2.  <span data-ttu-id="59e08-108">Connectez-vous à la base de données Oracle en tant que SYSDBA.</span><span class="sxs-lookup"><span data-stu-id="59e08-108">Connect to the Oracle database as SYSDBA.</span></span>  
  
3.  <span data-ttu-id="59e08-109">Créer l’utilisateur Windows en tant qu’un utilisateur externe dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="59e08-109">Create the Windows user as an external user in the Oracle database.</span></span> <span data-ttu-id="59e08-110">Notez que le nom d’utilisateur doit être en majuscules.</span><span class="sxs-lookup"><span data-stu-id="59e08-110">Note that the user name must be in upper case.</span></span>  
  
    ```  
    CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME>” IDENTIFIED EXTERNALLY;  
    ```  
  
4.  <span data-ttu-id="59e08-111">Accorder les privilèges nécessaires pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="59e08-111">Grant privileges to the user.</span></span>  
  
    ```  
    GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME>”;  
    ```  
  
5.  <span data-ttu-id="59e08-112">Pour activer l’utilisateur nouvellement créé, la journalisation à l’aide de l’authentification Windows, pour accéder aux artefacts de base de données Oracle, vous pouvez modifier le schéma de l’utilisateur vers le schéma SCOTT.</span><span class="sxs-lookup"><span data-stu-id="59e08-112">To enable the newly created user, logging in using Windows Authentication, to access the Oracle database artifacts, you can change the user’s schema to the SCOTT schema.</span></span> <span data-ttu-id="59e08-113">Vous pouvez ajouter la commande SQL suivante au script d’ouverture de session qui modifie le schéma par défaut de l’utilisateur à SCOTT lorsque l’utilisateur ouvre une session.</span><span class="sxs-lookup"><span data-stu-id="59e08-113">You can add the following SQL command to the logon script that changes the user’s default schema to SCOTT when the user logs on.</span></span>  
  
    ```  
    alter session set current_schema=SCOTT;  
    ```  
  
6.  <span data-ttu-id="59e08-114">Même si vous avez modifié le schéma de l’utilisateur pour le schéma SCOTT, vous serez toujours pas être en mesure de voir les artefacts de base de données Oracle lors de la navigation et la génération de métadonnées à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59e08-114">Even though you changed the schema of the user to the SCOTT schema, you will still not be able to see the Oracle database artifacts while browsing and generating metadata using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="59e08-115">Il s’agit, car l’utilisateur nouvellement créé n’a pas d’autorisations pour le schéma SCOTT.</span><span class="sxs-lookup"><span data-stu-id="59e08-115">This is because the newly created user does not have permissions for the SCOTT schema.</span></span> <span data-ttu-id="59e08-116">Assurez-vous que vous avez fourni des autorisations pour le schéma SCOTT à l’utilisateur nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="59e08-116">Make sure you provided permission for the SCOTT schema to the newly created user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e08-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59e08-117">See Also</span></span>  
 <span data-ttu-id="59e08-118">[Configurer le Client Oracle pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="59e08-118">[Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md) </span></span>  
[<span data-ttu-id="59e08-119">Créer une connexion à la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="59e08-119">Create a connection to the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)