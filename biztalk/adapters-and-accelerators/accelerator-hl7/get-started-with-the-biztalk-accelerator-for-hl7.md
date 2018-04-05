---
title: Prise en main BizTalk Accelerator pour HL7 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.gettingstarted
helpviewer_keywords:
- BizTalk Accelerator for HL7
- BizTalk Accelerator for HL7, getting started
- getting started
ms.assetid: e842d501-2037-4fd6-a518-d29b25877250
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bebe61b152c7a74c2d45c0604e23b0a39bc6a4fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-accelerator-for-hl7"></a>Prise en main BizTalk Accelerator pour HL7
À l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)], vous pouvez développer des processus d’entreprise entre vos systèmes informatiques de soins de santé. À l’aide de [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], les développeurs, les professionnels de l’informatique et les analystes d’interface peuvent fonctionner dans un environnement commun pour développer des solutions en fonction de BTAHL7 intégrées de bout en bout entre les applications de soins de santé.  
  
 Plus spécifiquement, avec [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] vous pouvez :  
  
-   **Simplifier l’intégration d’applications de soins de santé**. Créer, gérer et suivre les processus d’entreprise distribuées à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] environnement de développement.  
  
-   **Normaliser l’échange de données entre les applications médicales**. Transformer la transmission de données existant entre les applications à le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] standard.  
  
-   **Augmenter l’efficacité**. Automatiser tous les processus de communication entre les applications médicales avec une intervention manuelle minimale.  

Cette section fournit des informations de rôle spécifiques sur la façon dont vous pouvez utiliser [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] pour faciliter l’intégration d’Application d’entreprise (IAE) dans le nombre et le domaine de la santé pour automatiser des solutions de santé business-to-business .  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]fournit quatre scénarios distincts dans le didacticiel format pour chaque type de solution. Avant de commencer ces didacticiels, vous devez comprendre les concepts fondamentaux dans [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]et les outils et les processus qui sont nécessaires pour démarrer la création de solutions avec [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)].  

> [!TIP] 
> Avant de commencer ces leçons, [en savoir plus sur l’accélérateur HL7 et les outils BizTalk disponibles](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).  
  
 Les descriptions ci-dessous fournissent une compréhension générale de chaque [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] didacticiel.  
  
## <a name="end-to-end-tutorial"></a>Didacticiel de bout en bout  
 Le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] didacticiel de bout en bout vous fournit les étapes détaillées pour faciliter le processus d’entreprise dans un scénario d’abonné et le serveur de publication. Ce scénario est une situation dans laquelle un serveur de publication, par exemple, une décharge d’admission et transfert le système envoie un message à des abonnés spécifiques.  
  
 Le message achemine vers le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] moteur d’Interface, qui à son tour reçoit, traite, valide, remet en forme, puis achemine le message vers les abonnés. Les abonnés dans ce scénario sont un hôpital informations et un système de pharmacie.  
  
 Ce scénario utilise les types d’adaptateur de fichier et le protocole de couche inférieure minimale (MLLP). Le serveur de publication ne doive pas être prenant en charge des abonnés et le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interface moteur envoie un accusé de réception approprié au serveur de publication après le traitement du message.  
  
## <a name="interrogative-tutorial"></a>Didacticiel interrogative  
 Le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interrogative didacticiel vous fournit des instructions détaillées pour l’implémentation d’un système de requête-réponse entre les sous-systèmes d’une organisation. Dans ce scénario, une application de métier (LOB) dans l’admission, décharger et de transfert système envoie une requête vers le système d’Information hôpital pour obtenir des résultats de laboratoire patient. Une fois que le système d’Information hôpital reçoit la requête, il envoie les données demandées sur le système qui a émis la requête.  
  
 Ce scénario utilise MLLP comme protocole de transport pour tous les messages, y compris les accusés de réception.  
  
## <a name="message-enrichment-tutorial"></a>Didacticiel d’enrichissement de message  
 Le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] didacticiel d’enrichissement vous fournit les étapes détaillées pour résoudre un problème commercial particulier : le scénario d’enrichissement de message. Le scénario d’enrichissement de message est une situation dans laquelle vous devez ajouter à ou enrichir, un message qui n’est pas conforme HL7 et/ou est incomplète. Cette situation peut se produire avec une application, telle qu’une application d’enregistrement du patient, ou lorsque vous remplissez un message avec des données XML à partir de [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].  
  
 Dans le scénario d’enrichissement de message, vous capturez les messages avec [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]et fournir des données manquantes, par exemple, à partir d’une base de données des enregistrements de patient. Vous puis convertissez le message et l’envoyez à un laboratoire, d’assurance ou toute hérité de métier (LOB) application à l’aide de l’adaptateur MLLP.  
  
## <a name="batching-tutorial"></a>Didacticiel de traitement par lot  
 Le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] didacticiel de traitement par lot vous fournit des étapes détaillées pour recevoir et envoyer des messages par lot. Le traitement par lot implique de recevoir et/ou envoyer un groupe de messages individuels (ou les accusés de réception) en tant qu’un seul message composite.  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]prend en charge les scénarios de traitement par lot trois messages suivants :  
  
-   **Par lot entrant fragmenté**. Dans ce scénario, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] reçoit un lot de messages HL7, puis achemine les messages individuels dans le système de destination.  
  
-   **Traitement par lots dans / hors du lot**. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] reçoit un lot de messages HL7, vérifie les messages individuels dans le lot, et achemine ensuite le lot de messages pour le système de destination.  
  
-   **Créer (ou un lot de traitement par lot sortant)**. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]reçoit des messages individuels et les lots avant de les router vers le système de destination.  
  
## <a name="tutorial-links"></a>Liens de didacticiels  
  
-   [Didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)  
  
-   [Didacticiel interrogative](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)  
  
-   [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)  
  
-   [Didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)
  
## <a name="see-also"></a>Voir aussi
  
[Accessibilité des personnes handicapées](../../adapters-and-accelerators/accelerator-hl7/accessibility-for-people-with-disabilities5.md)