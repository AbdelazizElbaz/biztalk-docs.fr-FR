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
# <a name="examples-of-mt-messages"></a>Exemples de Messages de MT
**Commandes pour générer la solution (modèle de formulaire InfoPath) pour les messages MT différents :**  
  
 Les exemples suivants nécessitent que les schémas « Types.xsd de Base SWIFT », « SWIFT courantes données Types.xsd","MT102.xsd », « MT500.xsd » et « MT103.xsd » figurent tous dans c:\schemas. Ceci va générer la solution pour le modèle de formulaire dans le dossier « C:\GeneratedForms ». Le nom du dossier de la solution serait identique au nom du message pour lequel le formulaire InfoPath doit être généré. Ces exemples supposent que l’utilitaire a été placé dans le dossier de « C:\FormGeneratorUtility2008 ». Remplacez l’emplacement que vous avez sélectionné pour l’utilitaire dans le ci-dessous les commandes.  
  
-   **Pour générer un formulaire pour le schéma MT103 :**  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103`  
  
-   **Pour générer un formulaire pour le schéma MT103 MT102 et MT500 :**  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103 MT102 MT500`  
  
-   **Pour générer un formulaire pour le schéma MT103 (à partir du fichier) :**  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f P1forms.txt`