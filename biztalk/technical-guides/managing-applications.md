---
title: Gestion des Applications | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef1039fb-7460-444b-a45e-2783bdc7c109
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52e525499671a04228763c6792961c3204a3a2d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-applications"></a>Gestion des applications
Une application BizTalk est un conteneur logique d’artefacts de l’application, telles que les orchestrations, pipelines, schémas, mappages et les ports. Applications BizTalk permettent d’inclure des composants associés dans le même conteneur. Tout artefact d’une application peut faire référence à d’autres artefacts de cette application, ou à n’importe quel objet dans n’importe quelle application référencée. Pour obtenir une liste complète des artefacts qui peuvent être dans une application BizTalk, consultez [qu’est une Application BizTalk ?](http://go.microsoft.com/fwlink/?LinkId=154994) (http://go.microsoft.com/fwlink/?LinkId=154994).  
  
 Tous les jours de rationalisent les applications BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tâches. Vous pouvez déployer, gérer, Démarrer, arrêter et résoudre les problèmes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au niveau de l’application. Il en résulte dans sans confusion et moins de risque d’erreur pour les utilisateurs. Un conteneur d’application BizTalk contient  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]assemblys qui sont déployées par l’environnement Visual Studio. L’application peut également contenir des ports de réception, emplacements de réception, ports d’envoi, les paramètres de suivi de propriété et des liens de rôle. Vous pouvez ajouter manuellement des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] l’application, ou le déplacement des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys à partir d’autres applications. En outre, vous pouvez ajouter non -[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artefacts tels que les stratégies du moteur de règles d’entreprise (BRE) et les fichiers de définition BAM. Implicitement, l’application contient également toutes les liaisons sont représentées par leurs paramètres actuels.  
  
 Vous pouvez créer des ou des scripts de post-traitement à effectuer des actions lorsqu’une application est importée, installée ou désinstallée. Pour plus d’informations sur l’utilisation de ces scripts, consultez [à l’aide de Scripts de pré-traitement et post-traitement au déploiement d’Application personnaliser](http://go.microsoft.com/fwlink/?LinkId=154995) (http://go.microsoft.com/fwlink/?LinkId=154995).  
  
 Cette section décrit comment déployer, version et mettre à jour des applications et autres artefacts.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Déploiement d’une Application](../technical-guides/deploying-an-application.md)  
  
-   [Mise à jour d’une Application](../technical-guides/updating-an-application.md)