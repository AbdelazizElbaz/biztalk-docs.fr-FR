---
title: "Comment créer des Interfaces de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating component interfaces
- component interfaces, creating
ms.assetid: 9def053a-cbf6-4b34-b2e8-b2d03bffc5fe
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86ee68edba66b05d3c2541dd9c41cc074bd790b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-component-interfaces"></a>Création des interfaces de composant
Vous créez des interfaces de composant à l'aide du Concepteur d'applications PeopleSoft. Pour plus d'informations sur celui-ci, consultez la documentation de PeopleSoft Enterprise.  
  
 Vous pouvez ajouter des propriétés à partir des enregistrements de la vue du composant. Dans l'interface de composant, vous pouvez supprimer une propriété que vous ne souhaitez pas exposer. Vous pouvez renommer une propriété en double-cliquant dessus pour entrer un nouveau nom. Si vous renommez une propriété, vous pouvez la référencer dans l'interface de composant uniquement par le nouveau nom, et non par le nom de composant sous-jacent.  
  
 Plusieurs icônes peuvent être présentes en regard des propriétés. Par exemple, EMPLID possède une icône qui indique qu'il s'agit d'un champ de clé de l'enregistrement sous-jacent. NAME possède une icône qui indique qu'il s'agit d'un champ de clé de remplacement de l'enregistrement sous-jacent. (Pour obtenir une liste complète des icônes de propriétés, consultez la documentation PeopleBooks.)  
  
### <a name="creating-a-new-component-interface"></a>Création d'une interface de composant  
  
1.  Ouvrez le concepteur d'applications PeopleSoft.  
  
2.  Dans le menu **Fichier** , cliquez sur **Nouveau**.  
  
     ![](../core/media/psadapter-42-ps-new-compinterface.gif "PSAdapter_42_PS_New_CompInterface")  
  
3.  Dans le **nouveau** boîte de dialogue, sélectionnez **Interface de composant**, puis cliquez sur **OK**.  
  
     ![](../core/media/psadapter-43-ps-selectsourcecomp.gif "PSAdapter_43_PS_SelectSourceComp")  
  
4.  Dans le **sélectionner le composant Source pour l’Interface de composant** fenêtre, sélectionnez le composant à utiliser comme base pour l’interface de composant, puis cliquez sur **sélectionnez**.  
  
     ![](../core/media/psadapter-44-ps-appdesigner1.gif "PSAdapter_44_PS_AppDesigner1")  
  
    > [!NOTE]
    >  Si l'interface de composant est volumineuse, exposez les propriétés du composant manuellement.  
  
5.  Dans le **Concepteur d’applications** boîte de dialogue zone, choisissez une des options suivantes :  
  
    -   Cliquez sur **non** pour créer l’interface de composant sans afficher les propriétés et d’exposer les propriétés du composant manuellement.  
  
         a. Faites glisser les champs appropriés dans le volet gauche vers le volet droit.  
  
         b. Pour sélectionner diverses fonctions à effectuer, avec le bouton droit soit sur le volet droit ou gauche, selon le volet est actif.  
  
         Pour obtenir une liste complète des fonctions, consultez la documentation PeopleBooks.  
  
    -   Cliquez sur **Oui** pour créer l’interface de composant et afficher les propriétés de l’interface de composant sous-jacent.  
  
         ![](../core/media/psadapter-45-ps-appdesigner2.gif "PSAdapter_45_PS_AppDesigner2")  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes standard dans les Interfaces de composant](../core/standard-methods-in-component-interfaces.md)   
 [Annexe c : à l’aide des Interfaces de composant](../core/appendix-c-using-component-interfaces.md)   
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)