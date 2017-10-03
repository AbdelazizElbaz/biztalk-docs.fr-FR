---
title: "Programmation avec l’adaptateur de base de données Oracle sécurisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials
- adapter, security considerations when programming on
- credentials, setting in code
- credentials, protecting
- security
ms.assetid: 06213c14-42b8-4d4a-b238-0aedbc27ab6a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dab171bf2eef81221e6dde15756dc7b011c7ee92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-oracle-database-adapter"></a><span data-ttu-id="c367a-102">Programmation sécurisée avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="c367a-102">Secure programming with the Oracle Database adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="c367a-103">Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?</span><span class="sxs-lookup"><span data-stu-id="c367a-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="c367a-104">Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devez fournir un nom d’utilisateur et un mot de passe pour la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="c367a-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you must supply a user name and password for the Oracle database.</span></span> <span data-ttu-id="c367a-105">Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c367a-105">You should only do this from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="c367a-106">En entrant le Oracle les informations d’identification à partir de la **sécurité** onglet à la place de directement dans le **configurer un URI** champ, vous vérifiez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="c367a-106">By entering the Oracle credentials from the **Security** tab instead of directly into the **Configure a URI** field, you ensure the following:</span></span>  
  
-   <span data-ttu-id="c367a-107">Les informations d’identification ne s’affichera pas dans le **Uri** champ le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.</span><span class="sxs-lookup"><span data-stu-id="c367a-107">The credentials will not be displayed in the **Uri** field of the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dialog box where anyone with access to your computer screen can read them.</span></span>  
  
-   <span data-ttu-id="c367a-108">Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="c367a-108">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="c367a-109">Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour la base de données Oracle, consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c367a-109">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the Oracle database, see [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="c367a-110">Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?</span><span class="sxs-lookup"><span data-stu-id="c367a-110">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="c367a-111">Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service.</span><span class="sxs-lookup"><span data-stu-id="c367a-111"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="c367a-112">À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.</span><span class="sxs-lookup"><span data-stu-id="c367a-112">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="c367a-113">Étant donné que la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice.</span><span class="sxs-lookup"><span data-stu-id="c367a-113">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="c367a-114">Toutefois, il apparaît conseillé de le faire.</span><span class="sxs-lookup"><span data-stu-id="c367a-114">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="c367a-115">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] encourage l’utilisation de la **ClientCredentials** classe.</span><span class="sxs-lookup"><span data-stu-id="c367a-115">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] encourages the use of the **ClientCredentials** class.</span></span> <span data-ttu-id="c367a-116">Cette propriété spécifie si l’adaptateur accepte le nom d’utilisateur et un mot de passe pour la base de données Oracle dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c367a-116">This property specifies whether the adapter will accept the user name and password for the Oracle database in the connection URI.</span></span> <span data-ttu-id="c367a-117">**AcceptCredentialsInUri** par défaut est **false**, ce qui signifie que l’adaptateur lève une exception si l’URI de connexion contient des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="c367a-117">**AcceptCredentialsInUri** defaults to **false**, which means that the adapter will throw an exception if the connection URI contains credentials.</span></span> <span data-ttu-id="c367a-118">Vous pouvez définir **AcceptCredentialsInUri** à **true** pour fournir des informations d’identification dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c367a-118">You can set **AcceptCredentialsInUri** to **true** to supply credentials in the connection URI.</span></span>  
  
 <span data-ttu-id="c367a-119">L’exemple suivant montre comment utiliser le **informations d’identification** propriété à définir les informations d’identification pour la base de données Oracle sur un **ChannelFactory**.</span><span class="sxs-lookup"><span data-stu-id="c367a-119">The following example shows how to use the **Credentials** property to set credentials for the Oracle database on a **ChannelFactory**.</span></span>  
  
```  
// Create binding and endpoint  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress endpointAddress = new EndpointAddress("oracleDB://Adapter");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open the channel factory  
factory.Open();  
```  
  
 <span data-ttu-id="c367a-120">L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification pour la base de données Oracle sur un client WCF.</span><span class="sxs-lookup"><span data-stu-id="c367a-120">The following example shows how to use the **ClientCredentials** class to set credentials for the Oracle database on a WCF client.</span></span>  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
SQLEXECUTEClient sqlExecuteClient = new SQLEXECUTEClient("OracleDBBinding_SQLEXECUTE");  
  
// Set user name and password  
sqlExecuteClient.ClientCredentials.UserName.UserName = "SCOTT";  
sqlExecuteClient.ClientCredentials.UserName.Password = "TIGER";  
  
// Open the client  
sqlExecuteClient.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="c367a-121">Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?</span><span class="sxs-lookup"><span data-stu-id="c367a-121">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="c367a-122">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est hébergé in-process avec l’application ou le service qui la consomme.</span><span class="sxs-lookup"><span data-stu-id="c367a-122">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="c367a-123">Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c367a-123">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="c367a-124">Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="c367a-124">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="c367a-125">fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services.</span><span class="sxs-lookup"><span data-stu-id="c367a-125"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="c367a-126">Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span><span class="sxs-lookup"><span data-stu-id="c367a-126">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span></span> <span data-ttu-id="c367a-127">Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span><span class="sxs-lookup"><span data-stu-id="c367a-127">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c367a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c367a-128">See Also</span></span>  
<span data-ttu-id="c367a-129">[Sécuriser vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c367a-129">[Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md) </span></span>  
[<span data-ttu-id="c367a-130">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="c367a-130">Best Practices</span></span>](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)