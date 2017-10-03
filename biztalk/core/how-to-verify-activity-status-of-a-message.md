---
title: "Comment vérifier l’état de l’activité d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, verifying status
- PeopleSoft Integration Broker
- verifying message status in PeopleSoft
- messages, verifying status
ms.assetid: b8cee6f9-0f65-4228-a87a-3f3aca6182bf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 872c1a1fcfcc905caf926c8299f56d49178a8448
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-verify-activity-status-of-a-message"></a>Vérification de l'état d'activité d'un message
Le PeopleSoft Integration Broker permet de créer un hôte et un port HTTP PeopleSoft auxquels PeopleSoft envoie des événements. Suivez les étapes ci-dessous pour vérifier que le message est actif et acheminé.  
  
### <a name="to-verify-that-a-message-is-active-and-routed-correctly"></a>Pour vérifier qu'un message est actif et correctement acheminé  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **nom de l’Application PeopleSoft**, puis sélectionnez **Concepteur d’applications**.  
  
2.  Sur le **PeopleSoft Sign-on** écran, entrez le **ID utilisateur** et **mot de passe**, puis cliquez sur **OK**.  
  
     ![](../core/media/psadapter-24-task-userpass.gif "PSAdapter_24_Task_UserPass")  
  
     ![](../core/media/psadapter-25-task-emptydesigner.gif "PSAdapter_25_Task_EmptyDesigner")  
  
3.  Dans le Concepteur d’applications, sur le **fichier** menu, pointez sur **ouvrir**, puis sélectionnez **Message**.  
  
     ![](../core/media/psadapter-26-task-filemessage.gif "PSAdapter_26_Task_FileMessage")  
  
4.  Dans le **ouvrir la définition de** écran, dans le **nom** , entrez `LOCATION_SYNC`, puis cliquez sur **ouvrir**.  
  
     ![](../core/media/psadapter-27-task-locationsync.gif "PSAdapter_27_Task_LocationSync")  
  
5.  Dans le **définitions correspondant aux critères de sélection** section, double-cliquez sur le **LOCATION_SYNC** message pour afficher les propriétés.  
  
     ![](../core/media/psadapter-28-task-locationproperties.gif "PSAdapter_28_Task_LocationProperties")  
  
6.  Dans le Concepteur d’applications, cliquez sur **LOCATION_TBL**, puis sélectionnez **propriétés de Message**.  
  
     ![](../core/media/psadapter-29-task-loctionmenu.gif "PSAdapter_29_Task_LoctionMenu")  
  
7.  Sur le **propriétés de Message** , cliquez sur le **utilisez** onglet.  
  
     Vérifiez les informations suivantes, puis cliquez sur **OK**.  
  
    1.  **Message :** Active  
  
    2.  **Canal de message :** ENTERPRISE_SETUP  
  
    3.  **Version par défaut :** VERSION_1  
  
     ![](../core/media/psadapter-30-task-messageuse.gif "PSAdapter_30_Task_MessageUse")  
  
8.  Quittez le Concepteur d'applications.  
  
     Cette procédure garantit que Message est à l'état actif, qu'il utilise VERSION_1 et circule à travers le canal ENTERPRISE_SETUP dans PeopleSoft.  
  
9. Configurez le fichier Integration.Gateway.properties de façon à ce qu'il puisse communiquer avec l'application PeopleSoft.  
  
     Vérifiez que les propriétés suivantes sont définies :  
  
    -   **IG.ISC.ServerURL :** //server:9000  
  
    -   **IG.ISC.UserID :** ID pour PS  
  
    -   **IG.ISC.Password :** mot de passe pour PS  
  
    -   **IG.ISC.toolsrel :** version spécifique  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Port et l’hôte de HTTP PeopleSoft](../core/creating-a-peoplesoft-http-host-and-port.md)