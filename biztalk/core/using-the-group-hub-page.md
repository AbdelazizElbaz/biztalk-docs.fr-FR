---
title: "À l’aide de la Page Hub du groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50693ccc-a3b2-4ad0-9a05-d60dab404a07
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e035a363b71b70db390d88a8b0e32e2e9b531d92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-group-hub-page"></a>Utilisation de la page Hub du groupe
En sélectionnant le **groupe BizTalk** nœud dans la Console Administration de BizTalk Server, affiche la page Hub du groupe BizTalk Server dans le volet de détails. Cette page, divisée en trois sections, fournit une vue d'ensemble du fonctionnement de votre système BizTalk Server :  
  
-   Le **vue d’ensemble de la Configuration** section, située dans la partie supérieure de la page Hub du groupe, indique l’intégrité globale du groupe BizTalk en affichant l’état des applications, les instances d’hôte, et les gestionnaires d’adaptateur configurés dans ce groupe.  
  
-   Le **travail en cours** et **éléments suspendus** sections se trouvent au milieu de la page Hub du groupe.  
  
    -   Le **travail en cours** section affiche les instances de service, orchestrations en attente, ports inactifs et nouvelle tentative, les instances de service prêtes et instances de service planifiée en cours d’exécution.  
  
    -   Le **éléments suspendus** section affiche le nombre d’instances de service suspendues et instances pouvant être reprises et sans reprise possible.  
  
-   Le **Instances de Service suspendues groupées** section affiche les instances de service suspendues groupées par application, nom du service, code d’erreur et URI.  
  
    > [!NOTE]
    >  Les chiffres indiqués sur la page Hub du groupe correspondent à des approximations. Par exemple, les nombres affichés sous **exécutant des instances de service** ou **instances de service suspendues** ne peut pas égal au nombre de total de l’exécution des instances de service ou des instances de service suspendues l’état du système a été modifiée alors que les différentes statistiques sur la page Hub sont générés.  
  
-   Le **Instances de Service suivies** et **événements de Message suivis** sections exécutent des requêtes sur les événements de message et l’état des instances de service avec une correspondance maximale = 50.  
  
    -   **Instances de service suivies** requête recherche les instances de service suivies.  
  
    -   **Instances terminées** requête recherche les instances de service suivies dont l’état terminé.  
  
    -   **Instances arrêtées** requête recherche les instances de service suivies dont l’état arrêté.  
  
    -   **Événements des messages suivis** requête recherche les événements des messages suivis.  
  
    -   **Événements d’échec de transmission** recherche les événements de message suivi avec un type d’événement d’échec de la transmission de la requête.  
  
-   Le **rapports d’état EDI** et **rapports d’état EDIINT** sections, situées en bas de la page Hub du groupe, affiche quatre rapports sur les échanges EDI et l’autre sur les échanges AS2 : l’échange EDI État de l’accusé de réception corrélé rapports, le rapport d’état du lot, le rapport d’agrégation de l’échange, la Transaction rapport d’agrégation et le rapport Message AS2 et état MDN corrélé. Pour plus d’informations sur ces rapports, consultez [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md).  
  
    > [!NOTE]
    >  Les sections de rapport d’état EDIINT et EDI seront affiche uniquement si les fonctionnalités EDI/AS2 sont configurées pour ce groupe BizTalk.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [États d’Instance de service](../core/service-instance-states.md)  
  
-   [Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md)  
  
-   [À l’aide de l’onglet requête de la Console Administration](../core/using-the-administration-console-query-tab.md)  
  
-   [Affichage des messages suivis et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [Suivi des activités et contrôle d’intégrité](../core/health-and-activity-tracking.md)