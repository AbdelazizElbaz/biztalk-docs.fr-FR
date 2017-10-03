---
title: "Les valeurs de nœud vides dans la Source de Messages d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76f9d7c8-5a82-41e9-9077-7b1ddd80a837
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2a36271f5e9d66efc8ef0c50cdc9582f4de1261
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="empty-node-values-in-source-instance-messages"></a>Valeurs de nœud vides dans les messages d'instance source
Il pourra vous arriver, quand vous testerez un mappage, de vouloir que des nœuds de schéma soient dépourvus de contenu.  
  
## <a name="ceate-empty-node-values"></a>Valeurs de nœud vide Créez  
  
1.  Générez des données d'instance à l'aide de l'Éditeur BizTalk. Pour plus d’informations sur les données d’instance de génération, consultez [comment générer des Messages d’Instance](../core/how-to-generate-instance-messages.md).  
  
2.  Ouvrez le message d'instance d'entrée dans un éditeur de texte, effacez les données des éléments et attributs que vous souhaitez voir vides, puis enregistrez le fichier d'instance modifié.  
  
3.  Configurez le Mappeur BizTalk de façon à ce qu'il utilise le fichier que vous venez de modifier au moment de la validation et du test du schéma. Vous définissez le fichier dans la fenêtre Propriétés du schéma. Pour plus d’informations sur la définition des propriétés, consultez **propriétés du fichier de mappage** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
-  [Comment générer des Messages d’Instance](../core/how-to-generate-instance-messages.md)   
-  **Référence du schéma de propriété**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]