---
title: "À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
description: "Utiliser svcutil.exe pour une liaison non définis par défaut, ou pour créer une classe de Client WCF ou le contrat de Service WCF avec l’adaptateur SAP - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceModel Metadata Utility Tool, creating a WCF Client Class or a WCF service contract with the tool
- ServiceModel Metadata Utility Tool, configuring the tool for the adapter
ms.assetid: 7ac08012-bb12-4983-9402-be84fe3997d8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac86d1aa254de81c2778ce1a2c1f0e63c1c1e1ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="df43a-103">À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="df43a-103">Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="df43a-104">Vous pouvez utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ou un contrat de service WCF (interface) pour les opérations qui les [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose.</span><span class="sxs-lookup"><span data-stu-id="df43a-104">You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class or a WCF service contract (interface) for operations that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes.</span></span> <span data-ttu-id="df43a-105">Après avoir exécuté svcutil.exe pour générer une classe de client WCF ou d’un contrat de service WCF, vous pouvez inclure le fichier généré dans votre code et créer des instances de la classe générée ou implémenter un service WCF à partir de l’interface générée pour effectuer des opérations sur SAP système.</span><span class="sxs-lookup"><span data-stu-id="df43a-105">After you run svcutil.exe to generate either a WCF client class or a WCF service contract, you can include the generated file in your code and create instances of the generated class or implement a WCF service from the generated interface to perform operations on the SAP system.</span></span>  
  
 <span data-ttu-id="df43a-106">À l’aide de svcutil.exe vous oblige à fournir une URI qui contient les informations d’identification de connexion.</span><span class="sxs-lookup"><span data-stu-id="df43a-106">Using svcutil.exe requires you to supply a connection URI that contains credentials.</span></span> <span data-ttu-id="df43a-107">Étant donné que, par défaut, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] désactive les informations d’identification dans l’URI de connexion, vous devez configurer svcutil.exe pour utiliser une liaison non définis par défaut pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df43a-107">Because, by default, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="df43a-108">Vous pouvez également configurer les autres propriétés de liaison dans la liaison par défaut ; par exemple, pour créer un client WCF pour des opérations BAPI, vous devez définir le **EnableSafeTyping** liaison de propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="df43a-108">You can also configure other binding properties in the non-default binding; for example, to create a WCF client for BAPI operations, you must set the **EnableSafeTyping** binding property to **true**.</span></span>  
  
 <span data-ttu-id="df43a-109">Les sections suivantes vous montrent comment configurer svcutil.exe et comment utiliser svcutil.exe pour générer le code du client WCF ou un contrat de service WCF avec les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df43a-109">The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code or a WCF service contract with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
##  <span data-ttu-id="df43a-110"><a name="BKMK_ConfigureSvcutil"></a>Configuration de svcutil.exe pour l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="df43a-110"><a name="BKMK_ConfigureSvcutil"></a> Configuring svcutil.exe for the SAP Adapter</span></span>  
 <span data-ttu-id="df43a-111">Pour configurer svcutil.exe pour utiliser une liaison non définis par défaut, vous devez créer une copie locale de svcutil.exe et ensuite créer ou modifier une copie locale du fichier de configuration svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="df43a-111">To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.</span></span>  
  
1.  <span data-ttu-id="df43a-112">Créez un dossier et copier svcutil.exe dans le nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="df43a-112">Create a folder, and copy svcutil.exe into the new folder.</span></span> <span data-ttu-id="df43a-113">Vous pouvez généralement trouver svcutil.exe à l’emplacement d’installation du SDK Windows, en particulier, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="df43a-113">You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span></span>  
  
2.  <span data-ttu-id="df43a-114">Créez un fichier appelé svcutil.exe.config dans le nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="df43a-114">Create a file named svcutil.exe.config in the new folder.</span></span>  
  
