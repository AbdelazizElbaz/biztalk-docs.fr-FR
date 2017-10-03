---
title: "Résolution des problèmes de la Adapter3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards OneWorld adapters], connecting [Oracle databases]
- JD Edwards OneWorld adapters, troubleshooting
- troubleshooting [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], troubleshooting
- Oracle databases, connecting [JD Edwards OneWorld adapters]
ms.assetid: 2dd6a951-f113-4f43-b43f-057a239d05c4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15197bcdc84e813d31a8d5292f5559aca1f8ae01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a>Dépannage de l’adaptateur
Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld.  
  
## <a name="cannot-use-wildcards-in-send-and-receive-port-properties"></a>Impossible d'utiliser des caractères génériques dans les propriétés de port d'envoi et de réception  
 L'adaptateur pour JD Edwards OneWorld ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés suivants :  
  
|Propriété de port d'envoi|Propriété de port de réception|  
|------------------------|---------------------------|  
|Utilisateur|Chemin d'accès à l'événement|  
|Environnement JDE|Préfixe du nom de la cible d'événement|  
|Hôte||  
|Port||  
|Java_Home||  
|Fichiers JAR JDE||  
  
## <a name="connecting-to-oracle-database"></a>Connexion à la base de données Oracle  
 Lorsque vous utilisez une base de données Oracle avec JD Edwards, vous devez modifier le fichier jdeinterop.ini. À l'aide de l'authentification unique, la section [JDBj-ORACLE] définit l'emplacement Oracle tnsnames. Le paramètre de base de données doit être utilisé, et le fichier SQLNET.ORA doit être présent sur l'ordinateur BizTalk Server (inclus avec le client Oracle).  
  
 Ajoutez le code suivant au fichier jdeinterop.ini :  
  
1.  Sous [JDBj-ORACLE], tapez :  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  Sous [JDBj-BOOTSTRAP DATA SOURCE], tapez :  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des Ports d’envoi pour JD Edwards OneWorld](../core/how-to-create-send-ports-for-jd-edwards-oneworld.md)   
 [Résolution des problèmes de JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)