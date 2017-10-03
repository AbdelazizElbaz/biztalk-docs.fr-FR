---
title: "La gestion des flux de données entrantes dans les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1b7c4f7-99ba-4bfa-89ab-1fabfe0845d1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20fc34da3a5c8e65f81cd6bbbb699f52506cdc6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-incoming-data-streams-in-pipeline-components"></a>Gestion des flux de données entrantes dans les composants de pipeline
Vous devez tenir compte des points suivants lorsque vous écrivez du code de désassembleur personnalisé pour les composants du pipeline dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="do-not-close-the-incoming-data-stream-in-custom-dissasember-code"></a>Ne fermez pas le flux de données entrantes dans le code de désassembleur personnalisé  
 Lorsque vous écrivez du code de désassembleur personnalisé pour les composants du pipeline dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous de ne pas fermer le flux de données entrantes dans ce code. Le flux de données entrantes du message d'entrée est une ressource partagée. Il est également utilisé par le composant de suivi du corps du message dans le moteur de messagerie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Si vous fermez de manière implicite ou explicite le flux de données entrant, vous risquez de perdre des données de suivi et de ne pas pouvoir observer les données de flux à l'aide du suivi des événements de messages et des instances de service dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="use-the-seek-method-of-the-stream-class-to-set-the-data-stream-pointer-to-the-start-of-the-stream"></a>Utilisez la méthode Seek de la classe Stream pour orienter le pointeur de flux sur le début du flux  
 Assurez-vous que la lecture du flux de données entrantes s'effectue jusqu'à la fin du flux. Par exemple, si le code personnalisé lance une requête de lecture pour 300 Ko de données et que le code ne reçoit que 34 Ko de données, ne pensez pas que la fin du flux a été atteinte. Le code personnalisé doit toujours lire le flux de données entrantes jusqu'à ce qu'il renvoie 0 octet.  
  
 Avant de renvoyer le flux de données dans la logique de composant personnalisée, paramétrez le pointeur de flux de données à nouveau sur le début du flux. Par exemple, le code suivant illustre la logique d'utilisation de la méthode Seek pour orienter le pointeur vers le début du flux avant de renvoyer ce dernier.  
  
```  
myDataStream.Seek(0, SeekOrigin.Begin);  
return myDataStream;  
```  
  
 Si vous ne procédez pas ainsi et que le flux est lu jusqu'à la fin dans le composant en cours, le composant suivant reçoit un flux qui paraît vide car le pointeur n'a pas été paramétré sur le début du flux. Ceci peut entraîner des erreurs d'analyse et de validation inattendues dans les composants de pipeline suivants.