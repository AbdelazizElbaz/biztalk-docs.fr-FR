---
title: "Schémas de Document EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc3a30b8-0686-4c06-985b-13f2c95f8e99
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db79e5e4421719a936f68c409c166f9eac38605c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-document-schemas"></a><span data-ttu-id="af24c-102">Schémas de document EDI</span><span class="sxs-lookup"><span data-stu-id="af24c-102">EDI Document Schemas</span></span>
<span data-ttu-id="af24c-103">Les schémas de document définissent le corps d'un type de document de transaction EDI.</span><span class="sxs-lookup"><span data-stu-id="af24c-103">Document schemas define the body of an EDI transaction document type.</span></span>  
  
## <a name="schema-delivery-and-setup"></a><span data-ttu-id="af24c-104">Réception et configuration du schéma</span><span class="sxs-lookup"><span data-stu-id="af24c-104">Schema Delivery and Setup</span></span>  
 <span data-ttu-id="af24c-105">Schémas de document EDI sont remis dans un état compressé dans un fichier exécutable à extraction automatique, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe.</span><span class="sxs-lookup"><span data-stu-id="af24c-105">EDI document schemas are delivered in a compressed state in a self-extracting executable, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe.</span></span> <span data-ttu-id="af24c-106">Le fichier exécutable à extraction automatique garantit qu’une structure de dossiers appropriée est créé (par le type de codage et les sous-types version/publication).</span><span class="sxs-lookup"><span data-stu-id="af24c-106">The self-extracting executable ensures that an appropriate folder structure is created (per the encoding type and version/release sub types).</span></span> <span data-ttu-id="af24c-107">Une fois exécuté, il dépose les schémas EANCOM, EDIFACT, HIPAA et X12 dans des sous-dossiers au sein du répertoire de l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="af24c-107">When executed, the executable deposits EANCOM, EDIFACT, HIPAA, and X12 schemas into subfolders in the same directory as the executable.</span></span>  
  
 <span data-ttu-id="af24c-108">Les espaces de noms de schémas par défaut sont :</span><span class="sxs-lookup"><span data-stu-id="af24c-108">The default schema namespaces are:</span></span>  
  
-   <span data-ttu-id="af24c-109">Pour X12 : `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`</span><span class="sxs-lookup"><span data-stu-id="af24c-109">For X12 – `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`</span></span>  
  
-   <span data-ttu-id="af24c-110">Pour EDIFACT : `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`</span><span class="sxs-lookup"><span data-stu-id="af24c-110">For EDIFACT – `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`</span></span>  
  
## <a name="schema-naming-convention"></a><span data-ttu-id="af24c-111">Convention d'affectation de noms de schémas</span><span class="sxs-lookup"><span data-stu-id="af24c-111">Schema Naming Convention</span></span>  
 <span data-ttu-id="af24c-112">La convention d’affectation de noms pour le X12 et type de codage EDIFACT est \<codage > _\<Version >\<version >\_\<Doctype >.</span><span class="sxs-lookup"><span data-stu-id="af24c-112">The naming convention for the X12 and EDIFACT encoding type is \<Encoding>_\<Version>\<Release>\_\<Doctype>.</span></span> <span data-ttu-id="af24c-113">En voici quelques exemples : le schéma X12_00401_864.xsd pour le type de document X12 864 (version d'origine 004, version finale 01) et le schéma EDIFACT_D01C_AUTHOR.xsd pour le type de document EDIFACT AUTHOR (version d'origine D01, version finale C).</span><span class="sxs-lookup"><span data-stu-id="af24c-113">Examples are the X12_00401_864.xsd schema for the X12 864 document type (version 004, release 01) and the EDIFACT_D01C_AUTHOR.xsd schema for the EDIFACT AUTHOR document type (version D01, release C).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af24c-114">Le nom d'un schéma EDIFACT est sensible à la casse.</span><span class="sxs-lookup"><span data-stu-id="af24c-114">The schema name of an EDIFACT schema is case-sensitive.</span></span> <span data-ttu-id="af24c-115">Par exemple, EFACT_D98B_ORDERS et EFACT_d98B_Orders désignent deux schémas différents.</span><span class="sxs-lookup"><span data-stu-id="af24c-115">For example, EFACT_D98B_ORDERS and EFACT_d98B_Orders would be two different schemas.</span></span>  
  
