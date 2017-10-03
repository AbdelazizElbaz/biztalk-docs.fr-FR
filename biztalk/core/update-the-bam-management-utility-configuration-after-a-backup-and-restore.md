---
title: "Comment mettre à jour la Configuration après une sauvegarde et restauration de l’utilitaire BAM Management | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b27062b-546f-4030-983b-15d793912690
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf316e7275b3db47b02a7f09ed5d2a66571c4de1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-bam-management-utility-configuration-after-a-backup-and-restore"></a>Mise à jour de la configuration de l'utilitaire de gestion de l'analyse BAM après une sauvegarde et restauration
Lorsque la combinaison nom serveur\base de données change suite à une modification dans votre environnement BizTalk Server, par exemple une séquence de sauvegarde et restauration, vous devez mettre à jour le fichier de configuration de l'utilitaire de gestion de l'analyse BAM (bm.exe.config) afin de prendre en compte ces modifications de nom.  
  
### <a name="to-update-the-bam-management-configuration-file-a-after-backup-and-restore"></a>Pour mettre à jour le fichier de configuration de l'utilitaire de gestion de l'analyse BAM après une sauvegarde et restauration  
  
1.  Ouvrez le fichier bm.exe.config à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\bm.exe.config, puis en cliquant sur **OK**.  
  
2.  Recherchez la section appSettings dans le fichier et modifiez les valeurs suivantes :  
  
    ```  
    <!-- Default server and database for bm.exe. -->  
    <add key="DefaultServer" value="oldServerName" />  
    <add key="DefaultDatabase" value="BAMPrimaryImport" />  
    ```  
  
3.  to  
  
    ```  
    <!-- Default server and database for bm.exe. -->  
    <add key="DefaultServer" value="newServerName" />  
    <add key="DefaultDatabase" value="BAMPrimaryImport" />  
    ```  
  
4.  Enregistrez le fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données BAM](../core/managing-bam-databases.md)