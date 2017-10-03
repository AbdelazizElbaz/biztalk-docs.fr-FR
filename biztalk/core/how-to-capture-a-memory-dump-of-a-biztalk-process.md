---
title: "Comment capturer une image mémoire d’un processus BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8053fcf3-b331-4245-b3c3-21290463e0c0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87ad0f4a3eb3a49ea789d45a707bbc8b46cb4c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-biztalk-process"></a>Capture de l'image mémoire d'un processus BizTalk
Dans certaines circonstances, il peut être nécessaire de capturer l'image mémoire d'un processus exécuté sur un serveur BizTalk Server afin d'effectuer une analyse approfondie du processus. Les situations qui peuvent nécessiter l'analyse d'une image mémoire sont les suivantes :  
  
-   Un processus ne répond pas.  
  
-   Un processus se bloque.  
  
-   Un processus subit des fuites de mémoire.  
  
 Cette section inclut les étapes à suivre pour capturer le type approprié d'image mémoire.  
  
## <a name="installation-of-the-iis-diagnostics-toolkit"></a>Installation de l'ensemble d'outils de diagnostic IIS  
 Chacune des rubriques de cette section nécessite l’utilisation de la **outil** de la boîte à outils de diagnostic IIS pour capturer un vidage de mémoire. Pour installer le **outil** de la boîte à outils de diagnostic IIS, procédez comme suit :  
  
1.  Télécharger les outils de diagnostic IIS depuis [Internet Information Services des outils de Diagnostic](http://go.microsoft.com/fwlink/?LinkId=64426).  
  
2.  Double-cliquez sur le **iisdiag.msi** package pour lancer le programme d’installation de IIS Diagnostics Toolkit et choisir le **personnalisé** type d’installation.  
  
3.  Dans le **installation personnalisée** boîte de dialogue, assurez-vous que l’option pour le **outil de débogage Diagnostics 1.0** est activée et suivez les étapes décrites dans le programme d’installation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment capturer une image mémoire d’un processus qui ne répond pas](../core/how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive.md)  
  
-   [Comment capturer une image mémoire d’un processus bloqué](../core/how-to-capture-a-memory-dump-of-a-process-that-is-crashing.md)  
  
-   [Comment capturer une image mémoire d’un processus qui est une fuite de mémoire](../core/how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory.md)  
  
-   [L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)