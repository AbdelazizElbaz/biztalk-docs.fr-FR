---
title: "Les fonctionnalités de sécurité de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication
- security, authentication
- security, BizTalk Server
- security, security features
- BizTalk Server, security features
ms.assetid: db356439-1898-4c09-86de-458a9bd21b18
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58f87bab3118f824843167a7be97d831cecc0b7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-security-features"></a>Fonctionnalités de sécurité de BizTalk Server
Les applications de Services financiers et des solutions d’intégration de développement à l’aide de [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sont [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications et sont sécurisés par natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fonctionnalités de sécurité. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]les applications sont généralement constituées de la fonctionnalité de messagerie (message de traitement, de transformation, routage) et l’automatisation des flux de travail (automatisation des processus métier, les règles d’entreprise et la logique d’évaluation). [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Fournit la sécurité générale de la messagerie et de flux de travail automation. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Fournit des fonctionnalités de sécurité supplémentaires spécifiques à la sécurisation d’envoi, de réparation, l’approbation et entrée de message de l’utilisateur final. Pour plus d’informations sur [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]-sécurité spécifiques, consultez [A4SWIFT les fonctionnalités de sécurité pour Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/a4swift-security-features-for-message-repair-and-new-submission.md).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]est conçu autour d’un événement modèle de messagerie (centré sur le modèle de conception de base de données et éditeur-abonné MessageBox) dans lequel les messages et les documents, ainsi que les composants de traitement qui interagissent avec eux, sont basés sur XML et des services Web technologies. Pour aider à protéger l’intégrité d’un système constitué d’informations, les participants et les processus, les exigences principales suivantes guident des mécanismes de sécurité :  
  
-   **Protéger la confidentialité des éléments du système.** Protection de la confidentialité des communications dans une zone de calcul ouverte et l’environnement de mise en réseau sont la fonction de chiffrement. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]prend en charge les communications via l’infrastructure à clé publique (PKI), Secure Multipurpose Internet Mail Extensions (S/MIME) et Secure Sockets Layer (SSL) chiffrées. Pour authentifier et d’améliorer la protection de la confidentialité des messages, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] utilise beaucoup des certificats numériques (clés).  
  
     Infrastructure à clé publique est l’ensemble des protocoles Internet permettant de traiter les méthodologies qui favorisent l’échange sécurisé de clés, les procédures et la hiérarchie d’autorité d’authentification des clés et les algorithmes déployés à ces fins.  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]utilise le protocole S/MIME pour chiffrer et déchiffrer les messages envoyés et reçus dans les processus à plusieurs étapes, plusieurs, avec des (Data Encryption Standard), 3DES et prise en charge d’algorithme de chiffrement RC2. Pour la communication point à point chiffrées entre un client Web et un serveur Web, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] utilise le protocole SSL.  
  
-   **L’authentification des informations, les participants et les processus.** Pour authentifier les informations, les participants et les processus, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] s’appuie sur les certificats de signature [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et l’implémentation étendue de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] appelé unique de l’entreprise Sign-On (SSO). Certificats de signature sont les certificats numériques (ou clés) qui identifient des deux parties à l’autre dans un échange de messagerie. Un certificat de signature détermine également si un message a été modifié en transit.  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]permet les clés publiques stockées pour décoder signés numériquement les messages entrants et peut utiliser des clés privées pour signer les messages sortants qu’elle génère. L’authentification unique est la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] extension [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] qui permet des parties et les événements de messagerie qui sont engagés dans plusieurs étapes [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processus à s’authentifier, quel que soit l’étape du processus, à n’importe quelle ressource dans le processus, sans nécessiter plusieurs ouvertures de session.  
  
-   **Autoriser l’utilisation des ressources.** L’autorisation est l’allocation et la gestion des droits d’utilisation pour les ressources d’un système. Le serveur principal [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sont des mécanismes d’autorisation [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] rôles, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et la base de données MessageBox. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]stocke tous les messages entrants et sortants dans sa base de données MessageBox, avant de les envoyer à un processus d’orchestration et l’orchestration envoie les messages à un pipeline d’envoi. L’accès à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] bases de données et des ressources est attribué aux administrateurs, utilisateurs, et l’hôte de comptes à l’aide [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] rôles.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] architecture de sécurité est basée sur un ensemble robuste de mécanismes implémentés dans l’ensemble de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de diverses méthodologies conçu pour accroître la sécurité. Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composants qui incorporent les mécanismes de sécurité sont envoi et réception des adaptateurs, pipelines, la base de données MessageBox, les orchestrations et les propriétés de contexte de sécurité de message.  
  
 Ces composants utilisent des pipelines d’authentification requise, plusieurs ordinateurs hôtes logiques et leur propriété « Authentification de confiance » et les méthodologies de publication et l’autorisation de s’abonner/réception pour déployer les mécanismes de sécurité. Cette architecture de sécurité à facettes multiples de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fournit de nombreuses options permettant de concevoir et d’exécuter plusieurs Services financiers de messagerie et le flux de travail automation applications sécurisées.