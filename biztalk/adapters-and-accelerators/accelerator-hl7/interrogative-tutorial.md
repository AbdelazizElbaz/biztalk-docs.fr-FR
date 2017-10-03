---
title: Didacticiel interrogative | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interrogative tutorial
- interrogative tutorial, about the tutorial
- tutorials, interrogative tutorial
ms.assetid: 93988429-5544-4920-821f-54f0a67bda72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b35a5bc8ba7574df7499fef5d63a100993c4201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interrogative-tutorial"></a>Didacticiel interrogative
Ce didacticiel contient des procédures détaillées qui décrivent la façon dont vous utilisez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour faciliter le processus d’entreprise dans un scénario de requête/réponse.  
  
> [!NOTE]
>  Pour utiliser ce didacticiel, vous devez installer les outils de test MLLP. Ces outils ne sont pas installés par une installation classique de BTAHL7. Vous devez exécuter une installation personnalisée et sélectionnez **outil de Test MLLP** à partir du dossier de l’adaptateur et **Test Instances** à partir du dossier d’artefacts. Si les outils de test sont installés, votre système doit contenir le dossier \< *lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\MLLP utilitaires. Consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).  
  
## <a name="interrogative-scenario"></a>Scénario interrogative  
 Ce didacticiel utilise le scénario de Interrogative ou de requête/réponse. Dans ce scénario, le flux d’activité est similaire à celui indiqué dans l’illustration suivante. La liste numérotée, la figure suivante décrit le flux de travail.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")  
  
1.  Le flux de travail commence lorsqu’un système d’admission décharger et de transfert (ADT) envoie une requête à un système d’informations. Le message HL7 utilise la «**req ^ Q01**« schéma. Dans le didacticiel, l’utilitaire MllpSend simule le ADT port de réception envoie le message de requête au système informations hôpital via le ADT dans le moteur d’intégration BTAHL7.  
  
2.  Le moteur d’intégration BTAHL7 reçoit le message de requête à partir du système ADT et le valide. Ensuite, le pipeline de BTAHL7 renvoie un accusé de réception à ADT.  
  
3.  Le moteur d’Interface BTAHL7 traite le message, et ensuite les itinéraires du message de requête à la destination de HIS de tiers via le port d’envoi.  
  
4.  Après avoir reçu l’accusé de réception de la requête d’origine, le système ADT attend une réponse. L’hôpital informations système renvoient un message de réponse via le port de réception. Pour ce didacticiel, l’utilitaire MllpSend simule un système d’informations du message de réponse.  
  
5.  Le moteur d’Interface BTAHL7 traite le message de réponse et puis l’achemine au tiers de destination via le port d’envoi ADT.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)  
  
-   [Étape 1 : Créer et déployer des en-tête commun et schémas d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md)  
  
-   [Étape 2 : Créer des schémas courants pour V2.4](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)  
  
-   [Étape 3 : Créer et déployer un projet déclencheur d’événement (Message)](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)  
  
-   [Étape 4 : Créer le Port de réception pour accepter les Messages de requête ADT](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)  
  
-   [Étape 5 : Créer le Port de réception pour l’acceptation de ses Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)  
  
-   [Étape 6 : Créer un Port d’envoi pour remettre des Messages de requête](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-query-messages.md)  
  
-   [Étape 7 : Créer un Port d’envoi pour remettre des Messages de réponse](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)  
  
-   [Étape 8 : Configurer les informations de tiers](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)  
  
-   [Étape 9 : Redémarrer BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md)  
  
-   [Étape 10 : Vérifier que le scénario Interrogative](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-interrogative-scenario.md)  

## <a name="next-step"></a>Étape suivante  
 [Préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)
  
## <a name="see-also"></a>Voir aussi  
[Prise en main BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)