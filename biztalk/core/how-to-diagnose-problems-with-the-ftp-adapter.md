---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 499d23d3-b705-4527-9929-147be157e6b3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e66be2e498449b1cdcc70e05c6195ccd8e4395d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-ftp-adapter"></a>Diagnostic des problèmes relatifs à l'adaptateur FTP
Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur FTP.  
  
### <a name="check-the-ftp-log-files-on-the-ftp-server-for-errors"></a>Recherche des erreurs dans les fichiers journaux FTP du serveur FTP  
  
-   Les fichiers journaux du serveur FTP source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur FTP. Les fichiers journaux FTP d'un ordinateur Windows Server ou Windows XP se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\MSFTPSVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur FTP.  
  
### <a name="enable-logging-for-the-ftp-receive-location-or-send-port"></a>Activer l'enregistrement dans des fichiers journaux pour l'emplacement de réception ou le port d'envoi FTP  
  
-   Configurer le FTP emplacement de réception ou port d’envoi avec un **journal** dossier. L'adaptateur FTP y consignera des informations de journalisation détaillées. Le **journal** dossier option est disponible sur le **propriétés du Transport FTP** boîte de dialogue lors de la configuration d’un port de réception emplacement ou d’envoi avec le type de transport FTP.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)