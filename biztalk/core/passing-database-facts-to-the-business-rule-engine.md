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
# <a name="passing-database-facts-to-the-business-rule-engine"></a><span data-ttu-id="0611f-102">Transmission de faits de base de données au moteur de règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="0611f-102">Passing Database Facts to the Business Rule Engine</span></span>
<span data-ttu-id="0611f-103">Lorsque vous utilisez l’outil Éditeur des règles d’entreprise pour tester une stratégie qui nécessite un objet DataConnection/TypedDataTable en tant que fait, un objet DataConnection/TypedDataTable est automatiquement créé pour vous et déclaré dans la mémoire de travail du moteur de règles métier.</span><span class="sxs-lookup"><span data-stu-id="0611f-103">When you use the Business Rule Composer tool to test a policy that requires a DataConnection/TypedDataTable object as a fact, a DataConnection/TypedDataTable object is automatically created for you and asserted into the Business Rule Engine's working memory.</span></span> <span data-ttu-id="0611f-104">De plus, toute mise à jour de la base de données effectuée par la stratégie est automatiquement validée.</span><span class="sxs-lookup"><span data-stu-id="0611f-104">Additionally, any database updates by the policy are committed automatically.</span></span>  
  
 <span data-ttu-id="0611f-105">En revanche, lorsque vous appelez la stratégie à partir d’une orchestration, soit par à l’aide de la forme Appeler règles, ou par programme, l’objet DataConnection/TypedDataTable n’est créé pour vous et les mises à jour de la base de données ne sont pas validées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0611f-105">In contrast, when you invoke the policy from an orchestration, either by using the Call Rules shape or programmatically, the DataConnection/TypedDataTable object is not created for you and the database updates are not committed automatically.</span></span> <span data-ttu-id="0611f-106">Dans ce cas, vous devez créer un objet DataConnection/TypedDataTable passez-le en tant que fait au moteur de règles et valider les modifications de la base de données par programme en utilisant l’une des méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="0611f-106">In this case, you should create a DataConnection/TypedDataTable object, pass it as a fact to the rule engine, and commit the database changes programmatically by using one of the following methods.</span></span>  
  
## <a name="passing-a-dataconnection-object-from-an-orchestration"></a><span data-ttu-id="0611f-107">Transmission d'un objet DataConnection à partir d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="0611f-107">Passing a DataConnection Object from an Orchestration</span></span>  
 <span data-ttu-id="0611f-108">Le code ci-dessous montre comment créer un objet DataConnection dans l'orchestration, configurer la forme Appeler règles pour transmettre l'objet DataConnection en tant que paramètre, puis valider les modifications de la base de données une fois la stratégie exécutée.</span><span class="sxs-lookup"><span data-stu-id="0611f-108">The following sample code demonstrates how to create a DataConnection object in the orchestration, configure the Call Rules shape to pass the DataConnection object as a parameter, and commit any database updates after the policy is executed.</span></span>  
  
1.  <span data-ttu-id="0611f-109">Créez les variables suivantes à l'aide de l'onglet Vue Orchestration lorsque l'orchestration est ouverte dans le Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="0611f-109">Create the following variables using the Orchestration View tab with the orchestration open in the Orchestration Designer.</span></span>  
  
    ```  
    DataCon of type Microsoft.RuleEngine.DataConnection   
    SqlCon of type System.Data.SqlClient.SqlConnection   
    SqlTran of type System.Data.SqlClient.SqlTransaction   
    ```  
  
2.  <span data-ttu-id="0611f-110">Dans une forme Expression avant la forme Appeler règles, créez un objet DataConnection.</span><span class="sxs-lookup"><span data-stu-id="0611f-110">In an Expression shape before the Call Rules shape, create a DataConnection object.</span></span> <span data-ttu-id="0611f-111">L’exemple de code suivant montre comment créer un objet DataConnection.</span><span class="sxs-lookup"><span data-stu-id="0611f-111">The following code example demonstrates how to create a DataConnection object.</span></span>  
  
    ```  
    SqlCon.ConnectionString = "Data Source=(local);Initial Catalog=Test;Integrated Security=SSPI";   
    SqlCon.Open();   
    SqlTran = SqlCon.BeginTransaction();   
    DataCon = new Microsoft.RuleEngine.DataConnection("test", "FlagTable", SqlCon, SqlTran);    
    ```  
  
3.  <span data-ttu-id="0611f-112">Configurez la forme Appeler règles pour transmettre la variable DataCon en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="0611f-112">Configure the Call Rules shape to pass the DataCon variable as a parameter.</span></span> <span data-ttu-id="0611f-113">Pour plus d’informations, consultez [l’utilisation de la forme de règles d’appeler](../core/how-to-use-the-call-rules-shape.md).</span><span class="sxs-lookup"><span data-stu-id="0611f-113">For more information, see [How to Use the Call Rules Shape](../core/how-to-use-the-call-rules-shape.md).</span></span>  
  
