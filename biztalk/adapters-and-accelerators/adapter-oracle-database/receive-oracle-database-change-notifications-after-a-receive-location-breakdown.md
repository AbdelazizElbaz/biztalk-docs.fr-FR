---
title: "Recevoir des notifications de modification de base de données Oracle après une répartition d’emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22ad6da2-2979-4158-b1d1-d54095223af9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f20fdcd30362a87a49be17d061a9fe86595c78c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications-after-a-receive-location-breakdown"></a>Recevoir des notifications de modification de base de données Oracle après une répartition d’emplacement de réception
Envisagez un scénario où vous avez une application BizTalk qui reçoit les messages de notification de modification de base de données lorsque des modifications sont apportées à la table ACCOUNTACTIVITY. Si l’emplacement de réception est configuré en tant que partie de décompose l’application BizTalk et simultanément les enregistrements sont ajoutés dans la table ACCOUNTACTIVITY, vous ne recevrez pas de notifications pour les enregistrements récemment ajoutés. Vous également ne saura pas quand l’emplacement de réception est à nouveau disponible. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose une propriété de liaison, **NotifyOnListenerStart**, que vous pouvez configurer pour obtenir une notification indiquant que l’emplacement de réception a récupéré. Vous pouvez spécifier les valeurs suivantes pour le **NotifyOnListenerStart** propriété de liaison :  
  
-   Définissez cette propriété sur **True**, pour recevoir une notification informant que l’emplacement de réception est disponible dès que l’emplacement de réception récupère.  
  
-   Définissez cette propriété sur **False**, ne pas recevoir une notification informant que l’emplacement de réception a récupéré après restauration de l’emplacement de réception.  
  
 Valeur par défaut est **True**.  
  
## <a name="configuring-the-oracle-database-adapter-behavior"></a>Configuration du comportement de l’adaptateur de base de données Oracle  
 Pour une des méthodes, il est inutile d’exécuter des tâches de spécifiques lors de la génération de métadonnées ou lors de la configuration de l’application BizTalk. Vous ne devez définir le **NotifyOnListenerStart** propriété de liaison en conséquence sur le WCF-Custom ou WCF-OracleDB emplacement de réception. Pour créer l’application BizTalk, vous devez effectuer le même ensemble de tâches comme décrit dans [réception Oracle de base de données modifiées Notifications incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md). Toutefois, lors de la configuration de l’application BizTalk à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez essayer de modifier la valeur de **NotifyOnListenerStart** propriété de liaison et de voir la différence dans les deux configurations.  
  
 La figure suivante illustre la réception des notifications en fonction de la valeur de la **NotifyOnListenerStart** propriété de liaison.  
  
 ![Configurer l’adaptateur SQL pour les notifications](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")  
  
 Notez que dans le premier scénario, lorsque le **NotifyOnListenerStart** a la valeur **True** et enregistrements sont insérés dans la table de base de données lors de l’emplacement de réception est arrêté, l’adaptateur vous envoie uniquement un message de notification lorsque l’emplacement de réception s’affiche. L’adaptateur n’effectue aucune opération pour traiter les enregistrements qui ont été insérées pendant que l’emplacement de réception a été arrêté. Le client de l’adaptateur doit implémenter la logique pertinente dans leur application pour traiter les enregistrements qui ont été insérées pendant que l’emplacement de réception a été arrêté.  
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de modification de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)