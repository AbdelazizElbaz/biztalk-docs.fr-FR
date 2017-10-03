---
title: "Les processus privés de l’initiateur | Documents Microsoft"
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
- erros
- LOBs
- messages, message flow
- private processes, initiator
- private processes, message flow
- private processes, errors
ms.assetid: 8444a5c8-445a-4bbd-a793-a16816fcb397
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 569d176a15ba5236d5f44d87406d9bbc0a19fca9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="initiator-private-process"></a>Processus privés de l’initiateur
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise le processus privé initiateur (PrivateInitiator.odx) pour traiter le contenu de service à un ordinateur de l’initiateur. Notamment :  
  
-   Création du service de contenu d’un message d’origine et le routage du message vers le processus public, dans l’itinéraire vers le partenaire commercial  
  
-   Traitement d’un message de signal de retour et le routage à l’application de métier (LOB)  
  
-   Dans le cas d’un PIP double action, le traitement d’un message de retour de réponse et de leur routage vers l’application LOB.  
  
 Le processus privé également définit les métadonnées et ajoute les pièces jointes. Le processus privé Achemine les messages sortants pour le processus public, qui ajoute des en-têtes de Framework RNIF (RosettaNet Implementation) et prépare le message pour la transmission. Le processus privé Achemine les messages entrants dans la table MessagesToLOB les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données, dans l’itinéraire à l’application métier.  
  
 Ce processus privé automatise les processus de commande de requête/bons d’achat qui utilisent 3A2 et 3 a 4 processus Partner Interface (PIP). Il gère également tous les autres messages PIP. Vous pouvez personnaliser le processus privé pour vos processus d’entreprise spécifiques.  
  
## <a name="message-flow"></a>Flux de messages  
 Le flux de messages à travers le processus privé initiateur est comme suit :  
  
1.  Le processus privé initiateur reçoit le message d’origine à partir de la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données. L’application métier principale achemine le message à cette table.  
  
2.  Le processus privé prépare le contenu du service d’un message de déclenchement et l’envoie au processus public.  
  
3.  Le processus privé initiateur passe ensuite à un état d’attente, à l’écoute d’un signal de retour.  
  
4.  Lorsqu’il reçoit un signal de retour du processus public, le processus privé construit un message de signal et envoie le signal à la table MessagesToLOB dans les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données, dans l’itinéraire à l’application métier.  
  
5.  Le processus privé envoie une notification à l’application métier qu’il placer le message de signal dans la table MessagesToLOB.  
  
6.  Si la version RNIF est 1.1, le processus privé attend un message de signal d’accusé de réception acceptation. S’il reçoit le signal, il construit le message de signal et envoie le signal à la table MessagesToLOB, dans l’itinéraire à l’application métier.  
  
7.  Si l’ou les messages d’origine était un message d’action unique, le processus privé est terminé une fois que ce dernier a renvoyé le message de signal pour l’application métier. Si le message d’origine était un message à double action, le processus privé attend un message de réponse.  
  
8.  Si le processus privé reçoit un message de réponse du processus public, il construit un message de réponse dans le format de l’application métier. Cela implique la mise en route le modèle de message LOB, sérialise le contenu de service XML et le chargement les parties de message XML dans le message LOB.  
  
9. Le processus privé Achemine le message dans la table MessagesToLOB les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données.  
  
10. Si une pièce jointe du message de réponse, le processus privé appelle l’outil AttachmentHelper pour traiter la pièce jointe.  
  
11. Le processus privé envoie une notification à l’application métier qu’il placer le message de réponse dans la table MessagesToLOB et puis est terminée.  
  
## <a name="handling-of-incorrect-messages"></a>Gestion des Messages incorrects  
 Lorsque le processus privé initiateur reçoit un message incorrect à partir de l’application métier, le processus privé renvoie un message d’exception à l’objet LOB. Toutefois, le processus privé ne publie pas le message incorrect dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console Administration de BizTalk. Par conséquent, vous n’êtes pas en mesure d’afficher le message incorrect dans la Console Administration de BizTalk. Vous pouvez utiliser le message d’exception d’accéder au message incorrect pour déterminer quel message était incorrect et alors accéder au message incorrect dans la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données. Toutefois, ce message ne peut pas être le même que le message qui traitent les privé consommé, car modifier la procédure stockée et l’adaptateur utilisé pour traiter le message. Ils ajoutent un élément racine et l’espace de noms au message. L’adaptateur et la procédure stockée éventuellement retournent plusieurs enregistrements.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus privés](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)   
 [Processus privés de répondeur](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)   
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [Exemple de PrivateInitiator](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)