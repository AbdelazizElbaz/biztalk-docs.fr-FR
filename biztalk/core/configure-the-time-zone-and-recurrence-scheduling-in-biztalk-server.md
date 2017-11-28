---
title: "Configurer le fuseau horaire et la planification de périodicité dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60ae7be-747e-4034-8b99-46bd7e25fe67
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ab4cd85af0d15d7b089b106dc33aa77f1a10639
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server"></a>Configurer le fuseau horaire et la planification de périodicité dans BizTalk Server
Le fuseau horaire et configurez une planification périodique sur vos emplacements de réception dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , la fonctionnalité de planification avancée sur les emplacements de réception inclut certaines options. À l’aide d’advanced options de planification, définissez le fuseau horaire et également définir une planification périodique.

Cette rubrique vous montre comment configurer ces fonctionnalités.

## <a name="prerequisites"></a>Conditions préalables
Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

## <a name="time-zone"></a>Fuseau horaire

Le **planification** propriétés d’un emplacement de réception inclut un **fuseau horaire** propriété. Si la valeur, le fuseau horaire que vous choisissez dans l’emplacement de réception est utilisé au lieu du fuseau horaire sur l’ordinateur local. 

Toutes les dates et heures dans les **planification** propriétés sont spécifiques au fuseau horaire que vous choisissez. Toutes les planifications existantes sont migrées vers le fuseau horaire du serveur qui héberge la base de données de gestion BizTalk (BizTalkMgmtDb). 

Vous pouvez également ajuster pour l’heure d’été (DST). Lorsqu’elle est activée, la planification s’ajuste automatiquement à l’heure d’été du fuseau horaire que vous choisissez. Cette option n’a aucun impact sur la planification si :

* Le fuseau horaire spécifié n’a pas d’une heure
* L’heure d’été n’est pas prise en charge dans le fuseau horaire que vous choisissez

## <a name="enable-recurrence-schedule"></a>Activer la planification de la périodicité
1. Dans le **Administration de BizTalk Server** de la console, avec le bouton droit de vos emplacements de réception, puis sélectionnez **propriétés**. 
2. Sur le **planification** page, sélectionnez **activer la fenêtre de service**. Le **l’heure de début** et **heure de fin** définir la première fois que la planification est autorisée à exécuter :

    ![Activer les fenêtres de Service de Port de réception](../core/media/enable-service-windows-for-receive-port.PNG)

3. Les options de planification supplémentaires sont affichent :

    ![Planification avancées pour le Port de réception](../core/media/advanced-scheduling-for-receive-port.PNG)

4. Le **périodicité** s’exécute chaque jour, semaine ou mois que vous choisissez, le port de réception : 

    1. Utilisez le **quotidienne** périodicité pour exécuter le port de réception chaque *x* nombre de jours, en commençant à la **à partir de** date que vous choisissez, et uniquement dans le **fenêtre de service**  vous choisissez :

        ![Planification quotidienne](../core/media/daily-shcedule.png)

    2. Utilisez le **hebdomadaire** périodicité pour exécuter le port de réception d’un jour spécifique au sein d’une semaine et uniquement dans les **fenêtre de service** vous choisissez : 

        ![Planification hebdomadaire](../core/media/weekly-shcedule.png)

    3. Utilisez le **mensuel** périodicité pour exécuter le port de réception selon une planification mensuelle. Le **jours** et **sur** options sont disponibles. 
    
        Utilisez le **jours** périodicité pour exécuter le port de réception sur des dates spécifiques dans le **mois** vous choisissez : 

        ![Calendrier mensuel](../core/media/monthly-shcedule.PNG)

        Utilisez le **sur** périodicité pour exécuter le port de réception sur certains jours du mois :

        ![tous les mois selon la planification](../core/media/monthly-on-shcedule.PNG)

5. Sélectionnez **OK** pour enregistrer vos modifications. 

## <a name="see-also"></a>Voir aussi
[Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)