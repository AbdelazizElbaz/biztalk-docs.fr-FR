---
title: "Comment capturer une image mémoire d’un processus qui est une fuite de mémoire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67404919-33a6-40ac-b1c4-09841db12fcf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2999ce9a188b2d9b94df11328485e8b7440ecec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory"></a>Capture de l'image mémoire d'un processus subissant des fuites de mémoire
On considère que le processus BizTalk BTSNTSvc.exe subit une fuite de mémoire lorsqu'il ne parvient pas à libérer la mémoire dont il n'a plus besoin, ce qui entraîne avec le temps une réduction de la quantité de mémoire disponible. L’utilisation de la mémoire du processus peut être déterminée en consultant la valeur sous la **util** colonne de la **processus** onglet disponible dans **le Gestionnaire des tâches**. Si le processus continue à consommer de la mémoire dans le temps sans la libérer, les performances globales du système en seront affectées.  
  
 Cette rubrique contient les instructions permettant de capturer l'image mémoire d'un processus BizTalk suspecté de subir des fuites de mémoire, à l'aide d'une règle ou par une capture manuelle de l'image mémoire. Utilisez la méthode de capture manuelle de l'image mémoire si l'occurrence de la fuite de mémoire n'est pas prévisible.  
  
### <a name="to-capture-a-memory-dump-of-a-process-that-is-leaking-memory-by-using-a-rule"></a>Pour capturer l'image mémoire d'un processus subissant des fuites de mémoire à l'aide d'une règle  
  
1.  Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.  
  
2.  Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Ajout de règle n’est pas affichée, cliquez sur le **outils** menu, sélectionnez **les Actions de règle**, puis cliquez sur **ajouter une règle**pour afficher l’Assistant Ajout de règle.  
  
3.  Sélectionnez le **fuite de mémoire et de mémoire** option dans le **sélectionner le Type de règle** boîte de dialogue et cliquez sur **suivant**.  
  
4.  Sélectionnez le processus BTSNTSvc.exe suspecté de subir des fuites de mémoire et cliquez sur **suivant**.  
  
5.  Dans le **configurer la durée du suivi** boîte de dialogue comme suit :  
  
    1.  Si la croissance de mémoire se produit immédiatement, cochez l’option **démarrer le suivi immédiatement lorsque la règle est activée**. Si la croissance de mémoire ne se produit pas immédiatement, spécifiez un nombre approprié de minutes dans le **mise en route** démarre après laquelle le suivi de zone de texte.  
  
        > [!NOTE]
        >  Le croissance de la mémoire pour le processus peut ne pas être immédiatement observable si la fuite de mémoire n'intervient qu'avec le chargement d'un composant particulier dans la mémoire, par exemple si une orchestration BizTalk fait référence à un composant externe.  
  
    2.  Spécifiez un nombre approprié de minutes dans le **le suivi des** zone de texte après laquelle le suivi sera arrêté. Ce nombre de minutes doit être suffisamment élevé pour permettre la reproduction de la fuite de mémoire. Une image mémoire du processus sera capturée à l'issue de ce délai.  
  
    3.  Cochez l’option **créer automatiquement un incident de règle pour obtenir une image utilisateur sur la sortie inattendue du processus**.  
  
    4.  Cliquez sur **Suivant**.  
  
6.  Dans le **sélectionnez Vider emplacement et nom de la règle** boîte de dialogue cliquez **suivant** pour accepter les valeurs par défaut.  
  
7.  Dans le **règle terminée** boîte de dialogue cliquez **Terminer** pour accepter la valeur par défaut de **activer la règle maintenant**.  
  
8.  Par défaut, une image mémoire du processus sera enregistrée à la Files\IIS Resources\DebugDiag\Logs\\<*nom de règle de blocage*> répertoire de l’ordinateur local après les intervalles de temps spécifié dans le **configurer la durée du suivi** boîte de dialogue s’est écoulé.  
  
### <a name="to-manually-capture-a-memory-dump-of-a-process-that-is-leaking-memory"></a>Pour capturer manuellement l'image mémoire d'un processus subissant des fuites de mémoire  
  
1.  Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.  
  
2.  Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Ajout de règle s’affiche, cliquez sur **Annuler**.  
  
3.  Cliquez pour sélectionner le **processus** onglet de l’outil de Diagnostic de débogage.  
  
4.  Cliquez sur le processus BTSNTSvc.exe suspecté de subir des fuites de mémoire et cliquez sur **surveiller les fuites**.  
  
5.  Surveiller l’utilisation de la mémoire du processus dans **le Gestionnaire des tâches** et lors de l’utilisation de la mémoire du processus est proche de 60-80 % de la mémoire disponible sur l’ordinateur BizTalk ; capturer manuellement une image mémoire du processus en cliquant sur le processus et en sélectionnant l’option à **créer une image utilisateur complète**.  
  
6.  Par défaut, une image mémoire du processus sera enregistré dans le répertoire \Program Files\IIS Resources\DebugDiag\Logs\Misc\ de l'ordinateur local.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)