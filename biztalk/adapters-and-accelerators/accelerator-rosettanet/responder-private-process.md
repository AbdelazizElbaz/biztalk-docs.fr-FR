---
title: "Processus de répondeur privé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- messages, private processes
- LOBs
- messages, message flow
- private processes, responder
- private processes, message flow
ms.assetid: 69b58320-977c-44d2-a7d6-f986213aecf2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8ba5ca38eb64859182242c944d260c9db15c880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="responder-private-process"></a>Processus privés de répondeur
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise le processus privé répondeur (PrivateResponder.odx) pour traiter le contenu de service sur un ordinateur hébergeant le répondeur. Notamment :  
  
-   Acheminement d’un message entrant à l’application de métier (LOB)  
  
-   Création du service de contenu d’un message de réponse et le routage du message vers le processus public, dans l’itinéraire à l’ordinateur de répondeur  
  
 Le processus privé également définit les métadonnées et ajoute les pièces jointes au message de réponse. Le processus privé Achemine les messages sortants pour le processus public répondeur, qui ajoute des en-têtes de Framework RNIF (RosettaNet Implementation) et prépare le message pour la transmission. Le processus privé Achemine les messages entrants dans la table MessagesToLOB les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données, dans l’itinéraire à l’application métier.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut deux exemples de processus privé répondeur que vous pouvez personnaliser pour votre processus d’entreprise spécifiques. Le premier est un exemple de processus PrivateResponder qui contient le code pour le processus privé répondeur installé par [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. Pour plus d’informations, consultez [PrivateResponder exemple](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md).  
  
 Le deuxième exemple est l’exemple de processus privé PIP3A4PrivateResponder qui automatise les processus de commande de requête/bons d’achat qui utilisent 3A2 et 3 a 4 processus Partner Interface (PIP). Il gère également tous les autres messages PIP. Pour plus d’informations, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
## <a name="message-flow"></a>Flux de messages  
 Le flux de messages à travers le processus privé du répondeur est comme suit :  
  
1.  Le processus privé répondeur reçoit le message entrant d’origine du processus publics répondeur, dans l’itinéraire à partir de l’ordinateur de l’initiateur.  
  
2.  Le processus privé construit le message de l’application métier. Cela implique la mise en route le modèle de message LOB, sérialise le contenu de service XML et le chargement les parties de message XML dans le message LOB.  
  
3.  Le processus privé Achemine le message dans la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données, dans l’itinéraire à l’application métier principale.  
  
4.  Si le message d’origine a une pièce jointe, le processus privé appelle le composant AttachmentHelper pour traiter la pièce jointe.  
  
5.  Le processus privé envoie une notification à l’application métier qu’il enregistré le message de réponse dans la table MessagesToLOB.  
  
6.  Si le message est un message d’action unique, le processus privé est terminé.  
  
7.  Si le message est un message de double action, le processus privé attend une réponse de l’application métier.  
  
8.  Lorsque le processus privé reçoit la réponse de l’application métier, il génère un message de réponse et envoie le message vers le processus public.  
  
9. Le processus privé attend le signal dans le processus public. S’il reçoit le signal, il construit le message de signal LOB et l’envoie à l’application métier. Si la version RNIF est 1.1, le processus privé sera d’écoute pour un signal d’accusé de réception deuxième et à sa réception, de construire le message de signal LOB et envoyer à l’application métier. Le processus privé notifie l’application métier après l’envoi de chaque message de signal.  
  
10. Si le processus privé reçoit un message de Notification d’échec (n) à partir du processus public, dans l’itinéraire à partir de l’initiateur, le processus privé construit une «[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Exception », le message et envoie à l’application métier.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus privés](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)   
 [Processus privés de l’initiateur](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)   
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [Exemple de PrivateResponder](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)