---
title: "Comment installer le Package d’installation Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
ms.assetid: c6b38a2f-ad07-4ccd-b267-9e3510df88c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21fbacd76598a3a86cfa70b4761bc74420afe561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-web-setup-package"></a>Comment installer le Package d’installation Web
Le contenu du dossier de distribution permet d'installer le service Web sur un ordinateur de destination.  
  
### <a name="to-install-the-web-setup-package"></a>Pour installer le package d'installation Web  
  
1.  Copiez le dossier de distribution sur l’ordinateur de destination.  
  
    > [!IMPORTANT]
    >  Le composant d'exécution BizTalk Server doit être installé sur l'ordinateur de destination et les assemblys BizTalk appropriés doivent être déployés et installés dans le Global Assembly Cache.  
  
2.  Exécutez le. Fichier MSI pour installer le service Web et suivez l’Assistant Installation vous invite à entrer.  
  
    > [!IMPORTANT]
    >  Supprimez le suffixe « _Setup » lorsque l’Assistant vous invite à entrer le répertoire virtuel. Supprimer le suffixe garantit que les adresses d’emplacement de réception correspondent aux fichiers .asmx de service Web.  
  
3.  Vérifiez que les paramètres de sécurité du répertoire virtuel sont appropriés pour l'autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)