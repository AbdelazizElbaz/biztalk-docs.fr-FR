---
title: "Étendre l’infrastructure de fournisseur de carte et le programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4d5e6f2-b3bc-46e2-b8f7-d7e271d4a8c0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6ab5caf03d113e313e00a74c11641058e86b886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-resolver-and-adapter-provider-framework"></a>Étendre l’infrastructure de fournisseur de carte et le programme de résolution
Le programme de résolution et l’infrastructure d’adaptateurs fournisseur prend en charge pour le point de terminaison et la résolution de la transformation et le routage, et elle peut également fournir des métadonnées personnalisées pour les services. L’infrastructure peut résoudre les points de terminaison et définir les propriétés de l’adaptateur de sortie dynamiquement. Après un programme de résolution composant résout un point de terminaison (par exemple, pour rechercher une URL sortante à l’aide de Universal Description, Discovery and Integration [UDDI]), un composant du fournisseur d’adaptateur définit des propriétés spécifiques des adaptateurs Microsoft BizTalk Server inscrits.  
  
 Il existe trois grands domaines où vous pouvez étendre l’infrastructure de fournisseur de carte et de programme de résolution :  
  
-   [Création d’un programme de résolution personnalisé](../esb-toolkit/creating-a-custom-resolver.md)  
  
-   [Création d’un programme de résolution personnalisé avec un conteneur Unity](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)  
  
-   [Création d’un fournisseur de l’adaptateur personnalisé](../esb-toolkit/creating-a-custom-adapter-provider.md)