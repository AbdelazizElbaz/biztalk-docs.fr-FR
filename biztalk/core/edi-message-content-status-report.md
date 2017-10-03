---
title: "Rapport d’état du contenu du Message EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29acab25-354d-42f0-b6e3-37ebca47addb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62dbb260bb23e3ed5de7e8d416158a0e142c6c32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-message-content-status-report"></a><span data-ttu-id="656ed-102">Rapport d'état sur le contenu d'un message EDI</span><span class="sxs-lookup"><span data-stu-id="656ed-102">EDI Message Content Status Report</span></span>

## <a name="overview"></a><span data-ttu-id="656ed-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="656ed-103">Overview</span></span>
<span data-ttu-id="656ed-104">Ce rapport d'état affiche les en-têtes et la charge d'un document informatisé.</span><span class="sxs-lookup"><span data-stu-id="656ed-104">This status report displays the headers and payload of a transaction set.</span></span> <span data-ttu-id="656ed-105">Afficher ce rapport en double-cliquant sur un document informatisé dans le rapport d’état détails du document informatisé, puis en cliquant **vue de contenu du document informatisé**.</span><span class="sxs-lookup"><span data-stu-id="656ed-105">You display this report by right-clicking a transaction set within the Transaction Set Details status report, and then clicking **View Transaction Set Content**.</span></span>  
  
 <span data-ttu-id="656ed-106">Ce rapport est disponible uniquement si vous avez sélectionné le **stocker les transactions/données utiles pour les rapports** propriété dans la Général Page de la boîte de dialogue Propriétés EDI pour le tiers associé.</span><span class="sxs-lookup"><span data-stu-id="656ed-106">This report is available only if you have selected the **Store transaction set/payload for reporting** property in the General Page of the EDI Properties dialog box for the related party.</span></span>  
  
 <span data-ttu-id="656ed-107">Ce rapport offre deux affichages du contenu :</span><span class="sxs-lookup"><span data-stu-id="656ed-107">This report provides two views of the content:</span></span>  
  
-   <span data-ttu-id="656ed-108">L'affichage au format texte propose l'affichage du contenu du document informatisé sous une forme lisible, par exemple dans un fichier texte EDI.</span><span class="sxs-lookup"><span data-stu-id="656ed-108">A Text Format view that shows the contents of the transaction set in human-readable form, as in an EDI text file.</span></span> <span data-ttu-id="656ed-109">Cette vue affiche l'en-tête ST, les données du document informatisé et le code de fin SE, en plaçant chaque segment sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="656ed-109">This view shows the ST header, the transaction set payload, and the SE trailer, with each segment on a separate line.</span></span>  
  
-   <span data-ttu-id="656ed-110">L'affichage au format binaire propose l'affichage du contenu du document informatisé en format texte non délimité, avec une table des représentations hexadécimales de chaque caractère ASCII du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="656ed-110">A Binary Format view that shows the contents of the transaction set in non-delimited text format and a table of the hexadecimal representations for each ASCII character in the transaction set.</span></span>  
  
