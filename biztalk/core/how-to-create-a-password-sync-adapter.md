---
title: "Comment créer un adaptateur de synchronisation de mot de passe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caa5bd13-efd9-4544-b5df-17d01c6ac5d8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c47381cc1ed71788673602c1db7eec5b5ac049ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-password-sync-adapter"></a>Comment créer un adaptateur de synchronisation de mot de passe
Un adaptateur de synchronisation de mot de passe est une application qui utilise le composant Programme d'aide à la synchronisation des mots de passe pour échanger des notifications avec l'authentification unique de l'entreprise (SSO). Ce composant possède une interface COM et une interface .NET Framework, mais il n'est pas indispensable que votre adaptateur soit un composant COM. Vous pouvez concevoir votre adaptateur comme un processus autonome, une application COM+ ou un service Windows.  
  
### <a name="to-create-a-password-sync-adapter"></a>Pour créer un adaptateur de synchronisation de mot de passe  
  
1.  Signalez au service d'authentification unique de l'entreprise que votre fournisseur est actif, via `ISSOPSWrapper.InitializeAdapter`.  
  
     `InitializeAdapter` avise ledit service qu'un fournisseur, généralement celui qui fait l'appel, est actuellement activé et qu'il échangera les mises à jour de mot de passe avec le système. Vous pouvez également utiliser`InitializeAdapter` pour activer d'autres ressources comme les adaptateurs de groupe.  
  
2.  Envoyez les mises à jour de mot de passe au service d'authentification unique de l'entreprise via `ISSOPSWrapper.SendNotification`.  
  
     Vous devez déterminer comment vous recevrez les mises à jour de mot de passe provenant d'un système non-Windows. Une fois que vous avez reçu une mise à jour, vous pouvez la transmettre au service d'authentification unique de l'entreprise via `SendNotification`. Notez que `SendNotification` n’est pas limité à l’envoi des mises à jour du mot de passe : l’architecture de `SendNotification` vous permet également d’envoyer d’autres types de notifications.  
  
3.  Demandez des mises à jour de mot de passe au service d'authentification unique de l'entreprise via `ISSOPSWrapper.ReceiveNotification`.  
  
     L'adaptateur de synchronisation de mot de passe étant une technologie de type « pull », le service d'authentification unique de l'entreprise n'appelle jamais votre adaptateur. C'est plutôt ce dernier qui appelle périodiquement `ReceiveNotification` pour savoir si des mises à jour sont disponibles. Vous pouvez choisir de définir l'indicateur WAIT sur `ReceiveNotification`. Cela bloquera le thread jusqu'à ce qu'une notification soit disponible.  
  
     Notez que le service d'authentification unique de l'entreprise adresse un message texte standard pour signaler un changement de mot de passe à l'adaptateur. Il incombe à l'adaptateur d'éviter toute divulgation non autorisée des informations sur les mots de passe. Il doit aussi se protéger des programmes espions ou des attaques émanant d'autres sources non valides, y compris du composant Programme d'aide à la synchronisation des mots de passe.  
  
     Une fois que vous avez reçu une mise à jour de mot de passe émanant du service d'authentification unique de l'entreprise via le paramètre `pReceiveNotification`, vous devez la transmettre à votre système non-Windows. Comme avec `SendNotification`, il vous incombe de déterminer le meilleur moyen de communiquer avec le serveur distant.  
  
4.  Désactivez votre adaptateur via `ISSOPSWrapper.ShutdownAdapter`.  
  
     `ShutdownApplication` devrait être la dernière méthode appelée par un adaptateur, indiquant que ce dernier n'échangera plus de mises à jour de mot de passe avec le service d'authentification unique de l'entreprise.  
  
     Notez que le service d'authentification unique de l'entreprise met en mémoire tampon tout changement de mot de passe effectué par un utilisateur quand l'adaptateur est arrêté, à concurrence d'une taille limite dans le tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)   
 [Synchronisation des mots de passe](../core/synchronizing-passwords.md)