---
title: "Le traitement de la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, process management solutions
ms.assetid: 0b26447e-d8f1-4084-aa34-6e7f8ffccea5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 145dd8e616048f1caaa1a59ec41d099e93e47880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-business-process-management-solution"></a>Traitement dans la Solution gestion des processus d’entreprise
Cette section décrit le fonctionnement de la Solution de gestion des processus métier : traitement des commandes, utilisation d’interruptions, et comment il gère les exceptions ainsi que les actions peut être retentée.  
  
 Le traitement des commandes s’appuie sur deux orchestrations principales, **OrderBroker** et **OrderManager**. Le **OrderBroker** orchestration est écrit de sorte qu’il peut y avoir plusieurs orchestrations du Gestionnaire de commande, un pour chaque type de commande. La solution contient uniquement un **OrderManager**. assez générique pour pouvoir s'adapter à tous les autres types de commandes.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md)  
  
-   [Logique du Gestionnaire de processus](../core/process-manager-logic.md)  
  
-   [Dans les étapes de traitement de commande de traitement](../core/processing-in-the-order-processing-stages.md)  
  
-   [Gestion des interruptions dans la Solution gestion des processus d’entreprise](../core/interrupt-handling-in-the-business-process-management-solution.md)  
  
-   [Gestion des exceptions dans la Solution gestion des processus d’entreprise](../core/exception-handling-in-the-business-process-management-solution.md)