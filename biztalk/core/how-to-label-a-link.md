---
title: "Étiquette d’un lien à | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fb81763-8b50-4334-88a8-efad1c5d82d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0e47a776fdbc8eccbc1037b3c73b069d810eee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-label-a-link"></a>Attribution d'une étiquette à un lien
Les étiquettes permettent de spécifier le but d'un fonctoid ou d'une liaison dans un mappage. Vous pouvez utiliser la **étiquette** propriété pour nommer une liaison. Ceci est utile lorsque votre mappage contient de grandes structures de schéma et que l'identification des entrées et liaisons de sortie vers un fonctoid devient difficile.  
  
> [!NOTE]
>  Pour plus d’informations sur l’étiquette et commentaire fonctoids, consultez [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).  
  
 La figure suivante illustre une étiquette de liaison.  
  
 ![Étiquetage d’un lien](../core/media/new-labelling-link.gif "New_Labelling_link")  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
### <a name="to-add-a-label-to-a-link"></a>Pour ajouter une étiquette à une liaison  
  
1.  Sélectionnez la liaison à laquelle ajouter une étiquette.  
  
2.  Dans le **propriétés** fenêtre, indiquez le nouveau nom dans la **étiquette** champ.  
  
    > [!IMPORTANT]
    >  Le nombre maximal de caractères autorisé est de 256. Si une chaîne comportant plus de 256 caractères est spécifiée, les 256 premiers caractères sont acceptés et le reste est ignoré.  
  
     ![Lier les propriétés de l’étiquette](../core/media/new-to-label-link.gif "New_To_Label_Link")  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)