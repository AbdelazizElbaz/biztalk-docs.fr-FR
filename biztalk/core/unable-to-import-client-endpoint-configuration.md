---
title: "Impossible d’importer la configuration du point de terminaison client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8375e153-ed1c-4bf4-b461-ac026a4b3478
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30be7958ca07dde47d147711da06a276e86ff714
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-client-endpoint-configuration"></a>Impossible d'importer la configuration du point de terminaison client
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d'importer la configuration du point de terminaison client|  
  
## <a name="explanation"></a>Explication  
 Plusieurs explications sont possibles. Le fichier de configuration peut contenir des caractères non valides. L'élément racine est peut-être manquant. Les données au niveau racine sont peut-être non valides.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifier la validité du fichier de configuration. Essayez d’ouvrir le fichier de configuration avec l’éditeur de Configuration de Service (**svcConfigEditor.exe**) et vérifiez chaque propriété.