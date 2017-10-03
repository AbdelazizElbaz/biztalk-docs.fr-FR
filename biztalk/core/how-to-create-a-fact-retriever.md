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
# <a name="how-to-create-a-fact-retriever"></a>Création d'un extracteur de faits
Un extracteur de faits est un composant utilisé pour déclarer des instances de faits à long terme dans une stratégie, et ce durant l'exécution de celle-ci. Vous pouvez implémenter la **IFactRetriever** d’interface et de configurer une version de stratégie pour utiliser cette implémentation au moment de l’exécution pour les instances de faits à long terme. La version de stratégie appelle la **UpdateFacts** méthode de l’implémentation d’extracteur de faits sur chaque cycle d’exécution, si un extracteur de faits est configuré pour cette version particulière.  
  
 Vous pouvez implémenter la **IFactRemover** interface sur un extracteur de faits. Le moteur de règles appelle la **UpdateFactsAfterExecution** méthode de la **IFactRemover** interface lorsque la stratégie est supprimée. Vous avez ainsi la possibilité d'effectuer un certain nombre de tâches après l'exécution, telles que la validation des modifications de base de données ou le retrait d'instances d'objet de la mémoire de travail du moteur de règles.  
  
## <a name="to-specify-a-fact-retriever-for-a-policy"></a>Spécification d'un extracteur de faits pour une stratégie  
 Vous pouvez utiliser le code suivant pour configurer l'ensemble de règles permettant d'utiliser une classe appelée « Extracteur » en tant qu'extracteur de faits dans l'assembly appelé « MyAssembly ».  
  
```  
RuleEngineComponentConfiguration fr = new RuleEngineComponentConfiguration("MyAssembly", "Retriever");  
RuleSet rs = new RuleSet("ruleset");  
// associate the execution configuration with a ruleset  
RuleSetExecutionConfiguration rsCfg = rs.ExecutionConfiguration;  
rsCfg.FactRetriever = factRetriever;  
```  
  
> [!NOTE]
>  Si vous spécifiez un nom simple d'assembly tel que MyAssembly comme premier paramètre pour le constructeur RuleEngineComponentConfiguration, le moteur de règles BizTalk suppose qu'il s'agit d'un assembly privé et recherche l'assembly dans votre dossier d'applications. Si vous spécifiez nom d’assembly qualifié complet, tel que **MyAssembly, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = a310908b42c024fe**, le moteur de règles suppose qu’il est un assembly partagé et recherche l’assembly dans global cache (GAC) de l’assembly. Vous trouverez les définitions des noms d’assembly simples et complets à [http://go.microsoft.com/fwlink/?LinkId=64535](http://go.microsoft.com/fwlink/?LinkId=64535).  
  
 Vous pouvez concevoir l'extracteur de faits avec la logique requise propre à l'application afin d'établir la connexion aux sources de données requises, de déclarer les données dans le moteur en tant que faits à long terme et de spécifier la logique pour actualiser ou déclarer dans le moteur de nouvelles instances des faits à long terme. Jusqu'à leur mise à jour, les valeurs initialement déclarées dans le moteur et donc mises en cache seront utilisées dans les cycles d'exécution ultérieurs. Retourne un objet qui est analogue à un jeton de l’implémentation d’extracteur de faits et peut être utilisée avec le **factsHandleIn** objet afin de déterminer s’il faut mettre à jour des faits existants ou nouveaux faits d’assertion. Lorsqu’une version de stratégie appelle son extracteur de faits pour la première fois, le **factsHandleIn** objet est toujours null et puis prend la valeur de l’objet retourné après l’exécution de l’extracteur de faits.  
  
 Sachez que pour une même instance de moteur de règles, il n'est pas nécessaire de déclarer plusieurs fois un fait à long terme. Par exemple, lorsque vous utilisez la **appeler règles** forme dans une orchestration, l’instance de stratégie est déplacée dans un cache interne. Tous les faits à court terme sont alors retirés et les faits à long terme sont conservés. Si la même stratégie est appelée à nouveau, soit par la même instance d'orchestration, soit par une autre instance d'orchestration du même hôte, cette instance de stratégie est extraite du cache et réutilisée. Dans certains scénarios de traitement par lots, plusieurs instances de la même stratégie peuvent être créées. Si une nouvelle instance de stratégie est créée, vous devez vous assurer de déclarer les faits à long terme qui conviennent.  
  
 De plus, vous devrez écrire un code personnalisé pour implémenter les stratégies suivantes :  
  
-   Savoir quand mettre à jour les faits à long terme  
  
-   Suivi permettant de savoir quelle instance de moteur de règles utilise quels faits à long terme  
  
 L'exemple de code suivant montre différentes implémentations d'extracteur de faits, qui sont associées à MyPolicy pour déclarer MyTableInstance en tant que fait à long terme, en utilisant divers types de liaisons.  
  
## <a name="datatable-binding"></a>Liaison DataTable  
  
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
  
## <a name="datarow-binding"></a>Liaison DataRow  
  
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
  
 L'exemple de code suivant montre comment déclarer les faits .NET et XML dans une implémentation d'extracteur de faits.  
  
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
  
## <a name="dataconnection-binding"></a>Liaison DataConnection  
  
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
  
 Notez que **DataConnection**s doit toujours être redéclaré, quand il est fourni à partir d’un extracteur de faits, comme indiqué dans l’exemple de code précédent. L’instance du moteur utilise le **DataConnection** pour interroger la base de données basée sur les conditions de règle, et toutes les lignes renvoyées par la requête seront déclarées dans la mémoire de travail en tant que **TypedDataRow**s. Redéclaration de l’objet DataConnection garantit que les lignes à partir d’une exécution précédente du moteur sont effacés de la mémoire.  
  
 En fait, il est peu avantageuse constitue à l’assertion d’une **DataConnection** via un fait extracteur, sauf qu’elle offre un moyen d’externaliser la source de données.