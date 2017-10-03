---
title: Erreurs de Configuration de port | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92eae0d8-a0c4-4f8c-b91a-fd98b9f6931a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f0e51c06fab9dadb60fc43a003108e50bbb0fab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="port-configuration-errors"></a>Erreurs en relation avec la configuration des ports
Informations sur le diagnostic et résolution des erreurs de Configuration du Port WCF.  

## <a name="cannot-merge-operation-due-to-communication-pattern-conflict"></a>Impossible de fusionner l'opération en raison d'un conflit de modèles de communication
  
||Détails|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de fusionner l'opération « {0} » en raison d'un conflit de modèles de communication.  Toutes les opérations doivent être unidirectionnelles ou avec requête-réponse|  
  
### <a name="explanation"></a>Explication  
 Cette erreur indique que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tente de fusionner des types de ports possédant différents modèles de communication.  
  
### <a name="user-action"></a>Action de l'utilisateur  
 À l'aide de l'Assistant Configuration du port, vérifiez que tous les ports en cours de fusion possèdent la même direction de communication (unidirectionnelle ou de requête-réponse).  
  
 Pour plus d’informations sur la configuration du port, consultez [comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md).
 
## <a name="port-types-that-have-a-combination-of-one-way-and-request-response-operations-are-not-allowed"></a>Les types de ports associant les opérations de requête-réponse et unidirectionnelles ne sont pas autorisés 
  
||Détails|  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Les types de ports associant les opérations de requête-réponse et unidirectionnelles ne sont pas autorisés. Corrigez le type de port de description « {0} » de service « {{1} », puis réexécutez l’Assistant|  
  
### <a name="explanation"></a>Explication  
 Cette erreur indique que le service que vous tentez d'utiliser est associé à des opérations unidirectionnelles et bidirectionnelles (ou avec requête-réponse).  
  
### <a name="user-action"></a>Action de l'utilisateur  
 Corrigez le service WCF avec les opérations appropriées (soit unidirectionnelles, soit avec requête-réponse) et tentez à nouveau de l'utiliser (si vous en êtes propriétaire). Sinon, contactez le fournisseur de services.
