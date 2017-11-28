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
# <a name="empty-node-values-in-source-instance-messages"></a><span data-ttu-id="ec6d7-102">Valeurs de nœud vides dans les messages d'instance source</span><span class="sxs-lookup"><span data-stu-id="ec6d7-102">Empty Node Values in Source Instance Messages</span></span>
<span data-ttu-id="ec6d7-103">Il pourra vous arriver, quand vous testerez un mappage, de vouloir que des nœuds de schéma soient dépourvus de contenu.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-103">There may be times when you do not want content in all of the schema nodes when you test a map.</span></span>  
  
## <a name="ceate-empty-node-values"></a><span data-ttu-id="ec6d7-104">Valeurs de nœud vide Créez</span><span class="sxs-lookup"><span data-stu-id="ec6d7-104">Ceate empty node values</span></span>  
  
1.  <span data-ttu-id="ec6d7-105">Générez des données d'instance à l'aide de l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-105">Generate instance data using BizTalk Editor.</span></span> <span data-ttu-id="ec6d7-106">Pour plus d’informations sur les données d’instance de génération, consultez [comment générer des Messages d’Instance](../core/how-to-generate-instance-messages.md).</span><span class="sxs-lookup"><span data-stu-id="ec6d7-106">For more information about generating instance data, see [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md).</span></span>  
  
2.  <span data-ttu-id="ec6d7-107">Ouvrez le message d'instance d'entrée dans un éditeur de texte, effacez les données des éléments et attributs que vous souhaitez voir vides, puis enregistrez le fichier d'instance modifié.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-107">Open the input instance message in a text editor, delete the data from elements and attributes that you want to be empty, and then save the modified instance file.</span></span>  
  
3.  <span data-ttu-id="ec6d7-108">Configurez le Mappeur BizTalk de façon à ce qu'il utilise le fichier que vous venez de modifier au moment de la validation et du test du schéma.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-108">Configure BizTalk Mapper to use the file you just modified when the schema is validated and tested.</span></span> <span data-ttu-id="ec6d7-109">Vous définissez le fichier dans la fenêtre Propriétés du schéma.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-109">You set the file in the Properties window for the schema.</span></span> <span data-ttu-id="ec6d7-110">Pour plus d’informations sur la définition des propriétés, consultez **propriétés du fichier de mappage** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="ec6d7-110">For more information about setting properties, see **Map File Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ec6d7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec6d7-111">See Also</span></span>  
-  [<span data-ttu-id="ec6d7-112">Comment générer des Messages d’Instance</span><span class="sxs-lookup"><span data-stu-id="ec6d7-112">How to Generate Instance Messages</span></span>](../core/how-to-generate-instance-messages.md)   
-  <span data-ttu-id="ec6d7-113">**Référence du schéma de propriété**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="ec6d7-113">**Schema Property Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>