3.  <span data-ttu-id="df43a-115">Ajouter une liaison et un point de terminaison client dans le fichier svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="df43a-115">Add a binding and a client endpoint to the svcutil.exe.config file.</span></span> <span data-ttu-id="df43a-116">Vous devez exécuter svcutil.exe depuis le nouveau dossier pour vous assurer que la configuration correcte est utilisée.</span><span class="sxs-lookup"><span data-stu-id="df43a-116">You must run svcutil.exe from the new folder to ensure that the correct configuration is used.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="df43a-117">L’attribut de nom du point de terminaison client doit spécifier le schéma utilisé dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="df43a-117">The name attribute of the client endpoint must specify the scheme used in the connection URI.</span></span> <span data-ttu-id="df43a-118">Cette valeur respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="df43a-118">This value is case-sensitive.</span></span>  
  
    ```  
    <configuration>  
      \<system.serviceModel>  
        <client>  
          \<!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="sap"  
                    binding="sapBinding"  
                    bindingConfiguration="SAPBinding"  
                    contract="IMetadataExchange" />  
        </client>  
        <bindings>  
          <sapBinding>  
            <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
          </sapBinding>  
        </bindings>  
  
      \</system.serviceModel>  
  
    </configuration>  
    ```  
  
 <span data-ttu-id="df43a-119">Vous pouvez définir les propriétés de liaison de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans la configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="df43a-119">You can set any of the binding properties of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in the binding configuration.</span></span> <span data-ttu-id="df43a-120">Par exemple, vous pouvez spécifier la liaison par défaut suivante pour utiliser svcutil.exe pour générer un client WCF pour des opérations BAPI.</span><span class="sxs-lookup"><span data-stu-id="df43a-120">For example, you could specify the following non-default binding to use svcutil.exe to generate a WCF client for BAPI operations.</span></span>  
  
