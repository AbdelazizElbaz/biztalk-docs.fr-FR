---
title: "Prise en charge du jeu de caractères EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4f4492b-8cbe-48ed-810a-3e73e1cb5996
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c1463d8a06ab5da89306aababfe19362d6308dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-character-set-support"></a><span data-ttu-id="d9063-102">Prise en charge du jeu de caractères EDI</span><span class="sxs-lookup"><span data-stu-id="d9063-102">EDI Character Set Support</span></span>
<span data-ttu-id="d9063-103">Cette rubrique présente les jeux de caractères pris en charge dans les fonctionnalités EDI de [!INCLUDE[prague](../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9063-103">This topic indicates which character sets are supported in the EDI features of [!INCLUDE[prague](../includes/prague-md.md)].</span></span>  
  
|<span data-ttu-id="d9063-104">Codage EDI</span><span class="sxs-lookup"><span data-stu-id="d9063-104">EDI Encoding</span></span>|<span data-ttu-id="d9063-105">Jeux de caractères pris en charge</span><span class="sxs-lookup"><span data-stu-id="d9063-105">Supported Character Sets</span></span>|  
|------------------|------------------------------|  
|<span data-ttu-id="d9063-106">X12 (y compris HIPAA)</span><span class="sxs-lookup"><span data-stu-id="d9063-106">X12 (including HIPAA)</span></span>|<span data-ttu-id="d9063-107">X12 - Jeu de caractères de base (sous-ensemble d'ASCII)</span><span class="sxs-lookup"><span data-stu-id="d9063-107">X12 - Basic character set (subset of ASCII)</span></span>|  
|-|<span data-ttu-id="d9063-108">X12 - Jeu de caractères étendu (sous-ensemble d'ASCII, inclut également des caractères ISO8859-1)</span><span class="sxs-lookup"><span data-stu-id="d9063-108">X12- Extended character set (subset of ASCII and also includes ISO8859-1 chars)</span></span>|  
|-|<span data-ttu-id="d9063-109">UTF8/UNICODE</span><span class="sxs-lookup"><span data-stu-id="d9063-109">UTF8/UNICODE</span></span>|  
|<span data-ttu-id="d9063-110">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="d9063-110">EDIFACT</span></span>|<span data-ttu-id="d9063-111">UNOA</span><span class="sxs-lookup"><span data-stu-id="d9063-111">UNOA</span></span>|  
|-|<span data-ttu-id="d9063-112">UNOB</span><span class="sxs-lookup"><span data-stu-id="d9063-112">UNOB</span></span>|  
|-|<span data-ttu-id="d9063-113">UNOC - ISO 8859-1 : traitement des informations - partie 1 : alphabet Latin n°</span><span class="sxs-lookup"><span data-stu-id="d9063-113">UNOC- ISO 8859-1 : Information processing - Part 1: Latin alphabet No.</span></span> <span data-ttu-id="d9063-114">1</span><span class="sxs-lookup"><span data-stu-id="d9063-114">1</span></span>|  
|-|<span data-ttu-id="d9063-115">KECA - KS_C_5601-1987 (page de codes 949 Windows)</span><span class="sxs-lookup"><span data-stu-id="d9063-115">KECA - KS_C_5601-1987 (Windows 949 Code page)</span></span>|  
|-|<span data-ttu-id="d9063-116">UNOX (ISO2022 – JP)</span><span class="sxs-lookup"><span data-stu-id="d9063-116">UNOX (ISO2022 – JP)</span></span>|  
|-|<span data-ttu-id="d9063-117">De données codées UNOY - UTF8 **Remarque :** les caractères UNOD à UNOK définit qui prennent en charge UTF-8 données encodées sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d9063-117">UNOY- UTF8 encoded data **Note:**  The UNOD through UNOK character sets that support UTF8 encoded data are also supported.</span></span>|  
  
## <a name="setting-the-edi-character-set"></a><span data-ttu-id="d9063-118">Configuration du jeu de caractères EDI</span><span class="sxs-lookup"><span data-stu-id="d9063-118">Setting the EDI Character Set</span></span>  
 <span data-ttu-id="d9063-119">Dans un échange X12, vous pouvez définir le jeu de caractères d'un pipeline en configurant la propriété de pipeline CharacterSet.</span><span class="sxs-lookup"><span data-stu-id="d9063-119">For X12 encoded interchanges, you can set the character set for a pipeline by setting the CharacterSet pipeline property.</span></span> <span data-ttu-id="d9063-120">Pour plus d’informations, consultez [configuration des propriétés de Pipeline EDI](../core/configuring-edi-pipeline-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d9063-120">For more information, see [Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9063-121">Il existe un contrôle du jeu de caractères X12 dans la page Génération de l'enveloppe d'échange X12 de la boîte de dialogue Propriétés X12/EDI de la console Administration de BizTalk Server, mais celui-ci sert uniquement à valider les valeurs des propriétés entrées dans la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="d9063-121">There is an X12 character set control in the X12 Interchange Envelope Generation page of the X12 EDI Properties dialog box in the BizTalk Server Administration console, but that control is only used to validate the values entered for the properties in the EDI Properties dialog box.</span></span>  
  
 <span data-ttu-id="d9063-122">Pour les échanges EDIFACT, vous avez la possibilité de définir le jeu de caractères pour un tiers en configurant la propriété de tiers UNB1.1 sur Tiers en tant que récepteur d'échanges dans la page de propriétés Définition du segment UNB.</span><span class="sxs-lookup"><span data-stu-id="d9063-122">For EDIFACT encoded interchanges, you can set the character set for a party by setting the UNB1.1 party property in the UNB Segment Definition property page for the party as interchange receiver.</span></span> <span data-ttu-id="d9063-123">Le codage utilisé dans un échange entrant est déterminé par la valeur du champ UNB1.1 de l'en-tête de l'échange.</span><span class="sxs-lookup"><span data-stu-id="d9063-123">The encoding used in an incoming interchange is determined by the value of the UNB1.1 field in the header of the interchange.</span></span> <span data-ttu-id="d9063-124">Pour plus d’informations, consultez [configuration des enveloppes (EDIFACT-paramètres des documents informatisés)](../core/configuring-envelopes-edifact-transaction-set-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d9063-124">For more information, see [Configuring Envelopes (EDIFACT-Transaction Set Settings)](../core/configuring-envelopes-edifact-transaction-set-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9063-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9063-125">See Also</span></span>  
 <span data-ttu-id="d9063-126">[Configuration des propriétés de Pipeline EDI](../core/configuring-edi-pipeline-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d9063-126">[Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md) </span></span>  
 [<span data-ttu-id="d9063-127">Configuration d’enveloppes (EDIFACT-informatisés paramètres)</span><span class="sxs-lookup"><span data-stu-id="d9063-127">Configuring Envelopes (EDIFACT-Transaction Set Settings)</span></span>](../core/configuring-envelopes-edifact-transaction-set-settings.md)