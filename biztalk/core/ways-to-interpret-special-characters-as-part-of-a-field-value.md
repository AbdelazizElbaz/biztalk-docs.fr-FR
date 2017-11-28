---
title: "Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e19a202-4e4d-42e0-ba1e-fddc52792b21
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b96a3c7502a47541e8e58ec3df3eccf6098e3abc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-interpret-special-characters-as-part-of-a-field-value"></a><span data-ttu-id="77b66-102">Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ</span><span class="sxs-lookup"><span data-stu-id="77b66-102">Ways to Interpret Special Characters as Part of a Field Value</span></span>
<span data-ttu-id="77b66-103">Les champs des enregistrements positionnels et délimités peuvent contenir des caractères spéciaux de différents types tels que les caractères de remplissage, les caractères de retour à la ligne et les caractères d'échappement.</span><span class="sxs-lookup"><span data-stu-id="77b66-103">Fields in both positional and delimited records can contain special characters of different types, such as pad, wrap, and escape characters.</span></span> <span data-ttu-id="77b66-104">Les enregistrements délimités peuvent également contenir un ou plusieurs caractères délimiteur utilisés pour séparer les champs d'un enregistrement et les enregistrements entre eux.</span><span class="sxs-lookup"><span data-stu-id="77b66-104">Delimited records can also contain one or more different delimiter characters that are used to separate the fields within a record and one record from another record.</span></span> <span data-ttu-id="77b66-105">Ces caractères spéciaux font parfois partie des données elles-mêmes et ne doivent alors pas être interprétés comme spéciaux.</span><span class="sxs-lookup"><span data-stu-id="77b66-105">Sometimes these special characters are part of the data itself, and are not meant to be interpreted as special in those cases.</span></span>  
  
 <span data-ttu-id="77b66-106">Les schémas de fichier plat utilisés par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prennent en charge deux techniques différentes pour marquer les occurrences des caractères habituellement spéciaux comme faisant simplement partie des données contenues par un champ.</span><span class="sxs-lookup"><span data-stu-id="77b66-106">The flat file schemas used by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] support two different techniques for flagging occurrences of otherwise special characters as simply part of the data contained by a field.</span></span> <span data-ttu-id="77b66-107">Ces deux techniques utilisent les caractères d'échappement et les caractères de retour à la ligne respectivement.</span><span class="sxs-lookup"><span data-stu-id="77b66-107">These two techniques employ escape characters and wrap characters, respectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77b66-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="77b66-108">In This Section</span></span>  
  
-   [<span data-ttu-id="77b66-109">Caractères d’échappement</span><span class="sxs-lookup"><span data-stu-id="77b66-109">Escape Characters</span></span>](../core/escape-characters.md)  
  
-   [<span data-ttu-id="77b66-110">Encapsuler des caractères</span><span class="sxs-lookup"><span data-stu-id="77b66-110">Wrap Characters</span></span>](../core/wrap-characters.md)