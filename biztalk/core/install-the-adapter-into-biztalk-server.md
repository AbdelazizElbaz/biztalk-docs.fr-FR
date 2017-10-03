---
title: "Installer l’adaptateur dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1164468d-75a9-4116-87a6-6055948c198b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bc585e0574610a867d3f890ce456930bc936dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-adapter-into-biztalk-server"></a>Installation de l'adaptateur dans BizTalk Server
Une fois les entrées [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adéquates écrites dans le registre, l'adaptateur doit être ajouté à la base de données de gestion BizTalk. Une fois l'adaptateur ajouté à cette base de données, il est activement configuré et peut traiter des messages. Installez l'adaptateur dans la base de données à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Avant d'installer l'adaptateur dans la base de données, redémarrez l'instance de l'hôte.  
  
> [!NOTE]
>  Pour être visible et être ajouté à la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'adaptateur doit être correctement inscrit dans le Registre HKLM et doit implémenter les interfaces d'adaptateur adéquates.  
  
### <a name="to-install-the-static-sample-adapter"></a>Pour installer l'exemple d'adaptateur statique  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, double-cliquez sur le **groupe BizTalk** nœud.  
  
3.  Développez **paramètres de plateforme** et sélectionnez **cartes**.  
  
4.  Avec le bouton droit **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.  
  
5.  Dans le **propriétés de l’adaptateur** boîte de dialogue zone, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Nom|Type **statique**.|  
    |Adaptateur|Sélectionnez **Static DotNetFile** dans la liste déroulante.|  
    | Description|Type **exemple d’adaptateur statique**.|  
  
6.  Cliquez sur **OK**.  
  
     L'adaptateur statique apparaît dans la liste des adaptateurs, dans la fenêtre de droite de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-stop-and-restart-the-host-instance"></a>Pour arrêter et redémarrer l'instance de l'hôte  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, double-cliquez sur le **groupe BizTalk** nœud.  
  
3.  Développez **paramètres de plateforme**, sélectionnez **hôtes**, puis sélectionnez **BizTalkServerApplication** dans le volet de résultats.  
  
4.  Cliquez sur l’instance d’hôte (en règle générale, le nom d’ordinateur), puis cliquez sur **arrêter**.  
  
     L’état de l’instance d’hôte devient **arrêté**.  
  
5.  Dans le volet de résultats, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.  
  
     L’état de l’instance d’hôte devient **attente de démarrage**. Vous devez cliquer sur **Actualiser**, ou cliquez sur l’instance d’hôte, puis cliquez **Actualiser**, pour modifier l’état à **en cours d’exécution**.