```  
<bindings>  
  <sapBinding>  
    <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
  </sapBinding>  
</bindings>  
```  
  
 <span data-ttu-id="df43a-121">Pour plus d’informations sur la configuration d’une liaison par défaut de svcutil.exe, consultez le [personnalisé sécuriser les métadonnées de point de terminaison](https://msdn.microsoft.com/library/aa395212.aspx).</span><span class="sxs-lookup"><span data-stu-id="df43a-121">For more information about configuring a non-default binding for svcutil.exe, see the [Custom Secure Metadata Endpoint](https://msdn.microsoft.com/library/aa395212.aspx).</span></span>
  
## <a name="creating-a-wcf-client-class-or-a-wcf-service-contract-with-svcutilexe"></a><span data-ttu-id="df43a-122">Création d’une classe de Client WCF ou d’un contrat de Service WCF avec svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="df43a-122">Creating a WCF Client Class or a WCF Service Contract with svcutil.exe</span></span>  
 <span data-ttu-id="df43a-123">Pour utiliser svcutil.exe pour générer le code du client WCF ou un contrat de service WCF (interface) pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez fournir une URI qui spécifie un point de terminaison WS-MEX (Metadata Exchange) et l’ou les opérations dont vous voulez svcutil.exe pour connexion générer du code.</span><span class="sxs-lookup"><span data-stu-id="df43a-123">To use svcutil.exe to generate WCF client code or a WCF service contract (interface) for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must supply a connection URI that specifies a WS-Metadata Exchange (MEX) endpoint and the operation or operations for which you want svcutil.exe to generate code.</span></span> <span data-ttu-id="df43a-124">Vous devez également spécifier des informations d’identification de connexion pour le système SAP dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="df43a-124">You must also specify connection credentials for the SAP system in the connection URI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df43a-125">Avant de pouvoir utiliser svcutil.exe avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez le configurer pour utiliser un non définis par défaut de liaison ; pour plus d’informations sur la procédure à suivre, consultez [configuration de svcutil.exe pour l’adaptateur SAP](#BKMK_ConfigureSvcutil).</span><span class="sxs-lookup"><span data-stu-id="df43a-125">Before you can use svcutil.exe with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the SAP Adapter](#BKMK_ConfigureSvcutil).</span></span>  
  
 <span data-ttu-id="df43a-126">Vous spécifiez une opération de point de terminaison et la cible MEX dans le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] URI de connexion de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="df43a-126">You specify a MEX endpoint and target operations in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="df43a-127">Vous devez inclure le paramètre « wsdl » dans la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="df43a-127">You must include the "wsdl" parameter in the query string.</span></span> <span data-ttu-id="df43a-128">S’il est le premier paramètre dans la chaîne de requête, il est spécifié juste après le point d’interrogation ( ?).</span><span class="sxs-lookup"><span data-stu-id="df43a-128">If it is the first parameter in the query string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="df43a-129">Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="df43a-129">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="df43a-130">Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ».</span><span class="sxs-lookup"><span data-stu-id="df43a-130">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="df43a-131">Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’ID de nœud d’une opération de cible.</span><span class="sxs-lookup"><span data-stu-id="df43a-131">Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.</span></span>  
  
 <span data-ttu-id="df43a-132">Les trois exemples suivants montrent comment cibler différentes opérations à l’aide de svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="df43a-132">The following three examples show how to target various operations by using svcutil.exe.</span></span>  
  
 <span data-ttu-id="df43a-133">Cet exemple crée une classe de client WCF pour RFC_CALCULATE_TAXES.</span><span class="sxs-lookup"><span data-stu-id="df43a-133">This example creates a WCF client class for RFC_CALCULATE_TAXES.</span></span>  
  
 <span data-ttu-id="df43a-134">**.\svcutil «sap://User=YourUserName;MotDePasse=votreMotdePasse;Client=800;Lang=FR;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES»**</span><span class="sxs-lookup"><span data-stu-id="df43a-134">**.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**</span></span>  
  
 <span data-ttu-id="df43a-135">Cet exemple crée une classe de client WCF pour les SALESORDER_CREATEFROMDAT201 et SALESORDER_CREATEFROMDAT202 IDOC.</span><span class="sxs-lookup"><span data-stu-id="df43a-135">This example creates a WCF client class for both the SALESORDER_CREATEFROMDAT201 and SALESORDER_CREATEFROMDAT202 IDOC.</span></span>  
  
 <span data-ttu-id="df43a-136">**.\svcutil «sap://User=YourUserName;Motdepasse=votreMotdePasse;Client=800;Lang=fr;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send»**</span><span class="sxs-lookup"><span data-stu-id="df43a-136">**.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**</span></span>  
  
 <span data-ttu-id="df43a-137">Cet exemple crée un contrat de service WCF pour recevoir l’IDOC SALESORDER_CREATEFROMDAT201 à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="df43a-137">This example creates a WCF service contract to receive the SALESORDER_CREATEFROMDAT201 IDOC from the SAP system.</span></span> <span data-ttu-id="df43a-138">L’ID de nœud spécifie une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="df43a-138">The NODE ID specifies a Receive operation.</span></span> <span data-ttu-id="df43a-139">Cet exemple porte sur la récupération des métadonnées, il n’est pas nécessaire de spécifier les paramètres de l’écouteur dans query_string de l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="df43a-139">Because this example deals with retrieving metadata, there is no need to specify the listener parameters in the query_string of the connection URI.</span></span>  
  
 <span data-ttu-id="df43a-140">**.\svcutil «sap://User=YourUserName;Motdepasse=votreMotdePasse;Client=800;Lang=fr;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive»**</span><span class="sxs-lookup"><span data-stu-id="df43a-140">**.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="df43a-141">Vous devez placer l’URI de connexion dans des guillemets sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="df43a-141">You must place the connection URI in quotation marks on the command line.</span></span> <span data-ttu-id="df43a-142">Sinon, svcutil.exe essaie de récupérer les métadonnées pour les opérations qui les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="df43a-142">Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support.</span></span> <span data-ttu-id="df43a-143">Les résultats d’une tentative de ce type ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="df43a-143">The results of such an attempt are undefined.</span></span>  
  
 <span data-ttu-id="df43a-144">Par défaut, svcutil.exe place le code généré dans le fichier output.cs ; Toutefois, vous pouvez modifier le nom du fichier de sortie et de nombreuses autres options svcutil.exe utilise en définissant des commutateurs de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="df43a-144">By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches.</span></span> <span data-ttu-id="df43a-145">Pour plus d’informations sur les options que svcutil.exe prend en charge, consultez la [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="df43a-145">For more information about the options that svcutil.exe supports, see the [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).</span></span>
  
 <span data-ttu-id="df43a-146">SvcUtil.exe ne fournit pas la fonction de recherche pour les opérations (par exemple, en utilisant des caractères génériques).</span><span class="sxs-lookup"><span data-stu-id="df43a-146">Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters).</span></span> <span data-ttu-id="df43a-147">Vous devez spécifier explicitement les ID de nœud pour les opérations spécifiques que vous souhaitez cibler.</span><span class="sxs-lookup"><span data-stu-id="df43a-147">You must explicitly specify node IDs for the specific operations you want to target.</span></span> <span data-ttu-id="df43a-148">L’ID de nœud d’une opération est équivalente à la chaîne d’action de message.</span><span class="sxs-lookup"><span data-stu-id="df43a-148">The node ID of an operation is equivalent to its message action string.</span></span> <span data-ttu-id="df43a-149">Vous ne pouvez pas spécifier les ID font référence uniquement aux catégories de nœud.</span><span class="sxs-lookup"><span data-stu-id="df43a-149">You cannot specify node IDs that refer only to categories.</span></span> <span data-ttu-id="df43a-150">Pour plus d’informations sur l’ID du nœud qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span><span class="sxs-lookup"><span data-stu-id="df43a-150">For more information about the node IDs that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).</span></span>  
  
 <span data-ttu-id="df43a-151">Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] offre des avancées et fonctionnalités de recherche qui peuvent grandement simplifier la génération d’une classe de client WCF et d’un contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="df43a-151">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class and WCF service contract.</span></span> <span data-ttu-id="df43a-152">Pour plus d’informations sur la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="df43a-152">For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
