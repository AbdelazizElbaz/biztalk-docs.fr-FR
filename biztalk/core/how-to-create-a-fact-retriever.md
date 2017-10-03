---
title: "Comment créer un extracteur de faits | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IFactRetriever interface
- Business Rules Framework, bindings
- factsHandleIn object
- Business Rules Framework, code samples
- Business Rules Framework, fact retrievers
- UpdateFacts method
- Business Rules Framework, programming
ms.assetid: 503dc769-3ada-4099-a5fe-4dd03d995600
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20ea60356580ae7d5a6ac2be3336ec07314211f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-fact-retriever"></a><span data-ttu-id="0cd34-102">Création d'un extracteur de faits</span><span class="sxs-lookup"><span data-stu-id="0cd34-102">How to Create a Fact Retriever</span></span>
<span data-ttu-id="0cd34-103">Un extracteur de faits est un composant utilisé pour déclarer des instances de faits à long terme dans une stratégie, et ce durant l'exécution de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="0cd34-103">A fact retriever is a component that is used to assert instances of long-term facts into a policy during its execution.</span></span> <span data-ttu-id="0cd34-104">Vous pouvez implémenter la **IFactRetriever** d’interface et de configurer une version de stratégie pour utiliser cette implémentation au moment de l’exécution pour les instances de faits à long terme.</span><span class="sxs-lookup"><span data-stu-id="0cd34-104">You can implement the **IFactRetriever** interface and configure a policy version to use this implementation at run time to bring in the long-term fact instances.</span></span> <span data-ttu-id="0cd34-105">La version de stratégie appelle la **UpdateFacts** méthode de l’implémentation d’extracteur de faits sur chaque cycle d’exécution, si un extracteur de faits est configuré pour cette version particulière.</span><span class="sxs-lookup"><span data-stu-id="0cd34-105">The policy version invokes the **UpdateFacts** method of the fact retriever implementation on every execution cycle, if a fact retriever is configured for that particular version.</span></span>  
  
 <span data-ttu-id="0cd34-106">Vous pouvez implémenter la **IFactRemover** interface sur un extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="0cd34-106">You can optionally implement the **IFactRemover** interface on a fact retriever component.</span></span> <span data-ttu-id="0cd34-107">Le moteur de règles appelle la **UpdateFactsAfterExecution** méthode de la **IFactRemover** interface lorsque la stratégie est supprimée.</span><span class="sxs-lookup"><span data-stu-id="0cd34-107">The rule engine invokes the **UpdateFactsAfterExecution** method of the **IFactRemover** interface when the policy is disposed.</span></span> <span data-ttu-id="0cd34-108">Vous avez ainsi la possibilité d'effectuer un certain nombre de tâches après l'exécution, telles que la validation des modifications de base de données ou le retrait d'instances d'objet de la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="0cd34-108">This provides an opportunity to you to do any post-execution work such as committing any database changes or retracting any object instances from the rule engine's working memory.</span></span>  
  
## <a name="to-specify-a-fact-retriever-for-a-policy"></a><span data-ttu-id="0cd34-109">Spécification d'un extracteur de faits pour une stratégie</span><span class="sxs-lookup"><span data-stu-id="0cd34-109">To specify a fact retriever for a policy</span></span>  
 <span data-ttu-id="0cd34-110">Vous pouvez utiliser le code suivant pour configurer l'ensemble de règles permettant d'utiliser une classe appelée « Extracteur » en tant qu'extracteur de faits dans l'assembly appelé « MyAssembly ».</span><span class="sxs-lookup"><span data-stu-id="0cd34-110">You could use the following code to configure the rule set to use a class named "Retriever" in the assembly named "MyAssembly" as the fact retriever.</span></span>  
  
```  
RuleEngineComponentConfiguration fr = new RuleEngineComponentConfiguration("MyAssembly", "Retriever");  
RuleSet rs = new RuleSet("ruleset");  
// associate the execution configuration with a ruleset  
RuleSetExecutionConfiguration rsCfg = rs.ExecutionConfiguration;  
rsCfg.FactRetriever = factRetriever;  
```  
  
