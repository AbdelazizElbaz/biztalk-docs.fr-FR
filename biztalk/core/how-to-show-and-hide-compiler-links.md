---
title: Comment afficher et masquer les liaisons du compilateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66bfd9de-c4d2-46ee-854f-cf7c7cd07368
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d9b9ee8901ea2d93a73fd227a0ac1623e25669
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-show-and-hide-compiler-links"></a>Affichage et masquage des liaisons du compilateur
Lorsque vous compilez un mappage, le Mappeur BizTalk crée des liens supplémentaires, baptisés liens de compilateur et représentant l'ensemble des liaisons nécessaires dans le mappage. Certains de ces liens ont uniquement un caractère implicite conféré par les liens que vous avez créés. Lorsque vous compilez, ou testez, un mappage, la dernière ligne de la fenêtre de sortie Visual Studio vous permet d'afficher ou de masquer ces liens de compilateur supplémentaires dans la fenêtre principale. Par défaut, les liens de compilateur apparaissent sous forme de lignes en pointillés rouges.  
  
### <a name="to-show-or-hide-compiler-links"></a>Pour afficher ou masquer des liens de compilateur  
  
1.  Dans l’Explorateur de solutions, cliquez sur la carte dont vous souhaitez afficher, puis cliquez sur les liens de compilateur **Test Map**.  
  
2.  Dans la fenêtre liste d’erreurs Visual Studio, accédez à la fin et double-cliquez sur la ligne indiquant **double-cliquez ici pour afficher/masquer les liaisons du compilateur**.  
  
     Pour faire passer l'état de l'affichage des liens de compilateur d'affiché à masqué, ou de masqué à affiché, il vous suffit de double-cliquer sur cette ligne à nouveau.  
  
    > [!NOTE]
    >  Lorsque vous génération/regénération d’un projet ou solution BizTalk contenant un ou plusieurs mappages, le message **double-cliquez ici pour afficher/masquer les liaisons du compilateur** s’affiche dans le **liste d’erreurs** fenêtre de Visual Studio pour tous les mappages dans le projet ou la solution.  
  
 Pour tester un mappage, vous devez configurer les propriétés des instances d'entrée et de sortie. Pour plus d’informations sur la façon de configurer ces propriétés, consultez [comment configurer la Validation de mappage et les paramètres de Test](../core/how-to-configure-map-validation-and-test-parameters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)