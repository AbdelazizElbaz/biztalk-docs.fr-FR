---
title: Comment tester des Interfaces de composant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing component interfaces
- component interfaces, testing
ms.assetid: d637f76d-170d-4543-a2b2-a4ac4001386b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be50521e5c4421d8ac8902bcf7a414d734c3b9f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-component-interfaces"></a>Test des interfaces de composant
L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise fait appel aux métadonnées et aux interfaces de composant PeopleSoft ; il permet donc de traiter de nouvelles interfaces de composant ou des interfaces de composant modifiées. L'adaptateur n'émet aucune hypothèse à propos des interfaces de composant à l'exception du fait qu'elles sont logiques et valides. Ainsi, chaque interface de composant doit être testée avant qu'elle puisse être utilisée comme source pour l'adaptateur.  
  
 Si un utilisateur ou une mise à niveau PeopleSoft apporte des modifications à l'application sous-jacente et que ces modifications invalident une interface de composant, l'utilisateur doit réparer celle-ci avant que l'adaptateur puisse l'utiliser.  
  
### <a name="to-test-a-component-interface"></a>Pour tester une interface de composant  
  
1.  Dans le Concepteur d’applications, sur le **outils** menu, cliquez sur **tester une Interface de composant**.  
  
     ![](../core/media/psadapter-54-ps-testcompinterface1.gif "PSAdapter_54_PS_TestCompInterface1")  
  
2.  Dans le **testeur d’Interface de composant** boîte de dialogue zone, l’interface de composant de test en utilisant l’une méthodes suivantes. Après avoir terminé d'apporter des modifications, cliquez avec le bouton droit sur le premier élément dans le volet.  
  
    > [!NOTE]
    >  Si besoin, cliquez sur la boîte de dialogue pour l'amener au premier plan.  
  
    -   Pour tester l’interface de composant à l’aide de la méthode Find, cliquez sur **trouver**.  
  
         Le **testeur d’Interface de composant - résultats de la recherche** boîte de dialogue s’ouvre, affichant toutes les entrées possibles pour le composant sous-jacent. Si le nombre d'entrées est supérieur à 300, un message s'affiche.  
  
         a. Dans le volet gauche de la **résultats de la recherche** boîte de dialogue, sélectionnez un champ.  
  
         b. Pour afficher les données pertinentes pour le champ concerné, cliquez sur **sélectionnés**.  
  
         L'écran suivant s'affiche.  
  
         ![](../core/media/psadapter-55-ps-testcompinterface2.gif "PSAdapter_55_PS_TestCompInterface2")  
  
         Si les paramètres de sécurité l'autorisent, vous pouvez modifier les valeurs des champs individuels.  
  
         La boîte de dialogue suivante s'affiche.  
  
         ![](../core/media/psadapter-56-ps-testcompinterface3.gif "PSAdapter_56_PS_TestCompInterface3")  
  
    -   Pour tester l’interface de composant à l’aide de la `Get` méthode :  
  
         a. Entrez l’ou les clés existante.  
  
         b. Cliquez sur **obtenir existant**.  
  
         Cette action a pour effet de renvoyer les propriétés exposées qui correspondent à la clé que vous avez entrée.  
  
         Vous pouvez modifier les valeurs si **mettre à jour les accès** a été spécifié.  
  
         Vous pouvez également tester l'interface de composant à l'aide de la méthode `Create`.  
  
         ![](../core/media/psadapter-57-ps-testcompinterface4.gif "PSAdapter_57_PS_TestCompInterface4")  
  
    -   Pour tester l’interface de composant à l’aide de la `Create` méthode :  
  
         a. Entrez toutes les valeurs de clés requises.  
  
         b. Cliquez sur **créer de nouveaux**.  
  
         Lorsque vous entrez des valeurs valides dans **créer des clés**, un volet qui affiche les données JOBCODE s’ouvre après que le nom de la Table est développé avec les données par défaut en place.  
  
         Vous pouvez maintenant modifier des champs.  
  
         ![](../core/media/psadapter-58-ps-testcompinterface5.gif "PSAdapter_58_PS_TestCompInterface5")  
  
         Les modifications sont validées en fonction de la logique d'entreprise sous-jacente du composant.  
  
3.  Pour enregistrer vos modifications, cliquez sur le **enregistrer** icône.  
  
     Les clés qui ont été utilisées pour créer l'enregistrement peuvent être utilisées avec la méthode Get pour afficher des données. Les données qui ont été ajoutées peuvent être affichées dans le composant PeopleSoft, comme l'illustre l'exemple suivant.  
  
     ![](../core/media/psadapter-59-ps-testcompinterface6.gif "PSAdapter_59_PS_TestCompInterface6")  
  
     **Date d’effet** est une des valeurs par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)   
 [Annexe c : à l’aide des Interfaces de composant](../core/appendix-c-using-component-interfaces.md)