4.  <span data-ttu-id="0611f-114">Dans une forme Expression située après la forme Appeler règles, validez les modifications que la stratégie a apportées à la base de données.</span><span class="sxs-lookup"><span data-stu-id="0611f-114">In an Expression shape after the Call Rules shape, commit the database changes made by the policy.</span></span> <span data-ttu-id="0611f-115">L'exemple de code suivant démontre comment valider les modifications que la stratégie a apportées à la base de données.</span><span class="sxs-lookup"><span data-stu-id="0611f-115">The following code example demonstrates how to commit the database changes made by the policy.</span></span>  
  
    ```  
    DataCon.Update();   
    SqlTran.Commit();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="0611f-116">Vous devez utiliser un [SqlTransaction](http://msdn.microsoft.com/library/system.data.sqlclient.sqltransaction.aspx) de l’objet uniquement si la stratégie met à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="0611f-116">You need to use a [SqlTransaction](http://msdn.microsoft.com/library/system.data.sqlclient.sqltransaction.aspx) object only if the policy updates the database.</span></span>  
  
## <a name="passing-a-dataconnection-object-from-a-fact-retriever"></a><span data-ttu-id="0611f-117">Transmission d'un objet DataConnection à partir d'un extracteur de faits</span><span class="sxs-lookup"><span data-stu-id="0611f-117">Passing a DataConnection Object from a Fact Retriever</span></span>  
 <span data-ttu-id="0611f-118">Voici les étapes courantes à effectuer pour transmettre un objet DataConnection à partir d'un extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="0611f-118">Here are the typical steps you need to implement to pass a DataConnection object from a fact retriever component.</span></span>  
  
1.  <span data-ttu-id="0611f-119">Créez un extracteur de faits qui puisse créer et déclarer un objet DataConnection dans la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="0611f-119">Create a fact retriever component that creates and asserts a DataConnection object into the rule engine's working memory.</span></span> <span data-ttu-id="0611f-120">Pour plus d’informations sur la création d’un extracteur de faits, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md).</span><span class="sxs-lookup"><span data-stu-id="0611f-120">For more information about how to create a fact retriever component, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span>  
  
2.  <span data-ttu-id="0611f-121">Implémentez la [IFactRemover](http://msdn.microsoft.com/library/Microsoft.RuleEngine.IFactRemover.aspx) interface sur l’extracteur de faits et de valider les modifications de base de données à partir de la [UpdateFactsAfterExecution](http://msdn.microsoft.com/library/microsoft.ruleengine.ifactremover.updatefactsafterexecution.aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="0611f-121">Implement the [IFactRemover](http://msdn.microsoft.com/library/Microsoft.RuleEngine.IFactRemover.aspx) interface on fact retriever component, and commit the database changes from the [UpdateFactsAfterExecution](http://msdn.microsoft.com/library/microsoft.ruleengine.ifactremover.updatefactsafterexecution.aspx) method.</span></span> <span data-ttu-id="0611f-122">Une fois ceci effectué avec l'exécution de la stratégie, cette méthode est appelée par le moteur de règle.</span><span class="sxs-lookup"><span data-stu-id="0611f-122">This method is called by the rule engine after it is done with executing the policy.</span></span>  
  
3.  <span data-ttu-id="0611f-123">Configurez la stratégie pour utiliser l'extracteur de faits à l'aide de l'Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="0611f-123">Configure the policy to use the fact retriever component by using the Business Rule Composer tool.</span></span> <span data-ttu-id="0611f-124">Pour plus d’informations, consultez [comment configurer un extracteur de faits pour une stratégie](../core/how-to-configure-a-fact-retriever-for-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="0611f-124">For more information, see [How to Configure a Fact Retriever for a Policy](../core/how-to-configure-a-fact-retriever-for-a-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0611f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0611f-125">See Also</span></span>  
 <span data-ttu-id="0611f-126">[Accès aux données dans le moteur de règles d’entreprise](../core/data-access-in-the-business-rule-engine.md) </span><span class="sxs-lookup"><span data-stu-id="0611f-126">[Data Access in the Business Rule Engine](../core/data-access-in-the-business-rule-engine.md) </span></span>  
 <span data-ttu-id="0611f-127">[Comment créer un extracteur de faits](../core/how-to-create-a-fact-retriever.md) </span><span class="sxs-lookup"><span data-stu-id="0611f-127">[How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md) </span></span>  
 [<span data-ttu-id="0611f-128">Comment configurer un extracteur de faits pour une stratégie</span><span class="sxs-lookup"><span data-stu-id="0611f-128">How to Configure a Fact Retriever for a Policy</span></span>](../core/how-to-configure-a-fact-retriever-for-a-policy.md)