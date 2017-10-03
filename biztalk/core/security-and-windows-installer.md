---
title: "Sécurité et le programme d’installation Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows installer
- Windows installer
ms.assetid: efa68c3e-2006-4665-bd41-07defaf4e2e2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4418994a4b5ff705d1faef751ac8c96ba86f9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-and-windows-installer"></a>Sécurité et Windows Installer
Windows Installer est un outil puissant permettant d'installer et de mettre à jour des applications BizTalk. Lorsque vous l'utilisez, vous devez connaître les problèmes de sécurité posés par certains créateurs de fichiers Windows Installer (.msi) malveillants afin de savoir les éviter.  
  
 Ce sont les administrateurs qui exécutent généralement les fichiers .msi. Par conséquent, les processus exécutés au cours de l'installation ou de la mise à jour d'une application sont associés à des privilèges très élevés. Un créateur de fichiers .msi malveillant peut donc exploiter ce fait de plusieurs façons et notamment :  
  
-   Exécuter des fichiers de script apportant des changements non souhaités à votre système ou vos fichiers.  
  
-   Écraser le catalogue COM.  
  
-   Écraser les valeurs du registre. Ces modifications ne peuvent pas être restaurées.  
  
-   Inonder le système de fichiers.  
  
 Lorsque vous manipulez des fichiers .msi, vous devez, au minimum, prendre les précautions suivantes :  
  
-   Installer uniquement des fichiers .msi approuvés.  
  
    > [!NOTE]
    >  Il est conseillé aux personnes chargées de générer des fichiers .msi de prendre des mesures supplémentaires pour signer les fichiers .msi afin que les utilisateurs puissent vérifier que leur source est approuvée.  
  
-   Tester minutieusement les fichiers .msi avant de les utiliser dans un environnement de production.  
  
-   Stocker les fichiers .msi dans des dossiers protégés, sécurisés par les listes de contrôle d'accès discrétionnaires (DACL) appropriées.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité pour le déploiement d’Application](../core/security-considerations-for-application-deployment.md)