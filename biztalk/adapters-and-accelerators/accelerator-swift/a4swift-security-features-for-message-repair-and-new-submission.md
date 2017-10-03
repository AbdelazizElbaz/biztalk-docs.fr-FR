---
title: "Les fonctionnalités de sécurité A4SWIFT pour Message Repair et New Submission | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, messages
- A4SWIFT, security
- security, A4SWIFT
- messages, security
ms.assetid: c34bcba7-fecd-4e2f-ab49-a6ccfd96198b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00170fcdca39de36290e73779881a5d697be8010
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a4swift-security-features-for-message-repair-and-new-submission"></a>Fonctionnalités de sécurité A4SWIFT pour Message Repair et New Submission
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]Fournit des fonctionnalités de l’emploi pour la création de messages SWIFT, réparation, la vérification de changement de clé et l’approbation. Les utilisateurs de créer, modifier et passez en revue les messages SWIFT à l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], qui fournit une interface utilisateur et de la représentation sous forme de graphique pour les messages financières (FIN). [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]restitue le formulaire de vérification de l’entrée/réparation/changement de clé à partir du XML généré par le runtime d’A4SWIFT et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. A4SWIFT fournit un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] modèle pour chaque FIN de message type (basé sur le schéma XSD d’A4SWIFT correspondant) afin que vous pouvez ouvrir les types de messages SWIFT FIN dans [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]. A4SWIFT fournit les fonctionnalités suivantes pour vous aider à la sécurité.  
  
## <a name="infopath-forms"></a>Formulaires InfoPath  
 Via le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms générés avec l’utilitaire FormGenerator fourni par A4SWIFT, les utilisateurs professionnels envoient et récupérer SWIFT vers et à partir des boîtes de réception des messages et des dossiers Windows SharePoint Services Web sécurisés mis en œuvre sur les boîtes d’envoi. [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]La sécurité du dossier Web fournie complètement par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] à l’aide des listes de contrôle d’accès (ACL) du système de fichiers [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et les fonctionnalités de sécurité Internet Information Services (IIS). Protection des données sur le câble » » entre [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] dossiers Web et [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] par Secure Sockets Layer (SSL) et HTTPS des protocoles de transport.  
  
 A4SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] les formulaires sont créés en tant que « non approuvé ». Cet état fournit le plus haut niveau de sécurité. Pour plus d’informations sur approuvés et non approuvés, consultez [sécurité InfoPath](../../adapters-and-accelerators/accelerator-swift/infopath-security.md).  
  
## <a name="runtime-service"></a>Service d’exécution  
 A4SWIFT fournit une exécution du service (implémenté en tant qu’une orchestration BizTalk) pour s’authentifier, valider, traiter et acheminer les messages SWIFT entre les dossiers SharePoint Web, les orchestrations de réparation / d’entrée de message, les systèmes back-end et enfin, pour les solutions SWIFT réseau. Ce service de runtime est appelé A4SWIFT Message Repair et New Submission.  
  
## <a name="secure-messages"></a>Sécuriser des Messages  
 Le stockage et la remise de SWIFT les messages échangés entre [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], et Message Repair et New Submission est sécurisé par les services sous-jacents ([!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], IIS, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]) et des protocoles (SSL, HTTPS) de transport. Toutefois, l’infrastructure de création, de réparation, réception et envoi de messages composées d’une réparation de Message et New Submission, [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], et [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] requièrent une sécurité au niveau utilisateur supplémentaire pour appliquer l’authenticité et la protection des messages SWIFT géré par les utilisateurs finaux.  
  
 A4SWIFT également définit et implémente la sémantique de sécurité au niveau de l’utilisateur pour vous assurer que les messages SWIFT modifiés et envoyées uniquement par la confiance des utilisateurs autorisés, et ces données de message ne sont pas modifiées ou falsifiées au cours des étapes de l’envoi asynchrones processus (par exemple, tandis que les messages sont assis dans un dossier SharePoint Web en attente de l’intervention de l’utilisateur). Coordonnées et précis sur la station de travail, les fonctionnalités de sécurité (via [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]) et serveur (via A4SWIFT Message Repair et New Submission) appliquer ces stratégies de sécurité au niveau de l’utilisateur.