> [!NOTE]
>  <span data-ttu-id="0cd34-111">Si vous spécifiez un nom simple d'assembly tel que MyAssembly comme premier paramètre pour le constructeur RuleEngineComponentConfiguration, le moteur de règles BizTalk suppose qu'il s'agit d'un assembly privé et recherche l'assembly dans votre dossier d'applications.</span><span class="sxs-lookup"><span data-stu-id="0cd34-111">If you specify simple assembly name such as MyAssembly as the first parameter for RuleEngineComponentConfiguration constructor, the BizTalk rule engine assumes that it is a private assembly and looks for the assembly in your application folder.</span></span> <span data-ttu-id="0cd34-112">Si vous spécifiez nom d’assembly qualifié complet, tel que **MyAssembly, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = a310908b42c024fe**, le moteur de règles suppose qu’il est un assembly partagé et recherche l’assembly dans global cache (GAC) de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0cd34-112">If you specify fully qualified assembly name such as **MyAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=a310908b42c024fe**, the rule engine assumes that it is a shared assembly and looks for the assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="0cd34-113">Vous trouverez les définitions des noms d’assembly simples et complets à [http://go.microsoft.com/fwlink/?LinkId=64535](http://go.microsoft.com/fwlink/?LinkId=64535).</span><span class="sxs-lookup"><span data-stu-id="0cd34-113">You can find the definitions of simple and fully qualified assembly names at [http://go.microsoft.com/fwlink/?LinkId=64535](http://go.microsoft.com/fwlink/?LinkId=64535).</span></span>  
  
 <span data-ttu-id="0cd34-114">Vous pouvez concevoir l'extracteur de faits avec la logique requise propre à l'application afin d'établir la connexion aux sources de données requises, de déclarer les données dans le moteur en tant que faits à long terme et de spécifier la logique pour actualiser ou déclarer dans le moteur de nouvelles instances des faits à long terme.</span><span class="sxs-lookup"><span data-stu-id="0cd34-114">You can design the fact retriever with the required application-specific logic to connect to the required data sources, assert the data as long-term facts into the engine, and specify the logic for refreshing or asserting new instances of the long-term facts into the engine.</span></span> <span data-ttu-id="0cd34-115">Jusqu'à leur mise à jour, les valeurs initialement déclarées dans le moteur et donc mises en cache seront utilisées dans les cycles d'exécution ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="0cd34-115">Until updated, the values that are initially asserted into the engine and consequently cached will be used on subsequent execution cycles.</span></span> <span data-ttu-id="0cd34-116">Retourne un objet qui est analogue à un jeton de l’implémentation d’extracteur de faits et peut être utilisée avec le **factsHandleIn** objet afin de déterminer s’il faut mettre à jour des faits existants ou nouveaux faits d’assertion.</span><span class="sxs-lookup"><span data-stu-id="0cd34-116">The fact retriever implementation returns an object that is analogous to a token and can be used along with the **factsHandleIn** object to determine whether to update existing facts or assert new facts.</span></span> <span data-ttu-id="0cd34-117">Lorsqu’une version de stratégie appelle son extracteur de faits pour la première fois, le **factsHandleIn** objet est toujours null et puis prend la valeur de l’objet retourné après l’exécution de l’extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="0cd34-117">When a policy version calls its fact retriever for the first time, the **factsHandleIn** object is always null and then takes the value of the return object after the fact retriever's execution.</span></span>  
  
 <span data-ttu-id="0cd34-118">Sachez que pour une même instance de moteur de règles, il n'est pas nécessaire de déclarer plusieurs fois un fait à long terme.</span><span class="sxs-lookup"><span data-stu-id="0cd34-118">Note that for the same rule engine instance, a long-term fact only needs to be asserted once.</span></span> <span data-ttu-id="0cd34-119">Par exemple, lorsque vous utilisez la **appeler règles** forme dans une orchestration, l’instance de stratégie est déplacée dans un cache interne.</span><span class="sxs-lookup"><span data-stu-id="0cd34-119">For example, when you use the **Call Rules** shape in an orchestration, the policy instance is moved into an internal cache.</span></span> <span data-ttu-id="0cd34-120">Tous les faits à court terme sont alors retirés et les faits à long terme sont conservés.</span><span class="sxs-lookup"><span data-stu-id="0cd34-120">At this time, all short-term facts are retracted and long-term facts are kept.</span></span> <span data-ttu-id="0cd34-121">Si la même stratégie est appelée à nouveau, soit par la même instance d'orchestration, soit par une autre instance d'orchestration du même hôte, cette instance de stratégie est extraite du cache et réutilisée.</span><span class="sxs-lookup"><span data-stu-id="0cd34-121">If the same policy is called again, either by the same orchestration instance or by a different orchestration instance in the same host, this policy instance is fetched from the cache and reused.</span></span> <span data-ttu-id="0cd34-122">Dans certains scénarios de traitement par lots, plusieurs instances de la même stratégie peuvent être créées.</span><span class="sxs-lookup"><span data-stu-id="0cd34-122">In some batch processing scenarios, several policy instances of the same policy could be created.</span></span> <span data-ttu-id="0cd34-123">Si une nouvelle instance de stratégie est créée, vous devez vous assurer de déclarer les faits à long terme qui conviennent.</span><span class="sxs-lookup"><span data-stu-id="0cd34-123">If a new policy instance is created, you must ensure that the correct long-term facts are asserted.</span></span>  
  
 <span data-ttu-id="0cd34-124">De plus, vous devrez écrire un code personnalisé pour implémenter les stratégies suivantes :</span><span class="sxs-lookup"><span data-stu-id="0cd34-124">Additionally, you would need to write custom code to implement the following strategies:</span></span>  
  
