---
title: Comment configurer une Application | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, applications
- applications, configuring
ms.assetid: e1cd1efb-e1ea-4344-8e23-668628d6c5a9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 888fc0ff78ebac3ac2314fe3106de4b7b6b51f16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-application"></a>Configuration d'une application
La présente rubrique explique comment configurer les artefacts d'une application à l'aide de la console Administration de BizTalk Server, de la façon suivante :  
  
-   liaison des ports logiques et liens de rôles aux ports physiques et tiers ;  
  
-   mappage des orchestrations à l'hôte sous lequel elles doivent être exécutées ;  
  
-   configuration des ports d'envoi et de réception, des groupes de ports d'envoi et des emplacements de réception.  
  
 Si l'application ne contient pas au moins une orchestration, un port d'envoi, un groupe de ports d'envoi, un port de réception ou un emplacement de réception, les informations de cette rubrique ne s'appliquent pas.  
  
 À l’issue de cette configuration, vous serez en mesure de démarrer l’application, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
> [!NOTE]
>  Vous pouvez également configurer les artefacts de manière individuelle à partir de l'application. Pour plus d'informations sur la configuration des artefacts individuels, voir les liens à la fin de cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-an-application"></a>Pour configurer une application  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, cliquez sur l’application, puis cliquez sur **configurer**.  
  
3.  Dans le **Orchestrations** liste dans le volet gauche, cliquez sur une orchestration, configurer les propriétés comme décrit dans le tableau suivant, puis cliquez sur **OK**. S’il n’y a aucune orchestration dans cette application, le **Orchestrations** liste n’affiche pas.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Hôte**|Choisir dans la liste déroulante un hôte dans lequel inscrire l'application.|  
    |**Liaisons - Ports logiques entrants**|Afficher le nom d'un port logique d'entrée. Les ports logiques se trouvent dans les surfaces de port des orchestrations.|  
    |**Liaisons - Ports de réception**|Dans la liste déroulante, sélectionner le port de réception physique à lier au port logique entrant correspondant. Cette liste contient les ports de l'application active, ainsi que les ports des éventuelles applications référencées.|  
    |**Liaisons - Ports logiques sortants**|Afficher le nom d'un port logique de sortie. Les ports logiques se trouvent dans les surfaces de port des orchestrations.|  
    |**Liaisons - groupes de ports d’envoi d’envoi**|Dans la liste déroulante, sélectionner le port d'envoi ou le groupe de ports d'envoi à lier au port logique sortant correspondant. Cette liste contient les ports de l'application active, ainsi que les ports des éventuelles applications référencées.|  
  
4.  Dans le **messagerie** dans le volet gauche, cliquez sur **Ports d’envoi et groupes de ports d’envoi**, configurez les propriétés comme décrit dans le tableau suivant, puis cliquez sur **OK**. Cette liste contient tous les ports d'envoi et groupes de ports d'envoi de l'application active.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nouveau**|Créer un port d'envoi ou un groupe de ports d'envoi. Options pour envoyer des ports sont identiques aux options disponibles lorsque vous cliquez sur le **Ports d’envoi** nœud dans l’arborescence de la console et pointez sur **nouveau**. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Consultez également [la création d’un groupe de ports d’envoi](../core/how-to-create-a-send-port-group.md).|  
    |**Propriétés**|Afficher les propriétés du port d'envoi ou du groupe de ports d'envoi sélectionné. Si vous sélectionnez un port d’envoi, le **propriétés de Port d’envoi** page affiche, où vous pouvez configurer le port. Si vous sélectionnez un groupe de ports d’envoi, le **propriétés groupes de ports d’envoi** page affiche, où vous pouvez configurer le groupe de ports d’envoi. Pour plus d’informations sur la configuration des propriétés, consultez [gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md).|  
    |**Nom**|Afficher le nom des ports d'envoi physiques.|  
    |**Filter**|Afficher l'expression de filtre appliquée à ce port d'envoi. Les filtres sont définis dans le **propriétés de Port d’envoi** fenêtre.|  
    |**URI**|Afficher l'URI du port sélectionné.|  
  
5.  Dans le **messagerie** dans le volet gauche, cliquez sur **Ports et emplacements**, configurez les propriétés comme décrit dans le tableau suivant, puis cliquez sur **OK**. Cette liste contient tous les ports et emplacements de réception de l'application active.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nouveau**|Créer un port de réception. Options pour recevoir des nouveaux ports sont identiques aux options disponibles lorsque vous cliquez sur le **Ports de réception** nœud dans l’arborescence de la console et pointez sur **nouveau**. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).|  
    |**Propriétés**|Afficher les propriétés de l'élément sélectionné. Si vous avez sélectionné un port de réception, le **propriétés du Port de réception** page affiche, où vous pouvez configurer le port. Si vous avez sélectionné un emplacement de réception, le **propriétés des emplacements de réception** page affiche, où vous pouvez configurer l’emplacement de réception. Pour sélectionner un port de réception, cliquez sur le texte en gras à droite de **port de réception**. Pour plus d’informations sur la configuration des propriétés, consultez [Ports de réception gestion](../core/managing-receive-ports.md). Consultez également [la gestion des emplacements de réception](../core/managing-receive-locations.md).|  
    |**Nom**|Afficher le nom de l'emplacement de réception associé à un port de réception.|  
    |**URI**|Afficher l'URI de l'emplacement de réception sélectionné.|  
  
6.  Dans le volet gauche, cliquez sur **des liens de rôle**, configurez les propriétés décrites dans le tableau suivant, puis cliquez sur **OK**. S’il en existe aucun lien de rôle dans l’application, le **des liens de rôle** n’affiche pas de lien.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Inscrire**|Cliquez pour afficher les **inscrire les tiers** boîte de dialogue, où vous pouvez sélectionner un tiers à participer à l’échange défini par le rôle.|  
    |**Annuler l’inscription**|Retirer le tiers sélectionné de l'échange.|  
    |**Lier**|Établir une connexion entre le lien de rôle et les ports physiques par le biais d'un tiers.|  
    |**Tiers**|Afficher le nom du ou des tiers inscrits à ce rôle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Gestion des liens de rôle](../core/managing-role-links.md)   
 [La gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md)   
 [La gestion des Ports de réception](../core/managing-receive-ports.md)   
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)