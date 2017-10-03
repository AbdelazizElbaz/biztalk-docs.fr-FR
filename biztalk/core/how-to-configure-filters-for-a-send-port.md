---
title: "Comment configurer des filtres pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, configuring
- filters, send ports
- configuring, filters
- managing [send ports], configuring
- send ports, configuring
- send ports, filters
- managing [send ports], filters
ms.assetid: ad13ca8e-bb1d-4449-8163-49dd9d5d92f8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7845b6189f86054ba9661ea450575a2dcfe47953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-filters-for-a-send-port"></a>Configuration des filtres pour un port d'envoi
Cette rubrique décrit la configuration des filtres pour un port d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les filtres vous permettent de créer des applications de routage basé sur le contenu ou de messagerie simple. Un filtre définit des conditions pour les champs ou les propriétés de message qui déterminent les messages acheminés au port d'envoi. Un filtre ne filtre pas les messages qu'une orchestration achemine vers le port d'envoi.  
  
 Vous pouvez créer une ou plusieurs expressions de filtre, lesquelles sont constituées d'une propriété de message, d'un opérateur et d'une valeur validée avec la propriété par le biais de l'opérateur.  
  
 Par exemple, vous pouvez créer l'expression suivante :  
  
 MSMQ.MsgID = 1  
  
 Avec ce filtre, le groupe de ports d'envoi s'abonnera uniquement aux messages ayant un ID de message MSMQ correspondant à 1.  
  
 Vous pouvez créer des expressions supplémentaires et leur définir une relation AND ou OR avec d'autres expressions, par exemple :  
  
 MSMQ.MsgID = 1 OR  
  
 SMTP.From = MyServer  
  
 Dans ce cas, le groupe de ports d'envoi s'abonnera à tous les messages ayant un ID de message MSMQ de 1 ou qui proviennent du serveur SMTP nommé MyServer.  
  
> [!NOTE]
>  Si vous créez un filtre pour un port d'envoi dans une application qui utilise un schéma de propriété d'une autre application et que vous importiez ensuite la première application dans un nouveau groupe BizTalk, vous ne recevrez pas de message vous avertissant de l'absence de schéma et le filtrage ne fonctionnera pas une fois l'application installée et démarrée. Vous pouvez corriger ce problème en important l'application qui contient le schéma avant d'installer l'application sans schéma.  
  
> [!NOTE]
>  Le développeur peut configurer des filtres pour un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-filters-for-a-send-port"></a>Pour configurer les filtres d'un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle configurer des filtres de port d'envoi.  
  
3.  Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **filtres**.  
  
4.  Configurer des filtres comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Delete**|Supprimer l'expression de filtre sélectionnée.|  
    |**Monter**|Déplacer la propriété sélectionnée vers le haut de la séquence d'expression du filtre.|  
    |**Descendre**|Déplacer la propriété sélectionnée vers le bas de la séquence d'expression du filtre.|  
    |**Propriété**|Dans la liste, cliquer sur une propriété de message à utiliser dans cette expression de filtre.|  
    |**Opérateur**|Entrer ou sélectionner l'opérateur de l'expression.|  
    |**Valeur**|Taper la valeur à valider pour la propriété. Le type de valeur accepté varie en fonction du type de propriété. Pour afficher le type de valeur autorisé pour une propriété, placez votre souris sur la propriété. Les valeurs acceptables sont les suivants : Int : (entier) il doit être un nombre entier. Chaîne : Une chaîne de caractères. dateTime : une date et/ou une heure dans. NET-format pris en charge. Pour plus d'informations sur les formats d'heure pris en charge par .NET, voir la rubrique « DateTimeFormatInfo Class » de l'aide .NET Framework.|  
    |**Regrouper par**|Sélectionnez **et** ou **ou** pour indiquer la relation entre ceci et autres expressions de filtre.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)