---
title: "Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e19a202-4e4d-42e0-ba1e-fddc52792b21
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b96a3c7502a47541e8e58ec3df3eccf6098e3abc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-interpret-special-characters-as-part-of-a-field-value"></a>Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ
Les champs des enregistrements positionnels et délimités peuvent contenir des caractères spéciaux de différents types tels que les caractères de remplissage, les caractères de retour à la ligne et les caractères d'échappement. Les enregistrements délimités peuvent également contenir un ou plusieurs caractères délimiteur utilisés pour séparer les champs d'un enregistrement et les enregistrements entre eux. Ces caractères spéciaux font parfois partie des données elles-mêmes et ne doivent alors pas être interprétés comme spéciaux.  
  
 Les schémas de fichier plat utilisés par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prennent en charge deux techniques différentes pour marquer les occurrences des caractères habituellement spéciaux comme faisant simplement partie des données contenues par un champ. Ces deux techniques utilisent les caractères d'échappement et les caractères de retour à la ligne respectivement.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Caractères d’échappement](../core/escape-characters.md)  
  
-   [Encapsuler des caractères](../core/wrap-characters.md)