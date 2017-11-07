---
title: "Définir la justification des chaînes dans l’adaptateur JD Edwards OneWorld | Documents Microsoft"
description: "Mettre à jour le fichier jdearglist pour utiliser l’adaptateur JD Edwards OneWorld dans une orchestration BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b32d0106d95a1970b480e32dfa47a81ebf98ca
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="set-string-justification-in-jdearglist"></a>Définir la chaîne de la Justification dans Jdearglist

## <a name="overview"></a>Vue d'ensemble
Pour configurer certains arguments de chaîne de sorte qu'ils soient alignés à droite (et remplis à gauche) dans le fichier JD Edwards OneWorld jdearglist.txt, vous devez déterminer la fonction d'entreprise à laquelle vous souhaitez accéder et les champs associés que vous souhaitez appeler.  
  
 Vous devez mettre à jour le fichier jdearglist.txt avant de générer les liaisons (schémas) dans l'orchestration. Les instructions de mise à jour le fichier jdearglist.txt sont décrites dans [gestion des valeurs de chaîne](../core/handling-string-values1.md).  
  
 Si un message d'avertissement est consigné dans le journal d'audit, il vous informe que le fichier jdearglist.txt est manquant. Si vous exécutez la fonction d'entreprise SalesOrder ou PurchaseOrder, le fichier doit être situé au niveau de votre chemin d'accès, sans quoi elle ne fonctionnera pas.  
  
## <a name="see-also"></a>Voir aussi  
[Utiliser la gestion des exceptions BizTalk Server](using-biztalk-server-exception-handling1.md)