-   <span data-ttu-id="0cd34-125">Savoir quand mettre à jour les faits à long terme</span><span class="sxs-lookup"><span data-stu-id="0cd34-125">Know when to update the long-term facts</span></span>  
  
-   <span data-ttu-id="0cd34-126">Suivi permettant de savoir quelle instance de moteur de règles utilise quels faits à long terme</span><span class="sxs-lookup"><span data-stu-id="0cd34-126">Keep track of which rule engine instance uses which long-term facts</span></span>  
  
 <span data-ttu-id="0cd34-127">L'exemple de code suivant montre différentes implémentations d'extracteur de faits, qui sont associées à MyPolicy pour déclarer MyTableInstance en tant que fait à long terme, en utilisant divers types de liaisons.</span><span class="sxs-lookup"><span data-stu-id="0cd34-127">The following sample code shows different fact retriever implementations, which are associated with MyPolicy to assert MyTableInstance as a long-term fact, using different binding types.</span></span>  
  
## <a name="datatable-binding"></a><span data-ttu-id="0cd34-128">Liaison DataTable</span><span class="sxs-lookup"><span data-stu-id="0cd34-128">DataTable binding</span></span>  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
         if (factsHandleIn == null)   
  
         {  
            SqlDataAdapter dAdapt = new SqlDataAdapter();  
            dAdapt.TableMappings.Add("Table", "CustInfo");  
            SqlConnection conn = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
            conn.Open();  
            SqlCommand myCommand = new SqlCommand("SELECT * FROM CustInfo", conn);  
            myCommand.CommandType = CommandType.Text;  
            dAdapt.SelectCommand = myCommand;  
            DataSet ds = new DataSet("Northwind");  
            dAdapt.Fill(ds);  
            TypedDataTable tdt = new TypedDataTable(ds.Tables["CustInfo"]);  
            engine.Assert(tdt);  
            factsHandleOut = tdt;  
         }  
  
         else  
            factsHandleOut = factsHandleIn;  
         return factsHandleOut;  
      }  
   }  
}  
```  
  
## <a name="datarow-binding"></a><span data-ttu-id="0cd34-129">Liaison DataRow</span><span class="sxs-lookup"><span data-stu-id="0cd34-129">DataRow binding</span></span>  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
         if (factsHandleIn == null)   
  
         {  
            SqlDataAdapter dAdapt = new SqlDataAdapter();  
            dAdapt.TableMappings.Add("Table", "CustInfo");  
            SqlConnection conn = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
            conn.Open();  
            SqlCommand myCommand = new SqlCommand("SELECT * FROM CustInfo", conn);  
            myCommand.CommandType = CommandType.Text;  
            dAdapt.SelectCommand = myCommand;  
            DataSet ds = new DataSet("Northwind");  
            dAdapt.Fill(ds);  
            TypedDataTable tdt = new TypedDataTable(ds.Tables["CustInfo"]);  
  
            // binding to the first row of CustInfo table  
            TypedDataRow tdr = new TypedDataRow(ds.Tables["CustInfo"].Rows[0],tdt);  
            engine.Assert(tdr);  
            factsHandleOut = tdr;     
         }  
         else  
            factsHandleOut = factsHandleIn;  
         return factsHandleOut;  
      }  
   }   
}  
```  
  
 <span data-ttu-id="0cd34-130">L'exemple de code suivant montre comment déclarer les faits .NET et XML dans une implémentation d'extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="0cd34-130">The following sample code demonstrates how to assert .NET and XML facts in a fact retriever implementation.</span></span>  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
         if (factsHandleIn == null)   
         {  
            //create .NET object instances  
            bookInstance = new Book();  
            magazineInstance = new Magazine();              
  
            //create an instance of the XML object  
            XmlDocument xd = new XmlDocument();  
  
            //load the document  
            xd.Load(@"..\myXMLInstance.xml");  
  
            //create and instantiate an instance of TXD  
            TypedXmlDocument doc = new TypedXmlDocument("mySchema",xd1);  
  
            engine.Assert(bookInstance);  
            engine.Assert(magazineInstance);  
            engine.Assert(doc);  
            factsHandleOut = doc;  
         }  
         else  
            factsHandleOut = factsHandleIn;  
         return factsHandleOut;  
      }  
   }  
}  
```  
  
## <a name="dataconnection-binding"></a><span data-ttu-id="0cd34-131">Liaison DataConnection</span><span class="sxs-lookup"><span data-stu-id="0cd34-131">DataConnection Binding</span></span>  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
  
         {   
            string strCmd = "Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;";  
            SqlConnection conn = new SqlConnection(strCmd);  
            DataConnection dc = new DataConnection("Northwind", "CustInfo", conn);  
  
            engine.Assert(dc);  
            factsHandleOut = dc;           
         }  
         return factsHandleOut;  
      }  
   }  
}  
```  
  
 <span data-ttu-id="0cd34-132">Notez que **DataConnection**s doit toujours être redéclaré, quand il est fourni à partir d’un extracteur de faits, comme indiqué dans l’exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="0cd34-132">Note that **DataConnection**s should always be reasserted, when provided from a fact retriever, as shown in the preceding code sample.</span></span> <span data-ttu-id="0cd34-133">L’instance du moteur utilise le **DataConnection** pour interroger la base de données basée sur les conditions de règle, et toutes les lignes renvoyées par la requête seront déclarées dans la mémoire de travail en tant que **TypedDataRow**s.</span><span class="sxs-lookup"><span data-stu-id="0cd34-133">The engine instance uses the **DataConnection** to query the database based on the rule conditions, and any rows returned by the query would be asserted into the engine's working memory as **TypedDataRow**s.</span></span> <span data-ttu-id="0cd34-134">Redéclaration de l’objet DataConnection garantit que les lignes à partir d’une exécution précédente du moteur sont effacés de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="0cd34-134">Reasserting the DataConnection ensures that rows from a previous execution of the engine are cleared from memory.</span></span>  
  
 <span data-ttu-id="0cd34-135">En fait, il est peu avantageuse constitue à l’assertion d’une **DataConnection** via un fait extracteur, sauf qu’elle offre un moyen d’externaliser la source de données.</span><span class="sxs-lookup"><span data-stu-id="0cd34-135">In fact, there is little advantage to asserting a **DataConnection** through a fact retriever except that it provides a way to externalize the data source.</span></span>