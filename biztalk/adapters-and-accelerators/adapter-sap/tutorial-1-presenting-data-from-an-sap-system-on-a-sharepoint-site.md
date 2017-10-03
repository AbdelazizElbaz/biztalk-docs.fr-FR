---
title: "Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MOSS, creating an application in
- Microsoft Office SharePoint Server
- MOSS
- Microsoft Office SharePoint Server, creating an application in
ms.assetid: 6e31c365-446c-4fe1-8538-fa6c869eed63
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdc3ea5e41600aebcef1fda933735c418dec78c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site"></a><span data-ttu-id="99043-102">Didacticiel 1 : Présentation des données à partir d’un système SAP sur un Site SharePoint</span><span class="sxs-lookup"><span data-stu-id="99043-102">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>
<span data-ttu-id="99043-103">Ce didacticiel fournit des instructions détaillées sur l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft Office SharePoint Server pour présenter les données d’entreprise à partir d’un système SAP sur un portail SharePoint.</span><span class="sxs-lookup"><span data-stu-id="99043-103">This tutorial provides detailed instructions on using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft Office SharePoint Server to present business data from an SAP system on a SharePoint portal.</span></span> <span data-ttu-id="99043-104">Pour illustrer l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Office SharePoint Server, vous devez prendre en compte les deux entités courantes dans toute entreprise : clients et les commandes.</span><span class="sxs-lookup"><span data-stu-id="99043-104">To demonstrate how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Office SharePoint Server, consider the two most common entities in any business: customers and sales orders.</span></span> <span data-ttu-id="99043-105">Dans cet exemple, une application est créée dans Office SharePoint Server, qui utilise le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="99043-105">In this example, an application is created in Office SharePoint Server, which uses the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to do the following:</span></span>  
  
-   <span data-ttu-id="99043-106">Récupérer une liste de clients à partir du système SAP basé sur une chaîne de recherche.</span><span class="sxs-lookup"><span data-stu-id="99043-106">Retrieve a list of customers from the SAP system based on a search string.</span></span>  
  
-   <span data-ttu-id="99043-107">Sélectionnez un client à partir de la liste et détails présentes pour le client.</span><span class="sxs-lookup"><span data-stu-id="99043-107">Select a customer from the list and present details for the customer.</span></span>  
  
-   <span data-ttu-id="99043-108">Récupérer les commandes pour le client sélectionné.</span><span class="sxs-lookup"><span data-stu-id="99043-108">Retrieve the sales orders for the selected customer.</span></span>  
  
 <span data-ttu-id="99043-109">Pour extraire les données client à partir d’un système SAP, l’exemple utilise le document RFC SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="99043-109">To extract customer data from an SAP system, the example uses the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="99043-110">Pour extraire des informations sur les commandes client pour un client spécifique, il utilise le document RFC BAPI_SALESORDER_GETLIST.</span><span class="sxs-lookup"><span data-stu-id="99043-110">To extract information about sales orders for a specific customer, it uses the BAPI_SALESORDER_GETLIST RFC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99043-111">Certaines versions du système SAP exposent un RFC RFC_CUSTOMER_GET au lieu de SD_RFC_CUSTOMER_GET.</span><span class="sxs-lookup"><span data-stu-id="99043-111">Some versions of the SAP system expose an RFC_CUSTOMER_GET RFC instead of SD_RFC_CUSTOMER_GET.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99043-112">Avant de poursuivre le didacticiel, assurez-vous que vous avez installé tous les composants requis pour l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="99043-112">Before proceeding with the tutorial, make sure you have installed all the prerequisites for using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Office SharePoint Server.</span></span> <span data-ttu-id="99043-113">Pour plus d’informations sur la configuration requise, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation, généralement installé sur C:/Program Files/Microsoft  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] /Documents.</span><span class="sxs-lookup"><span data-stu-id="99043-113">For more information about the prerequisites, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide, typically installed at C:/Program Files/Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]/Documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99043-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="99043-114">In This Section</span></span>  
  
-   [<span data-ttu-id="99043-115">Étape 1 : Publier les artefacts SAP comme Service WCF</span><span class="sxs-lookup"><span data-stu-id="99043-115">Step 1: Publish the SAP Artifacts as a WCF Service</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)  
  
-   [<span data-ttu-id="99043-116">Étape 2 : Créer un fichier de définition d’Application pour les artefacts SAP</span><span class="sxs-lookup"><span data-stu-id="99043-116">Step 2: Create an Application Definition File for the SAP Artifacts</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)  
  
-   [<span data-ttu-id="99043-117">Étape 3 : Créer une Application SharePoint pour récupérer des données à partir de SAP</span><span class="sxs-lookup"><span data-stu-id="99043-117">Step 3: Create a SharePoint Application to Retrieve Data from SAP</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)  
  
-   [<span data-ttu-id="99043-118">Étape 4 : Tester votre Application SharePoint</span><span class="sxs-lookup"><span data-stu-id="99043-118">Step 4: Test Your SharePoint Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md)  
  
## <a name="see-also"></a><span data-ttu-id="99043-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99043-119">See Also</span></span>  
 [<span data-ttu-id="99043-120">Didacticiels de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="99043-120">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)