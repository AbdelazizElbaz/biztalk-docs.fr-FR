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
ms.openlocfilehash: 428d2987465ff1fe09f01979bbe9036def6350b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-sapdiscoveredobjectsxml-file-in-sap"></a>Sur le fichier SAPDiscoveredObjects.xml dans SAP
Si vous avez choisi d’installer le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, le programme d’installation copie le fichier SAPDiscoveredObjects.xml en général au \<lecteur d’installation > : \Program Files\Microsoft Shared\Adapters\SAP. Le contenu du fichier, après une nouvelle installation de le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], similaire à la suivante.  
  
```  
<DiscoveredObjects>  
  <SAP>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 L’objectif du fichier SAPDiscoveredObjects.xml consiste à stocker les objets SAP (tables et RFC) que vous découvrez à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] plug-in DDEX. Une fois que vous avez utilisé le plug-in DDEX pour ajouter des objets SAP, ils sont ajoutés à ce fichier XML. Voici à quoi ressemble le fichier XML.  
  
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
  
 Le `name` propriétés de la < Server\> élément contient le nom du serveur auquel vous vous connectez à l’aide du plug-in DDEX. Le `user` et `client` propriétés de la < Server\> élément contiennent les numéros de client et le nom d’utilisateur, respectivement. Le `type` propriété contient le type de chaîne de connexion (A, B ou D) utilisé pour se connecter à un système SAP. Pour plus d’informations sur les types de chaînes de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
 Le \<Tables > élément contient le nom des tables que vous ajoutez à l’aide du plug-in. De même, le \<RFC > élément contient les documents RFC que vous ajoutez à l’aide du plug-in. Si vous vous connectez à plus d’un serveur SAP, une autre \<Server > élément est ajouté au fichier XML, et les tables correspondantes et RFC sont répertoriés sous la \<Table > et \<RFC > élément.  
  
> [!NOTE]
>  Pour obtenir des instructions sur l’utilisation du plug-in Visual Studio DDEX, consultez [utiliser le fournisseur de données pour SAP avec le plug-in DDEX](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sur le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)