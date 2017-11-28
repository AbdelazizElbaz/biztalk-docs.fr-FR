---
title: Sur la norme HL7 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- standards [HL7]
- HL7, standards
- Health Level Seven (HL7)
ms.assetid: 15f26ae3-d1ad-40a4-aafe-7148ef30cadb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9185248b5b897fbc7c909786c419b07fc3fb9d61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-hl7-standard"></a><span data-ttu-id="604e0-102">Sur la norme HL7</span><span class="sxs-lookup"><span data-stu-id="604e0-102">About the HL7 Standard</span></span>
<span data-ttu-id="604e0-103">Le contrôle d’intégrité au niveau sept (HL7) standard vise à faciliter la communication dans les environnements de soins de santé.</span><span class="sxs-lookup"><span data-stu-id="604e0-103">The purpose of the Health Level Seven (HL7) standard is to facilitate communication in health care environments.</span></span> <span data-ttu-id="604e0-104">L’objectif principal est de fournir des normes pour l’échange de données entre les applications d’ordinateur de soins de santé qui éliminer ou réduisent considérablement la maintenance de programmation et un programme interface personnalisée dans le cas contraire peut être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="604e0-104">The primary goal is to provide standards for the exchange of data among health care computer applications that eliminate or substantially reduce the custom interface programming and program maintenance that may otherwise be required.</span></span> <span data-ttu-id="604e0-105">Vous pouvez délimiter cet objectif principal comme un ensemble d’objectifs :</span><span class="sxs-lookup"><span data-stu-id="604e0-105">You can delineate this primary goal as a set of goals:</span></span>  
  
-   <span data-ttu-id="604e0-106">Que la norme prend en charge les échanges entre les systèmes implémentés dans des environnements techniques le plus grand.</span><span class="sxs-lookup"><span data-stu-id="604e0-106">That the standard supports exchanges among systems implemented in the widest variety of technical environments.</span></span> <span data-ttu-id="604e0-107">Son implémentation doit être pratique dans un large éventail de langages de programmation et systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="604e0-107">Its implementation should be practical in a wide variety of programming languages and operating systems.</span></span> <span data-ttu-id="604e0-108">Il doit prennent également en charge les communications dans un large éventail d’environnements de communications, allant d’un intégral, compatible OSI, réseau de niveau sept « pile » dans les environnements moins complètes, y compris le point à point primitifs RS 232C interconnexions et le transfert des données par lot médias, tels que disquette et sur bande.</span><span class="sxs-lookup"><span data-stu-id="604e0-108">It should also support communications in a wide variety of communications environments, ranging from a full, OSI-compliant, seven level network "stack" to less complete environments, including primitive point-to-point RS 232C interconnections and transfer of data by batch media, such as floppy disk and tape.</span></span>  
  
-   <span data-ttu-id="604e0-109">Que la norme prend en charge le transfert immédiat des transactions uniques, ainsi que les transferts de fichiers de plusieurs transactions.</span><span class="sxs-lookup"><span data-stu-id="604e0-109">That the standard supports immediate transfer of single transactions along with file transfers of multiple transactions.</span></span>  
  
-   <span data-ttu-id="604e0-110">Que la norme permet d’obtenir le plus haut niveau possible de la normalisation, cohérente avec les variantes de site dans l’utilisation et le format de certains éléments de données.</span><span class="sxs-lookup"><span data-stu-id="604e0-110">That the standard achieves the greatest possible degree of standardization, consistent with site variations in the usage and format of certain data elements.</span></span> <span data-ttu-id="604e0-111">La norme doit tenir compte des variations de site nécessaires.</span><span class="sxs-lookup"><span data-stu-id="604e0-111">The standard should accommodate necessary site-specific variations.</span></span> <span data-ttu-id="604e0-112">Cela inclut, au moins, tables spécifiques au site, les définitions de code et les segments de message éventuellement spécifique (par exemple, les segments HL7 Z).</span><span class="sxs-lookup"><span data-stu-id="604e0-112">This will include, at least, site-specific tables, code definitions, and possibly site-specific message segments (for example, HL7 Z segments).</span></span>  
  
-   <span data-ttu-id="604e0-113">Que la norme doit prendre en charge croissance évolutive que de nouvelles spécifications sont reconnues.</span><span class="sxs-lookup"><span data-stu-id="604e0-113">That the standard must support evolutionary growth as new requirements are recognized.</span></span> <span data-ttu-id="604e0-114">Cela inclut la prise en charge du processus d’introduire des extensions et nouvelles versions dans des environnements d’exploitation existants.</span><span class="sxs-lookup"><span data-stu-id="604e0-114">This includes support of the process of introducing extensions and new releases into existing operational environments.</span></span>  
  
-   <span data-ttu-id="604e0-115">Que l’organisation HL7 doit baser la norme sur des expériences avec les protocoles de production existants et les protocoles standard de l’industrie acceptées.</span><span class="sxs-lookup"><span data-stu-id="604e0-115">That the HL7 organization should base the standard on experiences with existing production protocols and accepted industry-wide standard protocols.</span></span> <span data-ttu-id="604e0-116">Toutefois, la norme ne doit pas privilégier les intérêts propriétaires des sociétés spécifiques au détriment d’autres utilisateurs de la norme.</span><span class="sxs-lookup"><span data-stu-id="604e0-116">However, the standard should not favor the proprietary interests of specific companies to the detriment of other users of the standard.</span></span> <span data-ttu-id="604e0-117">En même temps, HL7 recherches conserver les attributs uniques qu’un fournisseur peut apporter à marketplace.</span><span class="sxs-lookup"><span data-stu-id="604e0-117">At the same time, HL7 seeks to preserve the unique attributes that an individual vendor can bring to the marketplace.</span></span>  
  
-   <span data-ttu-id="604e0-118">Bien qu’il soit utile et pertinentes pour vous concentrer sur les systèmes d’information dans le nombre, l’objectif à long terme de la norme doit être pour définir des formats et protocoles pour les applications de l’ordinateur dans les environnements de soins de santé.</span><span class="sxs-lookup"><span data-stu-id="604e0-118">While it is both useful and pertinent to focus on information systems within hospitals, the long-term goal of the standard should be to define formats and protocols for computer applications in all health care environments.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="604e0-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="604e0-119">In This Section</span></span>  
  
-   [<span data-ttu-id="604e0-120">Versions HL7</span><span class="sxs-lookup"><span data-stu-id="604e0-120">HL7 Versions</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-versions.md)