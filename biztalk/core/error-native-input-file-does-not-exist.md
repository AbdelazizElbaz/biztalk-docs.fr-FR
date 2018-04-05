---
title: 'Erreur : fichier d’entrée natif n’existe pas | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.nativeInputFileDoesNotExist
ms.assetid: 17713896-8557-4bf1-b5f0-871b905ae15e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333849007c808a20130f10dfb1f22a756024a4c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---native-input-file-does-not-exist"></a><span data-ttu-id="57d5c-102">Erreur : fichier d’entrée natif n’existe pas</span><span class="sxs-lookup"><span data-stu-id="57d5c-102">Error - Native Input File Does Not Exist</span></span>
<span data-ttu-id="57d5c-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="57d5c-103">**Error Code**</span></span>  
  
 <span data-ttu-id="57d5c-104">btm1040</span><span class="sxs-lookup"><span data-stu-id="57d5c-104">btm1040</span></span>  
  
 <span data-ttu-id="57d5c-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="57d5c-105">**Explanation**</span></span>  
  
 <span data-ttu-id="57d5c-106">Le fichier de message de l'instance d'entrée natif spécifié pour l'opération Test Map n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="57d5c-106">The native input instance message file specified for the Test Map operation does not exist.</span></span> <span data-ttu-id="57d5c-107">Lorsque la valeur de la **entrée TestMap** mapper la propriété a la valeur **natif**, vous devez spécifier un fichier de message d’instance natif existant pour le **Instance d’entrée TestMap** carte propriété.</span><span class="sxs-lookup"><span data-stu-id="57d5c-107">When the value of the **TestMap Input** map property is set to **Native**, you must specify an existing native instance message file for the **TestMap Input Instance** map property.</span></span>  
  
 <span data-ttu-id="57d5c-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="57d5c-108">**User Action**</span></span>  
  
 <span data-ttu-id="57d5c-109">Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="57d5c-109">Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property.</span></span> <span data-ttu-id="57d5c-110">Dans le **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez un natif existant de l’instance de fichier message conforme au schéma source du mappage.</span><span class="sxs-lookup"><span data-stu-id="57d5c-110">In the **Select Input File** dialog box, select an existing native instance message file that conforms to the source schema of the map.</span></span> <span data-ttu-id="57d5c-111">Ou bien, vous pouvez taper le chemin d’accès de ce fichier natif directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="57d5c-111">Alternatively, you can type the path of this native file directly into the value field of the **TestMap Input Instance** property.</span></span>