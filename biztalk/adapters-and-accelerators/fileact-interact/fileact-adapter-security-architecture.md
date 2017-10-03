---
title: "Architecture de sécurité de l’adaptateur FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faeebd6-5287-4ac4-a1db-e3c055d323d2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ed8352b788af12fd3c38f489e9ddb65d8375f2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-security-architecture"></a>Architecture de sécurité de l’adaptateur FileAct
Sécurité pour la transmission du fichier et la réception est implémentée via les fonctionnalités de certificat et de chiffrement inhérents aux SNL et les trous.  La gestion des certificats, etc., est complètement hors de portée de l’adaptateur FileAct. Tant que l’instance associée de SNL/trous est enregistrée pour le service FileAct avec SWIFT et le logiciel installé correctement sur SNL/trous, l’adaptateur utilise le fonctionnalités via les API SNL. L’adaptateur FileAct toujours la valeur du FACryptoMode sur « Avancé » (recommandé).  
  
> [!NOTE]
>  Pour la carte, vous pouvez créer un contexte de sécurité distincts pour chaque port d’envoi.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [État de l’adaptateur FileAct analyse](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)