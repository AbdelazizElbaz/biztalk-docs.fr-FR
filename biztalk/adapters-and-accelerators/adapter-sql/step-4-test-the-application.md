---
title: "Étape 4 : Tester l’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 488b13fa-7a71-4430-bbf5-dbf47ba55562
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 347c2bcf459d7e9ce7b1fb9efc07579be81d989d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-application"></a>Étape 4 : Tester l’Application
![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous testez l’application en insérant un enregistrement dans le **employé** table de la **ADAPTER_SAMPLES** base de données. Si l’application fonctionne correctement, l’orchestration reçoit une notification pour les modifications apportées à la **employé** table. L’orchestration extrait le type de notification reçue. Si la notification est pour une opération d’insertion, l’orchestration exécute la **UPDATE_EMPLOYEE** procédure stockée et reçoit une réponse. L’orchestration extrait les valeurs de **Employee_ID** et **nom** à partir de la réponse et les insère dans le **Purchase_Order** table.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez vérifier les éléments suivants :  
  
-   Un message de demande pour appeler le **UPDATE_EMPLOYEE** procédure stockée est disponible à l’adresse C:\TestLocation\CreateEmployeeMessage. Le message de demande ressemble à ceci :  
  
    ```  
    <UPDATE_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo" />  
    ```  
  
-   Un message de demande à appeler l’opération d’insertion sur la **Purchase_Order** table est disponible à l’adresse C:\TestLocation\CreatePOMessage. Le message de demande ressemble à ceci :  
  
    ```  
    <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Purchase_Order">  
      <Rows>  
        <Purchase_Order xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10</Employee_ID><Employee_Name>Employee_Name</Employee_Name>  
        </Purchase_Order>  
      </Rows>  
    </Insert>  
    ```  
  
    > [!NOTE]
    >  Les valeurs pour le **Employee_ID** et **Employee_Name** champs sont des espaces réservés. Les valeurs réelles sont insérés par l’orchestration au moment de l’exécution.  
  
-   Vous devez avoir terminé [étape 3 : configurer et démarrer l’Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md).  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Insérer un enregistrement dans le **employé** table. Vous pouvez le faire en exécutant l’instruction suivante à partir de SQL Server Management Studio.  
  
    ```  
    INSERT INTO [ADAPTER_SAMPLES].[dbo].[Employee] ([Name] ,[Designation] ,[Salary])  
    VALUES('John Smith' ,'Manager' ,500000)  
    ```  
  
2.  Vérifiez le **employé** table dans la base de données. Vous remarquerez que le nouvel enregistrement est ajouté par le **état** colonne est « 0 ».  
  
3.  Conserver l’actualisation du **employé** enregistrements de la table. Vous remarquerez que la **état** colonne pour le nouvel enregistrement est maintenant définie sur « 1 ».  
  
4.  Vérifiez le **Purchase_Order** table. Vous remarquerez qu’un enregistrement avec le même nom de l’employé et désignation, que vous avez fourni dans l’instruction Insert, est ajouté à la table.  
  
5.  Si vous avez fourni votre alias de messagerie dans la configuration du port SMTP, vous recevrez un message électronique avec le message de réponse pour l’opération d’insertion.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Tester l’application SampleApplication en insérant un enregistrement dans le **employé** table.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Si le test a réussi, félicitations ! Vous avez terminé la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] didacticiel.  
  
 Si le test a échoué, vérifiez votre travail avec attention et assurez-vous d'avoir ajouté les objets nécessaires et défini correctement leurs propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Configurer et démarrer l’Application](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)   
 [Leçon 5 : Déployer la Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)