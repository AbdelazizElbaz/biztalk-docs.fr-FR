---
title: "Comment capturer une image mémoire d’un processus qui ne répond pas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ad53376-2fab-4dee-8a6a-a44d157390f2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 520921010a8bbfd73de8c3b305a1270ca8363c46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive"></a>Capture de l'image mémoire d'un processus qui ne répond pas
Le processus BizTalk BTSNTSvc.exe est défini en tant que **négatif** lorsque le processus semble cesser de répondre. Les symptômes courants du blocage d'un processus sont les suivants :  
  
-   Les orchestrations semblent ne plus s'exécuter.  
  
-   Les messages ne sont pas traités.  
  
-   Des problèmes généraux de délai d'expiration apparaissent.  
  
-   Le processus BizTalk BTSNTSvc.exe consomme une quantité anormalement élevée de cycles de processeur tel qu’affiché dans le **processus** onglet de **le Gestionnaire des tâches**.  
  
 Pour capturer l'image mémoire d'un processus BTSNTSvc.exe bloqué, procédez comme suit.  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-hang-dump"></a>Pour configurer l’outil de diagnostic de débogage pour capturer un vidage de blocage  
  
1.  Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.  
  
2.  Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Configuration des règles s’affiche, cliquez sur le **Annuler** bouton.  
  
3.  Cliquez sur le **processus** onglet de l’outil de Diagnostic de débogage.  
  
4.  Cliquez avec le bouton droit sur le processus BTSNTSvc.exe qui ne répond pas et sélectionnez **créer une image utilisateur complète**. Par défaut, une image mémoire du processus sera enregistré dans le répertoire \Program Files\IIS Resources\DebugDiag\Logs\Misc de l'ordinateur local.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)