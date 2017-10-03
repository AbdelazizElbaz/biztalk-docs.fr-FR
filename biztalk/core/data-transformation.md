---
title: "Transformation de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, data translation
- data translation, about data translation
- data transformation, about data transformation
- maps, data transformation
- data transformation, maps
- data translation, maps
ms.assetid: a6aa5e9a-8d9c-478d-8f69-f9b16ed1a18c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ee1cd9b7e825f210032f7caaaa292496cfa44c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-transformation"></a><span data-ttu-id="00430-102">Transformation des données</span><span class="sxs-lookup"><span data-stu-id="00430-102">Data Transformation</span></span>
<span data-ttu-id="00430-103">Le mappage des données repose sur la transformation des données.</span><span class="sxs-lookup"><span data-stu-id="00430-103">Mapping data relies on data transformation.</span></span>  
  
 <span data-ttu-id="00430-104">La transformation des données est le processus de création d'une correspondance entre des enregistrements et des champs d'un schéma source et des enregistrements et des champs (souvent différents) d'un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="00430-104">Data transformation is the process of creating a correspondence between records and fields of a source schema to (often different) records and fields in a destination schema.</span></span> <span data-ttu-id="00430-105">Par exemple, elle peut consister à mapper les adresses d'expédition et de facturation d'un bon de commande avec celles d'une facture.</span><span class="sxs-lookup"><span data-stu-id="00430-105">An example of data transformation is to map shipping and billing address information from a purchase order to an invoice.</span></span> <span data-ttu-id="00430-106">Il s'agit là du type de mappage le plus basique.</span><span class="sxs-lookup"><span data-stu-id="00430-106">This is the most basic type of mapping.</span></span> <span data-ttu-id="00430-107">La transformation des données peut aussi s'appliquer à des opérations comme :</span><span class="sxs-lookup"><span data-stu-id="00430-107">Data transformation can also apply to operations such as:</span></span>  
  
-   <span data-ttu-id="00430-108">le calcul des données moyennes à partir d'un enregistrement de bouclage et l'envoi du résultat vers un champ du schéma de destination ;</span><span class="sxs-lookup"><span data-stu-id="00430-108">Averaging data from a looping record and sending the output to a single field in the destination schema.</span></span>  
  
-   <span data-ttu-id="00430-109">la conversion d'un caractère en son format ASCII ;</span><span class="sxs-lookup"><span data-stu-id="00430-109">Converting character data to its ASCII format.</span></span>  
  
-   <span data-ttu-id="00430-110">l'ajout ou la soustraction de données d'un ou de plusieurs enregistrements et l'envoi du résultat vers un champ du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="00430-110">Adding or subtracting data from one or more records and putting the result in a single field in the destination schema.</span></span>  
  
 <span data-ttu-id="00430-111">Pour convertir les données dans un autre format, utilisez un pipeline.</span><span class="sxs-lookup"><span data-stu-id="00430-111">If you want to translate data from one format to another, you would use a pipeline.</span></span> <span data-ttu-id="00430-112">Cela peut s'avérer utile pour résoudre les problèmes d'intégration des applications d'entreprise en convertissant un type de message donné dans les autres formats requis par les systèmes existants, mais cela ne peut pas se faire en utilisant un mappage.</span><span class="sxs-lookup"><span data-stu-id="00430-112">This can be helpful in solving enterprise application integration problems by translating a given type of message into alternative formats required by existing systems but cannot be done using a map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00430-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00430-113">See Also</span></span>  
 <span data-ttu-id="00430-114">[Mappages](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="00430-114">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="00430-115">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="00430-115">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)