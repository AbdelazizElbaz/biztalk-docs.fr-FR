---
title: "Étape 2 : Configurer l’Orchestration de BizTalk Server Administration Console1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration, configruing in BizTalk Server Administration console
- WCF-Custom port, creating
- migration
ms.assetid: fb057bce-5702-4ea0-8ed5-e299d3a78a11
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1783e56891ffd6d5d27058eab1df8a60663f481b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console"></a>Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server
![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous effectuez les tâches suivantes :  
  
-   Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages du système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.  
  
-   Configurer l’orchestration vous avez déployé dans la dernière étape pour utiliser le port WCF-Custom.  
  
## <a name="prerequisite"></a>Condition préalable  
  
-   Déployez l’orchestration de BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom.  
  
### <a name="to-create-a-wcf-custom-port"></a>Pour créer un port personnalisé WCF  
  
1.  Lorsque vous générez le schéma pour un RFC en utilisant le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk. Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception. Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/c927efde-29bd-4efe-9da5-942e7da65dbf).  
  
2.  Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans la console Administration de BizTalk Server.  
  
3.  Cliquez sur le port WCF-Custom, puis cliquez sur **propriétés**.  
  
4.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à un système SAP.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**. Dans le volet droit, cliquez sur le champ sous le **carte** colonne, puis, dans la liste déroulante, sélectionnez **ResponseMap**.  
  
     ![Configurer le mappage entrant sur le port WCF personnalisé](../../adapters-and-accelerators/adapter-sap/media/10129a7d-211b-464b-b05a-b3ea72f46873.gif "10129a7d-211b-464b-b05a-b3ea72f46873")  
  
8.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **les mappages sortants.** Dans le volet droit, cliquez sur le champ sous le **carte** colonne, puis, dans la liste déroulante, sélectionnez **RequestMap**.  
  
     ![Configurer le mappage sortant sur le port WCF personnalisé](../../adapters-and-accelerators/adapter-sap/media/4ffcb4cd-4f53-4b67-92e2-3225d15d97ee.gif "4ffcb4cd-4f53-4b67-92e2-3225d15d97ee")  
  
9. Cliquez sur **OK**.  
  
### <a name="to-configure-the-biztalk-application"></a>Pour configurer l’application BizTalk  
  
1.  Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez l’Application BizTalk où l’orchestration est déployée.  
  
2.  Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.  
  
3.  Dans le volet gauche, cliquez sur l’orchestration à configurer. Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.  
  
4.  Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.  
  
    1.  Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système SAP.  
  
    2.  Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse du système SAP.  
  
    3.  Sélectionnez le port d’envoi WCF-custom que vous avez créé précédemment dans cette rubrique.  
  
    4.  Cliquez sur **OK**.  
  
     Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages au système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour appeler le RFC SD_RFC_CUSTOMER_GET, comme décrit dans [étape 3 : tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : Migration d’un projet BizTalk RFC SAP](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)