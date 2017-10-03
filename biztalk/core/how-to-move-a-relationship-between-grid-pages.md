---
title: "Comment déplacer une relation entre les Pages de grille | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.movetopage
ms.assetid: 185add4d-c876-44b6-b6e0-71c15a9b7c26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5737adcb9159568bfea7c7cdde9dff8015b19706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-relationship-between-grid-pages"></a>Déplacement d'une relation entre les pages de grille
Les grands mappages incluent plusieurs ensembles de fonctoids et liens, ce qui peut rendre difficile l'identification des liens connectant plusieurs fonctoids. En pareil cas, vous pouvez déplacer un ensemble similaire de fonctoids et liens vers une autre page de grille pour rendre le mappage plus lisible. Cette rubrique contient des instructions détaillées pour effectuer cette opération.  
  
 Vous pouvez déplacer une relation d'une page de grille vers une autre, dans le même mappage uniquement, d'une des manières suivantes :  
  
-   À l’aide de la **déplacer vers la Page** boîte de dialogue  
  
-   en effectuant un glisser-déplacer du ou des fonctoids sélectionnés dans le ruban (et des liens associés).  
  
> [!IMPORTANT]
>  Vous pouvez déplacer un ou plusieurs fonctoids et leurs liens. Lorsque vous déplacez une relation, les étiquettes, commentaires et valeurs constantes (ainsi que les espaces réservés appropriés) associés à cette relation sont conservés.  
  
> [!IMPORTANT]
>  Vous ne pouvez pas glisser-déplacer les seuls liens vers une autre page de grille.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
### <a name="to-move-a-relationship-using-move-to-page-dialog-box"></a>Pour déplacer une relation à l'aide de la boîte de dialogue Déplacer vers la page  
  
1.  Dans le mappage, sélectionnez la page de grille depuis laquelle vous voulez déplacer une relation.  
  
2.  Cliquez sur un fonctoid ou un lien dans la relation que vous souhaitez déplacer, puis cliquez sur **déplacer vers la Page**. Un message vous informe que tous les éléments de mappage sélectionnés seront déplacés avec les liens et fonctoids qui leur sont associés. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Pour désactiver la boîte de message, dans le menu Visual Studio, accédez à **outils**, cliquez sur **Options**, cliquez sur **le Mappeur BizTalk**, cliquez sur **général**, et désactivez la **pour atteindre la page** option. Pour plus d’informations sur les options générales, consultez [comment personnaliser les paramètres généraux dans le Mappeur BizTalk](../core/how-to-customize-general-settings-in-biztalk-mapper.md).  
  
    > [!TIP]
    >  Vous pouvez également appuyer sur CTRL + M, CTRL + M pour ouvrir la **déplacer vers la Page** boîte de dialogue. Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
     ![Déplacer la relation sélectionnée vers une nouvelle page](../core/media/moving-a-functoid-new.gif "Moving_a_functoid_new")  
  
3.  Dans le **déplacer vers la Page** boîte de dialogue, sélectionnez la page de grille cible à laquelle vous souhaitez déplacer la relation, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Vous pouvez également créer une nouvelle page en sélectionnant  **\*(ajouter la nouvelle page)**, puis en cliquant sur **OK**.  
  
    > [!NOTE]
    >  Vous pouvez également appuyer sur les touches CTRL+M, CTRL+A pour ajouter une page de grille à un mappage. Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
     ![En sélectionnant la page de grille cible](../core/media/moving-a-functoid-step4.gif "Moving_a_functoid_Step4")  
  
     Le fonctoid/lien sélectionné (avec les fonctoids et liens associés) est déplacé vers la nouvelle page de grille. La figure ci-dessous illustre la relation sélectionnée (qui était en page 3) déplacée vers la page 1.  
  
     ![Relation sélectionnée est déplacée vers une nouvelle page](../core/media/moving-a-functoid-new2.gif "Moving_a_functoid_new2")  
  
### <a name="to-move-a-relationship-using-drag-and-drop"></a>Pour déplacer une relation à l'aide de la fonction glisser-déplacer  
  
1.  Dans le mappage, sélectionnez la page de grille depuis laquelle vous voulez déplacer une relation.  
  
2.  Sélectionnez le ou les fonctoids (et liens) à déplacer vers une autre page de grille. Cette action sélectionne de manière récursive les liens connectés aux fonctoids dans la sélection.  
  
3.  Faites glisser la sélection vers la page (sous l'onglet de page) dans laquelle vous voulez déplacer la relation.  
  
    > [!WARNING]
    >  Ne relâchez pas le bouton de la souris tant que vous n'avez pas exécuté l'étape 4.  
  
4.  Une fois la page de grille cible activée (dans la figure ci-dessus, la Page 1 est activée), déposez la sélection dans une cellule vide de la page de grille. La relation sélectionnée est déplacée vers la nouvelle page de grille.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des Pages de grille](../core/working-with-grid-pages.md)