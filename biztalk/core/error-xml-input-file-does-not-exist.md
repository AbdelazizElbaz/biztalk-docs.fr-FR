---
title: Erreur - XML d’entrée fichier n’existe pas | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.xmlInputFileDoesNotExist
ms.assetid: d222e615-60c8-46f5-a8de-fc59650978c7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4b70e749565bcf33f99c39faa0653c7fd952e9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---xml-input-file-does-not-exist"></a>Erreur - XML d’entrée fichier n’existe pas
**Code d’erreur**  
  
 btm1039  
  
 **Explication**  
  
 Le fichier de message de l'instance d'entrée XML spécifié pour l'opération Test Map n'existe pas. Lorsque la valeur de la **entrée TestMap** mapper la propriété est définie au format XML, vous devez spécifier un fichier de message XML instance existant pour le **Instance d’entrée TestMap** mapper la propriété.  
  
 **Action de l’utilisateur**  
  
 Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété. À l’aide de la **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez fichier de message qui est conforme au schéma source du mappage de l’instance XML existant. Ou bien, vous pouvez taper le chemin d’accès de ce fichier XML directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.