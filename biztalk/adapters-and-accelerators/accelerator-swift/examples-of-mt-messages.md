---
title: Exemples de Messages de MT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629042cc-b941-4c58-b0dd-ede056caf573
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73098c20aeb03e8013f7e20e04c8bb37ce31266e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="examples-of-mt-messages"></a><span data-ttu-id="c73a5-102">Exemples de Messages de MT</span><span class="sxs-lookup"><span data-stu-id="c73a5-102">Examples of MT Messages</span></span>
<span data-ttu-id="c73a5-103">**Commandes pour générer la solution (modèle de formulaire InfoPath) pour les messages MT différents :**</span><span class="sxs-lookup"><span data-stu-id="c73a5-103">**Commands to generate the solution (InfoPath form template) for the Different MT messages:**</span></span>  
  
 <span data-ttu-id="c73a5-104">Les exemples suivants nécessitent que les schémas « Types.xsd de Base SWIFT », « SWIFT courantes données Types.xsd","MT102.xsd », « MT500.xsd » et « MT103.xsd » figurent tous dans c:\schemas.</span><span class="sxs-lookup"><span data-stu-id="c73a5-104">The following examples require that the "SWIFT Base Types.xsd", "SWIFT Common Data Types.xsd","MT102.xsd", "MT500.xsd", and "MT103.xsd" schemas are all in c:\schemas.</span></span> <span data-ttu-id="c73a5-105">Ceci va générer la solution pour le modèle de formulaire dans le dossier « C:\GeneratedForms ».</span><span class="sxs-lookup"><span data-stu-id="c73a5-105">This will generate the solution for InfoPath Form Template in the "C:\GeneratedForms" folder.</span></span> <span data-ttu-id="c73a5-106">Le nom du dossier de la solution serait identique au nom du message pour lequel le formulaire InfoPath doit être généré.</span><span class="sxs-lookup"><span data-stu-id="c73a5-106">The folder name of the solution would be same as the name of the message for which the InfoPath form needs to be generated.</span></span> <span data-ttu-id="c73a5-107">Ces exemples supposent que l’utilitaire a été placé dans le dossier de « C:\FormGeneratorUtility2008 ».</span><span class="sxs-lookup"><span data-stu-id="c73a5-107">These examples assume that the utility has been placed in “C:\FormGeneratorUtility2008” folder.</span></span> <span data-ttu-id="c73a5-108">Remplacez l’emplacement que vous avez sélectionné pour l’utilitaire dans le ci-dessous les commandes.</span><span class="sxs-lookup"><span data-stu-id="c73a5-108">Replace the location that you have selected for the utility in the below commands.</span></span>  
  
-   <span data-ttu-id="c73a5-109">**Pour générer un formulaire pour le schéma MT103 :**</span><span class="sxs-lookup"><span data-stu-id="c73a5-109">**To generate a form for the MT103 schema:**</span></span>  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103`  
  
-   <span data-ttu-id="c73a5-110">**Pour générer un formulaire pour le schéma MT103 MT102 et MT500 :**</span><span class="sxs-lookup"><span data-stu-id="c73a5-110">**To generate a form for the MT103, MT102, and MT500 schema:**</span></span>  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103 MT102 MT500`  
  
-   <span data-ttu-id="c73a5-111">**Pour générer un formulaire pour le schéma MT103 (à partir du fichier) :**</span><span class="sxs-lookup"><span data-stu-id="c73a5-111">**To generate a form for the MT103 schema (from the file):**</span></span>  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f P1forms.txt`