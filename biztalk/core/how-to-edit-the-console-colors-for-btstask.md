---
title: Comment modifier les couleurs de Console pour BTSTask | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725dcb7b-5a19-4166-9d1c-93f30ddca201
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d68529f01ab8131739d735ad82d804b41a9c021
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-edit-the-console-colors-for-btstask"></a><span data-ttu-id="f8e2f-102">Modification des couleurs de la console pour l'outil BTSTask</span><span class="sxs-lookup"><span data-stu-id="f8e2f-102">How to Edit the Console Colors for BTSTask</span></span>
<span data-ttu-id="f8e2f-103">Cette rubrique explique comment modifier les couleurs de premier plan utilisées pour l'affichage des données de BTSTask dans la console.</span><span class="sxs-lookup"><span data-stu-id="f8e2f-103">This topic describes how to edit the foreground colors that BTSTask outputs to the console.</span></span> <span data-ttu-id="f8e2f-104">Si l'arrière-plan de votre console est blanc, vous aurez des difficultés à lire les données de sortie BTSTask telles qu'elles s'affichent par défaut dans la console. Il se peut donc que vous deviez modifier les couleurs de premier plan de la console.</span><span class="sxs-lookup"><span data-stu-id="f8e2f-104">If your console background color is white, you will have difficulty reading the default BTSTask console output and will need to modify the console foreground colors.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8e2f-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f8e2f-105">Prerequisites</span></span>  
 <span data-ttu-id="f8e2f-106">Pour effectuer la procédure de cette rubrique, vous devez disposer de droit en lecture et en écriture sur le fichier BTSTask.exe.config contenu dans le dossier d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8e2f-106">To perform the procedure in this topic, you must have Read/Write permissions on the BTSTask.exe.config file contained in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder.</span></span>  
  
### <a name="to-edit-the-console-foreground-colors-for-btstask"></a><span data-ttu-id="f8e2f-107">Pour modifier les couleurs de premier plan de la console pour BTSTask</span><span class="sxs-lookup"><span data-stu-id="f8e2f-107">To edit the console foreground colors for BTSTask</span></span>  
  
1.  <span data-ttu-id="f8e2f-108">Sur l'ordinateur où vous souhaitez exécuter BTSTask, ouvrez le fichier BTSTask.exe.config dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], un éditeur de texte ou un éditeur XML.</span><span class="sxs-lookup"><span data-stu-id="f8e2f-108">On the computer where you want to run BTSTask, open BTSTask.exe.config in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or a text or XML editor.</span></span> <span data-ttu-id="f8e2f-109">Ce fichier se trouve dans le dossier d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8e2f-109">This file is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder.</span></span>  
  
2.  <span data-ttu-id="f8e2f-110">Modifiez les valeurs pour Console.ForegroundColor.Error, Console.ForegroundColor.Warning et Console.ForegroundColor.Info d'après les couleurs de premier plan souhaitées, respectivement, pour les messages d'erreur, les avertissements et les informations. Enregistrez ensuite le fichier.</span><span class="sxs-lookup"><span data-stu-id="f8e2f-110">Edit the values for the Console.ForegroundColor.Error, Console.ForegroundColor.Warning, and Console.ForegroundColor.Info keys according to the console foreground colors that you want for error messages, warnings, and information, respectively, and then save the file.</span></span> <span data-ttu-id="f8e2f-111">Pour une couleur de premier plan unique, au lieu de modifier toutes les valeurs, supprimez les entrées correspondantes.</span><span class="sxs-lookup"><span data-stu-id="f8e2f-111">(For monochrome, delete these three entries, rather than editing their values.)</span></span>  
  
     <span data-ttu-id="f8e2f-112">Les valeurs disponibles pour les couleurs de premier plan sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f8e2f-112">The available values for foreground colors are as follows:</span></span>  
  
     <span data-ttu-id="f8e2f-113">0 : noir</span><span class="sxs-lookup"><span data-stu-id="f8e2f-113">0: Black</span></span>  
  
     <span data-ttu-id="f8e2f-114">1 : DarkBlue</span><span class="sxs-lookup"><span data-stu-id="f8e2f-114">1: DarkBlue</span></span>  
  
     <span data-ttu-id="f8e2f-115">2 : printanier</span><span class="sxs-lookup"><span data-stu-id="f8e2f-115">2: DarkGreen</span></span>  
  
     <span data-ttu-id="f8e2f-116">3 : DarkCyan</span><span class="sxs-lookup"><span data-stu-id="f8e2f-116">3: DarkCyan</span></span>  
  
     <span data-ttu-id="f8e2f-117">4 : DarkRed</span><span class="sxs-lookup"><span data-stu-id="f8e2f-117">4: DarkRed</span></span>  
  
     <span data-ttu-id="f8e2f-118">5 : DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="f8e2f-118">5: DarkMagenta</span></span>  
  
     <span data-ttu-id="f8e2f-119">6 : DarkYellow</span><span class="sxs-lookup"><span data-stu-id="f8e2f-119">6: DarkYellow</span></span>  
  
     <span data-ttu-id="f8e2f-120">7 : gris</span><span class="sxs-lookup"><span data-stu-id="f8e2f-120">7: Gray</span></span>  
  
     <span data-ttu-id="f8e2f-121">8 : gris foncé</span><span class="sxs-lookup"><span data-stu-id="f8e2f-121">8: DarkGray</span></span>  
  
     <span data-ttu-id="f8e2f-122">9 : bleu</span><span class="sxs-lookup"><span data-stu-id="f8e2f-122">9: Blue</span></span>  
  
     <span data-ttu-id="f8e2f-123">10 : vert</span><span class="sxs-lookup"><span data-stu-id="f8e2f-123">10: Green</span></span>  
  
     <span data-ttu-id="f8e2f-124">11 : cyan</span><span class="sxs-lookup"><span data-stu-id="f8e2f-124">11: Cyan</span></span>  
  
     <span data-ttu-id="f8e2f-125">12 : rouge</span><span class="sxs-lookup"><span data-stu-id="f8e2f-125">12: Red</span></span>  
  
     <span data-ttu-id="f8e2f-126">13 : magenta</span><span class="sxs-lookup"><span data-stu-id="f8e2f-126">13: Magenta</span></span>  
  
     <span data-ttu-id="f8e2f-127">14 : jaune</span><span class="sxs-lookup"><span data-stu-id="f8e2f-127">14: Yellow</span></span>  
  
     <span data-ttu-id="f8e2f-128">15 : blanc</span><span class="sxs-lookup"><span data-stu-id="f8e2f-128">15: White</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e2f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8e2f-129">See Also</span></span>  
 [<span data-ttu-id="f8e2f-130">Référence de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="f8e2f-130">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)