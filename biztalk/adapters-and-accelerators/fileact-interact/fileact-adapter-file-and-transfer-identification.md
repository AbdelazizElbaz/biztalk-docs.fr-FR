---
title: "Fichier de l’adaptateur FileAct et Identification de transfert | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a9aaff1-8816-42cf-b100-fedf964caaf5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5340f9ad739009ff1cb1257365ceeeb7459511a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-file-and-transfer-identification"></a>Fichier de l’adaptateur FileAct et Identification de transfert
L’adaptateur FileAct d’A4SWIFT permet au développeur de fournir le fichier et le transfert des caractéristiques d’identification lors de l’exécution. Ces paramètres sont les suivantes :  
  
-   **Nom de fichier physique** : le chemin d’accès complet et le nom du fichier en lecture ou en écriture. Ce paramètre n’est jamais passé et est local pour le composant Gestionnaire de fichiers.  
  
-   **Nom de fichier logique** : le nom de fichier passé à partir de l’application émettrice à l’application réceptrice sur SWIFTNet. Ce paramètre est facultatif et, si ne pas fourni, le nom de fichier physique sans le chemin d’accès est utilisé.  
  
-   **Point de terminaison de fichier transfert événement** : le nom spécifié dans l’événement s’abonner primitifs par l’application de gestion des événements de transfert de fichier. Ce paramètre, le transfert de fichiers est liée à l’application qui reçoit les événements de rapports.  
  
-   **Référence de transfert de fichiers** : une chaîne de jeton créé et utilisé par le sous-système de FileAct en tant que handle sur le transfert de lui-même. Il s’agit simplement une chaîne unique pour ce transfert, en ce qui concerne l’adaptateur FileAct.  
  
-   **Transfert de clé** – chaîne affectée par l’application pour identifier le transfert pour abandonner à des fins. Si non fourni par l’application, il est le GUID associé au fichier.  
  
-   **Transfert de Partition** – une chaîne utilisée pour lier plusieurs transferts. Si ne pas fournies dans les appels par le développeur, ceci est le « nom de l’Application « spécifié lors de la définition de l’envoi pertinentes ou emplacement de réception.  
  
-   **Référence de l’utilisateur** – une chaîne définie par l’application pour identifier de façon unique le transfert de non répudiation. Si non fourni par l’application, ce sera le GUID associé au fichier.  
  
-   **ID de message** : l’identificateur de définition de façon unique la demande initiale ou la réponse. Il s’agit de GUID associé à la demande appropriée ou le message de réponse, tel que généré par l’adaptateur d’envoi. Par conséquent, le client génère l’ID de Message pour les demandes et le serveur uniquement pour les réponses.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [État de l’adaptateur FileAct analyse](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)