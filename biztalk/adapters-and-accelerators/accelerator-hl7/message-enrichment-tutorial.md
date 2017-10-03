---
title: "Didacticiel d’enrichissement de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial
- message enrichment tutorial, about the tutorial
- messages, tutorial
- tutorials, message enrichment tutorial
ms.assetid: 4ffb047f-457a-4a80-b7ec-4b61ae16f35f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532fc0e8a9aeefbc35a892277c68be8d640b5588
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-enrichment-tutorial"></a>Didacticiel d’enrichissement de message
Ce didacticiel fournit des instructions détaillées pour l’utilisation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour résoudre un problème commercial particulier : le problème d’enrichissement de message. Le didacticiel d’enrichissement de message décrit une situation dans laquelle vous devez ajouter à ou enrichir un message qui n’est pas conforme HL7 et/ou est incomplète. Cela peut se produire avec une application, telle qu’une application de patients, ou il peut se produire lorsque vous remplissez un message avec des données XML à partir de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].  
  
 Dans ce didacticiel, vous capturez les messages avec BTAHL7 et fournissez des données manquantes, par exemple, à partir d’une base de données de patients. Vous puis convertissez le message et l’envoyez à un laboratoire, d’assurance ou toute hérité line-of-business (LOB) application à l’aide de l’adaptateur MLLP (minimale inférieure Layer Protocol).  
  
 Dans ce didacticiel, vous utilisez une application client (WSClient.exe) du service Web pour envoyer un message au format XML, dans ce cas, un événement de déclencheur « sonnette » inscrire un Patient, via l’adaptateur SOAP pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] avec BTAHL7. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]reçoit le message dans un protocole SOAP port de réception et les itinéraires le message à une orchestration publié en tant qu’un service Web. Le message XML contient un nom du patient et le numéro de sécurité sociale. Vous enrichir le message et utilisez des schémas, une carte et une transformation pour convertir le message au format de HL7. Ensuite vous envoyer via un adaptateur MLLP au laboratoire, d’assurance, ou d’applications métiers.  
  
 La figure suivante illustre le processus du didacticiel.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")  
  
> [!NOTE]
>  Ce didacticiel requiert Windows Server Standard, Enterprise, Datacenter ou Web Edition et une installation personnalisée de BTAHL7 qui inclut le MLLP des outils de test. En outre, vous devez être familiarisé avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] développement dans [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] et les informations présentes dans [en savoir plus sur l’accélérateur HL7 et les outils BizTalk disponibles](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).  
  
> [!NOTE]
>  Vous pouvez éviter des erreurs par l’annulation du déploiement des assemblys, l’arrêt des ports d’envoi, et la désactivation des emplacements que vous avez utilisé dans les didacticiels précédents de réception.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Étape 1 : Configurer l’identité du Pool d’applications](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-application-pool-identity.md)  
  
-   [Étape 2 : Créer un nouveau projet](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)  
  
-   [Étape 3 : Assigner un nom fort à l’Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)  
  
-   [Étape 4 : Créer les schémas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)  
  
-   [Étape 5 : Promouvoir les propriétés de schéma](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)  
  
-   [Étape 6 : Valider les schémas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)  
  
-   [Étape 7 : Signer et générer des projets](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)  
  
-   [Étape 8 : Créer un mappage avec le Mappeur BizTalk](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)  
  
-   [Étape 9 : Valider et générez le projet de carte](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)  
  
-   [Étape 10 : Créer une Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)  
  
-   [Étape 11 : Créer des Variables d’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)  
  
-   [Étape 12 : Configurer les formes d’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)  
  
-   [Étape 13 : Créer et configurer des Ports](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)  
  
-   [Étape 14 : Publier l’Orchestration en tant que Service Web](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)  
  
-   [Étape 15 : Configurer l’envoi et Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)  
  
-   [Étape 16 : Démarrer l’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)  
  
-   [Étape 17 : Créer l’Application WSClient](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)  
  
-   [Étape 18 : Tester votre nouvelle Solution d’enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)