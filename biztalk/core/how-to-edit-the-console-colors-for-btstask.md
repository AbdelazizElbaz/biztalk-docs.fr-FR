---
title: Comment modifier les couleurs de Console pour BTSTask | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725dcb7b-5a19-4166-9d1c-93f30ddca201
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d68529f01ab8131739d735ad82d804b41a9c021
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-edit-the-console-colors-for-btstask"></a>Modification des couleurs de la console pour l'outil BTSTask
Cette rubrique explique comment modifier les couleurs de premier plan utilisées pour l'affichage des données de BTSTask dans la console. Si l'arrière-plan de votre console est blanc, vous aurez des difficultés à lire les données de sortie BTSTask telles qu'elles s'affichent par défaut dans la console. Il se peut donc que vous deviez modifier les couleurs de premier plan de la console.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer la procédure de cette rubrique, vous devez disposer de droit en lecture et en écriture sur le fichier BTSTask.exe.config contenu dans le dossier d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-edit-the-console-foreground-colors-for-btstask"></a>Pour modifier les couleurs de premier plan de la console pour BTSTask  
  
1.  Sur l'ordinateur où vous souhaitez exécuter BTSTask, ouvrez le fichier BTSTask.exe.config dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], un éditeur de texte ou un éditeur XML. Ce fichier se trouve dans le dossier d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Modifiez les valeurs pour Console.ForegroundColor.Error, Console.ForegroundColor.Warning et Console.ForegroundColor.Info d'après les couleurs de premier plan souhaitées, respectivement, pour les messages d'erreur, les avertissements et les informations. Enregistrez ensuite le fichier. Pour une couleur de premier plan unique, au lieu de modifier toutes les valeurs, supprimez les entrées correspondantes.  
  
     Les valeurs disponibles pour les couleurs de premier plan sont les suivantes :  
  
     0 : noir  
  
     1 : DarkBlue  
  
     2 : printanier  
  
     3 : DarkCyan  
  
     4 : DarkRed  
  
     5 : DarkMagenta  
  
     6 : DarkYellow  
  
     7 : gris  
  
     8 : gris foncé  
  
     9 : bleu  
  
     10 : vert  
  
     11 : cyan  
  
     12 : rouge  
  
     13 : magenta  
  
     14 : jaune  
  
     15 : blanc  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)