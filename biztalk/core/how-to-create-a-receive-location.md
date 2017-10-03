---
title: "Comment créer un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.procedure.createreceivelocation
helpviewer_keywords:
- receive locations, creating
- managing [receive locations], creating
- creating, receive locations
ms.assetid: ec0202cf-0e69-4ae2-aba6-8cd2c3c77e82
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe82afdc62a7ba2c10087c78a6a24c1722e5812a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-receive-location"></a>Création d'un emplacement de réception
La présente rubrique explique comment créer un emplacement de réception et spécifier son port de réception à l'aide de la console Administration de BizTalk Server. Un emplacement de réception est une adresse à laquelle parviennent des messages entrants, ainsi que le pipeline qui traite les messages reçus à cette adresse.  
  
 Pour que la création d'un emplacement de réception soit possible, l'application doit au préalable comporter un port de réception, du même type que l'emplacement de réception à créer. Pour obtenir des instructions sur la création d’un port de réception, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
 Vous pouvez créer les types d'emplacements de réception suivants :  
  
-   Unidirectionnel : utilisé pour les applications qui déposent un message et n'attendent pas de réponse synchrone  
  
-   Requête-réponse : utilisé avec les applications qui exigent une réponse à un message  
  
> [!NOTE]
>  Le développeur peut créer un emplacement de réception au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md). Vous avez, en outre, besoin des autorisations associées à la base de données d'authentification unique.  
  
### <a name="to-create-a-receive-location"></a>Pour créer un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle vous souhaitez créer un emplacement de réception.  
  
3.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel** ou **demande réponse un emplacement de réception**, en fonction du type d’emplacement de réception à créer.  
  
4.  Dans la fenêtre Sélectionner un Port de réception, cliquez sur le port de réception qui contiendra cet emplacement de réception, puis cliquez sur **OK**.  
  
5.  Dans le **propriétés de l’emplacement de réception** fenêtre, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Taper le nom de l'emplacement de réception.|  
    |**Type**|Sélectionner le type ou le protocole de transfert dans la liste déroulante. Si vous modifiez le type de transport, vous devez configurer les propriétés de transport, comme décrit ci-après.|  
    |**Configurer**|Après avoir sélectionné le type de transport, cliquez sur **configurer** pour afficher les **propriétés du Transport** boîte de dialogue zone et de configurer les propriétés de l’adaptateur pour l’emplacement de réception. Pour obtenir des instructions, cliquez sur **aide** dans la boîte de dialogue. Pour plus d’informations sur la configuration de chaque type d’adaptateur, consultez la rubrique appropriée sous [à l’aide des adaptateurs](../core/using-adapters.md).|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionner l'instance de l'hôte BizTalk Server dans laquelle l'emplacement de réception s'exécutera. Le gestionnaire de réception doit être exécuté sur cet hôte.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez le pipeline de réception à utiliser pour recevoir les messages à cet emplacement de réception.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez le pipeline d'envoi à utiliser pour envoyer des réponses à partir de cet emplacement de réception. Cette liste est uniquement disponible pour un emplacement de réception associé à un port de réception requête-réponse.|  
    |**Transformer en emplacement principal**|Cette case à cocher doit être activée si un port est associé à plusieurs emplacements de réception et que cet emplacement de réception est celui qui doit représenter le port de réception lorsque ce dernier est communiqué à une entité (un partenaire commercial, par exemple) souhaitant envoyer des messages à votre organisation. Le premier emplacement de réception créé est automatiquement sélectionné pour jouer le rôle d'emplacement de réception principal. Cette propriété demeure sélectionnée et indisponible tant que vous n'avez pas indiqué un emplacement de réception principal différent.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)