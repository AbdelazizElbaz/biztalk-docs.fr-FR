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
# <a name="examples-of-mx-messages"></a>Exemples de Messages de MX
Lignes de commande pour générer la solution (modèle de formulaire InfoPath) pour les messages de différents MX  
  
 Les exemples suivants nécessitent que les schémas de « pacs.004.001.01 » et « pain.002.001.01 » figurent tous dans c:\schemas. Ceci va générer la solution pour le modèle de formulaire dans le dossier « C:\GeneratedForms ». Le nom du dossier de la solution serait identique au nom du message pour lequel le formulaire InfoPath doit être généré. Ces exemples supposent que l’utilitaire a été placé dans le dossier de « C:\Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\FormGeneratorUtility ». Remplacez l’emplacement que vous avez sélectionné pour l’utilitaire dans le ci-dessous les commandes.  
  
-   **Pour générer un formulaire pour le schéma pacs.004.001.01 :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01`  
  
-   **Pour générer un formulaire pour le schéma pacs.004.001.01 et pain.002.001.01 :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01 pain.002.001.01`