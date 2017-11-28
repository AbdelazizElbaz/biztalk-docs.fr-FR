---
title: "À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
description: "Utiliser svcutil.exe pour une liaison non définis par défaut, ou pour créer une classe de Client WCF ou le contrat de Service WCF avec l’adaptateur Siebel - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d16481-cc8b-4e28-a33c-92e48a9a7e8f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0c2c016387f6b70870e04b211b0bdfe047de11d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="a4a8c-103">À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="a4a8c-103">Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="a4a8c-104">Vous pouvez utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF pour les opérations qui les [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-104">You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class for operations that the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes.</span></span> <span data-ttu-id="a4a8c-105">Après avoir exécuté svcutil.exe pour générer une classe de client WCF, vous pouvez inclure le fichier généré dans votre code et créer des instances de la classe de client WCF pour effectuer des opérations sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-105">After you run svcutil.exe to generate a WCF client class, you can include the generated file in your code and create instances of the WCF client class to perform operations on the Siebel system.</span></span>  
  
 <span data-ttu-id="a4a8c-106">À l’aide de svcutil.exe vous oblige à fournir une URI qui contient les informations d’identification de connexion.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-106">Using svcutil.exe requires you to supply a connection URI that contains credentials.</span></span> <span data-ttu-id="a4a8c-107">Étant donné que, par défaut, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] désactive les informations d’identification dans l’URI de connexion, vous devez configurer svcutil.exe pour utiliser une liaison non définis par défaut pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4a8c-107">Because, by default, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="a4a8c-108">Vous pouvez également configurer les autres propriétés de liaison dans la liaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-108">You can also configure other binding properties in the non-default binding.</span></span>  
  
 <span data-ttu-id="a4a8c-109">Les sections suivantes vous montrent comment configurer svcutil.exe et comment utiliser svcutil.exe pour générer le code du client WCF avec les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4a8c-109">The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
##  <span data-ttu-id="a4a8c-110"><a name="BKMK_ConfigureSvcutil"></a>Configuration de svcutil.exe pour une liaison non définis par défaut</span><span class="sxs-lookup"><span data-stu-id="a4a8c-110"><a name="BKMK_ConfigureSvcutil"></a>Configure svcutil.exe for a non-default binding</span></span>   
 <span data-ttu-id="a4a8c-111">Pour configurer svcutil.exe pour utiliser une liaison non définis par défaut, vous devez créer une copie locale de svcutil.exe et ensuite créer ou modifier une copie locale du fichier de configuration svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-111">To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.</span></span>  
  
 
1.  <span data-ttu-id="a4a8c-112">Créez un dossier et copier svcutil.exe dans le nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-112">Create a folder, and copy svcutil.exe into the new folder.</span></span> <span data-ttu-id="a4a8c-113">Vous pouvez généralement trouver svcutil.exe à l’emplacement d’installation du SDK Windows, en particulier, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-113">You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span></span>  
  
2.  <span data-ttu-id="a4a8c-114">Créez un fichier appelé svcutil.exe.config dans le nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-114">Create a file named svcutil.exe.config in the new folder.</span></span>  
  
