---
title: "Procédure d’ouverture, enregistrement, fermeture et renommage des mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aa88ca7-a731-4295-8692-6dd36fdf0872
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bad04c72e4c3f0caf1af8e223d3f17e4687b736
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-open-save-close-and-rename-maps"></a>Ouverture, enregistrement, fermeture et renommage des mappages
Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les mappages sont des fichiers du système de fichiers dotés de l'extension .btm. Toutefois, il est beaucoup plus courant de travailler avec les mappages en tant qu'éléments d'un projet BizTalk à partir desquels vous effectuez des opérations comme ouvrir, enregistrer et fermer des mappages.  
  
### <a name="to-open-a-map"></a>Pour ouvrir un mappage  
  
1.  Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez ouvrir.  
  
2.  Sur le **vue** menu, cliquez sur **ouvrir**.  
  
     Le mappage s'ouvre dans le Mappeur BizTalk.  
  
    > [!NOTE]
    >  Vous pouvez également avec le bouton droit de la carte dans l’Explorateur de solutions, puis cliquez sur **ouvrir**, ou double-cliquez simplement sur la carte dans l’Explorateur de solutions.  
  
### <a name="to-save-a-map"></a>Pour enregistrer un mappage  
  
1.  Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez enregistrer.  
  
2.  Sur le **fichier** menu, cliquez sur **enregistrer  *\<nom de la carte >***.  
  
### <a name="to-save-a-map-to-a-new-location"></a>Pour enregistrer un mappage à un nouvel emplacement  
  
1.  Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez enregistrer à un nouvel emplacement.  
  
2.  Sur le **fichier** menu, cliquez sur **enregistrer  *\<nom de la carte >* comme**.  
  
3.  Dans le **enregistrer le fichier sous** boîte de dialogue, accédez à l’emplacement du dossier où vous souhaitez enregistrer la carte.  
  
4.  Dans le **nom de fichier** zone, tapez un nom pour le fichier, puis cliquez sur **enregistrer**.  
  
    > [!IMPORTANT]
    >  N’utilisez pas les noms suivants pour les mappages : « XmlContent », « SourceSchemas », « TargetSchemas » ou « Et » ; Cela entraîne des problèmes de compilation dans le code c# généré dans l’assembly .NET correspondant. Pour plus d’informations sur les problèmes et leur résolution, consultez [résolution des problèmes de cartes](../core/troubleshooting-maps.md).  
  
### <a name="to-rename-a-map"></a>Pour renommer un mappage  
  
1.  Dans l’Explorateur de solutions, cliquez sur la carte que vous souhaitez renommer, puis cliquez sur **renommer**.  
  
2.  Dans la zone d'édition qui apparaît à l'emplacement du mappage dans l'Explorateur de solutions, tapez le nouveau nom du mappage ou modifiez son nom actuel, puis appuyez sur ENTRÉE.  
  
> [!NOTE]
>  Vous pouvez également modifier le **nom de Type** de la carte lorsque vous le renommez. Vous modifiez le **nom de Type** en sélectionnant le **carte** dans l’Explorateur de solutions et entrer le nouveau nom dans la **nom de Type** dans la fenêtre Propriétés.  
  
#### <a name="to-close-a-map"></a>Pour fermer un mappage  
  
1.  Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez fermer.  
  
2.  Dans le menu **Fichier** , cliquez sur **Fermer**.  
  
    > [!NOTE]
    >  Vous pouvez également cliquer sur l’icône de fermeture ([**x**]) dans le coin supérieur droit de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des mappages dans des projets](../core/managing-maps-within-projects.md)