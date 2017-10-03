---
title: "POP3 L’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- POP3 adapters, about POP3 adapters
- authenticating, POP3 adapters
- POP3 adapters
- POP3 adapters, receive adapters
- POP3 adapters, authenticating
- receive adapters, POP3 adapters
ms.assetid: 008f7fa7-60c3-4ea3-b90d-821e4029a04c
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbe21a3cf0e611a690cf22c88b1344926fa72744
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter"></a>Adaptateur POP3
Vous utilisez l'adaptateur POP3 (Post Office Protocol 3) pour extraire les données d'un serveur sur lequel résident des boîtes aux lettres POP3 vers un serveur exécutant Microsoft BizTalk Server via le protocole POP3.  
  
 L'adaptateur POP3 est constitué d'un seul adaptateur de réception. Ce dernier contrôle les emplacements de réception qui utilisent l'adaptateur POP3.  
  
 Cette rubrique traite du flux de travail de l'adaptateur de réception POP3.  
  
 **POP3 Adaptateur de réception**  
  
 L'adaptateur de réception POP3 extrait les messages électroniques d'une boîte aux lettres spécifiée située sur un serveur POP3 donné. Par défaut, il applique un traitement MIME aux messages électroniques téléchargés et soumet ces derniers à BizTalk Server en tant que messages BizTalk à parties multiples. Il peut recevoir et traiter des messages électroniques dans les formats suivants :  
  
-   Texte brut  
  
-   MIME codé  
  
-   MIME chiffré  
  
-   MIME codé et signé  
  
-   MIME chiffré et signé  
  
 **Prise en charge de traitement par lot pour l’adaptateur de réception POP3**  
  
 L'adaptateur de réception POP3 ne prend pas en charge le traitement par lot.  
  
 **Authentification avec le serveur POP3**  
  
 Les méthodes d'authentification suivantes sont prises en charge par l'adaptateur POP3 :  
  
-   **De base.** Le serveur POP3 utilise les informations d'identification fournies par l'utilisateur à des fins d'authentification.  Celles-ci sont envoyées en texte clair.  
  
-   **Digest (APOP).** Le serveur POP3 utilise une chaîne Digest à des fins d'authentification.  
  
-   **Authentification du mot de passe sécurisé (SPA).** Le serveur POP3 utilise les informations d'identification du processus actuel à des fins d'authentification.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Nouveautés de l’adaptateur POP3 ?](../core/what-is-the-pop3-adapter.md)  
  
-   [Configuration de l’adaptateur POP3](../core/configuring-the-pop3-adapter.md)  
  
-   [Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur POP3](../core/walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter.md)  
  
-   [Traitement des Messages à parties multiples avec l’adaptateur POP3](../core/processing-multi-part-messages-with-the-pop3-adapter.md)