---
title: "Limitations de l’adaptateur BizTalk pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 149cee03-43cd-4cb3-a937-6565f5e96ce5
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7611c56fbd24c7c7cf09d38d376df585b72b284
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-oracle-e-business-suite"></a><span data-ttu-id="aa28c-102">Limitations de l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="aa28c-102">Limitations of BizTalk Adapter for Oracle E-Business Suite</span></span>
## <a name="general-limitations"></a><span data-ttu-id="aa28c-103">Limitations générales</span><span class="sxs-lookup"><span data-stu-id="aa28c-103">General Limitations</span></span>  
 <span data-ttu-id="aa28c-104">Les éléments suivants sont connus limitations pour [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="aa28c-104">The following are known limitations for [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span></span>  
  
-   <span data-ttu-id="aa28c-105">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge la passerelle XML, file d’attente avancée et les événements de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="aa28c-105">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support XML Gateway, Advanced Queuing, and Business Events.</span></span>  
  
     <span data-ttu-id="aa28c-106">Toutefois, vous pouvez contourner la limitation des événements commerciaux de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="aa28c-106">However, you can get around the Business Events limitation in the following way:</span></span>  
  
    1.  <span data-ttu-id="aa28c-107">Dans Oracle Business événements système, créez un abonnement pour appeler une procédure PL/SQL personnalisée lorsqu’un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="aa28c-107">In Oracle Business Events System, create a subscription to invoke a custom PL/SQL procedure when a business event occurs.</span></span>  
  
    2.  <span data-ttu-id="aa28c-108">Écrire une procédure PL/SQL personnalisée qui reçoit l’événement de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="aa28c-108">Write a custom PL/SQL procedure that receives the business event.</span></span>  
  
    3.  <span data-ttu-id="aa28c-109">Utilisez la procédure PL/SQL personnalisée pour stocker les données résultantes (événement et la charge utile d’événement) dans une table.</span><span class="sxs-lookup"><span data-stu-id="aa28c-109">Use the custom PL/SQL procedure to store the resultant data (event and event payload) in a table.</span></span>  
  
    4.  <span data-ttu-id="aa28c-110">Utilisez le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger ou de recevoir des notifications à partir de la table.</span><span class="sxs-lookup"><span data-stu-id="aa28c-110">Use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll or receive notifications from the table.</span></span>  
  
-   <span data-ttu-id="aa28c-111">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les Types XML.</span><span class="sxs-lookup"><span data-stu-id="aa28c-111">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support XML Types.</span></span>  
  
-   <span data-ttu-id="aa28c-112">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne pas autoriser les clients à définir la valeur du premier élément dans un VARRAY avec la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="aa28c-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not enable clients to set the value of the first element in a VARRAY to NULL.</span></span>  
  
-   <span data-ttu-id="aa28c-113">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne pas les enregistrements de prise en charge qui contiennent des champs de type de tables PL/SQL de type d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="aa28c-113">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support records that contain fields of type PL/SQL tables of RECORD type.</span></span>  
  
-   <span data-ttu-id="aa28c-114">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les Types définis par l’utilisateur (UDT) qui ont des références circulaires.</span><span class="sxs-lookup"><span data-stu-id="aa28c-114">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support User-Defined Types (UDTs) that have circular references.</span></span>  
  
-   <span data-ttu-id="aa28c-115">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge le type de données BFILE à l’intérieur des types complexes (telles que l’enregistrement type, TABLE type, UDT et VARRAY).</span><span class="sxs-lookup"><span data-stu-id="aa28c-115">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support the BFILE data type inside complex types (such as RECORD type, TABLE type, UDT, and VARRAY).</span></span>  
  
-   <span data-ttu-id="aa28c-116">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge jusqu'à deux niveaux d’imbrication des UDT.</span><span class="sxs-lookup"><span data-stu-id="aa28c-116">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports UDT nesting only up to two levels.</span></span>  
  
-   <span data-ttu-id="aa28c-117">À l’exception des tables de PL/SQL, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT sont définis à l’intérieur d’un package.</span><span class="sxs-lookup"><span data-stu-id="aa28c-117">Except for PL/SQL tables, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that are defined inside a package.</span></span>  
  
-   <span data-ttu-id="aa28c-118">Lorsque l’utilisation des adaptateurs dans BizTalk Server, si les informations d’identification sur WCF-custom port d’envoi sont incorrectes, les messages de demande ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="aa28c-118">When using the adapters with BizTalk Server, if the credentials on the WCF-custom send port are incorrect, the request messages are not processed.</span></span> <span data-ttu-id="aa28c-119">Après avoir spécifié les informations d’identification correctes, le message est envoyé pour Oracle E-Business Suite et une réponse est reçue.</span><span class="sxs-lookup"><span data-stu-id="aa28c-119">After you specify the correct credentials, the message is sent to Oracle E-Business Suite and a response is received.</span></span> <span data-ttu-id="aa28c-120">Toutefois, le message de réponse n’est pas disponible pour le port de sortie.</span><span class="sxs-lookup"><span data-stu-id="aa28c-120">However, the response message is not available to the out port.</span></span> <span data-ttu-id="aa28c-121">Dans de tels scénarios, vous devrez peut-être redémarrer l’instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="aa28c-121">In such scenarios, you may need to restart the host instance.</span></span>  
  
## <a name="limitations-due-to-odpnet"></a><span data-ttu-id="aa28c-122">Limitations en raison de ODP.NET</span><span class="sxs-lookup"><span data-stu-id="aa28c-122">Limitations Due to ODP.NET</span></span>  
 <span data-ttu-id="aa28c-123">Les éléments suivants sont connus limitations pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en raison de la limitation de ODP.NET :</span><span class="sxs-lookup"><span data-stu-id="aa28c-123">The following are known limitations for [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] due to the limitation of ODP.NET:</span></span>  
  
-   <span data-ttu-id="aa28c-124">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les tables PL/SQL qui ne sont pas indexés par un champ numérique.</span><span class="sxs-lookup"><span data-stu-id="aa28c-124">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support PL/SQL tables that are not indexed by a numeric field.</span></span>  
  
-   <span data-ttu-id="aa28c-125">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les tableaux associatifs qui ne contiennent pas de n’importe quel élément.</span><span class="sxs-lookup"><span data-stu-id="aa28c-125">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support associative arrays that do not contain any element.</span></span>  
  
-   <span data-ttu-id="aa28c-126">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT qui contiennent le type de données TimeStamp avec les attributs de fuseau horaire local (TimeStampLTZ).</span><span class="sxs-lookup"><span data-stu-id="aa28c-126">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that contain the TimeStamp data type with local time zone attributes (TimeStampLTZ).</span></span>  
  
-   <span data-ttu-id="aa28c-127">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT qui contiennent un «. »</span><span class="sxs-lookup"><span data-stu-id="aa28c-127">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that contain a “.”</span></span> <span data-ttu-id="aa28c-128">(point) dans leurs noms.</span><span class="sxs-lookup"><span data-stu-id="aa28c-128">(period) in their names.</span></span>  
  
-   <span data-ttu-id="aa28c-129">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge les UDT qui contiennent des types de données objet BLOB, CLOB et NCLOB en tant que paramètre IN OUT.</span><span class="sxs-lookup"><span data-stu-id="aa28c-129">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support UDTs that contain BLOB, CLOB, and NCLOB data types as an IN OUT parameter.</span></span>  
  
-   <span data-ttu-id="aa28c-130">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge Varray de Varray des types simples suivants : BFILE, IntervalDS, IntervalYM, TimeStampLTZ et TimeStampTZ.</span><span class="sxs-lookup"><span data-stu-id="aa28c-130">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not support Varray of Varray of the following simple types: BFILE, IntervalDS, IntervalYM, TimeStampLTZ, and TimeStampTZ.</span></span>  
  
-   <span data-ttu-id="aa28c-131">En raison de la limitation d’associatifs, les tables de PL/SQL ou PL/SQL d’enregistrements qui contiennent un des types de données suivants ne sont pas gérées dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="aa28c-131">Due to the limitation of associative arrays, PL/SQL tables or PL/SQL tables of records that contain any of the following data types are not supported in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:</span></span>  
  
    -   <span data-ttu-id="aa28c-132">BFILE</span><span class="sxs-lookup"><span data-stu-id="aa28c-132">BFILE</span></span>  
  
    -   <span data-ttu-id="aa28c-133">BLOB</span><span class="sxs-lookup"><span data-stu-id="aa28c-133">BLOB</span></span>  
  
    -   <span data-ttu-id="aa28c-134">CLOB</span><span class="sxs-lookup"><span data-stu-id="aa28c-134">CLOB</span></span>  
  
    -   <span data-ttu-id="aa28c-135">IntervalDS</span><span class="sxs-lookup"><span data-stu-id="aa28c-135">IntervalDS</span></span>  
  
    -   <span data-ttu-id="aa28c-136">IntervalYM</span><span class="sxs-lookup"><span data-stu-id="aa28c-136">IntervalYM</span></span>  
  
    -   <span data-ttu-id="aa28c-137">Long</span><span class="sxs-lookup"><span data-stu-id="aa28c-137">Long</span></span>  
  
    -   <span data-ttu-id="aa28c-138">NCLOB</span><span class="sxs-lookup"><span data-stu-id="aa28c-138">NCLOB</span></span>  
  
    -   <span data-ttu-id="aa28c-139">ID de ligne</span><span class="sxs-lookup"><span data-stu-id="aa28c-139">RowID</span></span>  
  
    -   <span data-ttu-id="aa28c-140">TimeStamp</span><span class="sxs-lookup"><span data-stu-id="aa28c-140">TimeStamp</span></span>  
  
    -   <span data-ttu-id="aa28c-141">TimeStampLTZ</span><span class="sxs-lookup"><span data-stu-id="aa28c-141">TimeStampLTZ</span></span>  
  
    -   <span data-ttu-id="aa28c-142">TimeStampTZ</span><span class="sxs-lookup"><span data-stu-id="aa28c-142">TimeStampTZ</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa28c-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa28c-143">See Also</span></span>  
 [<span data-ttu-id="aa28c-144">Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="aa28c-144">Understand BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)