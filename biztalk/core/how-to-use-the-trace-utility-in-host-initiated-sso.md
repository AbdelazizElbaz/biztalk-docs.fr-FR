---
title: "L’authentification initiée par l’utilisation de l’utilitaire de suivi dans l’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, trace utility
- trace utility
ms.assetid: a53444d1-3f63-42a6-8ee6-b60ff9af9e41
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e00514515b31e79655fe457e1aa8682edf002183
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-trace-utility-in-host-initiated-sso"></a>L’authentification initiée par l’utilisation de l’utilitaire de suivi dans l’hôte
La principale méthode de résolution des problèmes est le suivi.  
  
## <a name="tracing"></a>Suivi  
 Utilisez l'utilitaire de ligne de commande Suivi pour activer le suivi de l'authentification unique.  
  
> [!NOTE]
>  Pour que la commande de suivi fonctionne, le fichier tracelog.exe doivent être dans le répertoire suivant :  
>   
>  \<*lecteur*> : \Program Files\Enterprise Single Sign-On  
  
> [!NOTE]
>  Vous pouvez télécharger ce fichier à partir de l’emplacement suivant : [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)  
  
#### <a name="to-use-the-trace-utility"></a>Pour utiliser l'utilitaire de suivi  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **Trace – start – high** pour définir le niveau de suivi élevé et lancer le suivi.  
  
5.  Exécutez le scénario avec une authentification unique initiée par l'hôte.  
  
6.  Type **Trace – stop** à la fin de la trace. Un fichier .bin est généré dans le répertoire ci-dessus, que vous pouvez envoyer à Microsoft à des fins d'analyse.  
  
## <a name="see-also"></a>Voir aussi  
 [L’authentification unique initiée par l’hôte](../core/host-initiated-sso.md)