## <a name="schema-contents"></a><span data-ttu-id="af24c-116">Contenu des schémas</span><span class="sxs-lookup"><span data-stu-id="af24c-116">Schema Contents</span></span>  
 <span data-ttu-id="af24c-117">Un schéma de document X12 démarre avec un en-tête de document informatisé ST et se termine avec un code de fin de document informatisé SE.</span><span class="sxs-lookup"><span data-stu-id="af24c-117">A document schema starts with the ST transaction set header and ends with the SE transaction set trailer for an X12-encoded document.</span></span> <span data-ttu-id="af24c-118">Un schéma de document EDIFACT démarre avec un en-tête de message UNH et un code de fin de message UNT.</span><span class="sxs-lookup"><span data-stu-id="af24c-118">It starts with the UNH message header and ends with the UNT message trailer for an EDIFACT-encoded document.</span></span> <span data-ttu-id="af24c-119">Le schéma définit chaque élément de données de ces en-têtes et codes de fin.</span><span class="sxs-lookup"><span data-stu-id="af24c-119">The schema defines each data element of these headers and trailers.</span></span>  
  
 <span data-ttu-id="af24c-120">Un schéma de document définit ensuite chaque segment du document informatisé ou du message, ainsi que les éléments de données au sein de ces segments.</span><span class="sxs-lookup"><span data-stu-id="af24c-120">A document schema then defines each segment within the transaction set/message and the data elements within those segments.</span></span> <span data-ttu-id="af24c-121">Par exemple, le schéma X12_00401_864.xsd définit les éléments BMG01, BMG02 et BMG03 des segments BMG.</span><span class="sxs-lookup"><span data-stu-id="af24c-121">For example, the X12_00401_864.xsd schema defines the BMG01, BMG02, and BMG03 elements of the BMG segments.</span></span> <span data-ttu-id="af24c-122">Le schéma spécifie les caractéristiques du type de données complexes du segment, telles que l'ordre des champs, le type de délimiteur et l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="af24c-122">The schema specifies the characteristics of the segment's complex data type, such as the field order, delimiter type, and namespace.</span></span> <span data-ttu-id="af24c-123">Si le segment contient des règles de validation de champs croisés, le schéma définit celles-ci.</span><span class="sxs-lookup"><span data-stu-id="af24c-123">If there are cross-field validation rules for the segment, the schema defines the rules.</span></span> <span data-ttu-id="af24c-124">Pour plus d’informations, consultez [Validation croisée du Segment de champ](../core/cross-field-segment-validation.md).</span><span class="sxs-lookup"><span data-stu-id="af24c-124">For more information, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).</span></span>  
  
 <span data-ttu-id="af24c-125">Le schéma spécifie les caractéristiques de chaque élément de données du segment, telles que le type de données simples, le nombre minimal d'occurrences, la longueur minimale et la longueur maximale.</span><span class="sxs-lookup"><span data-stu-id="af24c-125">The schema specifies the characteristics of each data element within the segment, such as the simple data type, minimum occurrences, minimum length, and maximum length.</span></span>  
  
 <span data-ttu-id="af24c-126">Si le type de message contient une boucle, le schéma définit les éléments de données de chaque boucle, le nombre minimal et maximal d'occurrences de la boucle, et si la boucle est liée ou non.</span><span class="sxs-lookup"><span data-stu-id="af24c-126">If there is a loop in the message type, the schema defines the data elements within each loop, the minimum and maximum occurrences of the loop, and whether the loop is bounded or unbounded.</span></span> <span data-ttu-id="af24c-127">Il définit également l'imbrication d'un segment, et si la boucle est explicite ou implicite.</span><span class="sxs-lookup"><span data-stu-id="af24c-127">The schema also defines nesting of a segment, and whether the loop is explicit or implicit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af24c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af24c-128">See Also</span></span>  
 <span data-ttu-id="af24c-129">[Structure des messages EDI](../core/edi-message-structure.md) </span><span class="sxs-lookup"><span data-stu-id="af24c-129">[EDI Message Structure](../core/edi-message-structure.md) </span></span>  
 [<span data-ttu-id="af24c-130">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="af24c-130">EDI Message Validation</span></span>](../core/edi-message-validation.md)