---
title: La Configuration de journalisation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 5cd7aec1-bd38-4d37-9a79-b01eeb89337d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 058a1fce8105a3147fb2e537a9182e7d886bb953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logging-configuration"></a>Configuration de journalisation
Ensemble, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] et [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] offrent numérique transactionnelles et d’intégration d’Application d’entreprise (IAE) des communications sécurisées pour les fournisseurs de soins de santé telles que nombre, ateliers et soins particuliers. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]permet de coordonner l’activité d’application et traitement des transactions, router des messages de manière dynamique, valider et transformer des données et le transport via une variété de cartes. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge l’American National Standards Institute ANSI-accredited d’intégrité au niveau sept (HL7) standard utilisé par les applications cliniques et d’administration dans les réseaux de fournisseur pour échanger des données médicales en temps réel de la messagerie.  
  
 Les messages HL7 qui passent par le système d’accélérateur peuvent être très critiques. Par exemple, les données pourraient être médical du patient ou une transaction financière. Pour assurer la conformité avec HL7 de sécurité et de confidentialité, les administrateurs système doivent être en mesure d’effectuer les opérations suivantes :  
  
-   Déboguer des messages suspendus  
  
-   Surveiller l’accès en continu pour détecter les intrus potentiels et de réduire le risque de failles de sécurité système et de fichier  
  
 Cette section fournit des informations conceptuelles et des procédures vous permettent de configurer l’audit et la journalisation, examiner et interpréter les données d’audit et journaux des événements et exécuter des requêtes sur les données enregistrées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Sur le processus d’enregistrement](../../adapters-and-accelerators/accelerator-hl7/about-the-logging-process.md)  
  
-   [Configuration de la journalisation](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)