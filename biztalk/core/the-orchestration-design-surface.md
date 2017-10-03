---
title: "L’aire de conception d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5fb190b-60d7-45e4-9883-7b3d2ed6b0c0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f943c1543cf50e4ecb1f25627cbccd7b4d72eab5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-orchestration-design-surface"></a>La surface de conception de l'orchestration
La surface de conception de l'orchestration est un concepteur visuel que vous pouvez utiliser pour créer une orchestration BizTalk. Elle constitue également un composant essentiel de Concepteur d'Orchestration. On peut le comparer à un canevas dans lequel vous pouvez glisser des formes de la Boîte à outils avant de les configurer. En tant que fenêtre d'éditeur Visual Studio, il occupe la principale zone de fenêtre utilisée par les autres fenêtres d'éditeur Visual Studio.  
  
 ![Concepteurs d’orchestration](../core/media/b96c16e5-58a2-4d8e-b66c-485864846cec.gif "b96c16e5-58a2-4d8e-b66c-485864846cec")  
Surface de conception de l'orchestration  
  
 Le nom de l'orchestration est affiché sur l'onglet supérieur de la fenêtre de la surface de conception de l'orchestration ainsi que dans la barre de titre de la fenêtre Visual Studio.  
  
 L’aire de conception elle-même est divisé en trois zones : la zone de processus et deux Surfaces du Port. La zone de processus centrale contient des formes qui décrivent le flux du processus proprement dit de l'orchestration.  Il est flanked des deux côtés par Surfaces du Port, qui contiennent des formes Port et le lien de rôle uniquement interagissant avec le **envoyer** et **réception** formes dans la zone de processus.  
  
 **Zone de processus**  
  
 La zone de processus est la partie principale de la surface de conception de l'orchestration du Concepteur d'Orchestration, elle y est toujours centrée horizontalement.  
  
 Des deux côtés de la zone de processus apparaissent les surfaces du port. Le **commencer** forme est placée en haut de l’aire de conception et de l’orchestration se développe vers le bas lorsque vous ajoutez des formes.  
  
 **Surfaces du port**  
  
 Deux surfaces du port sont affichées dans la surface de conception de l'orchestration, une de chaque côté de la zone de processus. Les Surfaces de port peuvent contenir deux types de formes : **Ports** et **des liens de rôle**. Ces formes interagissent avec le **envoyer** et **réception** formes dans la zone de processus.  
  
 Les surfaces du port peuvent être utilisées indifféremment avec les formes : ces dernières fonctionnent de manière identique que ce soit dans la surface du port de droite ou dans la surface du port de gauche. Avoir deux surfaces du port sur lesquelles placer de nouveaux ports vous permet de créer des orchestrations en entrecroisant moins les connecteurs, qui s'en trouvent alors plus lisibles.  
  
 Pour réduire ou développer les surfaces du port, il suffit de cliquer dessus ou de cliquer sur l'icône de double flèche.  
  
> [!IMPORTANT]
>  De nombreuses tâches du Concepteur d'Orchestration requièrent que vous sélectionniez divers éléments tels que des schémas ou des orchestrations. Si ces éléments ne figurent pas dans le projet actuel, vous devez vous rappeler d'ajouter à votre projet une référence à l'assembly qui contient l'élément que vous désirez sélectionner. Pour ce faire, cliquez sur le projet et sélectionnez **ajouter une référence**.  
  
 **Prise en charge du zoom**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'effectuer des zooms avant ou arrière sur la surface de conception de l'orchestration. Vous pouvez tirer parti de la prise en charge du zoom en suivant l'une des étapes suivantes :  
  
-   Cliquez sur l’aire du Concepteur d’Orchestration, sur le **Zoom** option de menu. Vous pouvez ensuite sélectionner le pourcentage d'agrandissement que vous désirez appliquer.  
  
-   Utilisez la touche CTRL et la roulette de la souris pour effectuer des zooms avant ou arrière : pour cela, maintenez la touche CTRL enfoncée tout en tournant la roulette vers le haut ou le bas. Tournez vers le haut pour réaliser un zoom arrière et tournez vers le bas pour réaliser un zoom avant.