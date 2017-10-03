---
title: "Comment créer et modifier un groupe d’adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1eef051-2ed7-4e28-8cb9-0145d6c8ed76
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6865de8eb67d9fe1a6ca8d93b7d2e6527ae36364
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-and-modify-an-adapter-group"></a>Comment créer et modifier un groupe d’adaptateurs
L'une des nouvelles fonctionnalités de l'authentification unique (SSO) permet de créer et de modifier des groupes d'adaptateurs. Comme le nom l'indique, un groupe d'adaptateurs correspond à un regroupement d'adaptateurs. Vous pouvez utiliser des groupes d’adaptateurs pour organiser les paramètres de sécurité et autres propriétés de vos adaptateurs.  
  
### <a name="to-create-and-modify-an-adapter-group"></a>Pour créer et modifier un groupe d’adaptateurs  
  
1.  Créez le groupe d'adaptateurs à l'aide un appel à l'outil ssops.  
  
     Dans le fichier XML associé, définissez l'indicateur de groupe comme groupe d'adaptateurs.  
  
2.  Ajoutez un ou plusieurs adaptateurs au groupe d'adaptateurs à l'aide de `ISSOPSAdmin.AddAdapterToAdapterGroup`.  
  
     À ce stade, votre groupe d’adaptateurs est prêt à fonctionner comme prévu. Si nécessaire, affichez la liste complète des adaptateurs associés à l'aide de `ISSOPSAdmin.GetAdaptersForAdapterGroup`.  
  
3.  Vous pouvez modifier les paramètres de votre groupe d'adaptateurs à l'aide de `ISSOPSAdmin.SetAdapterProperties`.  
  
4.  Une fois que vous avez terminé, vous pouvez supprimer l'adaptateur du groupe d'adaptateurs à l'aide de `ISSOPSAdmin.RemoveAdapterFromAdapterGroup`.  
  
5.  Enfin, vous pouvez supprimer le groupe d'adaptateurs à l'aide de `ISSOAdmin.DeleteApplication`.  
  
     Vous pouvez à la place décider de supprimer le groupe d'adaptateurs à l'aide de la commande `-delete` de l'outil ssops.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation des mots de passe](../core/synchronizing-passwords.md)