---
title: "Erreur : les entrées de mappage de Test non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.testMapInputsNotValid
ms.assetid: d885d366-92a3-4d2a-8e2b-58e06960864f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 912b70bcd74180a20d54da11dffdab79f54fc5b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---test-map-inputs-not-valid"></a>Erreur : les entrées de mappage de Test non valide
**Code d’erreur**  
  
 btm1036  
  
 **Explication**  
  
 Aucun fichier de message d’instance d’entrée n’a été spécifié pour l’opération Test Map et le type de l’entrée TestMap n’est pas défini sur **générer l’Instance**. Lorsque la valeur de la **entrée TestMap** mapper la propriété n’est pas définie sur **générer l’Instance**, vous devez spécifier un fichier de message d’instance pour le **Instance d’entrée TestMap** carte propriété.  
  
 **Action de l’utilisateur**  
  
 Si nécessaire, définissez l'une ou l'autre des propriétés de mappage suivantes :  
  
-   **Instance d’entrée TestMap.** Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété. À l’aide de la **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez une instance de message de fichier conforme au schéma source du mappage. Ou bien, vous pouvez taper le chemin d’accès de ce fichier directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.  
  
-   **Entrée TestMap.** Pour éviter de spécifier un fichier de message d’instance d’entrée, cliquez sur le mappage approprié dans l’Explorateur de solutions, cliquez sur **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés**boîte de dialogue pour le mappage, utilisez la liste déroulante de liste dans le champ de valeur de la **entrée TestMap** propriété pour sélectionner **générer l’Instance**. Dans ce cas, vous ne devez pas spécifier un fichier pour le **Instance d’entrée TestMap** propriété.