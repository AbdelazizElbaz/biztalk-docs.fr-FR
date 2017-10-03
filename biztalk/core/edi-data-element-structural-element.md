---
title: "Élément structurel d’élément données EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 775e8b87-b952-46d2-a506-5174d216a9aa
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600edb30ff157a520ac67eebce58428a62e27c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-data-element-structural-element"></a><span data-ttu-id="c6545-102">Élément structurel d'un élément de données EDI</span><span class="sxs-lookup"><span data-stu-id="c6545-102">EDI Data Element Structural Element</span></span>
<span data-ttu-id="c6545-103">L'élément de données constitue l'unité principale des données d'un message.</span><span class="sxs-lookup"><span data-stu-id="c6545-103">The data element is the primary unit of data in the message.</span></span> <span data-ttu-id="c6545-104">Les éléments de données sont séparés par un séparateur d'éléments de données, représenté par un astérisque dans un message X12 et par un signe plus dans un message EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="c6545-104">Data elements are separated by the data element separator, which is an asterisk by default for X12 and a plus sign by default for EDIFACT.</span></span> <span data-ttu-id="c6545-105">Le caractère facultatif des éléments de données est défini sur trois niveaux : obligatoire, facultatif ou conditionnel.</span><span class="sxs-lookup"><span data-stu-id="c6545-105">The optionality of data elements is defined as mandatory, optional, or conditional.</span></span>  
  
 <span data-ttu-id="c6545-106">Un élément de données peut être soit simple soit composite :</span><span class="sxs-lookup"><span data-stu-id="c6545-106">A data element can be either simple or composite.</span></span> <span data-ttu-id="c6545-107">les éléments de données simples sont des éléments numériques correspondant au plus petit niveau de données ;</span><span class="sxs-lookup"><span data-stu-id="c6545-107">Simple data elements are numeric and are the lowest level of data.</span></span> <span data-ttu-id="c6545-108">les éléments de données composites constituent des concaténations de sous-éléments, c'est-à-dire des éléments de données simples séparés par des séparateurs de composants.</span><span class="sxs-lookup"><span data-stu-id="c6545-108">Composite data elements are concatenations of sub element, which are simple data elements separated by a component separator.</span></span> <span data-ttu-id="c6545-109">Par défaut, le séparateur de composants est représenté par le signe deux-points pour les normes X12 et EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="c6545-109">By default, the component separator is the colon for X12 and EDIFACT.</span></span>  
  
 <span data-ttu-id="c6545-110">Dans le cas des messages EDIFACT, si les données à envoyer via EDI nécessitent l'envoi de caractères définis comme étant des séparateurs, vous devez utiliser un caractère d'échappement pour signaler que l'élément suivant n'est pas un séparateur mais bien une partie des données.</span><span class="sxs-lookup"><span data-stu-id="c6545-110">For EDIFACT-encoded messages, if the data to be sent via EDI needs to send any character defined for use as a separator, you need to use a release character to indicate that the following character is not a separator, but is part of the data.</span></span> <span data-ttu-id="c6545-111">Par défaut, le caractère d'échappement est le point d'interrogation (?).</span><span class="sxs-lookup"><span data-stu-id="c6545-111">The release character is by default the question mark (?).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6545-112">La norme X12 ne prend pas en charge le caractère d'échappement.</span><span class="sxs-lookup"><span data-stu-id="c6545-112">A release character is not supported for X12.</span></span> <span data-ttu-id="c6545-113">Lorsqu'un séparateur est rencontré dans les données d'un échange X12, au niveau de l'envoi ou de la réception, ce dernier est interrompu.</span><span class="sxs-lookup"><span data-stu-id="c6545-113">If a separator is encountered as part of the data of an X12-encoded interchange, on either the receive or send side, the interchange will be suspended.</span></span>