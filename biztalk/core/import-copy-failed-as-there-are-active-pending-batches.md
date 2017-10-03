---
title: "Échec de la copie de l’importation car il existe des lots actifs en attente | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17803f0a-3c70-4a8a-8e8d-7f874ed9ad92
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3055f3e95ef3d0fb8bf5a36dae5957e318f6e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-copy-failed-as-there-are-active-pending-batches"></a>Échec de la copie de l’importation car il existe des lots actifs en attente
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|Err_ActiveBatchFound|  
|Texte du message|Échec de l'importation ou de la copie en raison de lots actifs/en attente. Arrêtez les lots actifs/en attente et réessayez l'importation ou la copie.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu importer un fichier de liaison ou copier les paramètres, car les accords affectés disposent d'un ou de plusieurs lots actifs ou en attente.   
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que tous les lots dans les accords affectés figurent bien comme étant arrêtés dans les propriétés de ces derniers.