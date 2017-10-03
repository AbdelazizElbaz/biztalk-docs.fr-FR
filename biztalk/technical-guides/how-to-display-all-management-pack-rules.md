---
title: "Comment afficher toutes les règles de Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fdec550-6713-4f5f-8c04-d9218bf2df3c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08ec94eb3adb87bf6feaff032e00a61bc9b0fead
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-all-management-pack-rules"></a><span data-ttu-id="8f6e0-102">Comment afficher toutes les règles de Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="8f6e0-102">How to Display All Management Pack Rules</span></span>
<span data-ttu-id="8f6e0-103">Utilisez la procédure suivante pour afficher une liste de règles pour les packs d’administration que vous avez importé.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-103">Use the following procedure to display a list of rules for the management packs that you imported.</span></span> <span data-ttu-id="8f6e0-104">La liste des règles peut être affichée dans Office Excel.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-104">The list of rules can be viewed in Office Excel.</span></span>  
  
### <a name="to-display-management-pack-rules"></a><span data-ttu-id="8f6e0-105">Pour afficher les règles du Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="8f6e0-105">To display management pack rules</span></span>  
  
1.  <span data-ttu-id="8f6e0-106">Dans votre serveur d’administration, cliquez sur **programmes**, puis cliquez sur **System Center**.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-106">In your management server, click **Programs**, and then click **System Center**.</span></span>  
  
2.  <span data-ttu-id="8f6e0-107">Cliquez sur **interface de commande**.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-107">Click **Command Shell**.</span></span>  
  
3.  <span data-ttu-id="8f6e0-108">Dans l’interface de commande, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8f6e0-108">In the Command Shell, type the following command:</span></span>   
    `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-SCOMRule | export-csv "c:\rules.csv"`  
  
4.  <span data-ttu-id="8f6e0-109">Un fichier .csv est créé.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-109">A .csv file is created.</span></span> <span data-ttu-id="8f6e0-110">Vous pouvez ouvrir le fichier .csv dans Office Excel.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-110">You can open the .csv file in Office Excel.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f6e0-111">Dans Office Excel, vous pouvez être nécessaire de spécifier que le fichier .csv est un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="8f6e0-111">In Office Excel, you may be required to specify that the .csv file is a text file.</span></span>