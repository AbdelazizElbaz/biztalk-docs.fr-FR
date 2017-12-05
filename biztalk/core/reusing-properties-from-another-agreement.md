---
title: "Réutilisation des propriétés d’un autre accord | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e1cc60-d581-43ca-aa70-1e0d6238497a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7db2118f372014a3e8f108c1ff2273bc5aad976
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="reusing-properties-from-another-agreement"></a><span data-ttu-id="df7a9-102">Réutilisation des propriétés d'un autre accord</span><span class="sxs-lookup"><span data-stu-id="df7a9-102">Reusing Properties from Another Agreement</span></span>
<span data-ttu-id="df7a9-103">Vous pouvez réutiliser les propriétés entre les accords.</span><span class="sxs-lookup"><span data-stu-id="df7a9-103">You can reuse properties between agreements.</span></span> <span data-ttu-id="df7a9-104">Vous gagnez ainsi un temps précieux lorsque la plupart des propriétés d'un nouvel accord sont identiques à celles d'un accord existant.</span><span class="sxs-lookup"><span data-stu-id="df7a9-104">This can save a significant amount of time when either most or all of the properties of a new agreement are the same as those of an existing agreement.</span></span> <span data-ttu-id="df7a9-105">Le [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] interface utilisateur de BizTalk Server vous permet d’exporter un accord dans un fichier de modèle XML.</span><span class="sxs-lookup"><span data-stu-id="df7a9-105">The [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] user interface in BizTalk Server enables you to export an agreement into an XML template file.</span></span> <span data-ttu-id="df7a9-106">Vous pouvez ensuite l'importer pour réutiliser les mêmes propriétés d'accord.</span><span class="sxs-lookup"><span data-stu-id="df7a9-106">You can then import the XML template to reuse the same agreement properties.</span></span>  
  
 <span data-ttu-id="df7a9-107">L'exportation de l'accord dans un modèle XML permet de capturer la majorité, et non pas la totalité, des propriétés d'un accord.</span><span class="sxs-lookup"><span data-stu-id="df7a9-107">Exporting the agreement to an XML template captures most, but not all, properties from the agreement.</span></span> <span data-ttu-id="df7a9-108">Les propriétés suivantes seront *pas* être exportées vers le fichier XML :</span><span class="sxs-lookup"><span data-stu-id="df7a9-108">The following properties will *not* be exported to the XML template file:</span></span>  
  
-   <span data-ttu-id="df7a9-109">Toutes les propriétés de la **propriétés générales** page dans le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="df7a9-109">All the properties from the **General Properties** page in the **General** tab.</span></span>  
  
-   <span data-ttu-id="df7a9-110">Toutes les propriétés de la **Contacts** page dans le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="df7a9-110">All the properties from the **Contacts** page in the **General** tab.</span></span>  
  
-   <span data-ttu-id="df7a9-111">Toutes les propriétés de la **des propriétés supplémentaires** page dans le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="df7a9-111">All the properties from the **Additional Properties** page in the **General** tab.</span></span>  
  
-   <span data-ttu-id="df7a9-112">Dépendant de l’identificateur de paramètres à partir de la **identificateurs** page sous l’onglet d’accord unidirectionnel. Il s'agit des paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="df7a9-112">Identifier-related settings from the **Identifiers** page in the one-way agreement tab. These are:</span></span>  
  
    -   <span data-ttu-id="df7a9-113">**Pour X12**: ISA5, ISA6, ISA7, ISA8 et les paramètres du résolveur d’accord supplémentaire</span><span class="sxs-lookup"><span data-stu-id="df7a9-113">**For X12**: ISA5, ISA6, ISA7, ISA8, and additional agreement resolver settings</span></span>  
  
    -   <span data-ttu-id="df7a9-114">**Pour EDIFACT**: UNB 2.1, UNB 2.2, UNB 3.1, UNB 3.2 et paramètres du résolveur d’accord supplémentaire</span><span class="sxs-lookup"><span data-stu-id="df7a9-114">**For EDIFACT**: UNB 2.1, UNB 2.2, UNB 3.1, UNB 3.2, and additional agreement resolver settings</span></span>  
  
    -   <span data-ttu-id="df7a9-115">**Pour AS2**: AS2-To, AS2-From et les paramètres du résolveur d’accord supplémentaire</span><span class="sxs-lookup"><span data-stu-id="df7a9-115">**For AS2**: AS2-To, AS2-From, and additional agreement resolver settings</span></span>  
  
-   <span data-ttu-id="df7a9-116">Envoyer l’association de ports à partir de la **Ports d’envoi** page sous l’onglet d’accord unidirectionnel pour X12, EDIFACT et AS2 de contrats.</span><span class="sxs-lookup"><span data-stu-id="df7a9-116">Send port association from the **Send Ports** page in the one-way agreement tab for X12, EDIFACT, and AS2 agreements.</span></span>  
  
 <span data-ttu-id="df7a9-117">À l'exception des propriétés mentionnées précédemment, les propriétés suivantes seront exportées dans le fichier XML :</span><span class="sxs-lookup"><span data-stu-id="df7a9-117">Other than the properties listed above, the following properties will be exported to the XML template file:</span></span>  
  
-   <span data-ttu-id="df7a9-118">Tous les paramètres ayant trait au protocole de codage (X12, EDIFACT ou AS2).</span><span class="sxs-lookup"><span data-stu-id="df7a9-118">All settings related to the encoding protocol (X12, EDIFACT, or AS2).</span></span>  
  
-   <span data-ttu-id="df7a9-119">Tous les paramètres ayant trait aux lots (autres que l'ID de lot).</span><span class="sxs-lookup"><span data-stu-id="df7a9-119">All the batch-related settings (other than the batch ID).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df7a9-120">Toutes les propriétés applicables seront remplacées lors de la copie des propriétés dans l'accord de destination.</span><span class="sxs-lookup"><span data-stu-id="df7a9-120">All the applicable properties will be overwritten when you copy properties to the destination agreement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df7a9-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="df7a9-121">In This Section</span></span>  
  
-   [<span data-ttu-id="df7a9-122">Exportation des propriétés d’un accord vers un fichier XML</span><span class="sxs-lookup"><span data-stu-id="df7a9-122">Exporting Agreement Properties to an XML FIle</span></span>](../core/exporting-agreement-properties-to-an-xml-file.md)  
  
-   [<span data-ttu-id="df7a9-123">Importation des propriétés d’un accord à partir d’un fichier XML</span><span class="sxs-lookup"><span data-stu-id="df7a9-123">Importing Agreement Properties from an XML File</span></span>](../core/importing-agreement-properties-from-an-xml-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="df7a9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df7a9-124">See Also</span></span>  
 [<span data-ttu-id="df7a9-125">Configuration des propriétés EDI</span><span class="sxs-lookup"><span data-stu-id="df7a9-125">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)