---
title: Exemples de Messages de MX | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b592034f-2dd3-40e4-8f0b-eb6d65c38fff
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f5280f8ec2ce16344562907a95c1b0afa8c6627
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="examples-of-mx-messages"></a><span data-ttu-id="addf8-102">Exemples de Messages de MX</span><span class="sxs-lookup"><span data-stu-id="addf8-102">Examples of MX Messages</span></span>
<span data-ttu-id="addf8-103">Lignes de commande pour générer la solution (modèle de formulaire InfoPath) pour les messages de différents MX</span><span class="sxs-lookup"><span data-stu-id="addf8-103">Command Lines to generate the solution (InfoPath form template) for the Different MX messages</span></span>  
  
 <span data-ttu-id="addf8-104">Les exemples suivants nécessitent que les schémas de « pacs.004.001.01 » et « pain.002.001.01 » figurent tous dans c:\schemas.</span><span class="sxs-lookup"><span data-stu-id="addf8-104">The following examples require that the “pacs.004.001.01" and “pain.002.001.01” schemas are all in c:\schemas.</span></span> <span data-ttu-id="addf8-105">Ceci va générer la solution pour le modèle de formulaire dans le dossier « C:\GeneratedForms ».</span><span class="sxs-lookup"><span data-stu-id="addf8-105">This will generate the solution for InfoPath Form Template in the "C:\GeneratedForms" folder.</span></span> <span data-ttu-id="addf8-106">Le nom du dossier de la solution serait identique au nom du message pour lequel le formulaire InfoPath doit être généré.</span><span class="sxs-lookup"><span data-stu-id="addf8-106">The folder name of the solution would be same as the name of the message for which the InfoPath form needs to be generated.</span></span> <span data-ttu-id="addf8-107">Ces exemples supposent que l’utilitaire a été placé dans le dossier de « C:\Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\FormGeneratorUtility ».</span><span class="sxs-lookup"><span data-stu-id="addf8-107">These examples assume that the utility has been placed in “C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\FormGeneratorUtility” folder.</span></span> <span data-ttu-id="addf8-108">Remplacez l’emplacement que vous avez sélectionné pour l’utilitaire dans le ci-dessous les commandes.</span><span class="sxs-lookup"><span data-stu-id="addf8-108">Replace the location that you have selected for the utility in the below commands.</span></span>  
  
-   <span data-ttu-id="addf8-109">**Pour générer un formulaire pour le schéma pacs.004.001.01 :**</span><span class="sxs-lookup"><span data-stu-id="addf8-109">**To generate a form for the pacs.004.001.01 schema:**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01`  
  
-   <span data-ttu-id="addf8-110">**Pour générer un formulaire pour le schéma pacs.004.001.01 et pain.002.001.01 :**</span><span class="sxs-lookup"><span data-stu-id="addf8-110">**To generate a form for the pacs.004.001.01 and pain.002.001.01 schema:**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01 pain.002.001.01`