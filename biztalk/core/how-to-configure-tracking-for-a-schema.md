---
title: "Comment configurer le suivi pour un schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, configuring
- managing [schemas], configuring
- configuring [HAT tracking], schemas
- configuring, schemas
- configuring, tracking
- HAT, schemas
- managing [schemas], tracking
- schemas, tracking
- tracking, configuring
- tracking, schemas
ms.assetid: b5f69c98-8824-43b1-8f21-d84b60ac5431
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e15cb2210062901786b179ec75fe3880dea660b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-schema"></a>Configuration du suivi d'un schéma
Cette rubrique décrit la configuration du suivi d'un schéma à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour configurer le suivi, vous spécifiez les propriétés de message que vous voulez afficher dans les vues de requête de la page Hub du groupe de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour plus d’informations sur la création et l’utilisation de requêtes, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md). Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Si vous souhaitez n'afficher que les options de suivi, vous pouvez être connecté en tant que membre du groupe des opérateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-tracking-for-a-schema"></a>Pour configurer le suivi d'un schéma  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le schéma pour lequel vous voulez configurer le suivi, puis développez l’application contenant le schéma.  
  
3.  Cliquez sur **schémas**, cliquez sur le schéma, puis cliquez sur **propriétés**.  
  
4.  Dans le volet gauche, cliquez sur **suivi**.  
  
5.  Effectuez l’une des options suivantes pour spécifier les propriétés à utiliser pour le suivi des messages, puis cliquez sur **OK**:  
  
    -   Sélectionnez le **sélectionner toutes les propriétés de message** case à cocher pour utiliser toutes les propriétés répertoriées.  
  
        > [!NOTE]
        >  Cette case à cocher est disponible seulement pour les schémas qui contiennent des propriétés promues.  
  
    -   Activez la case à cocher de chaque propriété que vous voulez utiliser.  
  
        > [!NOTE]
        >  Cette option est disponible seulement pour les schémas qui contiennent des propriétés promues.  
  
> [!NOTE]
>  Il est conseillé de ne sélectionner que les options dont vous avez besoin, car le suivi des messages engendre une surcharge pour votre système, en matière de performances et de stockage.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas](../core/managing-schemas.md)