---
title: "Comment afficher les moniteurs d’un Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7c4d2b3-9c01-40f5-b983-bf29a3a5cacc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b3954052159633894e59b4251ee20b1ea0844a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-monitors-for-a-management-pack"></a><span data-ttu-id="287e6-102">Comment afficher les moniteurs d’un Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="287e6-102">How to Display Monitors for a Management Pack</span></span>
<span data-ttu-id="287e6-103">Pour afficher une liste des sorties des moniteurs et des remplacements à l’aide de l’interface de commande un pack d’administration, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="287e6-103">To display a list of outputs for a management pack's monitors and overrides using the Command Shell, use the following procedure.</span></span>  
  
### <a name="to-display-monitors-for-a-management-pack"></a><span data-ttu-id="287e6-104">Pour afficher les moniteurs pour un Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="287e6-104">To display monitors for a management pack</span></span>  
  
1.  <span data-ttu-id="287e6-105">Dans votre serveur d’administration, cliquez sur **programmes**, puis cliquez sur **System Center.**</span><span class="sxs-lookup"><span data-stu-id="287e6-105">In your management server, click **Programs**, and then click **System Center.**</span></span>  
  
2.  <span data-ttu-id="287e6-106">Cliquez sur **interface de commande**.</span><span class="sxs-lookup"><span data-stu-id="287e6-106">Click **Command Shell**.</span></span>  
  
3.  <span data-ttu-id="287e6-107">Dans l’interface de commande, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="287e6-107">In the Command Shell, type the following command:</span></span>   
    `get-scommanagementpack –DisplayName “DisplayName” | get-scommonitor | export.csv filename`  
  
4.  <span data-ttu-id="287e6-108">Un fichier .csv est créé.</span><span class="sxs-lookup"><span data-stu-id="287e6-108">A .csv file is created.</span></span> <span data-ttu-id="287e6-109">Le fichier .csv peut être ouvert dans Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="287e6-109">The .csv file can be opened in Microsoft Office Excel.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="287e6-110">Dans Excel, vous pouvez être nécessaire de spécifier que le fichier .csv est un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="287e6-110">In Excel, you may be required to specify that the .csv file is a text file.</span></span>  
  
 <span data-ttu-id="287e6-111">Par exemple, la commande suivante récupère les données pour les analyses associées à un des packs d’administration principaux :</span><span class="sxs-lookup"><span data-stu-id="287e6-111">For example, the following command retrieves data for the monitors associated with one of the core management packs:</span></span>   
`get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-ScomMonitor | export-csv "c:\monitors.csv"`