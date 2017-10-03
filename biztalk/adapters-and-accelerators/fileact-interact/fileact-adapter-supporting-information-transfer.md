---
title: "Le transfert des informations de prise en charge de l’adaptateur FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fc27561-9abb-4496-9db7-f221a6c90738
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5aefba5fe85a8a275d3b2050d8c08cc98f74d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-supporting-information-transfer"></a>Transfert des informations de prise en charge de l’adaptateur FileAct
L’adaptateur FileAct autorise le transfert facultatif de prendre en charge les informations des fichiers. Ces informations sont transférées à la discrétion de l’application. L’adaptateur ne tout traitement spécial de ces informations sur le côté d’origine, hormis pour vérifier qu’il est au format correct. Les éléments qui composent les informations de prise en charge sont les suivantes :  
  
-   Description du fichier et les informations de fichier  
  
-   Description de transfert et de transférer des informations  
  
-   Description de l’accusé de réception et les informations de l’accusé de réception  
  
-   Informations de description ou le refus de rejet  
  
> [!NOTE]
>  Un des composants d’informations de fichier définit la compression et la décompression. La compression et décompression sont la responsabilité de l’application, pas sur la carte.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [État de l’adaptateur FileAct analyse](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)