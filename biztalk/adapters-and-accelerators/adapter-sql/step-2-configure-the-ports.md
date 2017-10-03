---
title: "Étape 2 : Configurer les Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e804da96-26ae-482d-b6e1-67af24d639d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e31746fbbc34e24ab1638cb52c84f99e43a876b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-the-ports"></a>Étape 2 : Configurer les Ports
![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** dans cette étape, vous créez les ports physiques dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous créez un port physique pour chaque port logique que vous avez créé dans l’orchestration. Vous allez créer les ports suivants :  
  
-   WCF-Custom unidirectionnel port de réception pour recevoir des messages de notification pour les modifications apportées aux **employé** table dans une base de données SQL Server.  
  
-   Une requête-réponse WCF-Custom port d’envoi pour envoyer des messages de demande et de recevoir la réponse pour l’appel de la **UPDATE_EMPLOYEE** procédure stockée et d’effectuer l’opération d’insertion sur la **Purchase_Order**table. Dans l’orchestration, vous avez utilisé le même port d’envoi pour effectuer les opérations. De même, dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous allez utiliser un port d’envoi unique pour les deux opérations.  
  
-   Un port d’envoi unidirectionnel pour envoyer la réponse pour l’opération d’insertion. Dans ce didacticiel, car vous avez besoin informer le service des achats via un message électronique, vous créez ce port d’envoi en tant qu’un port SMTP.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 1 : déployer l’Orchestration](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md)).  
  
### <a name="to-create-a-physical-one-way-receive-port"></a>Pour créer les port de réception unidirectionnelle physique  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console sur le côté gauche, développez **Administration de BizTalk Server**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.  
  
3.  Développez **groupe BizTalk**, développez **Applications**, développez **SampleApplication**. Pour ce didacticiel, vous créez les ports et les applications au sein de l’application SampleApplication.  
  
4.  Suivez les instructions sous la section « Déploiement de cartes pour recevoir des Messages à partir de SQL Server » de [configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md). Nommez le port **NotifyReceivePort**.  
  
5.  Veillez à définir les propriétés de liaison suivantes pour configurer l’adaptateur pour recevoir des notifications de modifications apportées à la **employé** table.  
  
    |Propriété de liaison|Valeur|  
    |----------------------|-----------|  
    |**InboundOperationType**|Affectez la valeur **Notification**.|  
    |**NotificationStatement**|Affectez la valeur :<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **Remarque :** vous devez spécifier plus précisément les noms de colonnes dans l’instruction comme indiqué dans l’instruction Select suivante. En outre, vous devez toujours spécifier le nom de table, ainsi que le nom du schéma, par exemple, `dbo.Employee`.|  
    |**NotifyOnListenerStart**|Affectez la valeur **True**.|  
  
     Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
### <a name="to-create-a-request-response-send-port-for-two-operations"></a>Pour créer une requête-réponse un port d’envoi pour les deux opérations  
  
1.  Suivez les instructions sous la section « Déploiement de cartes pour envoi de Messages à SQL Server » de [configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md). Nommez le port **SQLOutboundPort**.  
  
2.  Étant donné que vous effectuez deux opérations utilisant le même port d’envoi, vous devez utiliser mappage d’action dynamique pour spécifier l’action pour l’opération. Lors de la configuration du port, dans le **Action** , spécifiez le mappage d’action de la manière suivante :  
  
    ```  
    \<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
      <Operation Name="UpdateEmp" Action="TypedProcedure/dbo/UPDATE_EMPLOYEE" />  
      <Operation Name="InsertPO" Action="TableOp/Insert/dbo/Purchase_Order" />  
    </BtsActionMapping>  
    ```  
  
     Notez que dans l’orchestration, vous avez créé deux opérations pour le port d’envoi requête-réponse : **UpdateEmp** et **InsertPO**. Par conséquent, dans la configuration du port physique fournissent les mêmes noms d’opération dans le mappage d’action dynamique. Dans l’extrait ci-dessus, l’action pour **UpdateEmp** opération est `TypedProcedure/dbo/UPDATE_EMPLOYEE`. De même, l’action pour **InsertPO** opération est `TableOp/Insert/dbo/Purchase_Order`.  
  
3.  Vous devez également configurer le port d’envoi pour utiliser le Mappeur que vous avez créé dans l’orchestration pour mapper le message de réponse de **UPDATE_EMPLOYEE** procédure stockée pour le message de demande pour l’opération Insert sur **Purchase_ Commande** table. Pour cela :  
  
    1.  Avec le bouton droit de la SQLOutboundPort dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, puis cliquez sur **propriétés**.  
  
    2.  À partir de la **SQLOutboundPort – propriétés de Port d’envoi** boîte de dialogue, dans le volet gauche, cliquez sur **mappages sortants**.  
  
    3.  Dans le volet de droite, dans le **mappages sortants** , cliquez sur la cellule sous la **carte** colonne, puis dans la liste déroulante, sélectionnez **Transform_1**. C’est le nom de la carte que vous avez créé dans l’orchestration BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
         Cliquez sur **OK**.  
  
         ![Configurer le mappage sortant](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-010-map-ports.gif "sql_adap_tut_010_map_ports")  
  
### <a name="to-create-an-smtp-send-port"></a>Pour créer un port d’envoi SMTP  
  
1.  Suivez les instructions situées sous la « comment configurer un Port d’envoi SMTP avec le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration « section à [http://go.microsoft.com/fwlink/?LinkId=141549](http://go.microsoft.com/fwlink/?LinkId=141549). Nommez le port **EmailResponse**.  
  
2.  Dans le cadre de la configuration du port, spécifiez l’adresse de messagerie pour le service des achats pour la **à** propriété.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez créé un WCF-Custom port de réception pour recevoir des notifications à partir de SQL Server, port d’envoi WCF-Custom pour effectuer des opérations sur SQL Server et un port SMTP pour envoyer la réponse à partir de SQL Server en tant qu’un message électronique au service des achats.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Configurer et démarrer l’application BizTalk, comme décrit dans [étape 3 : configurer et démarrer l’Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Déployer l’Orchestration](../../adapters-and-accelerators/adapter-sql/step-1-deploy-the-orchestration.md)   
 [Étape 3 : Configurer et démarrer l’Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)   
 [Leçon 5 : Déployer la Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)