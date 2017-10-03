---
title: "Déploiement d’un Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65f8ee21-0e52-4a74-b114-864a3069659c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73112fd9efb536452b8641faa976f42bb892b67c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-an-assembly"></a>Déploiement d’un Assembly
Déploiement d’un assembly, génère l’assembly et les importe, ainsi que des orchestrations, des pipelines, des schémas et des cartes (artefacts) qu’il contient dans la base de données de gestion BizTalk locale. Au départ, cela dans l’environnement de développement.  
  
 Déploiement associe également l’assembly à l’application BizTalk que vous avez spécifiées dans les propriétés du projet dans Visual Studio. Après le déploiement d'une solution, vous pouvez afficher et gérer les assemblys déployés et leurs artefacts dans la console Administration de BizTalk Server ou à l'aide de l'outil de ligne de commande BTSTask. Vous pouvez gérer les artefacts soit individuellement ou regroupées au sein de l’application.  
  
## <a name="deploying-an-assembly"></a>Déploiement d’un Assembly  
 Vous pouvez ajouter des assemblys pour des applications comme suit :  
  
-   Déployer un assembly dans une application à partir de l’environnement Visual Studio  
  
-   Ajouter manuellement des assemblys BizTalk Server à l’application à partir de la console Administration de BizTalk Server  
  
-   Ajouter un assembly BizTalk à une application à l’aide de script à partir de la ligne de commande  
  
-   Déplacer les assemblys BizTalk Server à partir d’autres applications à partir de la console Administration de BizTalk Server  
  
 Pour plus d’informations sur l’ajout d’assemblys pour les applications, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).  
  
## <a name="redeploying-assemblies"></a>Redéploiement des assemblys  
 En cours de développement et le débogage de vos assemblys BizTalk, vous devrez peut-être les redéployer plusieurs fois. BizTalk Server fournit un mécanisme simple de redéploiement. Si vous redéployez un assembly sans modifier le numéro de version, vous pouvez utiliser la propriété de redéploiement. BizTalk Server effectue automatiquement toutes les étapes de redéployer l’assembly pour vous.  
  
 Pour plus d’informations sur le redéploiement des assemblys, consultez [comment redéployer un BizTalk Assembly à partir de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720).  
  
### <a name="best-practices-for-redeploying-an-assembly"></a>Meilleures pratiques pour vous redéployez un Assembly  
 **Vous devez installer le nouvel assembly dans le GAC**  
  
-   Lorsque vous redéployez un assembly, vous devez toujours installer la nouvelle version de l’assembly dans le global assembly cache (GAC). Vous pouvez procéder à cette installation après le redéploiement de l'assembly. Pour plus d’informations, consultez [comment installer un Assembly dans le GAC](http://go.microsoft.com/fwlink/?LinkID=154828) (http://go.microsoft.com/fwlink/?LinkID=154828).  
  
 **Vous devez toujours redéployer au niveau de la solution lorsqu’il existe des dépendances**  
  
-   Si votre solution comporte plusieurs assemblys et que l'un ou plusieurs d'entre eux présentent une dépendance avec l'assembly à redéployer, vous devez redéployer les assemblys au niveau de la solution. Il s’agit, car lorsque vous redéployez un assembly au niveau du projet, BizTalk Server arrête, désinscrire, détacher et supprimer les artefacts dans tous les assemblys qui soit dépendent de cet assembly ou dont dépend cet assembly. BizTalk Server n'effectue pas ensuite les opérations nécessaires au déploiement, à la liaison, à l'inscription et au démarrage des artefacts. Lorsque vous redéployez la solution entière, en revanche, BizTalk Server effectue automatiquement les opérations nécessaires à l'annulation du déploiement et au redéploiement de tous les artefacts de la solution en fonction de leurs dépendances.  
  
 **Vous devrez peut-être à redéployer manuellement les assemblys dépendants**  
  
-   BizTalk Server annule toujours le déploiement des assemblys dépendants lorsqu’il annule un assembly, mais les cas suivants, vous devez effectuer les étapes supplémentaires à déployer, lier et inscrire les artefacts de chaque assembly dépendant après le redéploiement de l’assembly sur lequel le dépend de l’assembly :  
  
     si vous redéployez au niveau du projet un assembly dont dépend un autre assembly de la même solution ;  
  
     si vous redéployez un assembly au niveau de la solution, mais qu'un assembly dépendant existe dans une autre solution.  
  
 **Vous devez redémarrer les instances d’hôte**  
  
-   Lorsque vous redéployez un assembly qui contient une orchestration sans modifier le numéro de version de l'assembly, l'assembly existant est remplacé dans la base de données de gestion BizTalk. Pour que la modification entre en vigueur, cependant, vous devez redémarrer chaque instance de l'hôte auquel est liée l'orchestration. Vous avez la possibilité de configurer le redémarrage automatique de toutes les instances d'hôte sur l'ordinateur local au moment du redéploiement d'un assembly.  
  
     Lorsque vous redéployez un assembly qui contient une orchestration sans modifier le numéro de version de l'assembly, l'assembly existant est remplacé dans la base de données de gestion BizTalk. Pour que la modification entre en vigueur, cependant, vous devez redémarrer chaque instance de l'hôte auquel est liée l'orchestration. Vous avez la possibilité de configurer le redémarrage automatique de toutes les instances d'hôte sur l'ordinateur local au moment du redéploiement d'un assembly. Pour plus d’informations sur les propriétés de déploiement, consultez [comment définir les propriétés de déploiement dans Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154718) (http://go.microsoft.com/fwlink/?LinkID=154718).  
  
     Vous pouvez également arrêter et démarrer chaque instance d’hôte. Pour plus d’informations sur l’arrêt et démarrage d’une instance d’hôte, consultez [comment arrêter une Instance d’hôte](http://go.microsoft.com/fwlink/?LinkID=154829) (http://go.Microsoft.com/fwlink/?) LinkID = 154829) et [comment démarrer une Instance d’hôte](http://go.microsoft.com/fwlink/?LinkID=154830) (http://go.Microsoft.com/fwlink/?) LinkID = 154830).