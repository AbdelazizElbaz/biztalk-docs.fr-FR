---
title: "Se connecter à un système SAP à l’aide de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI
- adapters, connecting to an SAP system
- connection string
ms.assetid: d506a948-5f4a-420b-a404-508824683099
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75f8c4b8650b2c81b3b82bf520958646e20da380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-an-sap-system-using-the-adapter"></a><span data-ttu-id="4ec37-102">Se connecter à un système SAP à l’aide de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="4ec37-102">Connect to an SAP system using the adapter</span></span>
<span data-ttu-id="4ec37-103">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exige que les clients de l’adaptateur fournir une chaîne de connexion, appelée la connexion identificateur URI (Uniform Resource) pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="4ec37-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI) to connect to the SAP system.</span></span> <span data-ttu-id="4ec37-104">Avec un URI de connexion, les clients de carte peuvent spécifier des paramètres de connexion pour se connecter à un système externe. Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="4ec37-104">With a connection URI, adapter clients can specify connection parameters to connect to an external system.For more information about the connection URI, see [Create a connection to the SAP system](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).</span></span>  
  
 <span data-ttu-id="4ec37-105">Veillez à que respecter les consignes de sécurité lors de l’établissement d’une connexion avec un système SAP.</span><span class="sxs-lookup"><span data-stu-id="4ec37-105">Make sure you comply with the security guidelines when establishing a connection with an SAP system.</span></span> <span data-ttu-id="4ec37-106">Pour plus d’informations sur les règles de sécurité, consultez [sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).</span><span class="sxs-lookup"><span data-stu-id="4ec37-106">For more information about security guidelines, see [Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).</span></span>
  
## <a name="how-many-connections-can-the-adapter-open-to-the-sap-system"></a><span data-ttu-id="4ec37-107">Le nombre de connexions peut la carte ouverte pour le système SAP ?</span><span class="sxs-lookup"><span data-stu-id="4ec37-107">How Many Connections Can the Adapter Open to the SAP System?</span></span>  
 <span data-ttu-id="4ec37-108">Par défaut, le système SAP permet aux clients d’ouvrir de 100 connexions au système SAP.</span><span class="sxs-lookup"><span data-stu-id="4ec37-108">By default, the SAP system enables clients to open 100 connections to the SAP system.</span></span> <span data-ttu-id="4ec37-109">Toutefois, vous pouvez définir une variable d’environnement sur l’ordinateur exécutant le système SAP pour augmenter la limite du nombre de connexions.</span><span class="sxs-lookup"><span data-stu-id="4ec37-109">However, you can set an environment variable on the computer running the SAP system to increase the limit on the number of connections.</span></span> <span data-ttu-id="4ec37-110">Pour plus d’informations, consultez [dépanner les problèmes opérationnels avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="4ec37-110">For more information, see [Troubleshoot Operational Issues with the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec37-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ec37-111">See Also</span></span>  
 [<span data-ttu-id="4ec37-112">Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="4ec37-112">Architecture overview of the BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)