---
title: "Types de données XLANG-s | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, expressions
- Orchestration Designer, managing data
- Orchestration Designer, variables
- orchestrations, variables
- Orchestration Designer, expressions
ms.assetid: 5b08aaa6-1533-4bac-a76d-f9162e39bf4f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c21ed77c5fdd56485514d17ed75e921c63a56212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-data-types"></a><span data-ttu-id="32942-102">Types de données XLANG-s</span><span class="sxs-lookup"><span data-stu-id="32942-102">XLANG-s Data Types</span></span>
<span data-ttu-id="32942-103">XLANG/s définit des types de valeurs standard qui sont le reflet de leurs équivalents C#.</span><span class="sxs-lookup"><span data-stu-id="32942-103">XLANG/s defines standard value types that are reflections of their C# counterparts.</span></span> <span data-ttu-id="32942-104">Ceux-ci incluent **booléenne**, **octets**, **Char**, **décimal**, **Double**, **Int16** , **Int32**, **Int64**, **SByte**, **unique**, **chaîne**,  **UInt16**, **UInt32**, et **UInt64**.</span><span class="sxs-lookup"><span data-stu-id="32942-104">These include **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**.</span></span> <span data-ttu-id="32942-105">XLANG/s prend en charge les tableaux unidimensionnels, mais pas les littéraux de tableau.</span><span class="sxs-lookup"><span data-stu-id="32942-105">XLANG/s supports single-dimensional arrays, but does not support array literals.</span></span>  
  
 <span data-ttu-id="32942-106">XLANG/s gère également le traitement des messages.</span><span class="sxs-lookup"><span data-stu-id="32942-106">XLANG/s also has rich support for message handling.</span></span> <span data-ttu-id="32942-107">Ces derniers peuvent être basés sur des schémas, des classes .NET, des types de messages Web (WSDL) ou des types de messages complexes.</span><span class="sxs-lookup"><span data-stu-id="32942-107">Messages can be based on schemas, .NET classes, Web message types (WSDL), or complex message types.</span></span> <span data-ttu-id="32942-108">XLANG/s prend en charge les types de données complexes suivants :</span><span class="sxs-lookup"><span data-stu-id="32942-108">XLANG/s supports the following complex data types:</span></span>  
  
-   <span data-ttu-id="32942-109">**MessageType.**</span><span class="sxs-lookup"><span data-stu-id="32942-109">**messagetype.**</span></span> <span data-ttu-id="32942-110">ce type de données définit les types de messages à parties multiples définis en tant que combinaisons d'éléments de données et de messages XSD, et les types de messages de méthode (messages correspondant au format de signature de la méthode d'une classe ou d'une interface).</span><span class="sxs-lookup"><span data-stu-id="32942-110">This data type defines multipart message types which are defined as combinations of data elements and XSD-based messages and Method-Message types (messages that match the signature format of a method of a class or interface).</span></span>  
  
-   <span data-ttu-id="32942-111">**PortType.**</span><span class="sxs-lookup"><span data-stu-id="32942-111">**porttype.**</span></span> <span data-ttu-id="32942-112">ce type de données définit un ensemble d'opérations de port sur lesquelles peut agir une instance de port de ce type.</span><span class="sxs-lookup"><span data-stu-id="32942-112">This data type defines a collection of port operations that a port instance of that type can act upon.</span></span>  
  
-   <span data-ttu-id="32942-113">**correlationsettype.**</span><span class="sxs-lookup"><span data-stu-id="32942-113">**correlationsettype.**</span></span> <span data-ttu-id="32942-114">ce type de données définit les données qui seront utilisées dans n'importe quelle instance de variable d'un ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="32942-114">This data type defines the data that will be used in any instance of a correlation set variable.</span></span> <span data-ttu-id="32942-115">Les données d'un ensemble de corrélations représentent la méthode de routage utilisée pour garantir la distribution des messages circulant dans le système à l'instance d'exécution appropriée d'un processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="32942-115">Correlation set data is the routing mechanism used to ensure that messages moving through the system are dispatched to the appropriate running instance of a business process.</span></span> <span data-ttu-id="32942-116">Par exemple, si un bon de commande est envoyé à un partenaire commercial pour être traité, il est impératif que l'instance appropriée du processus d'entreprise correspondant au bon de commande soit appelée à son retour.</span><span class="sxs-lookup"><span data-stu-id="32942-116">For example, if a purchase order is sent to a trading partner for processing, it is imperative that the correct instance of the business process corresponding to that purchase order be invoked on its return.</span></span>  
  
-   <span data-ttu-id="32942-117">**servicelinktype.**</span><span class="sxs-lookup"><span data-stu-id="32942-117">**servicelinktype.**</span></span> <span data-ttu-id="32942-118">Ce type de données définit l’ensemble des **porttype** valeurs qui forment un groupe logiquement cohérent de ports utilisés dans un processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="32942-118">This data type defines the set of **porttype** values that form a logically consistent group of ports used in a business process.</span></span> <span data-ttu-id="32942-119">L'utilisation des liens de service constitue une méthode puissante d'attribution dynamique à un groupe de ports lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="32942-119">The use of service links is a powerful mechanism that allows dynamic assignment to a group of ports at run time.</span></span> <span data-ttu-id="32942-120">Vous pouvez alors définir un seul processus d'entreprise qui sera utilisé pour interagir avec plusieurs partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="32942-120">This allows you to define a single business process that can be used to interact with multiple trading partners.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32942-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32942-121">See Also</span></span>  
 <span data-ttu-id="32942-122">[Instructions XLANG-s](../core/xlang-s-statements.md) </span><span class="sxs-lookup"><span data-stu-id="32942-122">[XLANG-s Statements](../core/xlang-s-statements.md) </span></span>  
 <span data-ttu-id="32942-123">[Opérateurs et Variables XLANG-s](../core/xlang-s-variables-and-operators.md) </span><span class="sxs-lookup"><span data-stu-id="32942-123">[XLANG-s Variables and Operators](../core/xlang-s-variables-and-operators.md) </span></span>  
 <span data-ttu-id="32942-124">[Expressions XLANG-s](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="32942-124">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="32942-125">[Mots réservés XLANG-s](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="32942-125">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="32942-126">XLANG-s pour les Conversions de Type BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="32942-126">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)