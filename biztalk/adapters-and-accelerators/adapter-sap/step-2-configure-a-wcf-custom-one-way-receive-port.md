---
title: "Étape 2 : Configurer un WCF-Custom unidirectionnel Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way receive port, configuring
- migration
ms.assetid: e2a8f074-64d5-4e6c-84d0-318fb606c0ba
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6edf75f08bdf6a321188e484eb4f363366f8eb95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-a-wcf-custom-one-way-receive-port"></a>Étape 2 : Configurer un WCF-Custom unidirectionnel Port de réception
![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous configurez un port personnalisé WCF pour recevoir un IDOC de fichier plat à partir d’un système SAP. Après avoir configuré le port, vous configurez BizTalk application afin d’utiliser WCF-Custom port de réception.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir créé et déployé votre projet BizTalk de vPrev pour recevoir des IDOC à partir d’un système SAP.  
  
### <a name="to-configure-a-wcf-custom-one-way-receive-port"></a>Pour configurer les port de réception WCF-Custom unidirectionnel  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application sous lequel vous voulez créer le port de réception.  
  
4.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
5.  Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.  
  
6.  Sur le **emplacements de réception** , cliquez sur **nouveau**. Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :  
  
    1.  Spécifiez un nom pour l’emplacement de réception.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :  
  
    1.  Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour recevoir des messages à partir du système SAP. L’URI de connexion pour recevoir des messages à partir du système SAP doit être au format suivant :  
  
        ```  
        sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
        ```  
  
         L’illustration suivante montre la boîte de dialogue des propriétés de port avec l’URI spécifié :  
  
         ![URI de connexion pour recevoir des messages à partir de SAP](../../adapters-and-accelerators/adapter-sap/media/91e12582-aea3-4f13-8cdc-af69a9a11a5c.gif "91e12582-aea3-4f13-8cdc-af69a9a11a5c")  
  
         Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).  
  
    2.  Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**. Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        |Propriété de liaison|Affectez à la valeur|  
        |----------------------|------------------|  
        |flatFileSegmentIndicator|**SegmentType**. Cela indique que les fichiers plats doivent contenir le type de segment pour chaque segment dans l’IDOC.|  
        |padReceivedIdocWithSpaces|**Vrai**. Spécifie si chaque ligne dans l’IDOC est complétée avec des espaces pour la longueur correcte.|  
        |receiveIDocFormat|**Chaîne**. Spécifie que le message IDOC doit être représenté comme un champ de chaîne unique.|  
  
         Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    3.  Cliquez sur le **d’autres** onglet et spécifier les informations d’identification pour se connecter à un système SAP.  
  
    4.  Cliquez sur le **Messages** onglet et dans le **le corps du message BizTalk entrant** , choisissez le **chemin d’accès** option.  
  
    5.  Dans le **expression de chemin de corps** texte, spécifiez la requête XPath pour extraire l’IDOC de fichier plat du message XML. En procédant ainsi, le port de réception extrait les données de l’IDOC et ajuste la balise XML qui fait partie de la **ReceiveIdoc** opération pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour plus d’informations sur le schéma de message pour le **ReceiveIdoc** opération, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
         ![XPath de requête pour extraire le plate &#45; fichier IDOC](../../adapters-and-accelerators/adapter-sap/media/8b5b8165-a1e7-40ef-bcf7-de3149c6deb0.gif "8b5b8165-a1e7-40ef-bcf7-de3149c6deb0")  
  
         Vous devez spécifier la requête XPath suivante :  
  
        ```  
        /*[local-name()='ReceiveIdoc']/*[local-name()='idocData']  
        ```  
  
    6.  À partir de la **codage de nœud** la liste déroulante, sélectionnez **chaîne**.  
  
    7.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
9. Dans la boîte de dialogue Propriétés de l’emplacement de réception à partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
10. À partir de la **pipeline de réception** la liste déroulante, sélectionnez **ConvertToXML**. Ce pipeline désassembleur de fichier plat fait déjà partie du projet BizTalk vPrev pour convertir un IDOC de fichier plat en un IDOC XML.  
  
11. Cliquez sur **OK**.  
  
### <a name="to-configure-the-biztalk-application"></a>Pour configurer l’application BizTalk  
  
1.  Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.  
  
2.  Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.  
  
3.  Dans le volet gauche, cliquez sur l’orchestration à configurer. Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.  
  
4.  Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.  
  
    1.  Sélectionnez cette option WCF-Custom réception port que vous avez créé précédemment dans cette rubrique.  
  
    2.  Sélectionnez un port de fichier dans lequel vous recevez l’IDOC de fichier plat.  
  
    3.  Cliquez sur **OK**.  
  
     Pour plus d’informations sur la configuration d’une application, consultez [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui reçoit des IDOC à partir d’un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous devez maintenant tester l’application migrée de BizTalk en recevant un IDOC de fichier plat, comme décrit dans [étape 3 : tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Migration d’un SAP de réception projet BizTalk IDOC](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)