---
title: "Conversion des propriétés de Type de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, data type conversion
- MQBYTE property [MQSeries adapters]
- MQLONG property [MQSeries adapters]
- MQCHAR property [MQSeries adapters]
- configuring [MQSeries adapters], data type conversion
ms.assetid: 5b81eab0-f7a1-42f3-b212-a211b2893fd5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3705f1d0a20a48f0683a15588891ef3fe60889cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-conversion-of-properties"></a><span data-ttu-id="44d69-102">Conversion de Type de données de propriétés</span><span class="sxs-lookup"><span data-stu-id="44d69-102">Data Type Conversion of Properties</span></span>
<span data-ttu-id="44d69-103">Les propriétés d'en-tête d'un message MQSeries constituent des structures de données contenues dans le message lui-même.</span><span class="sxs-lookup"><span data-stu-id="44d69-103">Header properties in an MQSeries message are data structures contained in the message itself.</span></span> <span data-ttu-id="44d69-104">L'adaptateur MQSeries valide et convertit automatiquement certaines valeurs d'en-têtes de message MQSeries lors de l'envoi et de la réception de messages.</span><span class="sxs-lookup"><span data-stu-id="44d69-104">The MQSeries adapter automatically validates and converts certain values in MQSeries message headers when sending and receiving messages.</span></span>  
  
 <span data-ttu-id="44d69-105">Le tableau suivant décrit les types de données MQSeries, leur validation et leur conversion.</span><span class="sxs-lookup"><span data-stu-id="44d69-105">The following table describes the MQSeries data types and their validation and conversion.</span></span>  
  
|<span data-ttu-id="44d69-106">Type de données MQSeries</span><span class="sxs-lookup"><span data-stu-id="44d69-106">MQSeries data type</span></span>|<span data-ttu-id="44d69-107">Validation et conversion</span><span class="sxs-lookup"><span data-stu-id="44d69-107">Validation and conversion</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="44d69-108">MQLONG</span><span class="sxs-lookup"><span data-stu-id="44d69-108">MQLONG</span></span>|<span data-ttu-id="44d69-109">MQSeries effectue la validation.</span><span class="sxs-lookup"><span data-stu-id="44d69-109">MQSeries performs the validation.</span></span> <span data-ttu-id="44d69-110">Convertit en un nombre entier long.</span><span class="sxs-lookup"><span data-stu-id="44d69-110">Converts to a long integer.</span></span> <span data-ttu-id="44d69-111">Les valeurs non valides empêchent le placement du message dans la file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="44d69-111">Values that are not valid prevent the message from going to the MQSeries queue.</span></span>|  
|<span data-ttu-id="44d69-112">MQCHAR</span><span class="sxs-lookup"><span data-stu-id="44d69-112">MQCHAR</span></span>|<span data-ttu-id="44d69-113">Convertit en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="44d69-113">Converts to a string.</span></span>|  
|<span data-ttu-id="44d69-114">MQBYTE</span><span class="sxs-lookup"><span data-stu-id="44d69-114">MQBYTE</span></span>|<span data-ttu-id="44d69-115">Convertit en une chaîne contenant les caractères 0-9 et a-f ou A-F qui représente la valeur hexadécimale du nombre.</span><span class="sxs-lookup"><span data-stu-id="44d69-115">Converts to a string that contains the characters 0-9 and a-f or A-F, representing the hexadecimal value of the number.</span></span>|  
  
 <span data-ttu-id="44d69-116">Un grand nombre de propriétés MQSeries sont des entiers non signés 32 bits (4 octets).</span><span class="sxs-lookup"><span data-stu-id="44d69-116">Many of the MQSeries properties are 32-bit (4-byte) unsigned integers.</span></span> <span data-ttu-id="44d69-117">Étant donné que **uint** n’est pas une spécification de langage commun (CLS)-type conforme, vous devez les assigner à **objet** types avant de les utiliser dans les méthodes .NET.</span><span class="sxs-lookup"><span data-stu-id="44d69-117">Because **uint** is not a Common Language Specification (CLS)-compliant type, you must assign them to **object** types before using them in .NET methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d69-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44d69-118">See Also</span></span>  
 <span data-ttu-id="44d69-119">[Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md) </span><span class="sxs-lookup"><span data-stu-id="44d69-119">[MQSeries Adapter Properties](../core/mqseries-adapter-properties.md) </span></span>  
 <span data-ttu-id="44d69-120">[Propriétés relatives à BizTalk Server](../core/properties-related-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="44d69-120">[Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md) </span></span>  
 [<span data-ttu-id="44d69-121">Propriétés de contexte MQSeries</span><span class="sxs-lookup"><span data-stu-id="44d69-121">MQSeries Context Properties</span></span>](../core/mqseries-context-properties.md)