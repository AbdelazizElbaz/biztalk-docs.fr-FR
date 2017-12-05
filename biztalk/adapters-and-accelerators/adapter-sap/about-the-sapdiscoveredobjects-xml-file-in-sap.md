---
title: Sur le fichier SAPDiscoveredObjects.xml dans SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAPDiscoveredObjects.xml
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- Visual Studio DDEX plug-in
ms.assetid: 46ef600d-57ae-4c42-94ce-3099e42482f1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ba0c156e2ad6ab0fcbccb5ba7629f63b0aa490e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="about-the-sapdiscoveredobjectsxml-file-in-sap"></a><span data-ttu-id="6a7ce-102">Sur le fichier SAPDiscoveredObjects.xml dans SAP</span><span class="sxs-lookup"><span data-stu-id="6a7ce-102">About the SAPDiscoveredObjects.xml File in SAP</span></span>
<span data-ttu-id="6a7ce-103">Si vous avez choisi d’installer le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, le programme d’installation copie le fichier SAPDiscoveredObjects.xml en général au \<lecteur d’installation\>: \Program fichiers \Microsoft Shared\Adapters\SAP.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-103">If you chose to install the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) along with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, the setup program copies the SAPDiscoveredObjects.xml file typically at \<installation drive\>:\Program Files\Common Files\Microsoft Shared\Adapters\SAP.</span></span> <span data-ttu-id="6a7ce-104">Le contenu du fichier, après une nouvelle installation de le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], similaire à la suivante.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-104">The contents of the file, after a fresh installation of the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], resemble the following.</span></span>  
  
```  
<DiscoveredObjects>  
  <SAP>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 <span data-ttu-id="6a7ce-105">L’objectif du fichier SAPDiscoveredObjects.xml consiste à stocker les objets SAP (tables et RFC) que vous découvrez à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] plug-in DDEX.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-105">The purpose of the SAPDiscoveredObjects.xml file is to store the SAP objects (tables and RFCs) that you discover using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in.</span></span> <span data-ttu-id="6a7ce-106">Une fois que vous avez utilisé le plug-in DDEX pour ajouter des objets SAP, ils sont ajoutés à ce fichier XML.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-106">Once you have used the DDEX plug-in to add more SAP objects, they are added to this XML file.</span></span> <span data-ttu-id="6a7ce-107">Voici à quoi ressemble le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-107">The XML file looks like this.</span></span>  
  
```  
<DiscoveredObjects>  
  <SAP>  
    <Server name="server_name" user="user_name" client="800" type="connection_type">  
      <Tables>  
        <Table>KNA1</Table>  
        <Table>KNAS</Table>  
        <Table>KNAT</Table>  
      </Tables>  
      <RFCs>  
        <RFC>CUSTOMER_CONTACTPS_GET</RFC>  
        <RFC>CUSTOMER_CONTROL_AREA_DATA</RFC>  
        <RFC>CUSTOMER_PARTNERFS_GET</RFC>  
      </RFCs>  
    </Server>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 <span data-ttu-id="6a7ce-108">Le `name` propriétés de la < Server\> élément contient le nom du serveur auquel vous vous connectez à l’aide du plug-in DDEX.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-108">The `name` property of the <Server\> element contains the name of the server that you connect to using the DDEX plug-in.</span></span> <span data-ttu-id="6a7ce-109">Le `user` et `client` propriétés de la < Server\> élément contiennent les numéros de client et le nom d’utilisateur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-109">The `user` and `client` properties of the <Server\> element contain the user name and client numbers, respectively.</span></span> <span data-ttu-id="6a7ce-110">Le `type` propriété contient le type de chaîne de connexion (A, B ou D) utilisé pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-110">The `type` property contains the type of connection string (A, B, or D) used to connect to an SAP system.</span></span> <span data-ttu-id="6a7ce-111">Pour plus d’informations sur les types de chaînes de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ce-111">For more information about the types of connection strings, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
 <span data-ttu-id="6a7ce-112">Le \<Tables\> élément contient le nom des tables que vous ajoutez à l’aide du plug-in.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-112">The \<Tables\> element contains the name of the tables that you add using the plug-in.</span></span> <span data-ttu-id="6a7ce-113">De même, la \<RFC\> élément contient les documents RFC que vous ajoutez à l’aide du plug-in.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-113">Similarly, the \<RFCs\> element contains the RFCs that you add using the plug-in.</span></span> <span data-ttu-id="6a7ce-114">Si vous vous connectez à plus d’un serveur SAP, une autre \<Server\> élément est ajouté au fichier XML, et les tables correspondantes et RFC sont répertoriés sous la \<Table\> et \<RFC\> élément.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-114">If you connect to more than one SAP server, another \<Server\> element is added to the XML file, and the corresponding tables and RFCs are listed under the \<Table\> and \<RFCs\> element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a7ce-115">Pour obtenir des instructions sur l’utilisation du plug-in Visual Studio DDEX, consultez [utiliser le fournisseur de données pour SAP avec le plug-in DDEX](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ce-115">For instructions on using the Visual Studio DDEX plug-in, see [Use the Data Provider for SAP with the DDEX Plug-in](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7ce-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a7ce-116">See Also</span></span>  
 [<span data-ttu-id="6a7ce-117">À propos du fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="6a7ce-117">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)