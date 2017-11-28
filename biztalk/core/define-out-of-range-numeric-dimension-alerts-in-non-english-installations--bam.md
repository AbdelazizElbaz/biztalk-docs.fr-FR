---
title: "Comment définir des alertes de Dimension numérique de Out-of-Range dans les Installations Non anglaises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f1e0373-eadf-4c6d-9a38-a34d847f310f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea63008680c026eded843e32a7b2c6ff26dc0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-out-of-range-numeric-dimension-alerts-in-non-english-installations"></a><span data-ttu-id="dcef0-102">Définition d'alertes de dimension numérique hors limite dans les installations non anglaises</span><span class="sxs-lookup"><span data-stu-id="dcef0-102">How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations</span></span>
<span data-ttu-id="dcef0-103">Lorsque vous définissez des alertes qui incluent une condition pour une valeur qui se trouve en dehors de la dimension de plage numérique définie sur les installations non anglaises, vous devez modifier manuellement la définition BAM avec la version localisée de la chaîne **hors limites**.</span><span class="sxs-lookup"><span data-stu-id="dcef0-103">When setting alerts that include a condition for a value that is outside the defined numeric range dimension on non-English installations, you must manually modify the BAM definition with the localized version of the string **out of range**.</span></span>  
  
 <span data-ttu-id="dcef0-104">Le tableau suivant répertorie des exemples de valeurs hors limites traduites.</span><span class="sxs-lookup"><span data-stu-id="dcef0-104">The following table lists examples of localized out-of-range values.</span></span>  
  
|<span data-ttu-id="dcef0-105">Code langue</span><span class="sxs-lookup"><span data-stu-id="dcef0-105">Language code</span></span>|<span data-ttu-id="dcef0-106">Chaîne traduite</span><span class="sxs-lookup"><span data-stu-id="dcef0-106">Localized string</span></span>|  
|-------------------|----------------------|  
|<span data-ttu-id="dcef0-107">CN</span><span class="sxs-lookup"><span data-stu-id="dcef0-107">CN</span></span>|<span data-ttu-id="dcef0-108">超出范围</span><span class="sxs-lookup"><span data-stu-id="dcef0-108">超出范围</span></span>|  
|<span data-ttu-id="dcef0-109">DE</span><span class="sxs-lookup"><span data-stu-id="dcef0-109">DE</span></span>|<span data-ttu-id="dcef0-110">Außerhalb des gültigen Bereichs</span><span class="sxs-lookup"><span data-stu-id="dcef0-110">Außerhalb des gültigen Bereichs</span></span>|  
|<span data-ttu-id="dcef0-111">ES</span><span class="sxs-lookup"><span data-stu-id="dcef0-111">ES</span></span>|<span data-ttu-id="dcef0-112">Fuera de rango</span><span class="sxs-lookup"><span data-stu-id="dcef0-112">Fuera de rango</span></span>|  
|<span data-ttu-id="dcef0-113">FR</span><span class="sxs-lookup"><span data-stu-id="dcef0-113">FR</span></span>|<span data-ttu-id="dcef0-114">hors limites</span><span class="sxs-lookup"><span data-stu-id="dcef0-114">hors limites</span></span>|  
|<span data-ttu-id="dcef0-115">IT</span><span class="sxs-lookup"><span data-stu-id="dcef0-115">IT</span></span>|<span data-ttu-id="dcef0-116">Fuori intervallo</span><span class="sxs-lookup"><span data-stu-id="dcef0-116">Fuori intervallo</span></span>|  
|<span data-ttu-id="dcef0-117">JA</span><span class="sxs-lookup"><span data-stu-id="dcef0-117">JA</span></span>|<span data-ttu-id="dcef0-118">範囲外</span><span class="sxs-lookup"><span data-stu-id="dcef0-118">範囲外</span></span>|  
|<span data-ttu-id="dcef0-119">KO</span><span class="sxs-lookup"><span data-stu-id="dcef0-119">KO</span></span>|<span data-ttu-id="dcef0-120">범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="dcef0-120">범위를 벗어남</span></span>|  
|<span data-ttu-id="dcef0-121">TW</span><span class="sxs-lookup"><span data-stu-id="dcef0-121">TW</span></span>|<span data-ttu-id="dcef0-122">超過範圍</span><span class="sxs-lookup"><span data-stu-id="dcef0-122">超過範圍</span></span>|  
  
### <a name="to-define-out-of-range-alerts-in-non-english-installations"></a><span data-ttu-id="dcef0-123">Pour définir des alertes de dimension numérique hors limites dans les installations non anglaises</span><span class="sxs-lookup"><span data-stu-id="dcef0-123">To define out-of-range alerts in non-English installations</span></span>  
  
1.  <span data-ttu-id="dcef0-124">Accédez au dossier contenant le fichier .xml de définition d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="dcef0-124">Navigate to the folder containing your BAM definition xml file.</span></span>  
  
2.  <span data-ttu-id="dcef0-125">À l'aide d'un éditeur de texte ou d'un éditeur XML, ouvrez le fichier de définition d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="dcef0-125">Using a text editor or an XML editor, open the BAM definition file.</span></span>  
  
3.  <span data-ttu-id="dcef0-126">Repérez la dimension de découpage pour la dimension numérique.</span><span class="sxs-lookup"><span data-stu-id="dcef0-126">Locate the slicer dimension for the numeric dimension.</span></span> <span data-ttu-id="dcef0-127">Par exemple, si votre dimension de découpage est nommée **Alerts_NumDim**, recherchez le nœud suivant :</span><span class="sxs-lookup"><span data-stu-id="dcef0-127">For example, if your slicer dimension is named **Alerts_NumDim**, you would locate the following node:</span></span>  
  
    ```  
    <SlicerDimension Name="Alerts_NumDim">  
    <Level Name="(Out of Range)" />  
    </SlicerDimension>  
    ```  
  
4.  <span data-ttu-id="dcef0-128">Modifier la **hors plage** chaîne localisée de valeur de chaîne approprié.</span><span class="sxs-lookup"><span data-stu-id="dcef0-128">Change the **Out of Range** string value to the appropriate localized string.</span></span>  
  
5.  <span data-ttu-id="dcef0-129">Enregistrez le fichier et déployez la définition.</span><span class="sxs-lookup"><span data-stu-id="dcef0-129">Save the file and deploy the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcef0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcef0-130">See Also</span></span>  
 <span data-ttu-id="dcef0-131">[Qu’est un schéma de définition BAM ?](../core/what-is-a-bam-definition-schema.md) </span><span class="sxs-lookup"><span data-stu-id="dcef0-131">[What Is a BAM Definition Schema?](../core/what-is-a-bam-definition-schema.md) </span></span>  
 [<span data-ttu-id="dcef0-132">Comment déployer des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="dcef0-132">How to Deploy BAM Definitions</span></span>](../core/how-to-deploy-bam-definitions.md)