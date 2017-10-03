---
title: "Comment configurer les Options de Transport secondaire pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- managing [send ports], configuring
- configuring, backing up [send ports]
- managing [send ports], backup options
- send ports, configuring
- send ports, backup options
ms.assetid: f05f57a6-e62b-4640-a6e2-cb73e9de2a14
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ff8b1354772290ce9e04742a6130a6f6f2df627
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-backup-transport-options-for-a-send-port"></a>Configuration des options de transport secondaire pour un port d'envoi
La présente rubrique explique comment configurer les options de transport secondaire pour un port d'envoi à l'aide de la console Administration de BizTalk Server. Le transport secondaire que vous spécifiez n'est effectif que lorsque le transport principal échoue. Configuration du transport principal est décrit dans [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
> [!NOTE]
>  Pour les ports dynamiques, il n'y a aucune propriété à configurer, car les options de transport sont définies automatiquement au moment de l'exécution.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-specify-transport-options-for-a-send-port"></a>Pour spécifier des options de transport pour un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer des options de transport secondaire.  
  
3.  Développez **Ports d’envoi**, cliquez sur le port d’envoi à configurer, cliquez sur **propriétés**, puis cliquez sur **Transport secondaire**.  
  
4.  Configurer les propriétés de transport secondaire comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Type**|Sélectionner le type ou le protocole de transport secondaire adéquat dans la liste déroulante. En cas de sélection d'un port sollicitation-réponse, seuls les types de transports prenant en charge les sollicitations-réponses sont disponibles dans la liste déroulante.|  
    |**Configurer**|Après avoir sélectionné le type de transport secondaire, cliquez sur **configurer**, puis configurez les propriétés du transport. Pour plus d’informations sur la configuration des propriétés, cliquez sur **aide**.|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionner l'instance de l'hôte dans laquelle l'adaptateur d'envoi est exécuté.|  
    |**Nombre de tentatives**|Indiquer le nombre de tentatives d'envoi d'un message en cas d'échec du message pour le port d'envoi. La valeur par défaut est 3 et la plage autorisée s'étend de 0 à 1 000.|  
    |**Intervalle avant nouvelle tentative**|Indiquer l'intervalle (en minutes) devant séparer chaque tentative d'envoi du message. La valeur par défaut est de 5 ; la plage autorisée est de 0 à 525 600.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)