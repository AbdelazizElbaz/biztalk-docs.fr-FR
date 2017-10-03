---
title: "Installation de l’exemple de composant JMS MQRFH2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5bd855-512f-40a4-8038-ae9b847b1097
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b522d986524c77a53cf5a847f749a9ce41e2c50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-jms-mqrfh2-component-sample"></a>Installation de l’exemple de composant MQRFH2 JMS
Pour utiliser cet exemple avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], vous devez également installer les éléments suivants :  
  
-   IBM WebSphere MQ 5.3 (avec CSD12), WebSphere MQ 6.x ou WebSphere MQ 7.0  
  
-   Utilitaire pour les files d’attente et la récupération des messages de test de la « RfhUtil » JMS IBM  
  
 L’exemple de composant de MQRFH2 JMS requiert le composant JMS MQRFH2 doit résider dans le dossier PipelineComponents de votre dossier d’installation de Microsoft BizTalk Server et les schémas correspondants à résider dans le global assembly cache. L’installation de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core copie automatiquement et installe les assemblys dans les emplacements corrects. Toutefois, si nécessaire, vous pouvez effectuer ces tâches manuellement.  
  
 **Pour installer manuellement le composant de JMS MQRFH2 et des schémas**  
  
1.  Copiez l’assembly Microsoft.Practices.ESB.JMS.PipelineComponents.dll dans le dossier PipelineComponents de votre dossier d’installation de BizTalk Server.  
  
2.  Ajoutez l’assembly de schéma Microsoft.Practices.ESB.JMS.Schemas.Property.dll dans le global assembly cache à l’aide de l’outil de Configuration .NET Framework se trouve dans la section Outils d’administration de la **Démarrer** menu.  
  
 Cette section décrit le processus d’installation de l’exemple JMS MQRFH2 dans l’application BizTalk de GlobalBank.JMS. Avant d’installer cet exemple, vous devez installer le cœur de la boîte à outils ESB comme décrit dans [l’installation de BizTalk ESB Toolkit cœur](http://go.microsoft.com/fwlink/?LinkId=187612) ([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612)).  
  
 Vous pouvez installer l’exemple de composant de MQRFH2 JMS à partir du projet de la solution ou utilisez le fichier Windows Installer inclus avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Cette section contient les rubriques suivantes :  
  
-   [Installer l’exemple de MQRFH2 JMS à l’aide de Scripts d’installation](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)  
  
-   [Assemblys et artefacts installés par l’exemple de composant MQRFH2 JMS](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)  
  
-   [Testez l’Installation d’exemples de MQRFH2 JMS](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)