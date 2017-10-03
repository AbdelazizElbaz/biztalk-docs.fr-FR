---
title: Page Ajouter une alerte | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0023ee8d-a0d1-4257-95c6-38c95060bd62
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa93a777481c905dbedfffe5e7675335c4aec40b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-alert-page"></a>Page Ajouter une alerte
Figure 1 montre la page Ajouter une alerte, où vous pouvez créer une nouvelle alerte qui déclenche le portail lorsqu’un message d’erreur correspondant aux critères (conditions) spécifiés dans l’alerte arrive sur le portail.  
  
 ![Page Ajouter une alerte](../esb-toolkit/media/ch8-addalertpage.gif "Ch8-AddAlertPage")  
  
 **Figure 1**  
  
 **La page ESB Management Portal ajouter une alerte**  
  
 Dans la page Ajouter une alerte, vous pouvez procédez comme suit :  
  
-   Tapez un nom pour la nouvelle alerte dans le **entrer le nom alerte** zone de texte.  
  
-   Spécifier comment l’alerte est conformes aux valeurs des champs dans les exceptions entrantes dans le **ajouter des conditions de cette alerte** section de cette page. Sélectionnez un champ à partir du schéma de l’exception (tel que **Application, le Type d’erreur,** ou **gravité d’erreur)** dans les **critères** liste déroulante, sélectionnez un type de comparaison pour le (par exemple, =, **! =, > =, < =,** ou **comme**) dans le **opérateur** liste déroulante ; et tapez ou sélectionnez une valeur dans la troisième liste. Lorsque vous sélectionnez un champ d’exception, le **valeur** contrôle change vers une zone de texte ou une liste déroulante, vous pouvez entrer ou sélectionner une valeur correspondante.  
  
-   Après avoir sélectionné ou entrer les valeurs des critères, cliquez sur le **ajouter** lien pour ajouter cette condition à la liste dans le **Conditions** section de la page, puis répétez l’opération pour ajouter des conditions plus que vous avez besoin pour cette alerte .  
  
-   Cliquez sur le **enregistrer** bouton permettant de créer la nouvelle alerte avec le nom et les conditions que vous avez spécifié.