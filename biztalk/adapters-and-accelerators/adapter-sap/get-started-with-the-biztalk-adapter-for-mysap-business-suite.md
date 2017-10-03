---
title: "Prise en main l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
description: "Installer les RFC personnalisés, en savoir plus sur la carte, effectuez les tâches RFC et IDOC de SAP, parcourez les didacticiels pour utiliser l’adaptateur de mySAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2013253-f911-4e35-a33a-b4a9bcb136aa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e5607a255f50bf5295d4ea22c9a680d86f38e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="78089-103">Prise en main l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="78089-103">Get started with the BizTalk Adapter for mySAP Business Suite</span></span>
<span data-ttu-id="78089-104">Cette section fournit une vue d’ensemble de l’adaptateur, les conditions préalables et les rubriques pour les utilisateurs qui sont nouveaux pour Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="78089-104">This section provides an overview of the adapter, prerequisites, and topics for users who are new to Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="78089-105">Il traite des fonctionnalités de [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] et les différentes opérations qui peuvent être effectuées sur le système SAP à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="78089-105">It discusses the features of [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] and the different operations that can be performed on the SAP system using the adapter.</span></span>  

## <a name="what-is-an-adapter"></a><span data-ttu-id="78089-106">Qu’est un adaptateur ?</span><span class="sxs-lookup"><span data-stu-id="78089-106">What is an adapter?</span></span> 
<span data-ttu-id="78089-107">Un adaptateur est un composant logiciel qui vous permet d’envoyer et recevoir des messages vers et depuis un système de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="78089-107">An adapter is a software component that enables you to send and receive messages to and from a line-of-business (LOB) system.</span></span> <span data-ttu-id="78089-108">L’objectif de conception principale des cartes est de faciliter l’échange de documents entre partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="78089-108">The primary design goal of adapters is to facilitate the exchange of business documents between trading partners.</span></span> <span data-ttu-id="78089-109">Étant donné que chaque système d’entreprise peut-être adhérer aux protocoles et formats de document spécifique, l’adaptateur doit utiliser un mécanisme de remise qui est conforme aux normes communément reconnus et protocoles pour fournir une interface uniforme pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="78089-109">Because each business system may adhere to specific document formats and protocols, the adapter must use a delivery mechanism that conforms to commonly recognized standards and protocols to provide a uniform interface to the users.</span></span>  
  
 <span data-ttu-id="78089-110">Les adaptateurs peuvent être divisés en deux grandes catégories :</span><span class="sxs-lookup"><span data-stu-id="78089-110">The adapters can be divided into two broad categories:</span></span>  
  
-   <span data-ttu-id="78089-111">**Adaptateurs LOB**.</span><span class="sxs-lookup"><span data-stu-id="78089-111">**LOB adapters**.</span></span> <span data-ttu-id="78089-112">Ces adaptateurs fournissent le modèle de programmation orientée service à l’accès des systèmes métier, par exemple, les adaptateurs pour SAP ou Siebel.</span><span class="sxs-lookup"><span data-stu-id="78089-112">Such adapters provide service-oriented programming model to access LOB systems—for example, adapters for SAP or Siebel.</span></span>  
  
-   <span data-ttu-id="78089-113">**Les adaptateurs de données**.</span><span class="sxs-lookup"><span data-stu-id="78089-113">**Data adapters**.</span></span> <span data-ttu-id="78089-114">Ces adaptateurs fournissent le modèle de programmation orientée service aux bases de données, par exemple, un adaptateur pour la base de données Oracle ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="78089-114">Such adapters provide service-oriented programming model to access databases—for example, an adapter for the Oracle database or SQL Server.</span></span>  
  
 <span data-ttu-id="78089-115">Il existe cinq adaptateurs dans le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="78089-115">There are five adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]<span data-ttu-id="78089-116">(la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="78089-116"> (the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]<span data-ttu-id="78089-117">(la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="78089-117"> (the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)])</span></span>  
  
-   [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="78089-118">(la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span><span class="sxs-lookup"><span data-stu-id="78089-118"> (the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]<span data-ttu-id="78089-119">(le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), y compris [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="78089-119"> (the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]), including [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)])</span></span>  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]<span data-ttu-id="78089-120">(le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), y compris [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span><span class="sxs-lookup"><span data-stu-id="78089-120"> (the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]), including [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78089-121">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’est pas disponible pour des plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="78089-121">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is not available for 64-bit platforms.</span></span>  
  
 <span data-ttu-id="78089-122">Si vous ne connaissez pas déjà comment vous décidez d’utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans votre entreprise, il est recommandé que vous démarrez en explorant les fonctions et fonctionnalités de l’adaptateur décrites dans [comprendre l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md) .</span><span class="sxs-lookup"><span data-stu-id="78089-122">If you do not already know how you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] at your company, it is recommended that you start by exploring features and functionality of the adapter described in [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="78089-123">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="78089-123">Next steps</span></span>  
- [<span data-ttu-id="78089-124">Installez les RFC personnalisés pour le fournisseur de données pour SAP</span><span class="sxs-lookup"><span data-stu-id="78089-124">Install Custom RFCs for the Data Provider for SAP</span></span>](install-custom-rfcs-for-the-data-provider-for-sap.md)
  
-   [<span data-ttu-id="78089-125">Comprendre l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="78089-125">Understand BizTalk Adapter for mySAP Business Suite</span></span>](understand-biztalk-adapter-for-mysap-business-suite.md)  

- [<span data-ttu-id="78089-126">Effectuez les tâches RFC et IDOC de SAP</span><span class="sxs-lookup"><span data-stu-id="78089-126">Complete RFC and IDOC tasks on SAP</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)
  
-   [<span data-ttu-id="78089-127">Didacticiels de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="78089-127">SAP Adapter Tutorials</span></span>](sap-adapter-tutorials.md)  