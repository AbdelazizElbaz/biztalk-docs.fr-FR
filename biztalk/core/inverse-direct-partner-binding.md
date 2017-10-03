---
title: "Liaison directe de partenaires inversée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, partners
- process management solution tutorial, partner binding
ms.assetid: 4cf8717a-2098-46f4-8f58-9d05fb562e2a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6c9fe5e51f9f63ea098fa623dafbceeb670e75f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="inverse-direct-partner-binding"></a>Liaison directe de partenaires inversée
La solution de gestion des processus d'entreprise est conçue afin que vous puissiez modifier les étapes de traitement des commandes sans arrêter l'application. Pour séparer les étapes de traitement (**CableOrder1**, **CableOrder2**) à partir du Gestionnaire de processus (**OrderManager**), la solution utilise une technique différente pour lier les ports parmi ces orchestrations.  
  
 Dans la forme de liaison habituelle, diriger la liaison, la **OrderManager** orchestration utiliseriez l’orchestration étape du processus comme valeur pour la propriété Port d’Orchestration des partenaires. Dans la liaison directe ainsi le **OrderManager** orchestration dépend des noms forts (qui incluent les versions) des étapes de traitement. Cela rend impossible de modifier les étapes de traitement sans redéployer le **OrderManager** orchestration. Pour plus d’informations sur la liaison directe, consultez [liaisons de Port](../core/port-bindings.md). La liaison directe peut être illustrée comme suit :  
  
 ![Diagramme de liaison directe de partenaires inversée](../core/media/bpm-inverse-direct-binding.gif "BPM_Inverse_Direct_Binding")  
  
 Dans la liaison directe de partenaires inversée, l'orchestration de réception spécifie la liaison, au lieu de l'orchestration d'origine. Le port sur le **OrderManager** est simplement lié à lui-même. Autrement dit, le port sur le **OrderManager** est spécifié pour le **PartnerOrchestrationPort** propriété. Toutefois, les orchestrations d’étape de processus utilisent approprié **OrderManager** port comme valeur pour le **PartnerOrchestrationPort** propriété. Ceci permet de séparer le **OrderManager** à partir des versions des orchestrations d’étape de processus et leur permet d’être modifiées sans redéployer le **OrderManager**. La liaison directe n'autoriserait pas cette séparation. La liaison directe de partenaires inversée peut être illustrée comme suit :  
  
 ![Diagramme de la liaison directe](../core/media/bpm-direct-binding.gif "BPM_Direct_Binding")  
  
> [!NOTE]
>  La liaison directe inversée permet également de communiquer avec les orchestrations des partenaires comme avec une liste de distribution. Le **OrderManger** peut utiliser un port unique pour communiquer avec toutes les étapes. Ceci vous permet d'ajouter et de supprimer des étapes sans recréer l'orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)