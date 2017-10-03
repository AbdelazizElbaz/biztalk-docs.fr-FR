---
title: "Programmation sécurisée avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c84744a-6595-4d93-afe7-39a7ccf1b6a0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44886b490ce63e8c34e1a5bdb41554c96a0873ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-sql-adapter"></a><span data-ttu-id="3bcfa-102">Programmation sécurisée avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="3bcfa-102">Secure programming with the SQL adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="3bcfa-103">Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?</span><span class="sxs-lookup"><span data-stu-id="3bcfa-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="3bcfa-104">Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devrez peut-être fournir un nom d’utilisateur et un mot de passe pour la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you might have to supply a user name and password for the SQL Server database.</span></span> <span data-ttu-id="3bcfa-105">Vous devez entrer les informations d’identification à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-105">You must enter credentials from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="3bcfa-106">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne fournit pas une option pour spécifier le nom d’utilisateur et un mot de passe dans le cadre de l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-106">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not provide an option to specify the user name and password as part of the connection URI.</span></span> <span data-ttu-id="3bcfa-107">Cela offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="3bcfa-107">This ensures the following:</span></span>  
  
-   <span data-ttu-id="3bcfa-108">Les informations d’identification ne s’affichera pas dans le **configurer un URI** champ le **ajouter adaptateur Service référence un plug-in** boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-108">The credentials will not be displayed in the **Configure a URI** field of the **Add Adapter Service Reference Plug-in** dialog box where anyone with access to your computer screen can read them.</span></span>  
  
-   <span data-ttu-id="3bcfa-109">Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-109">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="3bcfa-110">Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour la base de données SQL Server, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="3bcfa-110">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the SQL Server database, see [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="3bcfa-111">Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?</span><span class="sxs-lookup"><span data-stu-id="3bcfa-111">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="3bcfa-112">Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-112"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="3bcfa-113">À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-113">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="3bcfa-114">Étant donné que la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-114">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="3bcfa-115">Toutefois, il apparaît conseillé de le faire.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-115">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="3bcfa-116">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requiert l’utilisation de la **ClientCredentials** classe pour passer des informations d’identification par programme.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requires the use of the **ClientCredentials** class for programmatically passing credentials.</span></span> <span data-ttu-id="3bcfa-117">Le **AcceptCredentialsInUri** liaison de la propriété est ignorée par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour empêcher les informations d’identification de passage dans l’URI.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-117">The **AcceptCredentialsInUri** binding property is ignored by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to prevent passing credentials in the URI.</span></span>  
  
 <span data-ttu-id="3bcfa-118">L’exemple suivant montre comment utiliser le **informations d’identification** propriété à définir les informations d’identification pour la base de données SQL Server sur un **ChannelFactory**.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-118">The following example shows how to use the **Credentials** property to set credentials for the SQL Server database on a **ChannelFactory**.</span></span>  
  
```  
// Create binding and endpoint  
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 <span data-ttu-id="3bcfa-119">L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification pour la base de données SQL Server sur un client WCF.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-119">The following example shows how to use the **ClientCredentials** class to set credentials for the SQL Server database on a WCF client.</span></span>  
  
```  
// Initialize a new client for the SELECT operation on the Employee table   
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient(binding,address);  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="3bcfa-120">Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?</span><span class="sxs-lookup"><span data-stu-id="3bcfa-120">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="3bcfa-121">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est hébergé in-process avec l’application ou le service qui la consomme.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-121">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="3bcfa-122">Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bcfa-122">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="3bcfa-123">Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-123">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="3bcfa-124">fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services.</span><span class="sxs-lookup"><span data-stu-id="3bcfa-124"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="3bcfa-125">Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span><span class="sxs-lookup"><span data-stu-id="3bcfa-125">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span></span> <span data-ttu-id="3bcfa-126">Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span><span class="sxs-lookup"><span data-stu-id="3bcfa-126">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3bcfa-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bcfa-127">See Also</span></span>  
[<span data-ttu-id="3bcfa-128">Sécuriser vos applications SQL</span><span class="sxs-lookup"><span data-stu-id="3bcfa-128">Secure your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[<span data-ttu-id="3bcfa-129">Meilleures pratiques pour sécuriser l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="3bcfa-129">Best practices to secure the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)