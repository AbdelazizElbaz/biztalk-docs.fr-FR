---
title: "Programmation sécurisée avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security considerations, when programming on the adapter
- credentials, best practices for setting in code
- credentials, protecting when using the Add Adapter Service Reference Visual Studio Plug-in
- security, best practices for setting credentials in code
ms.assetid: 8c2b6b36-7bd9-4678-a9c2-450e818f607a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aebe93918741b2603b8090add7ff40ed731097d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-siebel-adapter"></a><span data-ttu-id="577a9-102">Programmation sécurisée avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="577a9-102">Secure programming with the Siebel adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="577a9-103">Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?</span><span class="sxs-lookup"><span data-stu-id="577a9-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="577a9-104">Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devez fournir un nom d’utilisateur et un mot de passe pour le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="577a9-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you must supply a user name and password for the Siebel system.</span></span> <span data-ttu-id="577a9-105">Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="577a9-105">You should only do this from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="577a9-106">En entrant le Siebel les informations d’identification à partir de la **sécurité** onglet à la place de directement dans le **Uri** champ, vous vérifiez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="577a9-106">By entering the Siebel credentials from the **Security** tab instead of directly into the **Uri** field, you ensure the following:</span></span>  
  
-   <span data-ttu-id="577a9-107">Les informations d’identification ne s’affichera pas dans le **Uri** champ le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.</span><span class="sxs-lookup"><span data-stu-id="577a9-107">The credentials will not be displayed in the **Uri** field of the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dialog box where anyone with access to your computer screen can read them.</span></span>  
  
-   <span data-ttu-id="577a9-108">Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="577a9-108">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="577a9-109">Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour le système Siebel, consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="577a9-109">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the Siebel system, see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="577a9-110">Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?</span><span class="sxs-lookup"><span data-stu-id="577a9-110">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="577a9-111">Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service.</span><span class="sxs-lookup"><span data-stu-id="577a9-111"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="577a9-112">À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.</span><span class="sxs-lookup"><span data-stu-id="577a9-112">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="577a9-113">Étant donné que la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice.</span><span class="sxs-lookup"><span data-stu-id="577a9-113">Because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="577a9-114">Toutefois, il apparaît conseillé de le faire.</span><span class="sxs-lookup"><span data-stu-id="577a9-114">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="577a9-115">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] encourage l’utilisation de la **ClientCredentials** par le biais du **AcceptCredentialsInUri** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="577a9-115">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] encourages the use of the **ClientCredentials** class through the **AcceptCredentialsInUri** binding property.</span></span> <span data-ttu-id="577a9-116">Cette propriété spécifie si l’adaptateur accepte le nom d’utilisateur et un mot de passe pour le système Siebel dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="577a9-116">This property specifies whether the adapter will accept the user name and password for the Siebel system in the connection URI.</span></span> <span data-ttu-id="577a9-117">**AcceptCredentialsInUri** par défaut est **false**, ce qui signifie que l’adaptateur lève une exception si l’URI de connexion contient des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="577a9-117">**AcceptCredentialsInUri** defaults to **false**, which means that the adapter will throw an exception if the connection URI contains credentials.</span></span> <span data-ttu-id="577a9-118">Vous pouvez définir **AcceptCredentialsInUri** à **true** pour fournir des informations d’identification dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="577a9-118">You can set **AcceptCredentialsInUri** to **true** to supply credentials in the connection URI.</span></span> <span data-ttu-id="577a9-119">En fait, vous devez le faire dans certains cas ; par exemple, lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF pour les artefacts du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="577a9-119">In fact, you must do this in certain cases; for example, when you use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class for Siebel system artifacts.</span></span>  
  
 <span data-ttu-id="577a9-120">L’exemple suivant montre comment utiliser le **informations d’identification** classe pour définir les informations d’identification pour le système Siebel sur un **ChannelFactory**.</span><span class="sxs-lookup"><span data-stu-id="577a9-120">The following example shows how to use the **Credentials** class to set credentials for the Siebel system on a **ChannelFactory**.</span></span>  
  
```  
// Create binding and endpoint  
SiebelBinding binding = new SiebelBinding();  
EndpointAddress endpointAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=entserver&Language=enu ");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 <span data-ttu-id="577a9-121">L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification pour le système Siebel sur un client WCF.</span><span class="sxs-lookup"><span data-stu-id="577a9-121">The following example shows how to use the **ClientCredentials** class to set credentials for the Siebel system on a WCF client.</span></span>  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
BusinessObjects_Account_Account_OperationClient accountAccountClient = new BusinessObjects_Account_Account_OperationClient ("SiebelBinding_BusinessObjects_Account_Account_Operation");  
  
// Set user name and password  
accountAccountClient.ClientCredentials.UserName.UserName = "YourUserName";  
accountAccountClient.ClientCredentials.UserName.Password = "YourPassword";  
  
// Open the client  
accountAccountClient.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="577a9-122">Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?</span><span class="sxs-lookup"><span data-stu-id="577a9-122">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="577a9-123">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est hébergé in-process avec l’application ou le service qui la consomme.</span><span class="sxs-lookup"><span data-stu-id="577a9-123">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="577a9-124">Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="577a9-124">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="577a9-125">Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="577a9-125">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="577a9-126">fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services.</span><span class="sxs-lookup"><span data-stu-id="577a9-126"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="577a9-127">Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span><span class="sxs-lookup"><span data-stu-id="577a9-127">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span></span> <span data-ttu-id="577a9-128">Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span><span class="sxs-lookup"><span data-stu-id="577a9-128">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="577a9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="577a9-129">See Also</span></span>  
 [<span data-ttu-id="577a9-130">Sécuriser vos applications Siebel</span><span class="sxs-lookup"><span data-stu-id="577a9-130">Secure your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)  
[<span data-ttu-id="577a9-131">Meilleures pratiques pour sécuriser l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="577a9-131">Best practices to secure the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)