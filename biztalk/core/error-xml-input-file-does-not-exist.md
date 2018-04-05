---
title: Erreur - XML d’entrée fichier n’existe pas | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.xmlInputFileDoesNotExist
ms.assetid: d222e615-60c8-46f5-a8de-fc59650978c7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4b70e749565bcf33f99c39faa0653c7fd952e9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---xml-input-file-does-not-exist"></a><span data-ttu-id="35c84-102">Erreur - XML d’entrée fichier n’existe pas</span><span class="sxs-lookup"><span data-stu-id="35c84-102">Error - XML Input File Does Not Exist</span></span>
<span data-ttu-id="35c84-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="35c84-103">**Error Code**</span></span>  
  
 <span data-ttu-id="35c84-104">btm1039</span><span class="sxs-lookup"><span data-stu-id="35c84-104">btm1039</span></span>  
  
 <span data-ttu-id="35c84-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="35c84-105">**Explanation**</span></span>  
  
 <span data-ttu-id="35c84-106">Le fichier de message de l'instance d'entrée XML spécifié pour l'opération Test Map n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="35c84-106">The XML input instance message file specified for the Test Map operation does not exist.</span></span> <span data-ttu-id="35c84-107">Lorsque la valeur de la **entrée TestMap** mapper la propriété est définie au format XML, vous devez spécifier un fichier de message XML instance existant pour le **Instance d’entrée TestMap** mapper la propriété.</span><span class="sxs-lookup"><span data-stu-id="35c84-107">When the value of the **TestMap Input** map property is set to XML, you must specify an existing XML instance message file for the **TestMap Input Instance** map property.</span></span>  
  
 <span data-ttu-id="35c84-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="35c84-108">**User Action**</span></span>  
  
 <span data-ttu-id="35c84-109">Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="35c84-109">Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property.</span></span> <span data-ttu-id="35c84-110">À l’aide de la **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez fichier de message qui est conforme au schéma source du mappage de l’instance XML existant.</span><span class="sxs-lookup"><span data-stu-id="35c84-110">Using the **Select Input File** dialog box, select an existing XML instance message file that conforms to the source schema of the map.</span></span> <span data-ttu-id="35c84-111">Ou bien, vous pouvez taper le chemin d’accès de ce fichier XML directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="35c84-111">Alternatively, you can type the path of this XML file directly into the value field of the **TestMap Input Instance** property.</span></span>