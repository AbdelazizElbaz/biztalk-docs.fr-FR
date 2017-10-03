---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f06089a5-4747-4879-a796-157088868dba
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0481a3abdf497c093a87d7d74ea0356c7cad0d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-file-adapter"></a>Diagnostic des problèmes relatifs à l'adaptateur FILE
Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur FILE.  
  
### <a name="run-the-filemon-utility-to-diagnose-errors-that-occur-using-the-file-receive-or-file-send-adapter"></a>Exécutez l'utilitaire FileMon pour diagnostiquer les erreurs qui se produisent lors de l'utilisation des adaptateurs de réception et d'envoi FILE.  
  
1.  Téléchargez l’utilitaire FileMon à partir de [www.sysinternals.com](http://go.microsoft.com/fwlink/?LinkId=66235).  
  
2.  Installez l'utilitaire Filemon sur le serveur qui héberge le dossier ou le partage en cours de lecture ou d'écriture par l'adaptateur FILE.  
  
3.  Lancez l'utilitaire Filemon et appliquez un filtre pour surveiller uniquement les accès fichier effectués par l'instance BizTalk Host exécutant les gestionnaires d'adaptateur FILE (par exemple, BTSNTSvc.exe).  
  
4.  Reproduisez le scénario à l'origine du problème.  
  
5.  Désactivez la fonctionnalité de contrôle des fichiers de l'utilitaire Filemon, puis enregistrez le fichier journal généré sur le disque.  
  
6.  Vérifiez que le fichier journal généré ne contient pas d'erreurs.  
  
    > [!NOTE]
    >  Microsoft n'apporte aucune assistance relative à FileMon et ne garantit pas la pertinence de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Dépannage de l’adaptateur de fichier](../core/troubleshooting-the-file-adapter.md)