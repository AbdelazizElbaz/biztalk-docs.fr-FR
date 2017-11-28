---
title: "Classe SiebelConnectionStringBuilder dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelConnectionStringBuilder, supported properties and methods
- Data Provider for Siebel, SiebelConnectionStringBuilder
- SiebelConnectionStringBuilder
ms.assetid: 4995fce8-7e62-4af9-a731-47b16438067c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 088748c63983e76e64d32f54b3e999fadd88d23a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelconnectionstringbuilder-class-in-the-siebel-adapter"></a><span data-ttu-id="3957c-102">Classe SiebelConnectionStringBuilder dans l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3957c-102">SiebelConnectionStringBuilder class in the Siebel adapter</span></span>
<span data-ttu-id="3957c-103">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fournit un `DbConnectionStringBuilder` environnements pour obtenir les propriétés de connexion des outils de mise en œuvre pour activer SQL Server Integration Services (SSIS) et Visual Studio explorer le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] et les afficher sous la forme d’une interface graphique utilisateur pilotée par le PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="3957c-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbConnectionStringBuilder` implementation to enable SQL Server Integration Services (SSIS) and Visual Studio explorer tools environments to get the connection properties of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] and display them in the form of a GUI driven by the PropertyGrid.</span></span>  
  
 <span data-ttu-id="3957c-104">Pour créer un SiebelConnectionStringBuilder, utilisez l’approche suivante :</span><span class="sxs-lookup"><span data-stu-id="3957c-104">To create a SiebelConnectionStringBuilder, use the following approach:</span></span>  
  
```  
  
//In this example, factory is an instance of SiebelClientFactory  
SiebelConnectionStringBuilder bldr = (SiebelConnectionStringBuilder)factory.CreateConnectionStringBuilder();  
bldr.ConnectionString = connstr;  
```  
  
 <span data-ttu-id="3957c-105">Ou simplement :</span><span class="sxs-lookup"><span data-stu-id="3957c-105">Or, simply:</span></span>  
  
```  
  
SiebelConnectionStringBuilder bldr = new SiebelConnectionStringBuilder();  
```  
  
 <span data-ttu-id="3957c-106">Pour afficher les clés et les valeurs prises en charge dans le cadre de la `DbConnectionStringBuilder`, consultez [propriétés du fournisseur de données pour la chaîne de connexion Siebel](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="3957c-106">To see the keys and values supported as part of the `DbConnectionStringBuilder`, see [Data Provider properties for the Siebel Connection String](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3957c-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3957c-107">See Also</span></span>  
 [<span data-ttu-id="3957c-108">Étendre des Interfaces ADO.NET avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3957c-108">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)