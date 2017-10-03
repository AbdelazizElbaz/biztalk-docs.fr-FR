---
title: Comment nettoyer les ordinateur1 cible | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, removing
- send ports, removing
- cleaning target computer
ms.assetid: 78986a33-3c77-48dc-88c4-b78f52911c22
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7adf1761b6eb31ce158232c22af457b9c716a812
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-clean-the-target-computer"></a>Comment nettoyer l’ordinateur cible
Déploiement remplace la configuration d’emplacement de réception. Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  
  
### <a name="to-clean-the-target-computer"></a>Pour nettoyer l'ordinateur cible  
  
-   Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
     Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
         Par exemple, à une invite de commandes, exécutez :  
  
         **cscript RemoveSendPort.vbs \<nom du port d’envoi >**  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies1.md)