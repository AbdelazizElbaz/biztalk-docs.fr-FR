---
title: "L’utilisation de diagnostic de débogage pour analyser une image mémoire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986a91a7-feab-4014-bbd5-e8b966b8b841
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccc0faf72c9123ab7a501af8520f273e8c528b8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-debug-diagnostics-to-analyze-a-memory-dump"></a>Analyse d'une image mémoire à l'aide de l'outil de diagnostic de débogage
Les tests de diagnostic IIS **outil** inclut une fonctionnalité qui peut fournir une analyse de base d’un fichier de vidage mémoire capturé. Pour procéder à l'analyse d'un fichier d'image mémoire, procédez comme suit :  
  
### <a name="to-analyze-the-dump-file"></a>Pour analyser un fichier d'image mémoire  
  
1.  Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**,  **L’outil Diagnostics 1.0 de débogage**.  
  
2.  Cliquez sur le **analyse avancée** onglet.  
  
3.  Sous **Scripts d’analyse disponibles** sélectionnez **analyseurs d’incident/blocage** pour analyser un fichier de vidage sur incident/blocage ou sélectionnez **l’analyse de la sollicitation de la mémoire** pour analyser une mémoire image d’un processus suspecté de manquer de mémoire.  
  
4.  Cliquez sur le **ajouter des fichiers de données** bouton pour rechercher le fichier généré et cliquez sur le **ouvrir** pour ajouter le fichier de vidage à la liste des fichiers de données à analyser.  
  
5.  Cliquez sur le fichier d'image mémoire que vous venez d'ajouter.  
  
6.  Cliquez sur le **démarrer l’analyse** bouton.  
  
    > [!NOTE]
    >  L'analyseur tente de localiser et de télécharger les fichiers de symbole appropriés sur Internet s'ils ne sont pas installés sur l'ordinateur local. Si le code personnalisé est en cours d’exécution dans le processus BTSNTSvc.exe, mettez à jour le **chemin d’accès de recherche de symbole de débogage** option disponible dans le **chemins de recherche et de dossier** onglet de la **Options & Paramètres** boîte de dialogue pour inclure les fichiers de symboles appropriés. Cliquez sur le **outils** menu et sélectionnez **les paramètres et Options** pour afficher les **Options et paramètres** boîte de dialogue.  
  
7.  Une fois l'analyse terminée, un rapport est généré au format de fichier .mht et s'affiche dans Internet Explorer. Par défaut, ce rapport est enregistré dans le répertoire \Program Files\IIS Resources\DebugDiag\Reports de l'ordinateur local.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment capturer une image mémoire d’un processus BizTalk](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)