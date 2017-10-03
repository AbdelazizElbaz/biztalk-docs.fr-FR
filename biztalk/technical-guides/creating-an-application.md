---
title: "Création d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b6e325c-a86f-419d-9a27-864f4f035507
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4caf0531ee6cf952bfd343605b9b470c04c636d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-application"></a>Création d’une Application
Il existe trois façons de créer une application BizTalk. Il existe également plusieurs options de nom, faisant référence à et déploiement des artefacts aux applications.  
  
## <a name="creating-a-biztalk-application"></a>Création d’une Application BizTalk  
 Les trois méthodes sont les suivantes :  
  
1.  Vous pouvez créer l'application BizTalk en utilisant la commande Nouvelle application de la console Administration de BizTalk Server ou la commande AddApp de l'outil de ligne de commande BTSTask. Pour plus d’informations sur l’utilisation de ces commandes, consultez [la création d’une Application](http://go.microsoft.com/fwlink/?LinkId=155007) (http://go.microsoft.com/fwlink/?LinkId=155007).  
  
2.  Vous pouvez importer un fichier .msi exporté d'une autre application. Si l'application n'existe pas déjà dans le groupe BizTalk actuel, l'application et ses artefacts sont automatiquement créés dans le groupe BizTalk. Pour plus d’informations sur l’importation d’applications, consultez [comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).  
  
3.  Vous pouvez déployer des assemblys BizTalk à partir de Visual Studio dans une application BizTalk. Si l’application spécifiée dans les propriétés de déploiement pour un projet dans Visual Studio n’existe pas dans le groupe BizTalk actuel, il sera automatiquement créé. Pour plus d’informations sur le déploiement d’un assembly à partir de Visual Studio, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).  
  
 Pour déployer une application à l’aide d’un fichier .msi, l’application de destination n’avez pas besoin d’exister, mais est automatiquement créé. Toutefois, pour importer les liaisons d’une application vers un autre, l’application de destination doit déjà exister. Si ce n’est pas le cas, vous devez le créer en effectuant l’une des procédures répertoriées ci-dessus.  
  
 Pour plus d’informations sur les étapes spécifiques requises pour créer une application, consultez [la création d’une Application](http://go.microsoft.com/fwlink/?LinkId=155007) (http://go.microsoft.com/fwlink/?LinkId=155007).  
  
## <a name="application-options"></a>Options de l’application  
 Avant de créer une nouvelle application, vous devez procédez comme suit :  
  
-   Déterminer un nom qui est unique au sein du groupe BizTalk pour l’application.  
  
-   Ajoutez une référence à partir de la nouvelle application à toute application contenant des artefacts que vous souhaitez réutiliser dans la nouvelle application. Pour plus d’informations sur les dépendances entre les applications, consultez [des dépendances et déploiement d’applications](http://go.microsoft.com/fwlink/?LinkId=155008) (http://go.microsoft.com/fwlink/?LinkId=155008).  
  
-   Déterminez si vous souhaitez déployer certains artefacts dans des applications distinctes, par exemple, les artefacts partagés doivent être déployés dans leur propre application distincte.