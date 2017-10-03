---
title: Les instructions XLANG-s | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d0452-a8da-4285-b8b2-5a932ffcde28
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50f2ea904d134d22f08d86b1d600fdb3133a9c45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-statements"></a>Instructions XLANG-s
Instructions XLANG/s se décomposent généralement en deux catégories : les instructions simples qui agissent sur leurs propres, telles que **réception** ou **envoyer**et des instructions complexes qui contiennent ou regroupent les deux instructions simples ou autres instructions complexes, tels que **étendue**, **parallèles**, et **écouter**. Chaque instruction correspond à une forme d'orchestration dans le Concepteur d'orchestration BizTalk. XLANG/s définit les instructions suivantes :  
  
-   **groupe.** Permet de regrouper des opérations en une seule unité réductible et développable pour des raisons de commodité visuelle.  
  
-   **Envoyer.** Permet d'envoyer un message donné à un port donné.  
  
-   **réception.** Permet d'attendre la réception d'un message donné sur un port donné.  
  
-   **port.** Définit le moment et le mode de transmission des messages.  
  
-   **lien de rôle.** Permet de créer un ensemble de ports qui communiquent avec le même partenaire logique, par exemple avec les différents transports ou points de terminaison  
  
-   **transformation.** Permet de mapper les champs des messages existants dans les nouveaux messages.  
  
-   **assignation du message.** Permet d'envoyer un message donné à un port donné.  
  
-   **construire un message.** Définit un bloc de code XLANG/s où le message est créé et initialisé. Les messages existants peuvent être envoyés à un programme XLANG/s, mais il est impossible de les créer hors d'une construction. Ce mécanisme fournit la distribution de messages et offre un suivi de messages complet, car l'état d'un message est connu à tout instant.  
  
-   **orchestration d’appel.** Permet à une orchestration d'en appeler une autre de façon synchronisée. Les paramètres peuvent être passés et retournés.  
  
-   **Démarrer l’orchestration.** Permet à l'orchestration d'en appeler une autre de façon asynchrone.  
  
-   **règles d’appel.** Permet de configurer une stratégie de règles d'entreprise à exécuter dans l'orchestration.  
  
-   **expression.** XLANG/s prend en charge une syntaxe d'expressions riche pour supporter la diversité des scénarios d'utilisation requis pour la définition de protocole. Cette instruction permet d'affecter des propriétés de port, des propriétés de liaison de services, des messages, des variables et des objets, ainsi que d'appeler des méthodes, des propriétés et des champs de données statiques.  
  
-   **décider.** Permet d'exécuter sous certaines conditions l'un des chemins d'exécution, en fonction de la valeur des conditions qui lui sont associées.  
  
-   **délai.** Permet d'attendre jusqu'à une heure absolue ou une heure relative.  
  
-   **écouter.** Comme avec un **parallèles** instruction, le **écouter** instruction possède plusieurs chemins de branches d’exécution. Toutefois, les branches doivent commencer par une **délai** instruction ou un **réception** instruction. La branche qui reçoit le premier appel est exécutée. Les autres branches de la **écouter** instruction ne sont jamais exécutées.  
  
-   **actions parallèles.** Exécute plusieurs branches d'un processus d'entreprise simultanément. Le traitement de toutes les branches doit être terminé avant que des instructions suivant l'instruction parallèle soient exécutées.  
  
-   **boucle.** S'exécute de manière répétée tant que la condition qui lui est associée est vraie.  
  
-   **étendue.** Fournit du contexte à un bloc de code qui définit les variables et la sémantique transactionnelle qui s'appliquent à ce bloc. La durée de vie des variables peut être limitée à cette étendue. Il est possible d'appliquer la sémantique transactionnelle (À long terme, Atomique ou Aucune) à une étendue afin d'en modifier son comportement.  
  
-   **exception levée.** Permet d'appeler de manière explicite un gestionnaire d'exceptions/de pannes dans le bloc de code actif.  
  
-   **compenser.** Permet d'appeler de manière explicite un bloc de compensation associé à une étendue donnée. A **étendue** instruction peut avoir un ou plusieurs blocs de compensation associés. Le **compenser** instruction dirige l’exécution vers le bloc de compensation sélectionné.  
  
-   **suspendre.** Arrête provisoirement l'exécution d'un traitement qui peut être redémarrée par un opérateur ou une application. Une expression de chaîne associée à la **Terminer** instruction est accessible aux opérateurs et administrateurs via les journaux correspondants ou via une interface utilisateur.  
  
-   **mettre fin.** Arrête de force et de manière définitive tout traitement d'une planification. Une expression de chaîne associée à la **Terminer** instruction est accessible aux opérateurs et administrateurs via les journaux correspondants ou via une interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Formes d’orchestration](../core/orchestration-shapes.md)   
 [Types de données XLANG-s](../core/xlang-s-data-types.md)   
 [Opérateurs et Variables XLANG-s](../core/xlang-s-variables-and-operators.md)   
 [Expressions XLANG-s](../core/xlang-s-expressions.md)   
 [Mots réservés XLANG-s](../core/xlang-s-reserved-words.md)   
 [XLANG-s pour les Conversions de Type BPEL4WS](../core/xlang-s-to-bpel4ws-type-conversions.md)