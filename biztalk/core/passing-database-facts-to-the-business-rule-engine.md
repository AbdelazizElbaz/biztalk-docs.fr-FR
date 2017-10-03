---
title: "Passage des faits de la base de données pour le moteur de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62285bbe-ee64-4c26-b48e-55f666dc1304
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01ae35802263b71965698e0bb56d1ddbee9ae0a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="passing-database-facts-to-the-business-rule-engine"></a>Transmission de faits de base de données au moteur de règles d'entreprise
Lorsque vous utilisez l’outil Éditeur des règles d’entreprise pour tester une stratégie qui nécessite un objet DataConnection/TypedDataTable en tant que fait, un objet DataConnection/TypedDataTable est automatiquement créé pour vous et déclaré dans la mémoire de travail du moteur de règles métier. De plus, toute mise à jour de la base de données effectuée par la stratégie est automatiquement validée.  
  
 En revanche, lorsque vous appelez la stratégie à partir d’une orchestration, soit par à l’aide de la forme Appeler règles, ou par programme, l’objet DataConnection/TypedDataTable n’est créé pour vous et les mises à jour de la base de données ne sont pas validées automatiquement. Dans ce cas, vous devez créer un objet DataConnection/TypedDataTable passez-le en tant que fait au moteur de règles et valider les modifications de la base de données par programme en utilisant l’une des méthodes suivantes.  
  
## <a name="passing-a-dataconnection-object-from-an-orchestration"></a>Transmission d'un objet DataConnection à partir d'une orchestration  
 Le code ci-dessous montre comment créer un objet DataConnection dans l'orchestration, configurer la forme Appeler règles pour transmettre l'objet DataConnection en tant que paramètre, puis valider les modifications de la base de données une fois la stratégie exécutée.  
  
1.  Créez les variables suivantes à l'aide de l'onglet Vue Orchestration lorsque l'orchestration est ouverte dans le Concepteur d'orchestration.  
  
    ```  
    DataCon of type Microsoft.RuleEngine.DataConnection   
    SqlCon of type System.Data.SqlClient.SqlConnection   
    SqlTran of type System.Data.SqlClient.SqlTransaction   
    ```  
  
2.  Dans une forme Expression avant la forme Appeler règles, créez un objet DataConnection. L’exemple de code suivant montre comment créer un objet DataConnection.  
  
    ```  
    SqlCon.ConnectionString = "Data Source=(local);Initial Catalog=Test;Integrated Security=SSPI";   
    SqlCon.Open();   
    SqlTran = SqlCon.BeginTransaction();   
    DataCon = new Microsoft.RuleEngine.DataConnection("test", "FlagTable", SqlCon, SqlTran);    
    ```  
  
3.  Configurez la forme Appeler règles pour transmettre la variable DataCon en tant que paramètre. Pour plus d’informations, consultez [l’utilisation de la forme de règles d’appeler](../core/how-to-use-the-call-rules-shape.md).  
  
4.  Dans une forme Expression située après la forme Appeler règles, validez les modifications que la stratégie a apportées à la base de données. L'exemple de code suivant démontre comment valider les modifications que la stratégie a apportées à la base de données.  
  
    ```  
    DataCon.Update();   
    SqlTran.Commit();  
    ```  
  
> [!NOTE]
>  Vous devez utiliser un [SqlTransaction](http://msdn.microsoft.com/library/system.data.sqlclient.sqltransaction.aspx) de l’objet uniquement si la stratégie met à jour la base de données.  
  
## <a name="passing-a-dataconnection-object-from-a-fact-retriever"></a>Transmission d'un objet DataConnection à partir d'un extracteur de faits  
 Voici les étapes courantes à effectuer pour transmettre un objet DataConnection à partir d'un extracteur de faits.  
  
1.  Créez un extracteur de faits qui puisse créer et déclarer un objet DataConnection dans la mémoire de travail du moteur de règles. Pour plus d’informations sur la création d’un extracteur de faits, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md).  
  
2.  Implémentez la [IFactRemover](http://msdn.microsoft.com/library/Microsoft.RuleEngine.IFactRemover.aspx) interface sur l’extracteur de faits et de valider les modifications de base de données à partir de la [UpdateFactsAfterExecution](http://msdn.microsoft.com/library/microsoft.ruleengine.ifactremover.updatefactsafterexecution.aspx) (méthode). Une fois ceci effectué avec l'exécution de la stratégie, cette méthode est appelée par le moteur de règle.  
  
3.  Configurez la stratégie pour utiliser l'extracteur de faits à l'aide de l'Éditeur des règles d'entreprise. Pour plus d’informations, consultez [comment configurer un extracteur de faits pour une stratégie](../core/how-to-configure-a-fact-retriever-for-a-policy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données dans le moteur de règles d’entreprise](../core/data-access-in-the-business-rule-engine.md)   
 [Comment créer un extracteur de faits](../core/how-to-create-a-fact-retriever.md)   
 [Comment configurer un extracteur de faits pour une stratégie](../core/how-to-configure-a-fact-retriever-for-a-policy.md)