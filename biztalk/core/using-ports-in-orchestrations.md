---
title: "L’utilisation de Ports dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, receiving
- ports, configuring manually
- send ports, messages
- ports, creating
- ports, messages
- creating, ports
- send ports, sending
- ports, operations
- configuring, ports
- ports, deleting
- deleting, ports
- orchestrations, ports
- Port Configuration Wizard [Orchestration Designer]
- ports
- ports, about ports
- ports, configuring
ms.assetid: 968b2d1b-e233-4eb0-8254-9ec6b7642cdf
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7f48c1c070e3a3a3e7ebe7e86618a4fd9ebc90d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-ports-in-orchestrations"></a>Utilisation des ports dans des orchestrations
Les ports indiquent comment votre orchestration enverra et recevra des messages vers et à partir d'autres processus d'entreprise. Chaque port possède un type, une direction et une liaison qui déterminent ensemble la direction de communication, le modèle de communication, l'emplacement vers et à partir duquel le message est envoyé ou reçu, et comment la communication a lieu.  
  
> [!NOTE]
>  Il faut faire la distinction entre port et type de port. Un port est une instance d'un type de port. Plusieurs ports peuvent avoir le même type de port.  
  
 En fonction de ces facteurs, un port peut être associé à un URI (emplacement physique), un transport (FILE, HTTP, SOAP, SMTP ou Message Queuing BizTalk), un pipeline d'envoi pour préparer un message pour l'envoi (par exemple en l'assemblant, le chiffrant ou le compressant) et un pipeline de réception pour préparer un message reçu au traitement (par exemple en le désassemblant, le déchiffrant ou le décompressant).  
  
 Pour ajouter des ports à une orchestration, on procède sensiblement de la même façon que pour ajouter des contrôles à un formulaire Web ou Windows. Vous pouvez également ajouter des ports en utilisant la fenêtre Vue Orchestration.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Modèle de communication](../core/communication-pattern.md)  
  
-   [Direction de communication](../core/communication-direction.md)  
  
-   [Liaisons de port](../core/port-bindings.md)  
  
-   [L’utilisation de Ports dans les Orchestrations](../core/how-to-use-ports-in-orchestrations.md)  
  
-   [L’utilisation des Types de ports](../core/how-to-work-with-port-types.md)  
  
-   [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)  
  
-   [Utilisation de Ports à liaison directe dans les Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)   
 [À l’aide de liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md)