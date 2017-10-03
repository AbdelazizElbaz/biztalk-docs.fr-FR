---
title: "Étape 2 : Configurer un Port d’envoi unidirectionnel WCF-Custom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way send port, configuring
- migration
ms.assetid: ae13222e-42e7-45a7-9b2a-0a6779b21736
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f332e11aef32285fff84f0fe5f65834b1b20fc04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-a-wcf-custom-one-way-send-port"></a>Étape 2 : Configurer un Port d’envoi unidirectionnel WCF-Custom
![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous configurez un port personnalisé WCF pour envoyer l’IDOC de fichier plat à un système SAP. Après avoir configuré le port, vous configurez l’application BizTalk à utiliser le port d’envoi WCF-Custom.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir créé et déployé votre projet BizTalk de vPrev pour envoyer des IDOC à un système SAP.  
  
### <a name="to-configure-a-wcf-custom-one-way-send-port"></a>Pour configurer un port d’envoi unidirectionnel WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application sous lequel vous souhaitez créer le port d’envoi.  
  
4.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
5.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.  
  
6.  À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour envoyer des messages au système SAP. Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion du système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
         ![URI de connexion spécifié dans le port d’envoi](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")  
  
    2.  Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération. Pour envoyer un IDOC de fichier plat, vous devez utiliser le **SendIdoc** opération exposée par la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. **SendIdoc** opération permet aux clients de l’adaptateur envoyer des IDOC ayant un schéma faiblement typée. Pour plus d’informations, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md). L’illustration suivante montre le **Action** zone de texte avec l’action pour le **SendIdoc** opération.  
  
         ![Spécifier l’action dans le port d’envoi](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")  
  
    3.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**.  
  
    4.  Cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à un système SAP.  
  
    5.  Cliquez sur le **Messages** onglet et dans le **le corps du message WCF sortant** , choisissez le **modèle** option.  
  
    6.  Dans le **XML** texte, spécifiez le modèle qui servira à construire le message WCF. En procédant ainsi, vous créez un message qui est conforme à la **SendIdoc** opération pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour plus d’informations sur la structure du message pour le **SendIdoc** opération, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
         ![Spécifiez le modèle de message WCF sortant](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")  
  
         Pour l’opération SendIdoc, vous devez spécifier le modèle suivant :  
  
        ```  
        <SendIdoc xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/">  
        <idocData>\<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/></idocData>  
        </SendIdoc>  
        ```  
  
         Dans le modèle précédent, le `bts-msg-body` est port de réception IDOC XML qui est créé en utilisant le désassembleur de fichier plat associé au fichier. L’IDOC XML est encapsulé dans le message SendIdoc.  
  
    7.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** boîte de dialogue, à partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
9. À partir de la **pipeline d’envoi** la liste déroulante, sélectionnez **ConvertToFlatFile**. Ce pipeline assembleur de fichier plat fait déjà partie du projet BizTalk vPrev et est utilisé pour convertir un IDOC XML en un IDOC de fichier plat.  
  
10. Cliquez sur **OK**.  
  
### <a name="to-configure-the-biztalk-application"></a>Pour configurer l’application BizTalk  
  
1.  Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.  
  
2.  Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.  
  
3.  Dans le volet gauche, cliquez sur l’orchestration à configurer. Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.  
  
4.  Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.  
  
    1.  Sélectionnez le port de fichier dans lequel vous allez déposer l’IDOC de fichier plat.  
  
    2.  Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.  
  
    3.  Cliquez sur **OK**.  
  
     Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des IDOC à un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous devez maintenant tester l’application migrée de BizTalk en envoyant un IDOC de fichier plat, comme décrit dans [étape 3 : tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Migration d’un projet BizTalk SAP envoi IDOC](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)