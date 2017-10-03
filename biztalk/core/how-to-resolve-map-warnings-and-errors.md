---
title: "Comment résoudre les erreurs et avertissements de la carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a3e7f3-c96c-4d3d-9f7c-d2bfd9ace4fd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2983a53bb47aa66d1564772d0f8e033132e5a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resolve-map-warnings-and-errors"></a>Résolution des avertissements et des erreurs liés aux mappages
Lors de la compilation d’un mappage, il se peut que le processus donne lieu à des avertissements et des erreurs.  
  
## <a name="resolve-warnings-and-errors-when-building-a-map"></a>Résoudre les erreurs et des avertissements lors de la création d’un mappage  
  
1.  Pour les erreurs de liaison et de fonctoid, dans le **liste d’erreurs** fenêtre, double-cliquez sur n’importe quelle description.  
  
     La liaison, le fonctoid ou le nœud de schéma associé à l’erreur apparaît en surbrillance. Procédez à la résolution du problème.  
  
2.  Examinez le **Description** zone dans le **liste d’erreurs** fenêtre afin d’identifier les erreurs supplémentaires.  
  
3.  Cliquez sur le **sortie** onglet de fenêtre pour afficher les informations de message avertissement et d’erreur supplémentaires.  
  
4.  Une fois que vous avez résolu tous les problèmes, cliquez sur le nom de fichier de mappage dans l’Explorateur de solutions, puis cliquez sur **Test Map** ou **générer la Solution**, le cas échéant.  
  
    > [!NOTE]
    >  Si un avertissement s’affiche, le problème risque d’exister sur plusieurs pages de grille. Par exemple, vous disposez de la page de grille 1 avec un enregistrement (nommé **élément**) dans l’arborescence des schémas sources liée à un enregistrement (nommé **numéro**) dans l’arborescence de schéma de destination. Sur la page de grille 2 vous disposez d’un enregistrement (nommé **produit**) dans l’arborescence du schéma source lié à la même **nombre** enregistrement dans l’arborescence de schéma de destination. Dans ce scénario, un message d’avertissement est généré indiquant que vous disposez de plusieurs entrées pour le même enregistrement. Toutefois, si vous affichez la page de grille 1, vous voyez uniquement une seule entrée dans le **nombre** enregistrement. 
  
## <a name="see-also"></a>Voir aussi  
 [La compilation et test des mappages](../core/compiling-and-testing-maps.md)   
 [Erreurs du Mappeur BizTalk](../core/biztalk-mapper-errors.md)   
 [Résolution des problèmes de mappages](../core/troubleshooting-maps.md)