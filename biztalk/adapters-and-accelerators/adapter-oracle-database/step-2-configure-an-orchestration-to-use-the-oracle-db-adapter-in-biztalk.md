---
title: "Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server pour utiliser l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 598b4ab0-ff22-4dfa-aa9c-774c60c90227
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b348a21a54ece0e5db736e18f60c9bed2b8d047d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-orchestration-in-biztalk-server-administration-console-to-use-the-oracle-database-adapter"></a>Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server pour utiliser l’adaptateur de base de données Oracle
![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous effectuez les tâches suivantes :  
  
-   Créer un WCF-Custom envoi-port de réception pour envoyer et recevoir des messages à partir de la base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Configurer ce port pour utiliser les mappages que vous avez créé à l’étape précédente.  
  
-   Configurer l’orchestration vous avez déployé dans la dernière étape pour utiliser le port WCF-Custom.  
  
## <a name="prerequisite"></a>Condition préalable  
  
-   Vous devez avoir déployé l’orchestration BizTalk pour laquelle vous souhaitez configurer le port WCF-Custom.  
  
### <a name="to-create-a-wcf-custom-port"></a>Pour créer un port personnalisé WCF  
  
1.  Lorsque vous générez le schéma pour une opération sur la base de données Oracle à l’aide [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], un fichier de liaison est également ajouté au projet BizTalk. Vous pouvez importer ce fichier de liaison dans votre BizTalk application pour créer un WCF-Custom envoi-port de réception. Pour obtenir des instructions sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](http://msdn.microsoft.com/library/4cac9267-8bd8-453b-96b4-5c038912463f).  
  
2.  Après avoir importé le fichier de liaison, un port d’envoi est créé sous le **Ports d’envoi** dossier dans la console Administration de BizTalk Server.  
  
3.  Cliquez sur le port WCF-Custom, sur **propriétés**.  
  
4.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur le **général** onglet. Dans le volet droit, cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à une base de données Oracle.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages entrants**. Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **ResponseMap**.  
  
     ![Configurer le mappage entrant](../../adapters-and-accelerators/adapter-oracle-database/media/a5e49da1-fe34-46fe-80ca-9316d217171a.gif "a5e49da1-fe34-46fe-80ca-9316d217171a")  
  
8.  Dans le volet gauche de la boîte de dialogue de propriétés de port envoi, cliquez sur **mappages sortants**. Dans le volet droit, cliquez sur le champ sous le **carte** colonne et à partir de la liste déroulante, sélectionnez **RequestMap**.  
  
     ![Configurer le mappage sortant](../../adapters-and-accelerators/adapter-oracle-database/media/697b23d8-4231-4718-8a52-8013fac35e3e.gif "697b23d8-4231-4718-8a52-8013fac35e3e")  
  
9. Cliquez sur **OK**.  
  
### <a name="to-configure-the-biztalk-application"></a>Pour configurer l’application BizTalk  
  
1.  Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.  
  
2.  Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.  
  
3.  Dans le volet gauche, cliquez sur l’orchestration à configurer. Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.  
  
4.  Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.  
  
    1.  Sélectionnez le port de fichier dans lequel vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    2.  Sélectionnez le port de fichier dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données Oracle.  
  
    3.  Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.  
  
    4.  Cliquez sur **OK**.  
  
     Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des messages à la base de données Oracle à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Vous devez maintenant tester l’application migrée de BizTalk en envoyant un message de demande pour effectuer une opération d’insertion sur la base de données Oracle, comme décrit dans [étape 3 : tester l’application migrée à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/step-3-test-the-migrated-application-to-oracle-database-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Migration des projets BizTalk](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)