3.  <span data-ttu-id="a4a8c-115">Ajouter une liaison et un point de terminaison client dans le fichier svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-115">Add a binding and a client endpoint to the svcutil.exe.config file.</span></span> <span data-ttu-id="a4a8c-116">Vous devez exécuter svcutil.exe depuis le nouveau dossier pour vous assurer que la configuration correcte est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-116">You must run svcutil.exe from the new folder to ensure that the correct configuration is used.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a4a8c-117">L’attribut de nom du point de terminaison client doit spécifier le schéma utilisé dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-117">The name attribute of the client endpoint must specify the scheme used in the connection URI.</span></span> <span data-ttu-id="a4a8c-118">Cette valeur respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-118">This value is case-sensitive.</span></span>  
  
    ```  
    <configuration>  
      \<system.serviceModel>  
        <client>  
          \<!-- the name should match the required scheme of the Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="siebel"  
            binding="siebelBinding"  
            bindingConfiguration="SiebelBinding"  
            contract="IMetadataExchange" />  
        </client>  
        <bindings>  
          <siebelBinding>  
            <binding name="SiebelBinding" acceptCredentialsInUri="true" />  
          </siebelBinding>  
        </bindings>  
  
      \</system.serviceModel>  
  
    </configuration>  
  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="a4a8c-119">Vous pouvez définir les propriétés de liaison de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans la configuration de liaison.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-119">You can set any of the binding properties of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in the binding configuration.</span></span>  
  
 <span data-ttu-id="a4a8c-120">Pour plus d’informations sur la configuration d’une liaison par défaut de svcutil.exe, consultez la rubrique « Custom sécuriser les métadonnées Endpoint » dans la documentation WCF à [http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-120">For more information about configuring a non-default binding for svcutil.exe, see the "Custom Secure Metadata Endpoint" topic in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077).</span></span>  
  
## <a name="creating-a-wcf-client-class-with-svcutilexe"></a><span data-ttu-id="a4a8c-121">Création d’une classe de Client WCF avec svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="a4a8c-121">Creating a WCF Client Class with svcutil.exe</span></span>  
 <span data-ttu-id="a4a8c-122">Pour utiliser svcutil.exe pour générer le code du client WCF pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], vous devez fournir une connexion URI qui spécifie un **IMetadataExchange** (mex) au point de terminaison et l’ou les opérations pour lequel vous voulez svcutil.exe pour générer code.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-122">To use svcutil.exe to generate WCF client code for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], you must supply a connection URI that specifies an **IMetadataExchange** (mex) endpoint and the operation or operations for which you want svcutil.exe to generate code.</span></span> <span data-ttu-id="a4a8c-123">Vous devez également spécifier des informations d’identification de connexion pour le système Siebel dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-123">You must also specify connection credentials for the Siebel system in the connection URI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4a8c-124">Avant de pouvoir utiliser svcutil.exe avec la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], vous devez le configurer pour utiliser un non définis par défaut de liaison ; pour plus d’informations sur la procédure à suivre, consultez [configuration de svcutil.exe pour l’adaptateur Siebel](#BKMK_ConfigureSvcutil).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-124">Before you can use svcutil.exe with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the Siebel Adapter](#BKMK_ConfigureSvcutil).</span></span>  
  
 <span data-ttu-id="a4a8c-125">Vous spécifiez une opération de point de terminaison et la cible mex dans le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] URI de connexion de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="a4a8c-125">You specify a mex endpoint and target operations in the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="a4a8c-126">Vous devez inclure le paramètre « wsdl » dans query_string.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-126">You must include the "wsdl" parameter in the query_string.</span></span> <span data-ttu-id="a4a8c-127">S’il est le premier paramètre de query_string, elle est spécifiée juste après le point d’interrogation ( ?).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-127">If it is the first parameter in the query_string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="a4a8c-128">Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-128">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="a4a8c-129">Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ».</span><span class="sxs-lookup"><span data-stu-id="a4a8c-129">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="a4a8c-130">Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’ID de nœud d’une opération de cible.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-130">Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.</span></span>  
  
 <span data-ttu-id="a4a8c-131">Les deux exemples suivants montrent comment cibler différentes opérations à l’aide de svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-131">The following two examples show how to target various operations by using svcutil.exe.</span></span>  
  
 <span data-ttu-id="a4a8c-132">Cet exemple crée une classe de client WCF pour une opération d’insertion dans l’objet métier ACCOUNT\ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-132">This example creates a WCF client class for an insert operation on the ACCOUNT\ACCOUNT Business Object.</span></span>  
  
 <span data-ttu-id="a4a8c-133">**. \svcutil siebel://Username=YourUserName; » Mot de passe =YourPassword@Siebel_server:1234? SiebelEnterpriseServer = ent_server & SiebelObjectManager = obj_mgr & Language = fra & wsdl & op = http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert »**</span><span class="sxs-lookup"><span data-stu-id="a4a8c-133">**.\svcutil "siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"**</span></span>  
  
 <span data-ttu-id="a4a8c-134">Cet exemple crée une classe de client WCF pour une opération d’insertion et une opération de suppression sur l’objet métier ACCOUNT\ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-134">This example creates a WCF client class for both an insert operation and a delete operation on the ACCOUNT\ACCOUNT Business Object.</span></span>  
  
 <span data-ttu-id="a4a8c-135">**. \svcutil siebel://Username=YourUserName; » Mot de passe =YourPassword@Siebel_server:1234? SiebelEnterpriseServer = ent_server & SiebelObjectManager = obj_mgr & Language = fra & wsdl & op = http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert & op = http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete »**</span><span class="sxs-lookup"><span data-stu-id="a4a8c-135">**.\svcutil " siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete"**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a4a8c-136">Vous devez placer l’URI de connexion dans des guillemets sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-136">You must place the connection URI in quotation marks on the command line.</span></span> <span data-ttu-id="a4a8c-137">Sinon, svcutil.exe essaie de récupérer les métadonnées pour les opérations qui les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-137">Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not support.</span></span> <span data-ttu-id="a4a8c-138">Les résultats d’une tentative de ce type ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-138">The results of such an attempt are undefined.</span></span>  
  
 <span data-ttu-id="a4a8c-139">Par défaut, svcutil.exe place le code généré dans le fichier output.cs ; Toutefois, vous pouvez modifier le nom du fichier de sortie et de nombreuses autres options svcutil.exe utilise en définissant des commutateurs de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-139">By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches.</span></span>  
  
 <span data-ttu-id="a4a8c-140">SvcUtil.exe ne fournit pas la fonction de recherche pour les opérations (par exemple, en utilisant des caractères génériques).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-140">Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters).</span></span> <span data-ttu-id="a4a8c-141">Vous devez spécifier explicitement les ID de nœud pour les opérations spécifiques que vous souhaitez cibler.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-141">You must explicitly specify node IDs for the specific operations you want to target.</span></span> <span data-ttu-id="a4a8c-142">Vous ne pouvez pas spécifier les ID font référence uniquement aux catégories de nœud.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-142">You cannot specify node IDs that refer only to categories.</span></span> <span data-ttu-id="a4a8c-143">Pour plus d’informations sur l’ID du nœud qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-143">For more information about the node IDs that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).</span></span>  
  
 <span data-ttu-id="a4a8c-144">Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] fournit les fonctionnalités de recherche qui peuvent grandement simplifier la génération d’une classe de client WCF et les parcourir avancée.</span><span class="sxs-lookup"><span data-stu-id="a4a8c-144">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class.</span></span> <span data-ttu-id="a4a8c-145">Pour plus d’informations sur la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Siebel](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="a4a8c-145">For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for Siebel solution artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).</span></span>  
  
