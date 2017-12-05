---
title: "Exemple de scénario d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, business example
- examples, business processes
- health care organizations, business example
- business processes, example
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78229d903461fe2b84033b036ef02b2838832fc0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="sample-business-scenario"></a>Exemple de scénario commercial
Soins de santé des processus sont souvent complexes et impliquent de nombreux systèmes. Un exemple est le processus qui se produit lorsqu’un patient entre un hôpital et un médecin envoie le patient d’un laboratoire de test. Impliqués dans cette procédure sont cinq parties :  
  
-   Le médecin  
  
-   Le système d’enregistrement hôpital  
  
-   Le système d’entrée de commande cliniques  
  
-   Le système de laboratoire  
  
-   Le système de facturation  
  
 Les étapes suivantes peuvent se produire dans ce processus :  
  
1.  La participation doctor inscrit le patient.  
  
    1.  Un ADT ^ O04 message d’inscription est diffusée par le système d’enregistrement hôpital.  
  
    2.  Le ADT ^ O04 message est reçu par tous les services qui s’abonnent au message, y compris le système d’entrée de commande cliniques et le système de laboratoire.  
  
2.  Le médecin commandes une étude de diagnostic à partir de l’installation de laboratoire.  
  
    1.  Un ORM ^ O01 message d’ordre est envoyé à partir du système d’entrée de commande cliniques, après la validation de règles d’entreprise.  
  
    2.  Le ORM ^ O01 message est reçu par le système de laboratoire.  
  
3.  Le laboratoire reçoit la commande et renvoie une confirmation.  
  
    1.  Un ORR ^ message de confirmation de la commande O02 est envoyé par le système de laboratoire, indiquant que la commande peut être exécutée.  
  
    2.  L’ORR ^ O02 message est reçu par le système d’entrée de commande cliniques.  
  
4.  À la fin des tests, le laboratoire envoie les résultats pour le médecin et d’autres services.  
  
    1.  Un ORU ^ message des résultats des tests de R01 est envoyé à partir du système de laboratoire.  
  
    2.  L’ORU ^ R01 message est reçu par le système d’entrée de commande cliniques et le système de facturation.  
  
    3.  Le moteur de l’Interface envoie un message électronique au médecin, qui reçoit les résultats de laboratoire sur son PDA sans fil.  
  
## <a name="the-btahl7-solution"></a>La Solution BTAHL7  
 L’exemple de scénario d’entreprise présentée ci-dessus est un exemple d’un système de soins de santé besoins d’intégration. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) fournit une solution pour ce scénario qui propose les fonctionnalités suivantes :  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s’intègre tous les systèmes impliqués dans une disposition « hub and spoke ». Chaque système communique directement avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Ils n’ont pas à communiquer directement entre eux.  
  
2.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]gère les messages encodés HL7 en mode natif. Aucun codage personnalisé n’est requise.  
  
3.  Le ADT ^ O04 message d’inscription est diffusé à tous les systèmes qui y abonner. Le modèle de messagerie éditeur-abonné pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] garantit la souplesse de configuration et gestion de la liste des systèmes d’abonnement au message. Vous pouvez ajouter des systèmes ou les supprimer à partir de la liste des abonnements sans affecter le reste du système.  
  
4.  La règle d’entreprise permet de valider le ORM ^ message de commande O01 permettre être modifiée de manière dynamique sans affecter le reste du système.  
  
5.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]peut être configuré pour générer automatiquement le ORR ^ message de confirmation de commande (ACK) O02.  
  
6.  Si nécessaire, vous pouvez traiter par lot des messages avec d’autres utilisateurs pour l’envoi et les traiter dès réception à partir d’un lot.  
  
7.  Vous pouvez valider tous les messages dans le moteur et par rapport à la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]des schémas X 2 publié par l’organisation HL7.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BizTalk Server répond aux besoins de l’entreprise](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)