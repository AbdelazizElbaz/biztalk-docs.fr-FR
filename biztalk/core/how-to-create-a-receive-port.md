---
title: Comment créer un Port de réception | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.createreceiveport
helpviewer_keywords:
- receive ports, creating
- managing [receive ports], creating
- creating, receive ports
ms.assetid: 23fae441-be80-4759-b3d6-74787a40e65b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdecbc36962d3e4e45d35171747ff4c450959a83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-receive-port"></a>Comment créer un Port de réception
La présente rubrique explique comment créer un port de réception à l'aide de la console Administration de BizTalk Server. Un port de réception est groupe logique d'emplacements de réception similaires grâce auquel les services interagissent avec les partenaires externes en recevant des données.  
  
 Vous pouvez créer les types de ports de réception suivants :  
  
-   Unidirectionnel : utilisé pour les applications qui déposent un message et n'attendent pas de réponse synchrone  
  
-   Requête-réponse : utilisé avec les applications qui exigent une réponse à un message  
  
 En plus de la configuration décrite dans cette rubrique, vous pouvez également spécifier des options de suivi pour les messages traités par un port de réception, comme décrit dans [comment configurer le suivi pour un Port de réception](../core/how-to-configure-tracking-for-a-receive-port.md).  
  
> [!NOTE]
>  Si vous créez un port de réception sur un ordinateur distant alors que le réseau DTC n'est pas activé sur cet ordinateur, vous devrez redémarrer l'ordinateur distant une fois le port de réception créé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-create-a-receive-port"></a>Pour créer un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle créer un port de réception.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse**, en fonction pour le type de port que vous souhaitez créer.  
  
4.  Dans le **propriétés du Port de réception** fenêtre, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Taper le nom du port.|  
    |**Aucune authentification**|Cliquer sur cette option pour désactiver l'authentification. Il s'agit du paramètre par défaut.|  
    |**Supprimer les messages si l’authentification échoue**|Cliquez sur cette option pour activer l’authentification, mais abandonner les messages non authentifiés.|  
    |**Conserver les messages si l’authentification échoue**|Activer l'authentification et conserver les messages non authentifiés.|  
    |**Activer le routage des messages ayant échoué**|Activer cette case à cocher pour lancer une tentative d'acheminement des messages dont le traitement a échoué vers une application abonnée (un autre port de réception ou une planification d'orchestration). Désactiver la case à cocher pour interrompre les messages ayant échoué et générer un accusé de réception négatif (NACK). Par défaut, cette case à cocher est désactivée. Pour plus d’informations, consultez [comment activer le routage de Messages a échoué pour un Port de réception](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md).|  
  
5.  Dans le volet gauche, cliquez sur **emplacements de réception**, puis créez un emplacement de réception pour ce port de réception. Pour obtenir des instructions, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
6.  Dans le volet gauche, cliquez sur **mappages entrants**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Document source**|Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.|  
    |**Carte**|Sélectionner, dans la liste déroulante, le mappage à associer à ce port.|  
    |**Document cible**|Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.|  
  
7.  Si vous créez une requête-réponse port de réception, puis dans le volet gauche, cliquez sur **mappages sortants**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Document source**|Sélectionner, dans la liste déroulante, le schéma source à utiliser avec ce port.|  
    |**Carte**|Sélectionner, dans la liste déroulante, le mappage à associer à ce port.|  
    |**Document cible**|Sélectionner, dans la liste déroulante, le schéma de destination à utiliser avec ce port.|  
  
8.  Une fois terminé de configurer le port de réception, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)