---
title: Comptage des positions en octets | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf666ec-d15e-4d2d-9df9-49189f352c65
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3cdb7bbf1f0d6af04f0cc28ed1bdb7477b259de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="position-counting-in-bytes"></a><span data-ttu-id="22bd2-102">Comptage des positions en octets</span><span class="sxs-lookup"><span data-stu-id="22bd2-102">Position Counting in Bytes</span></span>

## <a name="overview"></a><span data-ttu-id="22bd2-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="22bd2-103">Overview</span></span>

<span data-ttu-id="22bd2-104">Vous pouvez utiliser la **compter les Positions par octet** propriété de la **schéma** nœud :</span><span class="sxs-lookup"><span data-stu-id="22bd2-104">You can use the **Count Positions In Bytes** property of the **Schema** node to:</span></span> 

* <span data-ttu-id="22bd2-105">Spécifiez comment les valeurs que vous entrez pour le **longueur positionnelle** et **décalage de position** propriétés des différents champs dans les enregistrements positionnels sont interprétées.</span><span class="sxs-lookup"><span data-stu-id="22bd2-105">Specify how the values you enter for the **Positional Length** and **Positional Offset** properties of the various fields within positional records are interpreted</span></span>
* <span data-ttu-id="22bd2-106">Spécifiez comment les valeurs que vous entrez pour le **décalage de la balise** propriété des enregistrements positionnels eux-mêmes sont interprétés.</span><span class="sxs-lookup"><span data-stu-id="22bd2-106">Specify how the values you enter for the **Tag Offset** property of the positional records themselves are interpreted</span></span>

<span data-ttu-id="22bd2-107">Par défaut, ces valeurs sont interprétées comme un nombre de caractères.</span><span class="sxs-lookup"><span data-stu-id="22bd2-107">By default, these values are interpreted as a number of characters.</span></span> <span data-ttu-id="22bd2-108">Mais lorsque le **compter les Positions par octet** est définie sur **True**, ces valeurs sont interprétées comme un nombre d’octets.</span><span class="sxs-lookup"><span data-stu-id="22bd2-108">But when the **Count Positions In Bytes** property is set to **True**, these values are interpreted as a number of bytes.</span></span>  
  
 <span data-ttu-id="22bd2-109">Définition de la **compter les Positions par octet** propriété **True** peut être nécessaire lors du traitement de caractères multioctets définie (MBCS ou DBCS) des données, ou lorsque vos messages de fichier plat proviennent de SAP, mainframes, ou autres systèmes susceptibles de compter les positions par octet.</span><span class="sxs-lookup"><span data-stu-id="22bd2-109">Setting the **Count Positions In Bytes** property to **True** might be necessary when dealing with multibyte character set (MBCS or DBCS) data, or when your flat file messages originate in SAP, mainframes, or other systems that may count positions in bytes.</span></span>  
  
 <span data-ttu-id="22bd2-110">Le comptage des longueurs de champ en octets peut être compliqué lorsque le nombre d'octets utilisés pour coder les caractères est variable et peut entraîner quelques problèmes pour la détermination des limites des champs.</span><span class="sxs-lookup"><span data-stu-id="22bd2-110">Counting field lengths in bytes can be complicated when the number of bytes used to encode characters is variable, and can result in some issues with respect to determining field boundaries.</span></span> <span data-ttu-id="22bd2-111">Lorsque le désassembleur de fichier plat analyse un fichier plat dans pareil cas, il tente de prendre des mesures d'analyse appropriées en fonction de sa connaissance du codage de caractères utilisé.</span><span class="sxs-lookup"><span data-stu-id="22bd2-111">When the flat file disassembler parses a flat file in such situations, it attempts to make appropriate parsing decisions based on its knowledge of the character encoding in use.</span></span>  
  
 <span data-ttu-id="22bd2-112">Un exemple de ce type de décision d'analyse est celui des octets de tête des codages de caractères MBCS.</span><span class="sxs-lookup"><span data-stu-id="22bd2-112">An example of this type of parsing decision concerns lead bytes in MBCS character encodings.</span></span> <span data-ttu-id="22bd2-113">Les octets de tête sont des valeurs d'octet connues utilisées pour commencer les codages de caractères multioctet. Ils ne doivent jamais se trouver seuls.</span><span class="sxs-lookup"><span data-stu-id="22bd2-113">Lead bytes are well-known byte values that are used to begin multibyte character encodings, and which should never occur on their own.</span></span> <span data-ttu-id="22bd2-114">En spécifiant la longueur des champs à l'aide d'octets plutôt que de caractères, vous pourrez être confronté à des situations où le dernier octet d'un champ se révèlera être un octet de tête, qui ne pourra donc pas constituer un caractère entier à lui seul.</span><span class="sxs-lookup"><span data-stu-id="22bd2-114">When specifying the length of the fields using bytes rather than character, situations may arise in which the last byte in a field is found to be a lead byte, which cannot constitute an entire character on its own.</span></span> <span data-ttu-id="22bd2-115">En pareil cas, le désassembleur de fichier plat traitera le caractère précédant immédiatement l'octet de tête comme dernier caractère du champ précédent, et commencera l'analyse du champ suivant à partir de l'octet de tête.</span><span class="sxs-lookup"><span data-stu-id="22bd2-115">In such cases, the flat file disassembler will treat the character occurring just prior to the lead byte as the last character in the previous field, and begin parsing the next field starting with the lead byte.</span></span>  

<span data-ttu-id="22bd2-116">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="22bd2-116">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="22bd2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22bd2-117">See Also</span></span>  
 [<span data-ttu-id="22bd2-118">Considérations concernant les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="22bd2-118">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   
