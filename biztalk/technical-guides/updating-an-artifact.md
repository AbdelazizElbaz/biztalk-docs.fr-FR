---
title: "Mise à jour d’un artefact | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40feab57-4286-4bdf-8f52-25d02b3fa60c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17d5f2ad910c59ded9c2499c929d73480fac7b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updating-an-artifact"></a>Mise à jour d’un artefact
Dépendances entre les artefacts de deux ou plusieurs applications BizTalk peuvent avoir un impact significatif sur le déploiement de l’application et la maintenance. Un artefact est dépendant d’un autre lorsqu’il a besoin d’utiliser cet artefact pour fonctionner correctement, par exemple une orchestration qui doit utiliser un pipeline spécifique afin de transmettre les messages correctement.  
  
 Pour mettre à jour un artefact dans une application, vous devez tout d’abord annuler son déploiement, ainsi que tous les artefacts qui en dépendent. Lorsque des artefacts dépendants existent dans la même application, BizTalk Server gère automatiquement les tâches d'annulation du déploiement et de redéploiement pour les artefacts mis à jour et dépendants. Ce n'est pas le cas, cependant, lorsque des artefacts dépendants existent dans différentes applications. Si vous souhaitez mettre à jour un artefact dans une application et un artefact dans une autre application a une dépendance sur ce dernier, vous devez annuler le déploiement et redéployer l’artefact dépendant manuellement comme suit :  
  
1.  Arrêtez, désinscrivez et supprimez la liaison de l'artefact dépendant.  
  
2.  Mettez à jour l'artefact dont il dépend.  
  
3.  Liez, inscrivez et démarrez l'artefact dépendant.  
  
 Pour éviter d’avoir à effectuer des étapes manuelles pour mettre à jour un artefact sur les autres artefacts dépendent, vous pouvez tenter de conserver tous les artefacts dépendants dans la même application. Cela n’est pas toujours possible, toutefois, étant donné que la plupart des types d’artefacts doivent être uniques dans un groupe BizTalk. Vous ne pouvez avoir le même artefact dans deux applications du même groupe, même si celles-ci contiennent des artefacts qui dépendent du même artefact. Pour plus d’informations sur le problème d’artefacts uniques, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](http://go.microsoft.com/fwlink/?LinkId=155141) (http://go.microsoft.com/fwlink/?LinkId=155141) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Vous pouvez ajouter l’artefact requis à une application et puis ajoutez une référence à cette application à partir d’autres applications contenant des artefacts qui en dépendent. Lorsque vous ajoutez une référence à une application, les artefacts qu'elle contient peuvent utiliser ceux de l'application à laquelle elle fait référence. Pour obtenir des instructions sur l’ajout d’une référence, consultez [comment ajouter une référence à une autre Application](http://go.microsoft.com/fwlink/?LinkID=155011) (http://go.microsoft.com/fwlink/?LinkID=155011) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Pour obtenir la liste des tâches de mise à jour des artefacts dans une application BizTalk, consultez [liste de vérification : mise à jour les artefacts dans une Application BizTalk](http://go.microsoft.com/fwlink/?LinkId=155647) (http://go.microsoft.com/fwlink/?LinkId=155647) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des Applications et des artefacts](../technical-guides/updating-applications-and-artifacts.md)