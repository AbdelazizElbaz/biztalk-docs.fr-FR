---
title: "Opérations sur les Services métier Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, on business services
- business services, operations on
ms.assetid: 29a1a88c-8c7b-46f1-8faf-49ddd32ba2f0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1ffd133d76b1f8cae3f1732e48f817fe4fb26b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-business-services-in-siebel"></a><span data-ttu-id="3f2cd-102">Opérations sur les Services métier de Siebel</span><span class="sxs-lookup"><span data-stu-id="3f2cd-102">Operations on Business Services in Siebel</span></span>
<span data-ttu-id="3f2cd-103">Un service d’entreprise Siebel est une collection de méthodes d’entreprise qui peuvent être appelées directement dans Siebel.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-103">A Siebel business service is a collection of business methods that can be directly invoked in Siebel.</span></span> <span data-ttu-id="3f2cd-104">Alors que les composants d’entreprise et les objets métier sont associés à des données spécifiques et des tables dans Siebel, services professionnels appellent les objets pour effectuer des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-104">Whereas business components and business objects are associated to specific data and tables in Siebel, business services invoke the objects to perform specific tasks.</span></span>  
  
 <span data-ttu-id="3f2cd-105">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] met en évidence les méthodes de service métier comme opération noms et prend en charge des IN, OUT et INOUT paramètres.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-105">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the business service methods as operation names and supports IN, OUT, and INOUT parameters.</span></span> <span data-ttu-id="3f2cd-106">Par exemple, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces le **ATPRunCheck** méthode sous forme d’opération.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-106">For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the **ATPRunCheck** method as an operation.</span></span> <span data-ttu-id="3f2cd-107">Cette méthode appartient à la **ATP** service métier.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-107">This method belongs to the **ATP** business service.</span></span>  
  
 <span data-ttu-id="3f2cd-108">Certaines conditions qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] impose tout en utilisant les services d’entreprise Siebel :</span><span class="sxs-lookup"><span data-stu-id="3f2cd-108">Certain conditions that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] imposes while using the Siebel business services:</span></span>  
  
-   <span data-ttu-id="3f2cd-109">Si une méthode de service d’entreprise Siebel prend un argument qui n’a pas de type de données spécifié, l’adaptateur expose l’argument sous forme de texte.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-109">If a Siebel business service method takes an argument that does not have the data type specified, the adapter exposes the argument as TEXT.</span></span>  
  
-   <span data-ttu-id="3f2cd-110">Un argument de méthode de service business Siebel permettre être des types suivants :</span><span class="sxs-lookup"><span data-stu-id="3f2cd-110">A Siebel business service method argument can be of the following types:</span></span>  
  
    -   <span data-ttu-id="3f2cd-111">Chaîne (exposé comme xsd : String)</span><span class="sxs-lookup"><span data-stu-id="3f2cd-111">String (exposed as xsd:string)</span></span>  
  
    -   <span data-ttu-id="3f2cd-112">Nombre (exposées en tant que xsd : decimal)</span><span class="sxs-lookup"><span data-stu-id="3f2cd-112">Number (exposed as xsd: decimal)</span></span>  
  
    -   <span data-ttu-id="3f2cd-113">Date (exposé comme xsd : DateTime, avec la facette de modèle indiquant que la partie heure doit être défini à 00:00:00)</span><span class="sxs-lookup"><span data-stu-id="3f2cd-113">Date (exposed as xsd:DateTime, with pattern facet indicating that time part must be set to 00:00:00)</span></span>  
  
    -   <span data-ttu-id="3f2cd-114">Hiérarchie (exposé comme xsd : String)</span><span class="sxs-lookup"><span data-stu-id="3f2cd-114">Hierarchy (exposed as xsd:string)</span></span>  
  
    -   <span data-ttu-id="3f2cd-115">Objet d’intégration (exposé comme xsd : String)</span><span class="sxs-lookup"><span data-stu-id="3f2cd-115">Integration Object (exposed as xsd:string)</span></span>  
  
     <span data-ttu-id="3f2cd-116">En outre, la méthode de service business vérifie si la valeur passée pour un argument est compatible avec le type correspondant.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-116">Also, the business service method verifies whether the value passed for an argument complies with the corresponding type.</span></span> <span data-ttu-id="3f2cd-117">Par conséquent, si une méthode de service d’entreprise accepte ou retourne des valeurs qui ne sont pas conformes avec le type d’argument correspondant, l’adaptateur peut lever une exception.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-117">So, if a business service method accepts or returns values that do not comply with the corresponding argument type, the adapter may throw an exception.</span></span> <span data-ttu-id="3f2cd-118">Si l’adaptateur parvient à appeler la méthode de service d’entreprise, le schéma de validation peut échouer.</span><span class="sxs-lookup"><span data-stu-id="3f2cd-118">If the adapter does succeed in invoking the business service method, the schema validation may fail.</span></span>  
  
 <span data-ttu-id="3f2cd-119">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="3f2cd-119">For information about:</span></span>  
  
-   <span data-ttu-id="3f2cd-120">Exécution d’opérations sur les services d’entreprise à l’aide de BizTalk Server, consultez [appeler Business Service méthodes à l’aide de BizTalk Server et l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="3f2cd-120">Performing operations on business services using BizTalk Server, see [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span></span>  
  
-   <span data-ttu-id="3f2cd-121">Structures et des actions SOAP pour effectuer des opérations sur les services, consultez des messages [des schémas de Message pour des opérations de Service Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)).</span><span class="sxs-lookup"><span data-stu-id="3f2cd-121">Message structures and SOAP actions to perform operations on business services, see [Message Schemas for Business Service Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f2cd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f2cd-122">See Also</span></span>  
 [<span data-ttu-id="3f2cd-123">Se connecter à un système SAP à l’aide de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="3f2cd-123">Connect to an SAP system using the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)