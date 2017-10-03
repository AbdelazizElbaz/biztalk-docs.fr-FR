---
title: "Comment mettre à jour la chaîne de connexion pour le classeur de données actives | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d2702fb-637c-46db-8b62-08ae15f983ba
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60de5d1ae904bdefffcf490e3a39d000b28a341d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-connection-string-for-the-live-data-workbook"></a>Mise à jour de la chaîne de connexion pour le classeur de données actives
Lorsque vous déplacez la base de données d'importation principale BAM vers un autre serveur, vous devez mettre à jour la chaîne de connexion contenue dans le classeur de données actives BAM pour qu'elle pointe vers le nouveau serveur. Pour ce faire, vous pouvez utiliser le complément BAM pour Excel.  
  
### <a name="to-update-the-live-data-workbook-to-point-to-a-new-server"></a>Pour mettre à jour le classeur de données actives pour qu'il pointe vers le nouveau serveur  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.  
  
2.  Cliquez sur le **fichier** menu, puis sur **ouvrir**. Accédez à votre classeur de données actives BAM, puis cliquez sur **ouvrir**.  
  
3.  Cliquez sur le **BAM** menu dans le **compléments** onglet, puis cliquez sur **connexion DB BAM** pour ouvrir le **sélectionner la base de données BAM** boîte de dialogue.  
  
4.  Dans le **SQL Server** texte, tapez le nom du serveur SQL sur lequel l’importation principale BAM de base de données maintenant réside.  
  
5.  Sélectionnez la base de données d’importation principale BAM à partir de la **nom de la base de données** liste déroulante.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
7.  Enregistrez le classeur.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)   
 [Configuration requise pour utiliser le complément BAM pour Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md)