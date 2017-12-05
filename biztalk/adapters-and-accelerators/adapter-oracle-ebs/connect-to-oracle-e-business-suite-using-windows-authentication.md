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
# <a name="connect-to-oracle-e-business-suite-using-windows-authentication"></a><span data-ttu-id="11e70-102">Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="11e70-102">Connect to Oracle E-Business Suite using Windows Authentication</span></span>
<span data-ttu-id="11e70-103">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients de carte à utiliser l’authentification Windows pour établir une connexion avec Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="11e70-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to use Windows Authentication to establish a connection with the Oracle E-Business Suite.</span></span> <span data-ttu-id="11e70-104">Pour utiliser l’authentification Windows des clients de l’adaptateur doivent spécifier une « / » pour le nom d’utilisateur et laissez le mot de passe vide.</span><span class="sxs-lookup"><span data-stu-id="11e70-104">To use Windows Authentication adapter clients must specify a “/” for user name and leave the password blank.</span></span> <span data-ttu-id="11e70-105">Pour plus d’informations sur la connexion à Oracle E-Business Suite à l’aide de l’authentification Windows, consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="11e70-105">For more information about connecting to the Oracle E-Business Suite using Windows Authentication, see [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).</span></span>  

## <a name="what-you-need-to-know"></a><span data-ttu-id="11e70-106">Ce que vous devez savoir</span><span class="sxs-lookup"><span data-stu-id="11e70-106">What you need to know</span></span>  
 <span data-ttu-id="11e70-107">Pour utiliser l’authentification Windows, vous devez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="11e70-107">To use Windows Authentication, you must do the following:</span></span>  
  
-   <span data-ttu-id="11e70-108">Si le **ClientCredentialType** est définie sur **base de données**, spécifiez « / » pour le nom d’utilisateur et laissez le mot de passe vide pour vous connecter à Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="11e70-108">If the **ClientCredentialType** property is set to **Database**, specify “/” for the user name and leave the password blank to connect to the Oracle E-Business Suite.</span></span>  
  
-   <span data-ttu-id="11e70-109">Si le **ClientCredentialType** est définie sur **EBusiness**, spécifiez les informations d’identification Oracle E-Business Suite pour vous connecter.</span><span class="sxs-lookup"><span data-stu-id="11e70-109">If the **ClientCredentialType** property is set to **EBusiness**, specify the Oracle E-Business Suite credentials to connect.</span></span> <span data-ttu-id="11e70-110">En outre, vous devez spécifier « / » pour le **OracleUserName** liaison de propriété et laisser le **OraclePassword** vide de la propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="11e70-110">Also, you must specify “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>  

## <a name="enable-windows-authentication"></a><span data-ttu-id="11e70-111">Activer l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="11e70-111">Enable Windows Authentication</span></span>  
 <span data-ttu-id="11e70-112">Pour activer la carte aux clients d’utiliser l’authentification Windows pour se connecter à une base de données Oracle, vous devez effectuer les tâches suivantes sur l’ordinateur exécutant la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="11e70-112">To enable adapter clients to use Windows Authentication to connect to an Oracle database, you must perform the following tasks on the computer running the Oracle database.</span></span>  
  
1.  <span data-ttu-id="11e70-113">Assurez-vous que le `sqlnet.ora` fichier sur le client et le serveur, disponible sous `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, a l’entrée suivante :</span><span class="sxs-lookup"><span data-stu-id="11e70-113">Make sure that the `sqlnet.ora` file on both the client and the server, available under `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, has the following entry:</span></span>  
  
    ```  
    SQLNET.AUTHENTICATION_SERVICES= (NTS)  
    ```  
  
2.  <span data-ttu-id="11e70-114">Connectez-vous à la base de données Oracle en tant que SYSDBA.</span><span class="sxs-lookup"><span data-stu-id="11e70-114">Connect to the Oracle database as SYSDBA.</span></span>  
  
3.  <span data-ttu-id="11e70-115">Créer l’utilisateur Windows en tant qu’un utilisateur externe dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="11e70-115">Create the Windows user as an external user in Oracle database.</span></span> <span data-ttu-id="11e70-116">Notez que le nom d’utilisateur doit être en majuscules.</span><span class="sxs-lookup"><span data-stu-id="11e70-116">Note that the user name must be in upper case.</span></span>  
  
    ```  
    CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
    ```  
  
4.  <span data-ttu-id="11e70-117">Accorder les privilèges nécessaires pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11e70-117">Grant privileges to the user.</span></span>  
  
    ```  
    GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
    ```  
  
5.  <span data-ttu-id="11e70-118">Les artefacts d’Oracle E-Business Suite sont disponibles sous le schéma d’applications.</span><span class="sxs-lookup"><span data-stu-id="11e70-118">The Oracle E-Business Suite artifacts are available under the APPS schema.</span></span> <span data-ttu-id="11e70-119">Pour activer l’utilisateur nouvellement créé, la journalisation à l’aide de l’authentification Windows, pour accéder aux artefacts Oracle E-Business Suite, schéma de l’utilisateur doit être remplacé par le schéma d’applications.</span><span class="sxs-lookup"><span data-stu-id="11e70-119">To enable the newly created user, logging in using Windows Authentication, to access the Oracle E-Business Suite artifacts, the user’s schema must be changed to the APPS schema.</span></span> <span data-ttu-id="11e70-120">Vous pouvez ajouter la commande SQL suivante au script d’ouverture de session qui modifie le schéma par défaut de l’utilisateur aux applications lorsque l’utilisateur ouvre une session.</span><span class="sxs-lookup"><span data-stu-id="11e70-120">You can add the following SQL command to the logon script that changes the user’s default schema to APPS when the user logs on.</span></span>  
  
    ```  
    alter session set current_schema=APPS;  
    ```  
  
6.  <span data-ttu-id="11e70-121">Même si vous avez modifié le schéma de l’utilisateur au schéma d’applications, vous serez toujours pas être en mesure de voir les artefacts d’Oracle E-Business Suite lors de la navigation et la génération de métadonnées à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11e70-121">Even though you changed the schema of the user to APPS schema, you will still not be able to see Oracle E-Business Suite artifacts while browsing and generating metadata using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="11e70-122">Il s’agit, car l’utilisateur nouvellement créé n’a pas d’autorisations pour le schéma d’applications.</span><span class="sxs-lookup"><span data-stu-id="11e70-122">This is because the newly created user does not have permissions for the APPS schema.</span></span> <span data-ttu-id="11e70-123">Assurez-vous que vous avez fourni les autorisations pour le schéma d’applications pour l’utilisateur nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="11e70-123">Make sure you provided permission for the APPS schema for the newly created user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e70-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11e70-124">See Also</span></span>  
<span data-ttu-id="11e70-125">[Configurer le client Oracle pour l’adaptateur de E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="11e70-125">[Configure the Oracle client for the E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md) </span></span>  
[<span data-ttu-id="11e70-126">Créer l’URI de connexion Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="11e70-126">Create the Oracle E-Business Suite connection URI</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)  
 [<span data-ttu-id="11e70-127">Créer une connexion à Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="11e70-127">Create a connection to Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)