---
title: "Comment créer de nouveaux mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43b36cd8-f28e-4349-87d5-c94b7d8761bf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 910d79782f4332ae1d706e12a8c5dda8c399a41b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-new-maps"></a>Comment créer de nouveaux mappages

## <a name="overview"></a>Vue d'ensemble
Pour construire un mappage BizTalk, vous devez suivre trois étapes détaillées :  
  
1.  Créer le nouveau mappage au sein d’un projet BizTalk.  
  
2.  Ajoutez les schémas source et de destination à la carte.  
  
3.  Établir l’ensemble de liens et, le cas échéant, les fonctoids intermédiaires spécifiant la façon dont le schéma source est mappé au schéma de destination.  
  
 Dans le contexte actuel, les deux premières étapes correspondent à la « création » du mappage. La troisième étape correspond à la « construction » du mappage. Pour obtenir des instructions détaillées sur la plupart des tâches liées au processus de construction du mappage, consultez [à l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md).  
  
## <a name="create-a-new-map"></a>Créer un nouveau mappage 
  
1.  Cliquez sur un projet BizTalk dans l’Explorateur de solutions, sélectionnez **ajouter**, puis sélectionnez **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles** zone, sélectionnez **carte**.  
  
3.  Sélectionnez le texte dans le **nom** zone, tapez un nom pour le mappage, puis sélectionnez **ajouter**.  
  
     Le Mappeur BizTalk s'ouvre dans la fenêtre d'édition Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], et présente trois volets distincts, côte à côte. De gauche à droite, ces volets affichent le schéma source, la grille (qui peut comporter plusieurs pages) et le schéma de destination.  
  
    > [!IMPORTANT]
    >  Vous ne pouvez pas utiliser les noms suivants pour les mappages : « XmlContent », « SourceSchemas », « TargetSchemas » ou « Et ». Ces noms ne peuvent pas être utilisés, car la compilation dans un assembly .NET engendre des restrictions de nom résultant du code C# généré.  
  
4.  Dans le Mappeur BizTalk, dans le volet gauche, sélectionnez **ouvrir le schéma Source**.  
  
5.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schémas** nœud, sélectionnez le schéma source approprié, puis **OK**.  

    > [!TIP] 
    > **En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez redimensionner la fenêtre du sélecteur de Type pour afficher le nom complet de votre schéma.
  
     Si une seule une racine unique existe dans le schéma source ou un nœud racine a été établi pour le schéma à l’aide la **référence de racine** propriété de la **schéma** nœud, le schéma source s’ouvre dans le volet gauche et que vous procéder à l’étape 7.  
  
6.  Si le schéma source a plusieurs nœuds racine et qu’aucun nœud racine n’a été établie pour le schéma source à l’aide du **schéma** du nœud **référence de racine** propriété, dans le **nœud racine pour la Source Schéma** boîte de dialogue, sélectionnez le nœud racine approprié, puis sélectionnez **OK**.  
  
    > [!IMPORTANT]
    >  Si vous choisissez un nœud racine d’un schéma dans le Mappeur BizTalk et que vous modifiez ensuite la **référence de racine** la propriété dans le schéma, la prochaine fois que vous ouvrez le schéma dans le Mappeur BizTalk, le nœud racine pas à jour pour la nouvelle référence racine configurée dans l’Éditeur BizTalk.  
  
7.  Dans le Mappeur BizTalk, dans le volet droit, sélectionnez **ouvrir le schéma de Destination**.  
  
8.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schéma** nœud dans l’arborescence, si nécessaire, sélectionnez le schéma de destination approprié, puis sélectionnez **OK**.  
  
     Si seule une racine unique existe dans le schéma de destination, ou un nœud racine a été établi pour le schéma de destination à l’aide de la **référence de racine** propriété de la **schéma** ouvre de nœud, le schéma de destination dans le volet droit, et vous ne devrez pas effectuer l’étape 9.  
  
9. Si le schéma de destination comporte plusieurs nœuds racine et qu’aucun nœud racine n’a été établie pour le schéma de destination à l’aide de la **référence de racine** propriété de la **schéma** nœud, dans le **nœud racine pour le schéma cible** boîte de dialogue, sélectionnez le nœud racine approprié, puis sélectionnez **OK**.  
  
     Le schéma de destination s’ouvre dans le volet de droite.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des mappages dans des projets](../core/managing-maps-within-projects.md)