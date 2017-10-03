---
title: "Publication des métadonnées de Service WCF pour les adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF services, publishing
ms.assetid: 4df09e8f-e0c9-41c5-bd71-13bb0e96cd97
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d922c0acecf81a96b0e40cebf739e7b56c5ffd3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-service-metadata-for-the-wcf-receive-adapters"></a><span data-ttu-id="33cd5-102">Publication des métadonnées de Service WCF pour les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="33cd5-102">Publishing Service Metadata for the WCF Receive Adapters</span></span>
<span data-ttu-id="33cd5-103">L'Assistant Publication de services WCF BizTalk permet de créer des services WCF à des fins de publication des métadonnées de service pour les emplacements de réception WCF existants.</span><span class="sxs-lookup"><span data-stu-id="33cd5-103">You can use the BizTalk WCF Service Publishing Wizard to create WCF services for publishing service metadata for existing WCF receive locations.</span></span> <span data-ttu-id="33cd5-104">Pour générer le code de modèle de service client à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Kit de développement logiciel (SDK) pour [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] et [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Composants d’exécution.</span><span class="sxs-lookup"><span data-stu-id="33cd5-104">To generate client service model code from the published metadata documents you can use the Service Model Metadata Utility tool (SvcUtil.exe) included in the [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Software Development Kit (SDK) for [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] and [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Runtime Components.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33cd5-105">Avant de publier des métadonnées de service pour les adaptateurs WCF, vous devez créer WCF à l’aide de la console Administration de BizTalk ou l’outil de ligne de commande BTSTask inclus dans les emplacements de réception [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33cd5-105">Before you publish service metadata for the WCF adapters, you must create the WCF receive locations by using the BizTalk Administration console or the BTSTask command-line tool included with [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="33cd5-106">Pour plus d’informations sur la création d’un service WCF, emplacement de réception, consultez la rubrique appropriée pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="33cd5-106">For more information about how to create a WCF receive location, see the appropriate topic for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
 <span data-ttu-id="33cd5-107">**Versions d’IIS**</span><span class="sxs-lookup"><span data-stu-id="33cd5-107">**Versions of IIS**</span></span>  
  
 <span data-ttu-id="33cd5-108">Le service WCF qui publie les métadonnées de service peut être exécuté sur les versions suivantes d'Internet Information Services (IIS) sous les systèmes d'exploitation suivants :</span><span class="sxs-lookup"><span data-stu-id="33cd5-108">The WCF service that publishes service metadata can be running on the following versions of Internet Information Services (IIS) on the following operating systems:</span></span>  
  
-   <span data-ttu-id="33cd5-109">**IIS 7.0/7.5 sur Windows Vista, Windows Server 2008 SP2 et Windows Server 2008 R2.**</span><span class="sxs-lookup"><span data-stu-id="33cd5-109">**IIS 7.0/7.5 on Windows Vista, Windows Server 2008 SP2, and Windows Server 2008 R2.**</span></span> <span data-ttu-id="33cd5-110">IIS 7.0/7.5 incluent le même modèle de processus avancé qu'IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="33cd5-110">IIS 7.0/7.5 provide the same advanced process model as IIS 6.0.</span></span> <span data-ttu-id="33cd5-111">Les services WCF BizTalk publiés doivent être exécutés dans le mode de compatibilité ASP.NET d'IIS 7.0/7.5.</span><span class="sxs-lookup"><span data-stu-id="33cd5-111">The published BizTalk WCF services must run in ASP.NET Compatibility Mode of IIS 7.0/7.5.</span></span> <span data-ttu-id="33cd5-112">Les métadonnées de service publiées par les applications Web dans IIS 7.0/7.5 pour les adaptateurs de réception WCF sont accessibles via le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="33cd5-112">The service metadata published by Web applications in IIS 7.0/7.5 for the WCF receive adapters can be accessed over the HTTP transport.</span></span>  
  
 <span data-ttu-id="33cd5-113">**Publication des métadonnées de service pour les emplacements de réception WCF**</span><span class="sxs-lookup"><span data-stu-id="33cd5-113">**Publishing service metadata for the WCF receive locations**</span></span>  
  
 <span data-ttu-id="33cd5-114">Pour publier les métadonnées de service pour les emplacements de réception, vous devez utiliser l'Assistant Publication de services WCF BizTalk pour créer une application Web qui héberge les services WCF afin de fournir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="33cd5-114">To publish service metadata for the WCF receive locations, you must use the BizTalk WCF Service Publishing Wizard to create a Web application to host WCF services that provide the service metadata.</span></span> <span data-ttu-id="33cd5-115">Ceci permet à un emplacement de réception d'être appelé comme s'il était un service WCF.</span><span class="sxs-lookup"><span data-stu-id="33cd5-115">This allows a receive location to be called as if it were a WCF service.</span></span>  <span data-ttu-id="33cd5-116">L'Assistant Publication de services WCF BizTalk génère les fichiers suivants dans le dossier racine de l'application Web créée :</span><span class="sxs-lookup"><span data-stu-id="33cd5-116">The BizTalk WCF Service Publishing Wizard generates the following files in the root folder of the created Web application:</span></span>  
  
