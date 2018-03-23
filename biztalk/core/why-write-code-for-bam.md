---
title: Pourquoi écrire du code pour l'analyse BAM ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4434f50a-e0a9-45e0-8c68-a059011e1296
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10b8ccb29d95daf8ccdf80d67faef3e50495af04
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="why-write-code-for-bam"></a>Pourquoi écrire du code pour l'analyse BAM ?
Dans la plupart des cas, vous pouvez utiliser les outils BAM suivants sans qu'il soit nécessaire d'écrire votre propre code pour réaliser les fonctions de suivi : complément BAM pour Excel, utilitaire de gestion de l'analyse BAM et l'Éditeur de modèle de suivi (TPE). L'analyse BAM de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit les intercepteurs pour les orchestrations BizTalk et les composants de messagerie (pipelines et ports). Un intercepteur est un logiciel qui instrumente une application de sorte qu'elle puisse collecter les données de façon générique en fonction d'un fichier de configuration. Pour que votre application utilise ces intercepteurs, vous pouvez vous servir de l'Éditeur de modèle de suivi. Pour plus d’informations sur l’éditeur de modèle de suivi, consultez [éditeur](../core/tracking-profile-editor.md).  
  
 Il existe toutefois deux principales situations pour lesquelles vous trouverez plus pratique d'instrumenter votre application à l'aide des API de l'analyse BAM :  
  
-   lorsqu'il n'existe aucun intercepteur BAM pour l'hôte à analyser ;  
  
-   lorsque l'intercepteur intégré n'est pas compatible avec la complexité de votre application.  
  
 Lorsqu’il n’existe aucun intercepteur intégré, vous pouvez utiliser l’analyse BAM **EventStream** API pour capturer les événements d’intérêt.  
  
> [!NOTE]
>  Vous pouvez combiner **EventStream** classes avec la **BAMInterceptor** classe pour créer votre propre intercepteur. L'exemple du kit de développement logiciel (SDK) API BAM illustre un intercepteur générique qu'il est possible d'étendre. La création de votre propre intercepteur vous permet d'instrumenter un certain nombre de processus similaires sans avoir à écrire un nouveau code pour chaque application. Pour afficher l’exemple du SDK API BAM, consultez [l’API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de Solutions BAM](../core/implementing-bam-solutions.md)