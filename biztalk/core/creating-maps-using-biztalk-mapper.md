---
title: "Création de mappages à l’aide du Mappeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, maps
- maps, creating
- orchestrations, maps
- translations [maps]
- maps, about maps
- transformations [maps]
- maps
ms.assetid: 265e61d8-8cff-44c9-a717-8e895cb4b9bf
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c12da6732729052119bfcc7841424db6d0dcaff9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-maps-using-biztalk-mapper"></a>Création de mappages à l'aide du Mappeur BizTalk
Le Mappeur BizTalk est un outil s'exécutant dans l'environnement Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Le Mappeur BizTalk peut servir à créer et modifier des mappages qui permettront de convertir ou de transformer des messages xml. Les mappages sont utilisés dans les orchestrations, comme le montre l'illustration suivante, et peuvent également être utilisés pour traiter les messages reçus sur le port d'envoi, puis pour transformer le message à envoyer via les ports de réception.  
  
 ![Diagramme de traitement entreprise avec mappages. ] (../core/media/ebiz-dev-busprcsg.gif "ebiz_dev_busprcsg")  
Mappages dans les processus d'entreprise  
  
 Les mappages vous permettent de convertir et de transformer des messages. La conversion consiste à convertir un message d'un format dans un autre, par exemple convertir un fichier plat en fichier XML. La transformation consiste à prendre les informations d'un message et à les placer dans un autre message. Par exemple, vous pouvez récupérer les adresses d'expédition et de facturation d'un bon de commande pour les insérer dans un document de facturation.  
  
 Le Mappeur BizTalk utilise son propre système graphique d'icônes et de liens pour représenter la conversion et la transformation des messages d'instance d'entrée en messages d'instance de sortie. Il utilise la même représentation graphique de schémas que l'Éditeur BizTalk. Le Mappeur BizTalk conserve ses mappages sous la forme de feuilles de style XSLT (Extensible Stylesheet Language Transformations).  
  
> [!NOTE]
>  Le Mappeur BizTalk prend en charge XSLT 1.0. Il ne prend pas en charge XSLT 2.0.  
  
 Pour plus d’informations sur la création de schémas, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md). Pour plus d’informations sur l’utilisation de mappages dans les orchestrations, consultez [création d’Orchestrations à l’aide de concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md).  
  
> [!NOTE]
>  Les performances d'un mappage dépendent de sa complexité (le nombre et le type de fonctoids, la taille des schémas d'entrée et de sortie), de la taille du message entrant et de votre configuration matérielle.  
  
 Pour plus d’informations sur l’utilisation des raccourcis clavier pour le Mappeur BizTalk, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Planification de la création de mappages](../core/planning-to-create-maps.md)  
  
-   [À propos des mappages](../core/about-maps.md)  
  
-   [À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md)  
  
-   [Création de mappages](../core/creating-maps.md)  
  
-   [La compilation et test des mappages](../core/compiling-and-testing-maps.md)  
  
-   [Résolution des problèmes de mappages](../core/troubleshooting-maps.md)