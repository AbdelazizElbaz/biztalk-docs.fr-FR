---
title: "Générer et tester le projet d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b5eb486-99ae-4661-b0d0-d2d363d97b73
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dddde1681ab95a4c1fe7b762d7608cac33580411
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="build-and-test-the-adapter-project"></a>Génération et test du projet Adaptateur
Pour tester toutes les modifications apportées au projet AdapterManagement, regénérez le projet. Une fois la regénération terminée avec succès, exécutez l'Assistant Ajouter les métadonnées de l'adaptateur pour vous assurer que tous les fichiers XSD internes et externes sont ajoutés au projet AdapterManagement. Pour obtenir des instructions sur l’utilisation de l’Assistant Ajout de métadonnées d’adaptateur, consultez [comment ajouter les métadonnées de l’adaptateur à un projet BizTalk](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md).  
  
 Pour tester les modifications apportées aux schémas de configuration, ouvrez chacune des pages de propriétés générées par le fichier XSD pour vous assurer qu'elles demandent et acceptent les données correctes. En configurant un port d’envoi, l’emplacement de réception, gestionnaire d’envoi et dans le Gestionnaire de réception le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration**.**  
  
> [!NOTE]
>  Il se peut qu'un adaptateur ne contienne pas tous les schémas de configuration. Par exemple, un adaptateur d'envoi qui ne prend pas en charge la réception des messages ne contient que les schémas TransmitLocation.xsd et TransmitHandler.xsd.  
  
### <a name="to-test-the-transmitlocationxsd-file"></a>Test du fichier TransmitLocation.xsd  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Développez le [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration** nœud, développez **groupe BizTalk**, développez le **Ports d’envoi** nœud **nouveau**, et puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez le nom du port d’envoi. Développez le **Transport** nœud, puis sélectionnez le **principal** nœud.  
  
4.  Dans le volet droit, dans le **valeur de Type de Transport** boîte, sélectionnez **statique**, puis cliquez sur **configurer**. L'écran qui s'affiche doit contenir les champs que vous avez spécifiés dans le fichier TransmitLocation.xsd.  
  
### <a name="to-test-the-receivelocationxsd-file"></a>Test du fichier ReceiveLocation.xsd  
  
1.  Développez le [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration** nœud, développez **groupe BizTalk**, développez le **Ports de réception** collection, développez port de réception nouvellement créé ou le port de réception auquel vous souhaitez ajouter un emplacement de réception, cliquez sur le **emplacements de réception** collection, pointez sur **nouveau**, puis cliquez sur **l’emplacement de réception unidirectionnel**.  
  
2.  Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez le port.  
  
3.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, dans le volet gauche, sélectionnez le **général** nœud.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez un nom pour l’emplacement de réception.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, dans le volet droit, le **valeur de Type de Transport** boîte, sélectionnez **statique** puis cliquez sur **configurer**. L'écran qui s'affiche doit contenir les champs que vous avez spécifiés dans le fichier ReceiveLocation.xsd.  
  
### <a name="to-test-the-receivehandlerxsd-file"></a>Test du fichier ReceiveHandler.xsd  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Développez le [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration** nœud, développez **groupe BizTalk,** développez **paramètres de plateforme**, développez **cartes**, Cliquez sur **statique**, puis cliquez sur **BizTalkServerApplication** avec la direction de **réception**.  
  
3.  Dans le volet de résultats, cliquez sur le Gestionnaire de réception, puis cliquez sur **propriétés**. Sur le **général** , cliquez sur **propriétés**. L'écran qui s'affiche doit contenir les champs que vous avez spécifiés dans le fichier ReceiveHandler.xsd.  
  
### <a name="to-test-the-transmithandlerxsd-file"></a>Test du fichier TransmitHandler.xsd  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **statique**, puis cliquez sur **BizTalkServerApplication** avec la direction de **envoyer**.  
  
2.  Dans le volet de résultats, cliquez sur le Gestionnaire de réception, puis cliquez sur **propriétés**. Sur le **général** , cliquez sur **propriétés**. L'écran qui s'affiche doit contenir les champs que vous avez spécifiés dans le fichier TransmitHandler.xsd.