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
# <a name="configure-the-oracle-client-for-the-oracle-database-adapter"></a><span data-ttu-id="9642b-102">Configurer le Client Oracle pour l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9642b-102">Configure the Oracle Client for the Oracle Database adapter</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="9642b-103">Cette rubrique s’applique uniquement si vous utilisez tnsnames.ora pour se connecter à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="9642b-103">This topic is relevant only if you are using tnsnames.ora to connect to the Oracle database.</span></span>  
  
 <span data-ttu-id="9642b-104">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] se connecte à la base de données Oracle par le biais du client Oracle installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9642b-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] connects to the Oracle database through the Oracle client installed on your computer.</span></span> <span data-ttu-id="9642b-105">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] transmet le nom de service réseau que vous spécifiez dans l’URI de connexion au client Oracle pour établir une connexion à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="9642b-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] passes the net service name that you specify in the connection URI to the Oracle client to establish a connection to the Oracle database.</span></span> <span data-ttu-id="9642b-106">Le nom de service réseau est un alias que le client Oracle utilise pour acquérir des informations de connexion pour le service de base de données Oracle cible.</span><span class="sxs-lookup"><span data-stu-id="9642b-106">The net service name is an alias that the Oracle client uses to acquire connection information for the target Oracle database service.</span></span>  
  
 <span data-ttu-id="9642b-107">Le client Oracle soit résolu nom de service réseau en fonction de la méthode d’affectation de noms qu’il est configuré pour utiliser.</span><span class="sxs-lookup"><span data-stu-id="9642b-107">The Oracle client resolves the net service name according to the naming method that it is configured to use.</span></span> <span data-ttu-id="9642b-108">Vous utilisez Oracle Net Configuration Assistant pour configurer les méthodes d’affectation de noms à utiliser par le client Oracle.</span><span class="sxs-lookup"><span data-stu-id="9642b-108">You use the Oracle Net Configuration Assistant to configure the naming methods to be used by the Oracle client.</span></span> <span data-ttu-id="9642b-109">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la méthode d’affectation de noms locale pour la connexion à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="9642b-109">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the Local Naming method for connecting to the Oracle database.</span></span> <span data-ttu-id="9642b-110">Cette méthode utilise un fichier local, tnsnames.ora, pour résoudre le nom de service réseau.</span><span class="sxs-lookup"><span data-stu-id="9642b-110">This method uses a local file, tnsnames.ora, to resolve the net service name.</span></span>  
  
 <span data-ttu-id="9642b-111">L’associe de fichier tnsnames.ora avec des noms de service réseau connecter descripteurs qui contiennent les informations que du client Oracle a besoin pour établir une connexion à un service de base de données Oracle spécifique (instance).</span><span class="sxs-lookup"><span data-stu-id="9642b-111">The tnsnames.ora file associates net service names with connect descriptors that contain the information the Oracle client needs to establish a connection to a specific Oracle database service (instance).</span></span> <span data-ttu-id="9642b-112">Voici un exemple d’entrée à partir de tnsnames.ora.</span><span class="sxs-lookup"><span data-stu-id="9642b-112">The following is a sample entry from tnsnames.ora.</span></span>  
  
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
  
 <span data-ttu-id="9642b-113">Dans cet exemple d’entrée, la carte est le nom de service réseau.</span><span class="sxs-lookup"><span data-stu-id="9642b-113">In this sample entry, ADAPTER is the net service name.</span></span> <span data-ttu-id="9642b-114">Le descripteur de connexion spécifie les informations d’adresse et le nom du service du service de base de données Oracle associé à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9642b-114">The connect descriptor specifies address information and the service name of the Oracle database service associated with ADAPTER.</span></span> <span data-ttu-id="9642b-115">Vous pouvez utiliser Oracle Net Configuration Assistant pour créer et configurer des noms de service réseau dans tnsnames.ora.</span><span class="sxs-lookup"><span data-stu-id="9642b-115">You can use the Oracle Net Configuration Assistant to create and configure net service names in tnsnames.ora.</span></span> <span data-ttu-id="9642b-116">Après avoir configuré le nom de service réseau, vous pouvez les spécifier dans l’URI de connexion comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9642b-116">After you have configured the net service name, you can specify it in a connection URI as in the following example.</span></span>  
  
```  
oracledb://ADAPTER  
```  
  
 <span data-ttu-id="9642b-117">Pour plus d’informations sur l’utilisation d’Oracle Net Configuration Assistant et tnsnames.ora, consultez Oracle Net Services Guide de l’administrateur de base de données.</span><span class="sxs-lookup"><span data-stu-id="9642b-117">For more information about using the Oracle Net Configuration Assistant and about tnsnames.ora, see the Oracle Database Net Services Administrator's Guide.</span></span> <span data-ttu-id="9642b-118">Contactez l’administrateur de base de données sur les détails de configuration pour votre installation spécifique.</span><span class="sxs-lookup"><span data-stu-id="9642b-118">Consult your database administrator about configuration details for your specific installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9642b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9642b-119">See Also</span></span>  
[<span data-ttu-id="9642b-120">Créer une connexion à la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="9642b-120">Create a connection to the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)