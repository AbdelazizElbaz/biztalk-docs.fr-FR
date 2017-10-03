---
title: "Comment configurer la planification pour un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, receive locations
- managing [receive locations], scheduling
- scheduling, receive locations
- managing [receive locations], configuring
ms.assetid: 2653e1c3-ddbd-4d3f-be64-2a5fcd7cf267
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea43814d6b7c23875bc222f6d6bd4aee5468b60f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-scheduling-for-a-receive-location"></a>Configuration de la planification pour un emplacement de réception
La présente rubrique explique comment configurer les propriétés de planification pour un emplacement de réception à l'aide de la console Administration de BizTalk Server. Vous pouvez configurer les dates auxquelles vous voulez que l'emplacement de réception démarre et arrête le traitement des messages. Vous pouvez également définir certains moments de la journée auxquels vous voulez que l'emplacement de réception traite les messages.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-scheduling-for-a-receive-location"></a>Pour configurer la planification pour un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend l'emplacement de réception pour lequel vous voulez configurer la planification.  
  
3.  Cliquez sur **emplacements de réception**, avec le bouton droit à l’emplacement de réception, puis cliquez sur **propriétés**.  
  
4.  Dans le volet gauche, cliquez sur **planification**, configurez les propriétés de planification comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Date de début**|Activez cette case à cocher et sélectionnez la date de début du traitement des messages par l'emplacement de réception en cliquant sur la date voulue dans le calendrier. Pour changer l'année, cliquez sur l'année affichée.|  
    |**Date de fin**|Activez cette case à cocher et sélectionnez la date de fin du traitement des messages par l'emplacement de réception en cliquant sur la date voulue dans le calendrier. Cette propriété est facultative. Si vous n'indiquez pas de date de fin, l'emplacement de réception demeure actif jusqu'à ce que vous le désactiviez.|  
    |**Activer la fenêtre de service**|Cette case à cocher pour configurer l’emplacement de réception pour recevoir les messages uniquement à certaines heures de la journée, puis spécifiez les heures dans le **heure de début et l’heure d’arrêt** cases. Si cette case à cocher est désactivée, l'emplacement de réception reçoit des messages quelle que soit l'heure. La valeur par défaut est False (désactivé).|  
    |**Heure de début**|Indiquer l'heure à laquelle l'emplacement de réception doit commencer à recevoir des messages. Cette case est disponible uniquement lorsque le **activer la fenêtre de service** case à cocher est activée.|  
    |**Heure de fin**|Indiquer l'heure à laquelle l'emplacement de réception doit cesser de recevoir des messages. Cette case est disponible uniquement lorsque le **activer la fenêtre de service** case à cocher est activée.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)