---
title: "Fonctionne de l’exemple d’enrichissement de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1188c1c9-b133-4438-b41c-ea6cffcf40fd
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ef516b992acbcee2936edb6341cbf1434ba4c79
ms.sourcegitcommit: 7497f6f23d7aadfa8535d0530493f8b4a2a50a0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2017
---
# <a name="how-the-message-enrichment-sample-works"></a>Fonctionne de l’exemple d’enrichissement de Message
 L’exemple d’enrichissement de Message montre qu’il est possible d’encapsuler un modèle d’intégration en tant que service générique réutilisable. Dans ce cas, l’exemple implémente le modèle de contenu enrichisseur. Le modèle de contenu enrichisseur implique généralement à l’aide d’une transformation pour préparer un message pour la transmettre à un service externe dans l’ordre pour rechercher des informations, puis une autre transformation pour intégrer la réponse dans un nouveau message qui contient également des données à partir de la message d’origine. Pour implémenter le modèle de façon générique, l’exemple d’enrichissement de Message fournit un service de feuille de route basée sur une orchestration qui peut utiliser jusqu'à deux programmes de résolution pour configurer l’enrichissement d’un message à l’aide des informations à partir d’une source externe.
  
 Le premier programme de résolution doit retourner des informations de routage ; elle peut également retourner transformer les informations à ses côtés. Si spécifié, la transformation est appliquée au message entrant avant d’être acheminé à l’emplacement spécifié par le programme de résolution. Dans l’itinéraire de l’exemple fourni, le fournisseur de l’adaptateur WCF-Custom est utilisé pour exécuter une procédure stockée SQL dans la base de données GlobalBankESB nommé GetOrderDetails et retournent le résultat.  
  
 Si vous le souhaitez, un second programme de résolution peut être inclus. Si fourni, le programme de résolution deuxième doit inclure les informations de transformation. Cette transformation recevra le message d’origine et le résultat retourné par la source de données a été contacté, en tant qu’entrée. Dans l’itinéraire de l’exemple, un mappage qui utilise une fonctoid Bouclage de table pour extraire des informations sur le message d’origine et le résultat de la procédure stockée et l’inclure dans le message InventoryOrder résultant est référencé.
