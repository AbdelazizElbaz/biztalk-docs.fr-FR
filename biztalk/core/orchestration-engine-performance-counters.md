---
title: "Compteurs de performances du moteur d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcaf7517-da4a-4ed0-a3bb-7e9b73931bff
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30c4b3dada1e3775c918d99b1ce0269ac8b1e2a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-engine-performance-counters"></a>Compteurs de performances du moteur d'orchestration
Le moteur d'orchestration gère plusieurs compteurs de performance que vous pouvez consulter avec l'Analyseur de performances pour connaître le nombre d'instances d'orchestration et de transactions qui ont été traitées par le moteur.  
  
 Pour exécuter l’Analyseur de performances, accédez à la **Démarrer** Menu, sélectionnez **exécuter**, tapez **perfmon**, puis appuyez sur **entrée**. Cliquez sur le **ajouter** bouton, puis sélectionnez **Orchestrations XLANG/s** à partir de la **objet de Performance** liste déroulante.  
  
 Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **Orchestrations XLANG/s** catégorie d’objet de performances :  
  
|Compteur|Commentaires|  
|-------------|--------------|  
|% mémoire physique utilisée|Pourcentage de mémoire physique totale utilisée sur l'ordinateur.|  
|Domaines d'application actifs|Nombre de domaines d'application d'orchestration chargés dans le processus.|  
|Moyenne facteur de lot|Nombre de points de persistance atteints depuis le démarrage de l'instance de l'hôte, divisé par le nombre de transactions sous-jacentes.|  
|Transactions de base de données|Nombre de transactions de base de données effectuées depuis le démarrage de l'instance de l'hôte.|  
|Transactions de base de données par seconde|Nombre moyen de transactions exécutées par seconde.|  
|Orchestrations pouvant être en attente|Nombre d'instances d'orchestration pouvant être mises en attente et actuellement hébergées par l'instance de l'hôte.|  
|Mise en attente des orchestrations|Nombre d'orchestrations qui se trouvent dans le processus de mise en attente.|  
|Cycle de mise en attente en cours|Indique s'il y a un cycle de mise en attente actuellement en cours.|  
|Cycles de mise en attente|Nombre de cycles de mise en attente réussis.|  
|Seuil de mise en attente|Nombre, en millisecondes, qui détermine la rapidité avec laquelle les orchestrations sont mises en attente. Si le moteur d'orchestration prévoit qu'une instance pourra être mise en attente dans un délai supérieur à ce seuil, il la met en attente.|  
|Orchestrations inactives|Nombre d'instances d'orchestration inactives actuellement hébergées par l'instance de l'hôte. Cela fait référence aux orchestrations qui ne progressent pas, mais qui ne peuvent pas être mises en attente. C'est le cas, par exemple, lorsqu'une orchestration attend une opération de réception, d'écoute ou de délai dans une transaction atomique et se retrouve de ce fait bloquée.|  
|Mémoire privée allouée (en mégaoctets)|Mégaoctets alloués à la mémoire privée de l'instance de l'hôte.|  
|Mémoire virtuelle allouée (en mégaoctets)|Mégaoctets réservés à la mémoire virtuelle de l'instance de l'hôte.|  
|Échecs de connexion à la base de données MessageBox|Nombre de tentatives de connexion à la base de données ayant échoué depuis le démarrage de l'instance de l'hôte.|  
|Bases de données MessageBox en ligne|Nombre de bases de données MessageBox actuellement disponibles pour l'application.|  
|Orchestrations completed (Orchestrations réussies)|Nombre d'instances d'orchestration terminées depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations completed/sec (Orchestrations réussies par seconde)|Nombre moyen d'orchestrations réussies par seconde.|  
|Orchestrations créées|Nombre d'instances d'orchestration créées depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations créées par seconde|Nombre moyen d'orchestrations créées par seconde.|  
|Orchestrations dehydrated (Orchestrations mises en attente)|Nombre d'instances d'orchestration mises en attente depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations dehydrated/sec (Orchestrations mises en attente par seconde)|Nombre moyen d'orchestrations mises en attente par seconde.|  
|Orchestrations discarded (Orchestrations supprimées)|Nombre d'instances d'orchestration supprimées de la mémoire depuis le démarrage de l'instance de l'hôte. Une orchestration peut être supprimée si le moteur ne parvient pas à conserver son état.|  
|Orchestrations discarded/sec (Orchestrations supprimées par seconde)|Nombre moyen d'orchestrations supprimées par seconde.|  
|Orchestrations rehydrated (Orchestrations réalimentées)|Nombre d'instances d'orchestration réalimentées depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations rehydrated/sec (Orchestrations réalimentées par seconde)|Nombre moyen d'orchestrations réalimentées par seconde.|  
|Orchestrations résidentes en mémoire|Nombre d'instances d'orchestration actuellement hébergées par l'instance de l'hôte.|  
|Orchestrations avec mise en attente planifiée|Nombre d'orchestrations pouvant être mises en attente pour lesquelles une requête de mise en attente est en cours.|  
|Orchestrations suspended (Orchestrations suspendues)|Nombre d'instances d'orchestration suspendues depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations suspended/sec (Orchestrations suspendues par seconde)|Nombre moyen d'orchestrations suspendues par seconde.|  
|Messages en attente|Nombre de messages reçus pour lesquels aucun accusé de réception n'a encore été envoyé à la base de données MessageBox.|  
|Opérations en attente|Nombre de blocs d'exécution de code planifiés pour l'exécution.|  
|Points de persistance|Nombre de fois que l'état d'une instance d'orchestration a été enregistré dans la base de données depuis le démarrage de l'instance de l'hôte.|  
|Points de persistance par seconde|Nombre moyen d'instances d'orchestration enregistrées par seconde.|  
|Runnable orchestrations (Orchestrations pouvant être exécutées)|Nombre d'instances d'orchestration prêtes à s'exécuter.|  
|Running orchestrations (Orchestrations en cours d'exécution)|Nombre d'instances d'orchestration en cours d'exécution.|  
|Étendues transactionnelles interrompues|Nombre d'étendues à long terme ou atomiques interrompues depuis le démarrage de l'instance de l'hôte.|  
|Étendues transactionnelles interrompues par seconde|Nombre moyen d'étendues suspendues par seconde.|  
|Étendues transactionnelles validées|Nombre d'étendues à long terme ou atomiques terminées depuis le démarrage de l'instance de l'hôte.|  
|Étendues transactionnelles validées par seconde|Nombre moyen d'étendues réussies par seconde.|  
|Étendues transactionnelles compensées|Nombre d'étendues à long terme ou atomiques compensées depuis le démarrage de l'application.|  
|Étendues transactionnelles compensées par seconde|Nombre moyen d'étendues compensées par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de performances du moteur](../core/engine-performance-characteristics.md)   
 [Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)