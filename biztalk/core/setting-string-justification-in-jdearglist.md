---
title: "Définition de Justification des chaînes dans Jdearglist | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, setting string justification
- strings, configuring
- strings, right-justified
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daecf4101ebf5dc8964562dc7f385d41279a3401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-string-justification-in-jdearglist"></a>Configuration de la justification des chaînes dans Jdearglist
Pour configurer certains arguments de chaîne de sorte qu'ils soient alignés à droite (et remplis à gauche) dans le fichier JD Edwards OneWorld jdearglist.txt, vous devez déterminer la fonction d'entreprise à laquelle vous souhaitez accéder et les champs associés que vous souhaitez appeler.  
  
 Vous devez mettre à jour le fichier jdearglist.txt avant de générer les liaisons (schémas) dans l'orchestration. Les instructions de mise à jour le fichier jdearglist.txt sont décrites dans [gestion des valeurs de chaîne](../core/handling-string-values1.md).  
  
 Si un message d'avertissement est consigné dans le journal d'audit, il vous informe que le fichier jdearglist.txt est manquant. Si vous exécutez la fonction d'entreprise SalesOrder ou PurchaseOrder, le fichier doit être situé au niveau de votre chemin d'accès, sans quoi elle ne fonctionnera pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/administering-biztalk-adapter-for-jd-edwards-oneworld.md)