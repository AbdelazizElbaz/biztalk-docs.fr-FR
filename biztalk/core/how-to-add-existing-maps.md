---
title: Comment ajouter des mappages existants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbeaea05-016e-488c-90f3-af8c6b9a3d84
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a61fb0faf5f4eed614257361b00cea781db2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-existing-maps"></a>Ajout de mappages existants
Il peut arriver que vous vouliez ajouter un mappage existant à un projet BizTalk. Pour ce faire, vous devez d’abord vous assurer que les schémas source et de destination du mappage sont inclus dans le projet BizTalk auquel vous ajoutez le mappage ou qu’ils sont référencés par l’assembly .NET correspondant.  
  
### <a name="to-add-an-existing-map-to-a-biztalk-project"></a>Pour ajouter un mappage existant à un projet BizTalk  
  
1.  Cliquez sur un projet BizTalk dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
2.  Dans le **ajouter un élément existant** boîte de dialogue, accédez au dossier contenant le mappage à ajouter, sélectionnez-le, puis cliquez sur **ajouter**.  
  
     Le mappage s'ouvre dans le Mappeur BizTalk. Le mappage ajouté apparaît également en tant qu’enfant du projet BizTalk actuel dans l’Explorateur de solutions.  
  
    > [!NOTE]
    >  Si vous avez accédé à un dossier différent de celui du projet BizTalk, une copie du mappage ajouté a été créée dans le dossier du projet et c’est cette copie qui a été ajoutée au projet. Les modifications ultérieures du mappage sont apportées à cette copie et non au mappage original contenu dans l’autre dossier.  
  
    > [!IMPORTANT]
    >  Les mappages BizTalk peuvent uniquement être ouverts par le Mappeur BizTalk, qui est hébergé dans le shell Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Si vous double-cliquez sur un mappage dans l’Explorateur Windows, une nouvelle instance de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] s’ouvrira et le mappage sera ouvert par le Mappeur BizTalk, à condition que les schémas correspondants soient correctement chargés.  
  
    > [!NOTE]
    >  Si le mappage existant contient des fonctoids personnalisés, alors les DLL correspondants doivent être copiés dans le dossier « %BTSINSTALLPATH%\Developer Tools\Mapper Extensions ». Si cela n'est pas fait, le mappage ne se chargera pas et lèvera une erreur suite à l'échec de chargement des fonctoids personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des mappages dans des projets](../core/managing-maps-within-projects.md)   
 [Développement de fonctoids personnalisés](../core/developing-custom-functoids.md)