---
title: "Primitives de bout en bout FileAct adaptateur en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8591120-7259-49cb-90ac-954d8be226ed
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c95e52d4fbd5ec0df8ee580583f429ffe9e0f08d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-real-time-end-to-end-primitives"></a>Primitives de bout en bout FileAct adaptateur en temps réel
SWIFTNet primitives sont une paire de documents XML échangés entre l’application et le lien SWIFTNet (SNL). Pour chaque là de primitive, de bout en bout côté sont deux versions de la primitive – un situé sur le côté client (ou envoi) et l’autre au niveau du serveur (ou de réception). Cela comprend un total de quatre messages : primitive de placer le fichier et une remise envoyer une Notification pour chaque primitive d’obtenir le fichier.  
  
 La figure suivante illustre les primitives de bout en bout FileAct.  
  
 ![FileAct fin &#45; à &#45; les primitives de bout](../../adapters-and-accelerators/fileact-interact/media/6e3520cc-9ec4-445c-9114-c7cb760c1068.gif "6e3520cc-9ec4-445c-9114-c7cb760c1068")  
  
## <a name="put-file"></a>Placez le fichier  
 Une application lance la primitive de placer un fichier pour envoyer un fichier dans le système de fichiers d’un autre utilisateur SWIFTNet. Comme une fonction de bout en bout, il sont des primitives de placer le fichier côté côté client et serveur. Ces collaborent pour effectuer un transfert de fichiers.  
  
 Chaque telle collaboration envoie un seul fichier. Plusieurs primitives de placer le fichier peuvent être exercées en parallèle.  
  
## <a name="get-file"></a>Obtention du fichier  
 Une application lance la primitive Get File pour extraire un fichier du système de fichiers d’un autre utilisateur SWIFTNet. Comme une fonction de bout en bout, il existe des primitives d’obtenir le fichier côté client et côté serveur. Ces collaborent pour effectuer un transfert de fichiers.  
  
 Chaque telle collaboration récupère un seul fichier. Plusieurs primitives d’obtenir le fichier peuvent être exercées en parallèle.  
  
## <a name="send-delivery-notification"></a>Envoyer une Notification de remise  
 Chaque fichier Put et chaque fichier obtenir primitif a la possibilité de l’envoi de la demande de fichier du côté réception renvoyer un accusé de réception associé pour le transfert de fichiers. Pour une primitive de placer le fichier, le message de demande contient la demande pour un accusé de réception.  
  
 Dans le cas d’un Get File primitifs, le message de réponse contient la demande pour un accusé de réception.  
  
 Dans les deux cas, après vérification que le fichier a été reçu dans son intégralité (en exerçant une des primitives de l’état pour vérifier que le transfert atteint l’état terminé) et que le fichier a été correctement sécurisé stockées (par exemple, sur un système back-office), le application de réception exerce séparément la primitive de l’accusé de réception pour retourner une confirmation positive de remise à l’expéditeur. Comme une fonction de bout en bout, il existe des primitives accusé de réception à la fois côté client et côté serveur. Ils collaborent pour mener à bien une notification de remise de fichier.  
  
 Accusé de réception exige le Générateur de service établir et conserver un protocole entre les expéditeurs et les récepteurs de fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [État de l’adaptateur FileAct analyse](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)