---
title: 'Erreur : fichier d’entrée natif n’existe pas | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.nativeInputFileDoesNotExist
ms.assetid: 17713896-8557-4bf1-b5f0-871b905ae15e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333849007c808a20130f10dfb1f22a756024a4c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---native-input-file-does-not-exist"></a>Erreur : fichier d’entrée natif n’existe pas
**Code d’erreur**  
  
 btm1040  
  
 **Explication**  
  
 Le fichier de message de l'instance d'entrée natif spécifié pour l'opération Test Map n'existe pas. Lorsque la valeur de la **entrée TestMap** mapper la propriété a la valeur **natif**, vous devez spécifier un fichier de message d’instance natif existant pour le **Instance d’entrée TestMap** carte propriété.  
  
 **Action de l’utilisateur**  
  
 Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété. Dans le **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez un natif existant de l’instance de fichier message conforme au schéma source du mappage. Ou bien, vous pouvez taper le chemin d’accès de ce fichier natif directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.