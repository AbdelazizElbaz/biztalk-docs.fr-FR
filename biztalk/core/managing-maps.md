---
title: "Gérer les mappages | Documents Microsoft"
description: "Liens pour travailler avec les mappages dans BizTalk Server, y compris l’affichage et la suppression des mappages"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e8e3057-5a9f-4b6b-b6ee-c71b7e6a51ac
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c86a1cd23fe8f06c2671be163409cd405e9cbe1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-maps"></a>Gérer les mappages

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur la gestion des mappages à l'aide de la console Administration de BizTalk Server. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise des mappages pour convertir les enregistrements et les champs d’un schéma pour les enregistrements et champs dans un autre schéma. Les mappages peuvent être utilisés par les orchestrations, les ports d'envoi et les ports de réception.  

## <a name="add-maps-to-an-application"></a>Ajout de mappages à une application  
 Les mappages sont créés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilés dans les assemblys BizTalk. Vous ne pouvez pas ajouter un mappage de manière individuelle à une application. Son ajout s'effectue dans les cas suivants :  
  
-   Lorsque vous ajoutez un assembly BizTalk contenant un mappage à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
-   Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un mappage, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
-   Lorsqu’un développeur déploie dans une application d’un assembly contenant un mappage à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
 Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md). Pour plus d’informations sur la création de mappages, consultez [création est mappé à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Afficher les mappages pour une Application](../core/how-to-view-the-maps-for-an-application.md)  
  
-   [Supprimer un mappage à partir d’une Application](../core/how-to-remove-a-map-from-an-application.md)