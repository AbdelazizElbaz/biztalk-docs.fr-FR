---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaf39fd8-b662-4b0c-b5e8-1af02cb4f79b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a41a347534c07b522de5fc073933758870bf8a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-smtp-adapter"></a>Diagnostic des problèmes relatifs à l'adaptateur SMTP
Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur SMTP.  
  
### <a name="check-the-smtp-log-files-of-the-smtp-server-for-errors"></a>Recherche des erreurs dans les fichiers journaux SMTP du serveur SMTP  
  
-   Les fichiers journaux du serveur SMTP cible contiennent des informations qui peuvent s'avérer utiles pour résoudre les problèmes relatifs à l'adaptateur SMTP. Les fichiers journaux SMTP sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\SMTPSVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur SMTP.  
  
    > [!NOTE]
    >  La journalisation SMTP est désactivée par défaut sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]. Pour plus d'informations sur l'activation de la journalisation pour SMTP, consultez la documentation Windows Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Dépannage de l’adaptateur SMTP](../core/troubleshooting-the-smtp-adapter.md)