---
title: Tutorial1 de bout en bout | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.endtoendtutorial
helpviewer_keywords:
- end-to-end tutorial, about the tutorial
- end-to-end tutorial
- tutorials, end-to-end tutorial
ms.assetid: 90625edc-70a0-42c9-a2fb-8eeb5465d766
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90dc31ac286f8ce1e38d9a511eb319828d8ae939
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-tutorial"></a>Didacticiel de bout en bout
Ce didacticiel contient des procédures détaillées qui décrivent la façon dont vous utilisez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour faciliter le processus d’entreprise dans un scénario d’abonné et le serveur de publication.  
  
> [!IMPORTANT]
>  Pour utiliser ce didacticiel, vous devez installer les outils de test lors de l’installation BTAHL7. Si vous avez effectué une installation par défaut pour installer BTAHL7, vous devez exécuter une installation personnalisée et installer les outils de test pour ce didacticiel fonctionne correctement. À la **le programme d’installation personnalisé** écran de l’installation personnalisée de BTAHL7, sélectionnez **outil de Test MLLP** à partir de la **carte** dossier, puis sélectionnez **Test Instances** à partir de la **artefacts** dossier. Pour plus d’informations, consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).  
  
## <a name="declarative-scenario"></a>Scénario déclaratif  
 Ce didacticiel utilise le scénario déclaratif ou publication/abonnement. Dans le scénario déclaratif, le flux d’activité est similaire à celui indiqué dans l’illustration suivante. La liste numérotée, la figure suivante décrit le flux de travail.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")  
Figure montrant le flux d’entreprise pour le scénario déclaratif  
  
1.  Le flux de travail commence lorsque le serveur de publication, par exemple, une décharge d’admission et système de transfert, envoie un message à des abonnés spécifiques. Le serveur de publication dans le flux de travail est « Tutorial_ADTSystem », et le message est appelé «**ADT ^ A103**. »  
  
2.  Le message est routé vers le moteur d’Interface de BTAHL7, qui à son tour reçoit, traite, valide, remet en forme, puis achemine le message vers les abonnés.  
  
3.  Les abonnés dans ce scénario sont un système d’Information hôpital (Tutorial_HISystem) et un système pharmacie (Tutorial_RXSystem). Ce scénario utilise les types d’adaptateur de fichier et MLLP. Le serveur de publication n'a pas besoin de connaître les abonnés et BTAHL7 correctement envoie un accusé de réception au serveur de publication après le traitement du message.  
  
4.  Le serveur de publication envoie le ADT ^ message A03 via un adaptateur MLLP unidirectionnel (Tutorial_1WayReceivePort).  
  
5.  La destination de ce message est le moteur d’Interface BTAHL7, par conséquent, le message entrant contient un message source (MSH3 = Tutorial_ADTSystem) et un message de destination (MSH5 = BTAHL7InterfaceEngine).  
  
6.  BTAHL7 génère un accusé de réception (ACK) après avoir correctement vérifié le message, puis envoie l’accusé de réception à le Tutorial_ADTSystem via l’adaptateur File.  
  
7.  Le système Tutorial_HISystem et le système Tutorial_RXSystem s’abonner au message ADT reçu par le moteur d’Interface BTAHL7.  
  
8.  La transformation se produit lorsque vous spécifiez des valeurs pour les champs à l’aide de la **MSH carte** onglet dans l’Explorateur de Configuration BTAHL7.  
  
     Par exemple, la partie Tutorial_RXSystem a MSH3 = BTHL7 spécifié dans le **MSH carte** onglet. Par conséquent, le message reçu par l’abonné aura « BTAHL7 » comme valeur pour le champ MSH3.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Test de votre Installation](../../adapters-and-accelerators/accelerator-hl7/testing-your-installation.md)  
  
-   [Préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)  
  
-   [Étape 1 : Créer et déployer des schémas d’en-tête et d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)  
  
-   [Étape 2 : Créer des schémas courants pour v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)  
  
-   [Étape 3 : Créer et déployer un projet déclencheur d’événement (Message)](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project.md)  
  
-   [Étape 4 : Créer le Port de réception pour l’acceptation de ADT ^ A03 des Messages à partir de systèmes ADT à l’aide de l’adaptateur MLLP](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)  
  
-   [Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur de fichier](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)  
  
-   [Étape 6 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur de fichier](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)  
  
-   [Étape 7 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)  
  
-   [Étape 8 : Configurer les informations de tiers](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)  
  
-   [Étape 9 : Redémarrer BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)  
  
-   [Étape 10 : Vérifier que le scénario de bout en bout](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-end-to-end-scenario.md)

## <a name="see-also"></a>Voir aussi
[Prise en main BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)