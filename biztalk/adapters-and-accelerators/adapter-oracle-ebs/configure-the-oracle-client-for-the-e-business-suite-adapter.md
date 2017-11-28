---
title: "Configurer le client Oracle pour l’adaptateur de E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842b6ecc-5334-4cc0-af10-baa7f692ad23
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ada64bf6f54c95f3d6e1c8f968a506476dbbc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-oracle-client-for-the-e-business-suite-adapter"></a><span data-ttu-id="4677d-102">Configurer le client Oracle pour l’adaptateur de E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="4677d-102">Configure the Oracle client for the E-Business Suite adapter</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="4677d-103">Cette rubrique s’applique uniquement si vous utilisez tnsnames.ora pour se connecter à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="4677d-103">This topic is relevant only if you are using tnsnames.ora to connect to the Oracle database.</span></span>  
  
 <span data-ttu-id="4677d-104">Pour établir une connexion à la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], l’adaptateur se connecte à la base de données Oracle sous-jacent via le client Oracle installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4677d-104">To establish a connection to the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], the adapter connects to the underlying Oracle database through the Oracle client installed on your computer.</span></span> <span data-ttu-id="4677d-105">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] transmet le nom de service réseau que vous spécifiez dans l’URI de connexion pour le client Oracle pour établir une connexion à Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="4677d-105">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] passes the net service name that you specify in the connection URI to the Oracle client to establish a connection to Oracle E-Business Suite.</span></span> <span data-ttu-id="4677d-106">Le nom de service réseau est un alias que le client Oracle utilise pour acquérir des informations de connexion pour le service de base de données Oracle cible.</span><span class="sxs-lookup"><span data-stu-id="4677d-106">The net service name is an alias that the Oracle client uses to acquire connection information for the target Oracle database service.</span></span>  
  
 <span data-ttu-id="4677d-107">Le client Oracle soit résolu nom de service réseau en fonction de la méthode d’affectation de noms qu’il est configuré pour utiliser.</span><span class="sxs-lookup"><span data-stu-id="4677d-107">The Oracle client resolves the net service name according to the naming method that it is configured to use.</span></span> <span data-ttu-id="4677d-108">Vous utilisez Oracle Net Configuration Assistant pour configurer les méthodes d’affectation de noms à utiliser par le client Oracle.</span><span class="sxs-lookup"><span data-stu-id="4677d-108">You use the Oracle Net Configuration Assistant to configure the naming methods to be used by the Oracle client.</span></span> <span data-ttu-id="4677d-109">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la méthode d’affectation de noms locale pour la connexion à Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="4677d-109">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports the Local Naming method for connecting to Oracle E-Business Suite.</span></span> <span data-ttu-id="4677d-110">Cette méthode utilise un fichier local, tnsnames.ora, pour résoudre le nom de service réseau.</span><span class="sxs-lookup"><span data-stu-id="4677d-110">This method uses a local file, tnsnames.ora, to resolve the net service name.</span></span>  
  
 <span data-ttu-id="4677d-111">Le fichier tnsnames.ora associe les noms de service réseau avec connexion descripteurs qui contiennent les informations que le client Oracle a besoin pour établir une connexion à un service de base de données Oracle spécifique (instance).</span><span class="sxs-lookup"><span data-stu-id="4677d-111">The tnsnames.ora file associates net service names with connect descriptors that contain the information that the Oracle client needs to establish a connection to a specific Oracle database service (instance).</span></span> <span data-ttu-id="4677d-112">Voici un exemple d’entrée à partir de tnsnames.ora.</span><span class="sxs-lookup"><span data-stu-id="4677d-112">The following is a sample entry from tnsnames.ora.</span></span>  
  
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
  
 <span data-ttu-id="4677d-113">Dans cet exemple d’entrée, la carte est le nom de service réseau.</span><span class="sxs-lookup"><span data-stu-id="4677d-113">In this sample entry, ADAPTER is the net service name.</span></span> <span data-ttu-id="4677d-114">Le descripteur de connexion spécifie les informations d’adresse et le nom du service du service de base de données Oracle associé à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="4677d-114">The connect descriptor specifies address information and the service name of the Oracle database service associated with ADAPTER.</span></span> <span data-ttu-id="4677d-115">Vous pouvez utiliser Oracle Net Configuration Assistant pour créer et configurer des noms de service réseau dans tnsnames.ora.</span><span class="sxs-lookup"><span data-stu-id="4677d-115">You can use the Oracle Net Configuration Assistant to create and configure net service names in tnsnames.ora.</span></span> <span data-ttu-id="4677d-116">Après avoir configuré le nom de service réseau, vous pouvez les spécifier dans l’URI de connexion comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4677d-116">After you have configured the net service name, you can specify it in a connection URI as in the following example.</span></span>  
  
```  
oracleebs://ADAPTER  
```  
  
 <span data-ttu-id="4677d-117">Pour plus d’informations sur l’utilisation d’Oracle Net Configuration Assistant et tnsnames.ora, consultez Oracle Net Services Guide de l’administrateur de base de données.</span><span class="sxs-lookup"><span data-stu-id="4677d-117">For more information about using the Oracle Net Configuration Assistant and about tnsnames.ora, see the Oracle Database Net Services Administrator's Guide.</span></span> <span data-ttu-id="4677d-118">Contactez l’administrateur de base de données sur les détails de configuration pour votre installation spécifique.</span><span class="sxs-lookup"><span data-stu-id="4677d-118">Consult your database administrator about configuration details for your specific installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4677d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4677d-119">See Also</span></span>  
 [<span data-ttu-id="4677d-120">Créer une connexion à Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="4677d-120">Create a connection to Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)