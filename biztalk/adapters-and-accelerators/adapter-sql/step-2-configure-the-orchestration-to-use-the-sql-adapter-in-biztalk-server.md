---
title: "Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6152560-5ff0-4bdc-818c-e906b9642f52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b090ae83f0ca36bb4ae95795480d5f0d1661f16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-using-the-sql-adapter"></a>Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server à l’aide de l’adaptateur SQL
![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous effectuez les tâches suivantes :  
  
-   Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages à partir de la base de données SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.  
  
-   Configurer l’orchestration vous avez déployé à l’étape précédente pour utiliser le port WCF-Custom.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Doit avoir déployé l’orchestration BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom, comme décrit dans [étape 1 : modifier le projet BizTalk à l’aide de l’adaptateur SQL vPrev](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md).  
  
### <a name="to-create-a-wcf-custom-port"></a>Pour créer un port personnalisé WCF  
  
1.  Lorsque vous générez le schéma pour une opération sur la base de données SQL Server à l’aide [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk. Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception. Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/48de3a04-4ce8-4ba9-91b6-7e125689fd53).  
  
2.  Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
3.  Cliquez sur le port WCF-Custom, puis cliquez sur **propriétés**.  
  
4.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, spécifiez les informations d’identification pour se connecter à une base de données SQL Server, puis cliquez sur **OK**.  
  
6.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**. Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **ResponseMap**.  
  
     ![Configurer le mappage entrant](../../adapters-and-accelerators/adapter-sql/media/21e5a23c-7319-4324-8f09-52118ebeeea9.gif "21e5a23c-7319-4324-8f09-52118ebeeea9")  
  
7.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages sortants**. Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **RequestMap**.  
  
     ![Configurer le mappage sortant](../../adapters-and-accelerators/adapter-sql/media/5b54e09b-8784-4df6-a279-e8aed813114e.gif "5b54e09b-8784-4df6-a279-e8aed813114e")  
  
8.  Cliquez sur **OK**.  
  
### <a name="to-configure-the-biztalk-application"></a>Pour configurer l’application BizTalk  
  
1.  Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez l’Application BizTalk où l’orchestration est déployée.  
  
2.  Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.  
  
3.  Dans le volet gauche, cliquez sur l’orchestration à configurer. Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.  
  
4.  Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
    1.  Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.  
  
    2.  Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données SQL Server.  
  
    3.  Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.  
  
    4.  Cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages à la base de données SQL Server à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour effectuer une opération d’insertion sur la base de données SQL Server, comme décrit dans [étape 3 : tester l’Application migrée qui utilise l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Migrer des projets BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-1-migrate-biztalk-projects-to-the-sql-adapter.md)