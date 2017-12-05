---
title: "Étiquette et commentaires à un fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.functiod.general
ms.assetid: 58ff3a07-cbb6-4817-b301-d2b434ed2ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5720402e548992044eda26366c8b7b50bb95746a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-label-and-comment-a-functoid"></a>Attribution d'une étiquette et ajout de commentaires à un fonctoid
L'utilité des étiquettes et des commentaires est de renseigner sur la finalité d'un fonctoid ou d'un lien dans un mappage. Vous pouvez utiliser la **étiquette** propriété afin de fournir un nom d’un fonctoid. Le **commentaires** propriété vous permet de fournir plus d’informations sur le fonctoid, des informations pertinentes en général sur l’opération en cours par celui-ci.  
  
 La figure suivante illustre l'étiquette et les commentaires pour un fonctoid. Le fonctoid ajoute deux entrées (Field1 et Field3) à partir du schéma source et affiche le résultat dans l'entrée Field4 du schéma cible. Dans cet exemple, l'étiquette du fonctoid est « Ajout de Field1 et Field3 » et le commentaire est « L'ajout correspond à une sortie dans Field4 ».  
  
 ![Insertion d’étiquettes de fonctoid et des commentaires](../core/media/label.gif "Label_")  
  
 Étant donné qu'un fonctoid peut faire partie d'un mappage très complexe, il est important de lui attribuer une étiquette appropriée et d'ajouter des commentaires pertinents. Vous pouvez attribuer une étiquette aux fonctoids et aux liens. Pour plus d’informations sur l’étiquette à un lien, consultez [étiquette un lien à](../core/how-to-label-a-link.md).  
  
 Vous pouvez attribuer une étiquette à un fonctoid et lui ajouter des commentaires de l'une des manières suivantes :  
  
-   À l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue.  
  
-   À l’aide de la **propriétés** fenêtre.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
### <a name="to-label-and-comment-a-functoid-from-configure-dialog-box"></a>Pour attribuer une étiquette et des commentaires à un fonctoid à l'aide de la boîte de dialogue Configurer  
  
1.  Cliquez sur le fonctoid que vous souhaitez attribuer une étiquette et commentaire, puis cliquez sur **configurer les entrées de fonctoid**.  
  
2.  Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur le **étiquette et commentaires** onglet.  
  
3.  Entrez les informations suivantes, puis cliquez sur **OK**.  
  
    -   **Étiquette –** Entrez le nouveau nom.  
  
        > [!IMPORTANT]
        >  Le nombre maximal de caractères autorisé est de 256. Si une chaîne comportant plus de 256 caractères est spécifiée, les 256 premiers caractères sont acceptés et le reste est ignoré.  
  
    -   **Commentaires –** Entrez les commentaires pour le fonctoid.  
  
        > [!IMPORTANT]
        >  Le nombre maximal de caractères autorisé est 1024. Si une chaîne comportant plus de 1 024 caractères est spécifiée, les 1024 premiers caractères sont acceptés et le reste est ignoré.  
  
### <a name="to-label-and-comment-a-functoid-from-properties-window"></a>Pour attribuer une étiquette et des commentaires à un fonctoid à l'aide de la fenêtre Propriétés  
  
1.  Sélectionnez le fonctoid auquel attribuer une étiquette et des commentaires.  
  
2.  Dans le **propriétés** fenêtre, entrez les informations suivantes, puis cliquez sur **OK**.  
  
    -   **Étiquette –** Entrez le nouveau nom.  
  
        > [!IMPORTANT]
        >  Le nombre maximal de caractères autorisé est de 256. Si une chaîne comportant plus de 256 caractères est spécifiée, les 256 premiers caractères sont acceptés et le reste est ignoré.  
  
    -   **Commentaires –** Entrez les commentaires pour le fonctoid.  
  
        > [!IMPORTANT]
        >  Le nombre maximal de caractères autorisé est 1024. Si une chaîne comportant plus de 1 024 caractères est spécifiée, les 1024 premiers caractères sont acceptés et le reste est ignoré.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des propriétés et paramètres d’entrée de fonctoid](../core/editing-functoid-properties-and-input-parameters.md)