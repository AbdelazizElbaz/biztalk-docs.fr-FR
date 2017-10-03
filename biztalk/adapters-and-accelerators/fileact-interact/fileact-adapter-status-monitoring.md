---
title: "État de l’adaptateur FileAct surveillance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15833004-4276-4975-a0e7-8fff3c82576b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5b717a02631d47b864cc9180cba2fba673c5da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-status-monitoring"></a>État de l’adaptateur FileAct analyse
Les états possibles d’un transfert de fichiers et les transitions entre ces États sont illustrées dans la figure suivante.  
  
 ![États de transfert de fichier de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/media/2e01feaa-6b68-49a2-a47d-6359be1f4034.gif "2e01feaa-6b68-49a2-a47d-6359be1f4034")  
  
 Les États de transfert de fichier sont :  
  
-   **Lancé** : le client a envoyé le message de négociation pour le serveur, mais n’a pas encore reçu la réponse. Le serveur a reçu la demande de négociation mais n’a pas encore envoyé la réponse.  
  
-   **Accepté** : le serveur a accepté la demande et a envoyé la TransferAnswer dans le message de réponse et le transfert est toujours en cours.  
  
-   **Rejeté** : le serveur a rejeté la demande et a la TransferAnswer dans le message de réponse et le transfert s’est arrêté.  
  
-   **En cours** – le transfert est en cours d’exécution et qu’il est en cours (renouvelé régulièrement comme indiqué ci-dessus).  
  
-   **Terminé** – le transfert de fichiers est terminée en ce côté du transfert est concerné, y compris la comparaison de la valeur digest.  
  
-   **Échec de** – le transfert de fichiers a échoué en raison d’un accès aux données, le traitement, l’exception de communication ou de délai d’attente. (Remarque : délai d’attente est appliquée par SWIFTNet lien, et la valeur est déterminée par SWIFT).  
  
-   **Abandonnée** – le transfert de fichiers a été annulé (soit côté mon problème l’abandon).  
  
-   **Inconnu et en double** – cet état se produit uniquement en raison de la synchronisation. Dans le cas d’un expéditeur, le fichier doit être envoyé à nouveau la mention éventuellement dupliqué (PDIndicator). Dans le cas d’un récepteur, lorsque le PDIndicator implique que le fichier peut ont déjà reçu, l’adaptateur FileAct recherche la duplication et si trouvée, renvoie une TransferAnswer de dupliqués, ce qui mettra fin à la tentative en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)