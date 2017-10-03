---
title: "Impossible de créer l’entrée dans la table AS2 EDIINT MIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1c75d70-e39e-4465-b32b-db646c059c9b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c51cac2861fabaf8fc50269623130c90f3d445b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-the-entry-in-the-as2-ediint-mic-table"></a>Impossible de créer l'entrée dans la table AS2 EDIINT MIC
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|AS2MicDataStoreCreateEntryError|  
|Texte du message|Impossible de créer l'entrée dans la table AS2 EDIINT MIC. Ceci est peut-être dû à l'écriture dans la table de combinaisons de valeurs AS2-From, AS2-To et MessageID en double.  Erreur : {0}|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique si des problèmes de connexion de base de données ou des clés de lignes existent déjà dans la table de base de données. Le message d'erreur complet doit fournir des informations sur la raison de l'échec de l'opération d'insertion. Les entrées de la table étant supprimées une fois le MDN reçu (correctement ou non), cette erreur ne doit jamais se produire une fois le MDN reçu.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, consultez le message d'erreur pour obtenir des informations sur la raison de l'échec de l'opération d'insertion. Dans SQL, dans la table EDIINT_MIC, déterminez s'il existe des doublons des combinaisons MessageID AS2-From et AS2-To. Si c'est le cas, supprimez-les.