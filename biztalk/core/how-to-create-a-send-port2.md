---
title: "Comment créer un Port2 envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.procedure.createsendport
helpviewer_keywords:
- managing [send ports], creating
- creating, send ports
- send ports, creating
ms.assetid: 7f0d07b8-1ac5-4032-bb08-2f7e05185f86
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796ba5da53257d0f198e4b8bf13ee81835efcf4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-send-port"></a>Comment créer un Port d’envoi
La présente rubrique explique comment créer un port d'envoi à l'aide de la console Administration de BizTalk Server. Lorsque vous créez un port d'envoi, vous devez sélectionner le type de port d'envoi à créer, comme indiqué ci-dessous :  
  
-   Unidirectionnel statique : un port d'envoi uniquement.  
  
-   Sollicitation-réponse statique : un port d'envoi qui attend une réponse.  
  
-   Unidirectionnel dynamique : un port d'envoi seulement pouvant être lié à un protocole et à un emplacement lors de l'exécution en fonction des propriétés de message.  
  
-   Sollicitation-réponse dynamique : un port d'envoi qui attend une réponse et pouvant être lié à un protocole et à un emplacement lors de l'exécution en fonction des propriétés de message.  
  
 Après la création d'un port d'envoi, vous pouvez effectuer les étapes supplémentaires suivantes pour terminer la configuration :  
  
-   Configuration de transport des options avancées, telles que le nombre de tentatives d’envoi de messages sur l’échec d’un message et la planification de fenêtre de service pour le port, comme décrit dans [comment configurer les Options avancées Transport pour un Port d’envoi](../core/how-to-configure-transport-advanced-options-for-a-send-port.md).  
  
-   Configurer un transport secondaire, dans le transport principal ne fonctionne pas, comme décrit dans des événements [comment configurer d’Options de Transport secondaire pour un Port d’envoi](../core/how-to-configure-backup-transport-options-for-a-send-port.md).  
  
-   Configurer des filtres pour déterminer quels messages sont routés vers ce port d’envoi à partir de la boîte de message, comme décrit dans [comment configurer des filtres pour un Port d’envoi](../core/how-to-configure-filters-for-a-send-port.md).  
  
-   Attribuer un certificat de sécurité pour le port d’envoi pour chiffrer ou signer des documents traités par le port d’envoi, comme décrit dans [comment attribuer un certificat à un Port d’envoi](../core/how-to-assign-a-certificate-to-a-send-port.md).  
  
-   Configurez les options de suivi pour les messages traités par le port d’envoi, comme décrit dans [comment configurer le suivi pour un Port d’envoi](../core/how-to-configure-tracking-for-a-send-port.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md). Vous avez, en outre, besoin des autorisations des administrateurs d'applications associées à authentification unique pour la base de données d'authentification unique de l'entreprise. Pour plus d’informations, consultez [groupes utilisateur SSO](../core/sso-user-groups.md).  
  
### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle créer un port d'envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur le type de port à créer.  
  
4.  Dans le **propriétés des Ports d’envoi** fenêtre, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Indiquer le nom du nouveau port d'envoi. Ce nom doit être unique dans le groupe BizTalk.|  
    |**Type de transport**|Sélectionner le type ou le protocole de transport adéquat dans la liste déroulante. En cas de sélection d'un port sollicitation-réponse, seuls les types de transports prenant en charge les sollicitations-réponses sont disponibles dans la liste déroulante. Cette propriété est uniquement disponible pour les ports statiques.|  
    |**Configurer**|Après avoir sélectionné le type de transport, cliquez sur **configurer** pour afficher les **propriétés du Transport** boîte de dialogue, qui fournit des options de configuration spécifique au transport. Cette propriété est uniquement disponible pour les ports statiques. Cliquez sur **aide** dans la boîte de dialogue pour obtenir des instructions de configuration.|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionner l'instance de l'hôte dans laquelle l'adaptateur d'envoi est exécuté. Cette propriété est uniquement disponible pour les ports statiques.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionner le pipeline en charge du traitement des messages émis par ce port. Après avoir sélectionné le pipeline, vous pouvez cliquer sur le bouton de sélection adjacent (**...** ) pour afficher la **configurer le Pipeline** boîte de dialogue, où vous configurez les propriétés de pipeline par instance pour ce port. Cliquez sur **aide** dans la boîte de dialogue pour obtenir des instructions de configuration.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionner le pipeline en charge du traitement des messages reçus par ce port. Les réponses aux messages reçus par ce pipeline sont renvoyées par ce même pipeline. Après avoir sélectionné le pipeline, vous pouvez cliquer sur le bouton de sélection adjacent (**...** ) pour afficher la **configurer le Pipeline** boîte de dialogue, où vous configurez les propriétés de pipeline par instance pour ce port. Cette propriété est uniquement disponible pour des ports de sollicitation-réponse.|  
  
5.  Si vous créez un port d’envoi avec sollicitation-réponse, dans le volet gauche, cliquez sur **mappages entrants** et procédez comme suit, en répétant que nécessaire si vous souhaitez ajouter plusieurs mappages :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Document source**|Dans la liste déroulante, sélectionner le document source du mappage entrant. Plusieurs mappages peuvent être définis pour un même port d'envoi, mais tous doivent avoir un document source unique.|  
    |**Carte**|Dans la liste déroulante, sélectionnez le mappage à associer aux documents source et cible.|  
    |**Document cible**|Dans la liste déroulante, sélectionner le document cible du mappage entrant.|  
  
6.  Dans le volet gauche, cliquez sur **mappages sortants** et procédez comme suit, en répétant que nécessaire si vous souhaitez ajouter plusieurs mappages :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Document source**|Sélectionner le document source du mappage sortant dans la liste déroulante.|  
    |**Carte**|Dans la liste déroulante, sélectionnez le mappage à associer aux documents source et cible.|  
    |**Document cible**|Sélectionner le document cible du mappage sortant dans la liste déroulante.|  
  
7.  Une fois terminé de configurer le port d’envoi, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)   
 [Gestion des Pipelines](../core/managing-pipelines.md)   
 [La gestion des mappages](../core/managing-maps.md)