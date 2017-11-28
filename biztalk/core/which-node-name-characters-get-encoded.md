---
title: "Qui le codage des caractères de nom de nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a581d2-48fa-4c36-b5c2-fe87c328a7f4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3895fd74ac63380d5502a05eed7c145e13bfd681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="which-node-name-characters-get-encoded"></a><span data-ttu-id="275c1-102">Caractères de nom de nœud codés</span><span class="sxs-lookup"><span data-stu-id="275c1-102">Which Node Name Characters Get Encoded</span></span>
<span data-ttu-id="275c1-103">XML impose certaines restrictions concernant les caractères pouvant être utilisés dans les noms XML, tels que les noms d'élément, notamment concernant le premier caractère d'un nom XML.</span><span class="sxs-lookup"><span data-stu-id="275c1-103">XML places some restrictions on the characters that can be used in XML names, such as element names, including some special restrictions on the first character of an XML name.</span></span> <span data-ttu-id="275c1-104">Les objectifs conceptuels de la détermination des caractères à autoriser et à exclure des noms XML conformes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="275c1-104">The conceptual goals in determining which characters to allow and which characters to exclude from legal XML names are:</span></span>  
  
-   <span data-ttu-id="275c1-105">Lorsque c’est possible, soyez inclusif plutôt qu'exclusif, de sorte que les nouveaux systèmes d'écriture puissent être pris en charge lorsqu’ils sont codés en Unicode.</span><span class="sxs-lookup"><span data-stu-id="275c1-105">Wherever applicable, be inclusive rather than exclusive, so that new writing systems can be accommodated as they are encoded in Unicode.</span></span>  
  
-   <span data-ttu-id="275c1-106">Excluez les caractères qui peuvent être utilisés ou sont utilisés en tant que délimiteurs afin que les noms XML puissent apparaître plus facilement dans un contexte délimité, autre que XML.</span><span class="sxs-lookup"><span data-stu-id="275c1-106">Exclude characters that may be or are used as delimiters, so that XML names can more easily appear in a non-XML, delimited context.</span></span>  
  
 <span data-ttu-id="275c1-107">Le tableau suivant indique les caractères pouvant être utilisés dans un nom XML, à n'importe quelle position dans le nom, autre que la première, ou non.</span><span class="sxs-lookup"><span data-stu-id="275c1-107">The following table shows which characters can be used in an XML name, either in any position within the name, or in any position other than the first.</span></span> <span data-ttu-id="275c1-108">Certains caractères autorisés sont toutefois exclus en première position d’un nom.</span><span class="sxs-lookup"><span data-stu-id="275c1-108">Some allowable characters are excluded from being the first character in the name.</span></span> <span data-ttu-id="275c1-109">Les caractères littéraux sont placés entre guillemets, et les séries sont placées entre crochets.</span><span class="sxs-lookup"><span data-stu-id="275c1-109">Literal characters are quoted, and ranges are shown within square brackets.</span></span>  
  
|<span data-ttu-id="275c1-110">Position dans le nom</span><span class="sxs-lookup"><span data-stu-id="275c1-110">Position in name</span></span>|<span data-ttu-id="275c1-111">Caractères autorisés</span><span class="sxs-lookup"><span data-stu-id="275c1-111">Allowed characters</span></span>|  
|----------------------|------------------------|  
|<span data-ttu-id="275c1-112">Toute position</span><span class="sxs-lookup"><span data-stu-id="275c1-112">Any position</span></span>|<span data-ttu-id="275c1-113">["A"-"Z"], ["a"-"z"], "_", [0x00C0-0x02FF], [0x0370-0x037D], [0x037F-0x1FFF], [0x200C-0x200D], [0x2070-0x218F], [0x2C00-0x2FEF], [0x3001-0xD7FF], [0xF900-0xEFFF]</span><span class="sxs-lookup"><span data-stu-id="275c1-113">["A"-"Z"], ["a"-"z"], "_", [0x00C0-0x02FF], [0x0370-0x037D], [0x037F-0x1FFF], [0x200C-0x200D], [0x2070-0x218F], [0x2C00-0x2FEF], [0x3001-0xD7FF], [0xF900-0xEFFF]</span></span>|  
|<span data-ttu-id="275c1-114">Toute position à l'exception de premier</span><span class="sxs-lookup"><span data-stu-id="275c1-114">Any position except first</span></span>|<span data-ttu-id="275c1-115">"-", ".", ["0"-"9"], 0x00B7, [0x0300-0x036F], [0x203F-0x2040]</span><span class="sxs-lookup"><span data-stu-id="275c1-115">"-", ".", ["0"-"9"], 0x00B7, [0x0300-0x036F], [0x203F-0x2040]</span></span>|  
  
 <span data-ttu-id="275c1-116">La meilleure pratique en anglais pour un nom d’élément ou d’attribut (un nom de nœud dans une arborescence de schéma) peut se résumer ainsi :</span><span class="sxs-lookup"><span data-stu-id="275c1-116">Best practice in English for an element or attribute name (a node name in the schema tree view) can be summarized as:</span></span>  
  
-   <span data-ttu-id="275c1-117">Utilisez des caractères alphanumériques, mais ne commencez pas par un chiffre.</span><span class="sxs-lookup"><span data-stu-id="275c1-117">Use alphanumeric characters, except do not begin a name with a numeral.</span></span>  
  
-   <span data-ttu-id="275c1-118">Utilisez le trait de soulignement (_), trait d’union (-), point (.) et point intermédiaire (·).</span><span class="sxs-lookup"><span data-stu-id="275c1-118">Use the underscore (_),hyphen (-), period (.), and middle dot (·).</span></span>  
  
-   <span data-ttu-id="275c1-119">N'utilisez pas d'espace.</span><span class="sxs-lookup"><span data-stu-id="275c1-119">Do not use white space.</span></span>  
  
-   <span data-ttu-id="275c1-120">Utilisez des mots significatifs ou des combinaisons de mots issues de langues naturelles.</span><span class="sxs-lookup"><span data-stu-id="275c1-120">Use meaningful words or combinations of words in natural languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275c1-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="275c1-121">See Also</span></span>  
 <span data-ttu-id="275c1-122">[Propriété de nom de nœud](../core/node-name-property.md) </span><span class="sxs-lookup"><span data-stu-id="275c1-122">[Node Name Property](../core/node-name-property.md) </span></span>  
 [<span data-ttu-id="275c1-123">Comment les caractères de nom de nœud codés</span><span class="sxs-lookup"><span data-stu-id="275c1-123">How Node Name Characters Get Encoded</span></span>](../core/how-node-name-characters-get-encoded.md)