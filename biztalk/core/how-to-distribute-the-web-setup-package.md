---
title: "Comment distribuer le Package d’installation Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, distributing
- Web services, deploying
ms.assetid: 0db71fdf-80d9-4ad5-b0d4-730d0bb549d4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed7e6277045593360cbdfe57848f7313054b60f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-distribute-the-web-setup-package"></a>Comment distribuer le Package d’installation Web
Après la création du package d'installation, vous devez créer un dossier de distribution dans lequel un fichier MSI et un fichier BindingInfo.xml sont copiés pour configurer le service Web.  
  
### <a name="to-distribute-the-web-setup-package"></a>Pour distribuer le package d'installation Web  
  
1.  Créez un dossier de distribution qui contiendra vos fichiers d'installation.  
  
2.  Copiez le fichier MSI du dossier de sortie du projet d'installation Web vers le dossier de distribution.  
  
3.  Copiez le fichier BindingInfo.xml du dossier temporaire du projet de service Web ASP.NET vers le dossier de distribution.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)