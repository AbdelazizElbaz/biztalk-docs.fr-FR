---
title: "Étape 9 : Vérifier que le scénario par lot entrant fragmentés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ba61866-2e1b-49e2-be57-ef281407d0a5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47d5ec8ffa7a7875af7073e60d6578149d532a7a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-9-verify-the-fragmented-inbound-batch-scenario"></a>Étape 9 : Vérifier que le scénario par lot entrant fragmentés
Dans cette étape, vous vérifiez le scénario fragmenté un lot de trafic entrant.  
  
 Vérification du scénario implique l’utilisation des outils suivants :  
  
-   **Outil de MllpSend**, que vous utilisez à partir de la ligne de commande pour envoyer un lot de messages au port de réception.  
  
-   **Outil de MllpReceive**, que vous utiliser à partir de la ligne de commande pour vérifier la réception des messages individuels (en tant que contenu dans le lot) à partir du port d’envoi. Cette instance de l’outil MllpReceive fonctionne comme une application métier-simulée. Sur la réception des messages, il génère également un accusé de réception vers le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’intégration.  
  
-   Une deuxième instance de l’outil MllpReceive, qui vous permet de vérifier la réception des accusés de réception du port d’envoi.  
  
### <a name="to-test-the-fragmented-inbound-batch-scenario"></a>Pour tester le scénario de fragmenter un lot entrant  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **invite de commandes**.  
  
2.  À l’invite de commandes, accédez au  **\<* lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator HL7\SDK\MLLP utilitaires * *.  
  
3.  À l’invite de commandes, tapez  **mllpreceive /p 41000/SB 11 /eb 28 /cr 13 /hl7ack «\<*lecteur*\>: \Program Files\Microsoft BizTalk \<version\>Accelerator for HL7\Samples\Sample Application accepter ACK.txt**, puis appuyez sur **entrée**. La fenêtre d’invite de commande passe à un état d’attente jusqu'à ce que vous exécutez l’étape 5 et le système reçoit l’entrée.  
  
    > [!NOTE]
    >  La commande à l’étape 3 s’exécute l’application du récepteur MLLP qui écoute le port 41000. Ce port est associé au port d’envoi qui remet des messages (tel que créé dans [étape 5 : créer un Port d’envoi pour remettre les Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)). L’outil MllpReceive agit comme l’application métier-qui reçoit les messages et renvoie l’accusé de réception (ACK) à BTAHL7 (tel qu’il est contenu dans l’exemple de fichier exemple Application accepter ACK.txt). L’outil affiche les messages qui lui a été retournés dans la fenêtre d’invite de commandes. La commande à l’étape 3 spécifie les caractères EB, service bus et CR par défaut du message MLLP.  
  
4.  Répétez les étapes 1 et 2 pour ouvrir une autre fenêtre d’invite de commandes et accédez au répertoire MLLP utilitaires. À l’invite de commandes, tapez **mllpreceive /p 41002**, puis appuyez sur **entrée**. La fenêtre d’invite de commande passe à un état d’attente jusqu'à ce que vous exécutez l’étape 5 et le système reçoit la sortie.  
  
    > [!NOTE]
    >  La commande à l’étape 4 s’exécute l’application du récepteur MLLP écoute le port 41002. Ce port est associé au port d’envoi qui remet les accusés de réception à la source du message de lot (tel que créé dans [étape 6 : créer un Port d’envoi pour remettre les accusés de réception](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)). L’outil MllpReceive agit comme l’application line-of-business qui a envoyé le lot d’origine. L’outil affiche les accusés de réception qui lui a été retournés dans la fenêtre d’invite de commandes. La commande à l’étape 4 spécifie les caractères EB, service bus et CR par défaut du message MLLP.  
  
5.  Répétez les étapes 1 et 2 pour ouvrir une autre fenêtre d’invite de commandes et accédez au répertoire MLLP utilitaires. À l’invite de commandes, tapez  **mllpsend /twoway/SB 11 /eb 28 /cr 13 /f «\<*lecteur*\>: \Batching Tutorial\Instances\FragmentedInboundBatch.txt « /p 21000 **, où \<* lecteur* \> est la lettre de lecteur de votre installation, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  La commande à l’étape 5 simule l’envoi du message de lot d’origine au port de réception. La console devrait afficher « les messages envoyés : 1 », indiquant que l’outil MllpSend envoyé le message de lot unique. Si elle n’affiche pas « les messages envoyés : 1 », consultez l’Observateur d’événements. Vérifiez que le texte de la commande entré à l’étape 5, puis résoudre les problèmes de la configuration de l’envoi et ports de réception et l’état de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et BTAHL7.  
  
### <a name="to-verify-the-results-of-the-fragmented-inbound-batch-tutorial"></a>Pour vérifier les résultats de ce didacticiel fragmenté de traitement par lots entrants  
  
1.  Vérifiez que, après un court délai, l’outil MllpReceive écoute les messages sur le port 41000 affiche le contenu des messages individuels fragmenté du lot et envoyé au tiers Tutorial_BatchSource. Le contenu des deux messages doit être comme suit :  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT ^ A03|000001|Tutorial_BatchSource|MESA_IS|  
    |ADT ^ A03|000002|Tutorial_BatchSource|MESA_IS|  
  
2.  Vérifiez que, après un court délai, l’outil MllpReceive l’écoute des accusés de réception sur le port 41002 affiche le contenu de deux accusés de réception renvoyés par le moteur d’intégration BTAHL7 à la source du lot. Le contenu de deux accusés de réception doit être comme suit :  
  
    |MSH.9|MSH.3|MSH.5|MSA.2|MSA.1|  
    |-----------|-----------|-----------|-----------|-----------|  
    |L’ACCUSÉ DE RÉCEPTION ^ A03 ^ L’ACCUSÉ DE RÉCEPTION|MESA_IS|Tutorial_BatchSource|000001|AA|  
    |L’ACCUSÉ DE RÉCEPTION ^ A03 ^ L’ACCUSÉ DE RÉCEPTION|MESA_IS|Tutorial_BatchSource|000002|AA|  
  
## <a name="see-also"></a>Voir aussi  
 [Partie 2 : Traitement par lots de dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [Partie 3 : Scénario de création de lot](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)