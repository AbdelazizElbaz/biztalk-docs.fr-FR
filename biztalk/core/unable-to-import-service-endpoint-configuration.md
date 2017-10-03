---
title: Impossible d'importer la configuration du point de terminaison du service | Microsoft Docs
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dae5154-04e2-4d9b-b2b2-85313683fd9e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4100435706ab26c0f4ab99dea4d2088ecad1c948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-service-endpoint-configuration"></a>Impossible d'importer la configuration du point de terminaison du service
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d’importer la configuration de point de terminaison de service|  
  
## <a name="explanation"></a>Explication  
 Plusieurs explications sont possibles. Le fichier de configuration peut contenir des caractères non valides. L'élément racine est peut-être manquant. Les données au niveau racine sont peut-être non valides.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifier la validité du fichier de configuration. Essayez d’ouvrir le fichier de configuration avec l’éditeur de Configuration de Service (**svcConfigEditor.exe**) et vérifiez chaque propriété.