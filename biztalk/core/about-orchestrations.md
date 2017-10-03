---
title: "À propos des Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations
- Orchestration Designer
- orchestrations, about orchestrations
- Orchestration Designer, about Orchestration Designer
ms.assetid: c0d9a3fb-da87-42cc-9e9e-e2c37232e606
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd3c1abeeb2c42c399a54aea4ba0128cc19bcd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-orchestrations"></a>À propos des Orchestrations
Une orchestration est un outil flexible et puissant servant à représenter un processus d'entreprise exécutable avec le langage XLANG/s. XLANG/s peut être considéré comme un langage de messagerie comportant certaines des fonctionnalités d'expression de C#. Vous pouvez concevoir un flux, générer et interpréter des données, appeler un code personnalisé et organiser tout le processus dans un dessin visuel intuitif. Lors de l'exécution, le moteur d'orchestration BizTalk exécute les fichiers XLANG/s qui constituent les processus d'entreprise exécutables produits par le Concepteur d'orchestration BizTalk.  
  
 Les messages, les actions d'envoi et de réception auxquels les messages sont soumis et les ports via lesquels ces derniers sont transportés sont tous des éléments fondamentaux des orchestrations. Le message est le moyen par lequel les orchestrations communiquent avec le monde extérieur ainsi que le support de transmission de l'e-business.  
  
 **Réception** et **envoyer** formes encapsulent les fonctionnalités que vous avez besoin pour recevoir des messages dans votre orchestration et envoyer des messages à partir de celui-ci. Nous vous recommandons de vous familiariser avec les diverses formes que le Concepteur d'orchestration fournit pour représenter le flux logique de votre orchestration.  
  
 Vous devez comprendre les concepts d'orchestration avancés que sont par exemple les services Web, la corrélation et les transactions à long terme. Vous n'aurez peut-être pas besoin d'utiliser toutes ces fonctionnalités, mais il est judicieux que vous sachiez en quoi elles peuvent vous rendre service.  
  
 Les services Web sont des programmes comportant des interfaces qui adhèrent aux normes définies dans le langage WSDL (Web Services Description Language). En définissant des types de messages, des ports, des types de ports et des opérations de façon standard, des systèmes disparates peuvent communiquer efficacement entre eux.  
  
 La corrélation est le mécanisme par lequel les messages sont associés à des instances d'exécution particulières d'une orchestration, de manière à ce que votre processus d'entreprise puisse récupérer les informations appropriées lors de l'exécution de plusieurs instances et du transfert de plusieurs messages.  
  
 Les transactions vous permettent de conserver correctement l'état d'une orchestration dans l'éventualité d'un problème inattendu. Le Concepteur d'orchestration offre divers moyens de gérer les exceptions, ce vous permet de faire face aux erreurs de façon contrôlée et prévisible.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [L’aire de conception d’Orchestration](../core/the-orchestration-design-surface.md)  
  
-   [Onglet des Orchestrations BizTalk, boîte à outils](../core/biztalk-orchestrations-tab-toolbox.md)  
  
-   [Étapes de développement d’orchestrations](../core/steps-in-orchestration-development.md)  
  
-   [Considérations de sécurité pour le développement d’Orchestrations](../core/security-considerations-for-developing-orchestrations.md)  
  
-   [Langage XLANG-s](../core/xlang-s-language.md)  
  
-   [Sur le moteur d’Orchestration BizTalk](../core/about-the-biztalk-orchestration-engine.md)