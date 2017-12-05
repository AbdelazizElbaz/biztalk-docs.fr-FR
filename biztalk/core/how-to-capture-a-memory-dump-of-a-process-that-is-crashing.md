---
title: "Comment capturer une image mémoire d’un processus bloqué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f436b72-2b6a-4519-acc3-e7ba978651fe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e87664180b7ad4d5fdcd121542974a08b8634d55
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-crashing"></a>Capture de l'image mémoire d'un processus bloqué
Le processus BizTalk BTSNTSvc.exe est défini en tant que **bloqué** lorsque le processus est arrêté inopinément par Windows. Un blocage est généralement le résultat d'une exception non gérée dans le processus, comme une violation d'accès ou un dépassement de capacité de pile. Dans ces situations, les fenêtres par défaut du débogueur, récupération d’urgence. Watson (drwtsn32.exe) intercepte l’exception et met fin au processus.  
  
 Pour capturer l'image mémoire d'un processus bloqué, configurez l'outil de diagnostic de débogage de sorte qu'il intercepte l'exception non gérée en procédant comme suit :  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-crash-dump"></a>Pour configurer l'outil de diagnostic de débogage afin de capturer l'image d'un processus bloqué  
  
1.  Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.  
  
2.  Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Ajout de règle n’est pas affichée, cliquez sur le **outils** menu, sélectionnez **les Actions de règle**, puis cliquez sur **ajouter une règle**pour afficher l’Assistant Ajout de règle.  
  
3.  Sélectionnez le **Crash** option dans le **sélectionner le Type de règle** boîte de dialogue et cliquez sur **suivant**.  
  
4.  Sélectionnez **un processus spécifique** dans les **sélectionner le Type de cible** boîte de dialogue et cliquez sur **suivant**.  
  
5.  Sélectionnez le processus BTSNTSvc.exe bloqué et cliquez sur **suivant**.  
  
6.  Dans le **Configuration avancée** boîte de dialogue cliquez **suivant** pour accepter les valeurs par défaut.  
  
7.  Dans le **sélectionnez Vider emplacement et nom de la règle** boîte de dialogue cliquez **suivant** pour accepter les valeurs par défaut.  
  
8.  Dans le **règle terminée** boîte de dialogue cliquez **Terminer** pour accepter la valeur par défaut de **activer la règle maintenant**.  
  
9. Par défaut, une image mémoire du processus sera enregistrée à la Files\IIS Resources\DebugDiag\Logs\\<*nom de la règle d’arrêt* \> répertoire de l’ordinateur local la prochaine fois qu’un exception non gérée se produit dans le processus.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)