|<span data-ttu-id="33cd5-117">Fichier</span><span class="sxs-lookup"><span data-stu-id="33cd5-117">File</span></span>|<span data-ttu-id="33cd5-118">Dossier</span><span class="sxs-lookup"><span data-stu-id="33cd5-118">Folder</span></span>|<span data-ttu-id="33cd5-119"> Description</span><span class="sxs-lookup"><span data-stu-id="33cd5-119">Description</span></span>|  
|----------|------------|-----------------|  
|<span data-ttu-id="33cd5-120">Services WCF (fichiers .svc)</span><span class="sxs-lookup"><span data-stu-id="33cd5-120">WCF services (.svc files)</span></span>|\|<span data-ttu-id="33cd5-121">Services WCF qui publient les métadonnées de service pour les emplacements de réception WCF.</span><span class="sxs-lookup"><span data-stu-id="33cd5-121">WCF services that publish service metadata for the WCF receive locations.</span></span> <span data-ttu-id="33cd5-122">Les services WCF publient les métadonnées de service pour extraction à l'aide d'une requête HTTP/GET.</span><span class="sxs-lookup"><span data-stu-id="33cd5-122">The WCF services publish service metadata for retrieval using an HTTP/GET request.</span></span>|  
|<span data-ttu-id="33cd5-123">Web.config</span><span class="sxs-lookup"><span data-stu-id="33cd5-123">Web.config</span></span>|\|<span data-ttu-id="33cd5-124">Fichier de configuration ASP.NET contenant les informations relatives aux comportements des applications Web ASP.NET, aux comportements des services WCF publiés, au point de terminaison des métadonnées et aux paramètres spécifiques à BizTalk.</span><span class="sxs-lookup"><span data-stu-id="33cd5-124">ASP.NET configuration file that contains information for the ASP.NET Web application behaviors, the published WCF service behaviors, the metadata endpoint, and the BizTalk-specific settings.</span></span> <span data-ttu-id="33cd5-125">L’Assistant génère le fichier Web.config lorsque la **httpGetEnabled** attribut de la  **\<serviceMetadata >** a la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="33cd5-125">The wizard generates Web.config when the **httpGetEnabled** attribute of the **\<serviceMetadata>** element is set to **true**.</span></span> <span data-ttu-id="33cd5-126">Vous pouvez utiliser un outil d'importation de métadonnées (tel que SvcUtil.exe) pour générer le code client requis pour appeler ce service dans l'environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="33cd5-126">You can use a metadata import tool (such as SvcUtil.exe) to generate the client code required to call this service in the development environment.</span></span> <span data-ttu-id="33cd5-127">L’adresse à laquelle les métadonnées sont publiées est l’adresse de point de terminaison du service WCF plus une **? wsdl** chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="33cd5-127">The address at which the metadata is published is the endpoint address of the WCF service plus a **?wsdl** query string.</span></span> <span data-ttu-id="33cd5-128">**Remarque :** la liaison de métadonnées par défaut générée par l’Assistant Publication WCF BizTalk n’est pas sécurisée et il autorise l’accès anonyme aux métadonnées.</span><span class="sxs-lookup"><span data-stu-id="33cd5-128">**Note:**  The default metadata binding generated by the BizTalk WCF Publishing Wizard is not secure and it allows anonymous access to the metadata.</span></span> <span data-ttu-id="33cd5-129">Les métadonnées de service contiennent une description détaillée du service et peuvent, intentionnellement ou non, contenir des informations sensibles.</span><span class="sxs-lookup"><span data-stu-id="33cd5-129">The service metadata contains a detailed description about the service and may intentionally or unintentionally contain sensitive information.</span></span> <span data-ttu-id="33cd5-130">Pour protéger les métadonnées de service contre un accès non autorisé, vous pouvez modifier le fichier Web.config pour utiliser une liaison sécurisée pour votre point de terminaison des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="33cd5-130">To protect service metadata from unauthorized access, you can modify Web.config to use a secure binding for your metadata endpoint.</span></span>|  
|<span data-ttu-id="33cd5-131">ServiceDescription.xml</span><span class="sxs-lookup"><span data-stu-id="33cd5-131">ServiceDescription.xml</span></span>|\|<span data-ttu-id="33cd5-132">Fichier XML qui décrit les contrats de service WCF publiés, types de messages inclus.</span><span class="sxs-lookup"><span data-stu-id="33cd5-132">XML file that describes the published WCF service contracts including the message types.</span></span>|  
|<span data-ttu-id="33cd5-133">Schémas BizTalk (fichiers .xsd)</span><span class="sxs-lookup"><span data-stu-id="33cd5-133">BizTalk schemas (.xsd files)</span></span>|<span data-ttu-id="33cd5-134">\App_Data</span><span class="sxs-lookup"><span data-stu-id="33cd5-134">\App_Data</span></span>|<span data-ttu-id="33cd5-135">Schémas XML définissant la structure des messages d'instance XML, qui sont utilisés dans l'emplacement de réception WCF.</span><span class="sxs-lookup"><span data-stu-id="33cd5-135">XML schemas defining the structure of XML instance messages, which are used in the WCF receive location.</span></span>|  
|<span data-ttu-id="33cd5-136">SchemaIndex.xml</span><span class="sxs-lookup"><span data-stu-id="33cd5-136">SchemaIndex.xml</span></span>|<span data-ttu-id="33cd5-137">\App_Data</span><span class="sxs-lookup"><span data-stu-id="33cd5-137">\App_Data</span></span>|<span data-ttu-id="33cd5-138">Fichier XML qui indique les fichiers de schéma XML utilisés dans l'emplacement de réception WCF.</span><span class="sxs-lookup"><span data-stu-id="33cd5-138">XML file that indicates the XML schema files used in the WCF receive location.</span></span>|  
|<span data-ttu-id="33cd5-139">Serialization.xsd</span><span class="sxs-lookup"><span data-stu-id="33cd5-139">Serialization.xsd</span></span>|<span data-ttu-id="33cd5-140">\App_Data</span><span class="sxs-lookup"><span data-stu-id="33cd5-140">\App_Data</span></span>|<span data-ttu-id="33cd5-141">Schéma XML exporté par [DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722) pour les types, les éléments et les attributs à partir de l’espace de noms, http://schemas.microsoft.com/2003/10/Serialization/.</span><span class="sxs-lookup"><span data-stu-id="33cd5-141">XML schema exported by [DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722) for the types, elements, and attributes from the namespace, http://schemas.microsoft.com/2003/10/Serialization/.</span></span>|  
|<span data-ttu-id="33cd5-142">BindingInfo.xml</span><span class="sxs-lookup"><span data-stu-id="33cd5-142">BindingInfo.xml</span></span>|<span data-ttu-id="33cd5-143">\App_Data\Temp</span><span class="sxs-lookup"><span data-stu-id="33cd5-143">\App_Data\Temp</span></span>|<span data-ttu-id="33cd5-144">Fichier de liaison BizTalk qui peut être importé à l'aide d'un outil ou d'un Assistant de ligne de commande pour configurer les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="33cd5-144">BizTalk binding file that can be imported by the development command-line tool or wizard to configure the receive locations.</span></span> <span data-ttu-id="33cd5-145">Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="33cd5-145">The published WCF services do not use this file and the Temp folder at run time.</span></span>|  
|<span data-ttu-id="33cd5-146">WcfServiceDescription.xml</span><span class="sxs-lookup"><span data-stu-id="33cd5-146">WcfServiceDescription.xml</span></span>|<span data-ttu-id="33cd5-147">\App_Data\Temp</span><span class="sxs-lookup"><span data-stu-id="33cd5-147">\App_Data\Temp</span></span>|<span data-ttu-id="33cd5-148">Fichier XML qui résume les paramètres que vous avez utilisés avec l'Assistant Publication de services WCF BizTalk pour créer cette application Web.</span><span class="sxs-lookup"><span data-stu-id="33cd5-148">XML file that summarizes the settings that you used with the BizTalk WCF Service Publishing Wizard to create this Web application.</span></span> <span data-ttu-id="33cd5-149">Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="33cd5-149">The published WCF services do not use this file and the Temp folder at run time.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="33cd5-150">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="33cd5-150">In This Section</span></span>  
  
-   [<span data-ttu-id="33cd5-151">Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception d’un service WCF pour le routage basé sur le contenu</span><span class="sxs-lookup"><span data-stu-id="33cd5-151">How to Use the BizTalk WCF Service Publishing Wizard to Publish Service Metadata for a WCF Receive Location for Content-Based Routing</span></span>](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md)  
  
-   [<span data-ttu-id="33cd5-152">Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception WCF lié à un Port d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="33cd5-152">How to Use the BizTalk WCF Service Publishing Wizard to Publish Service Metadata for a WCF Receive Location Bound to an Orchestration Port</span></span>](../core/publish-receive-location-service-metadata-biztalk-wcf-service-publishing-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="33cd5-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33cd5-153">See Also</span></span>  
 [<span data-ttu-id="33cd5-154">Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="33cd5-154">Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)