---
title: "Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, performing a SQLEXECUTE operation
- SQLEXECUTE operation, performing a
- how to, invoke the SQLEXECUTE operation
ms.assetid: d3f61e5f-4453-4a76-9bc6-40d91cb58224
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6bda1c864e7a6eff442099d6caf1a2bba98e7f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="6d076-102">Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="6d076-102">Run SQLEXECUTE operation in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="6d076-103">Le[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un ensemble standard d’opérations sur les objets de base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6d076-103">The[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a standard set of operations on Oracle database artifacts.</span></span> <span data-ttu-id="6d076-104">À l’aide de ces opérations, vous pouvez effectuer les opérations appel une fonction Oracle ou une procédure ou effectuer base SQL opérations data manipulation language (DML) sur les tables.</span><span class="sxs-lookup"><span data-stu-id="6d076-104">By using these operations, you can do things like call an Oracle function or procedure, or perform basic SQL data manipulation language (DML) operations on tables.</span></span> <span data-ttu-id="6d076-105">Toutefois, il peuvent y avoir scénarios pilotés par votre logique métier, vous devez effectuer les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] n’a pas été affiché.</span><span class="sxs-lookup"><span data-stu-id="6d076-105">However, there may be scenarios driven by your business logic that require you to perform operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not surface.</span></span> <span data-ttu-id="6d076-106">Par exemple, vous souhaiterez :</span><span class="sxs-lookup"><span data-stu-id="6d076-106">For example, you may want to:</span></span>  
  
-   <span data-ttu-id="6d076-107">Effectuer une opération sur les artefacts de base de données qui ne sont pas signalées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; par exemple, obtenir le CURVAL ou NEXTVAL d’une séquence Oracle.</span><span class="sxs-lookup"><span data-stu-id="6d076-107">Perform an operation on database artifacts that are not surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example, get the CURVAL or NEXTVAL of an Oracle SEQUENCE.</span></span>  
  
-   <span data-ttu-id="6d076-108">Effectuer des opérations de langage de définition de données ; par exemple, créer une table.</span><span class="sxs-lookup"><span data-stu-id="6d076-108">Perform Data Definition Language operations; for example, create a table.</span></span>  
  
-   <span data-ttu-id="6d076-109">Effectuer des opérations sur un objet de base de données qui n’était pas présente au moment du design ; par exemple, mettre à jour des enregistrements dans une table temporaire qui est créé par votre logique métier.</span><span class="sxs-lookup"><span data-stu-id="6d076-109">Perform operations on a database artifact that was not present at design time; for example, update records in a temporary table that is created by your business logic.</span></span>  
  
-   <span data-ttu-id="6d076-110">Effectuer des opérations DML plus complexes sur les tables que les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces ; par exemple, pour exécuter une requête qui inclut une clause JOIN.</span><span class="sxs-lookup"><span data-stu-id="6d076-110">Perform more complex DML operations on tables than the operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces; for example, to perform a query that includes a JOIN clause.</span></span>  
  
 <span data-ttu-id="6d076-111">Pour ces types de scénarios, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence l’opération SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="6d076-111">For these kinds of scenarios, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the SQLEXECUTE operation.</span></span> <span data-ttu-id="6d076-112">À l’aide de l’opération SQLEXECUTE, vous pouvez effectuer une instruction SQL paramétrable sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6d076-112">By using the SQLEXECUTE operation, you can perform a parameterized SQL statement on the Oracle database.</span></span> <span data-ttu-id="6d076-113">L’opération SQLEXECUTE prend en charge un bloc de paramètre d’entrée composé des jeux de paramètres qui vous permettent d’exécuter la même instruction SQL une fois pour chaque jeu.</span><span class="sxs-lookup"><span data-stu-id="6d076-113">The SQLEXECUTE operation supports an input parameter block comprised of parameter sets that enable you to execute the same SQL statement once for each set.</span></span> <span data-ttu-id="6d076-114">L’opération SQLEXECUTE renvoie les résultats de l’instruction SQL dans un jeu d’enregistrements générique.</span><span class="sxs-lookup"><span data-stu-id="6d076-114">The SQLEXECUTE operation returns the results of the SQL statement in a generic record set.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="6d076-115">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="6d076-115">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="6d076-116">Les exemples de cette rubrique utilisent une séquence Oracle nommé TID_SEQ.</span><span class="sxs-lookup"><span data-stu-id="6d076-116">The examples in this topic use an Oracle SEQUENCE named TID_SEQ.</span></span> <span data-ttu-id="6d076-117">Un script pour générer cette séquence est fourni avec les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="6d076-117">A script to generate this SEQUENCE is supplied with the SDK samples.</span></span> <span data-ttu-id="6d076-118">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="6d076-118">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="6d076-119">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="6d076-119">The WCF Client Class</span></span>  
 <span data-ttu-id="6d076-120">Le modèle de service WCF génère un client WCF dédié, **SQLEXECUTEClient**, pour l’opération SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="6d076-120">The WCF service model generates a dedicated WCF client, **SQLEXECUTEClient**, for the SQLEXECUTE operation.</span></span> <span data-ttu-id="6d076-121">Le code suivant illustre la **SQLEXECUTEClient** et la signature de la méthode que vous appelez pour appeler l’opération SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="6d076-121">The following code shows the **SQLEXECUTEClient** and the signature of the method that you call to invoke the SQLEXECUTE operation.</span></span>  
  
```  
public partial class SQLEXECUTEClient : System.ServiceModel.ClientBase<SQLEXECUTE>, SQLEXECUTE {  
  
    ...  
  
    public microsoft.lobservices.oracledb._2007._03.GenRecordRow[] SQLEXECUTE(string SQLSTATEMENT, string PARAMETERSCHEMA, microsoft.lobservices.oracledb._2007._03.PARAMETERDATA[] PARAMETERSET);   
}  
```  
  
 <span data-ttu-id="6d076-122">L’opération SQLEXECUTE retourne un jeu d’enregistrements générique.</span><span class="sxs-lookup"><span data-stu-id="6d076-122">The SQLEXECUTE operation returns a generic record set.</span></span> <span data-ttu-id="6d076-123">Ce jeu d’enregistrements contient les valeurs (le cas échéant) qui sont retournés par les instructions que l’opération SQLEXECUTE s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6d076-123">This record set contains the values (if any) that are returned by the statements that the SQLEXECUTE operation executes.</span></span> <span data-ttu-id="6d076-124">Vous pouvez passer des jeux de paramètres d’entrée à l’opération SQLEXECUTE dans une collection d’objets PARAMETERDATA, chacun d’eux constituée une collection de paramètres d’entrée, représenté sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="6d076-124">You can pass sets of input parameters to the SQLEXECUTE operation in a collection of PARAMETERDATA objects, each of which contains a collection of input parameters represented as strings.</span></span> <span data-ttu-id="6d076-125">Le code suivant montre la définition d’un ensemble PARAMETERDATA.</span><span class="sxs-lookup"><span data-stu-id="6d076-125">The following code shows the definition of a PARAMETERDATA set.</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class PARAMETERDATA : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private string[] PARAMETERField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public string[] PARAMETER {  
            get {  
                return this.PARAMETERField;  
            }  
            set {  
                this.PARAMETERField = value;  
            }  
        }  
    }  
}  
```  
  
## <a name="invoking-the-sqlexecute-operation"></a><span data-ttu-id="6d076-126">Appeler l’opération SQLEXECUTE</span><span class="sxs-lookup"><span data-stu-id="6d076-126">Invoking the SQLEXECUTE Operation</span></span>  
 <span data-ttu-id="6d076-127">Pour appeler l’opération SQLEXECUTE à l’aide d’un client WCF, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="6d076-127">To invoke the SQLEXECUTE operation by using a WCF client, perform the following steps.</span></span>  
  
1.  <span data-ttu-id="6d076-128">Générer un **SQLEXECUTEClient** classe pour la table ou vue cible.</span><span class="sxs-lookup"><span data-stu-id="6d076-128">Generate a **SQLEXECUTEClient** class for the target table or view.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6d076-129">L’opération SQLEXECUTE apparaissent sous le nœud racine (**/**) dans le **sélectionner une catégorie** volet dans le **ajouter une référence de Service de carte** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6d076-129">The SQLEXECUTE operation is surfaced under the root node (**/**) in the **Select a category** pane in the **Add Adapter Service Reference** dialog box.</span></span>  
  
2.  <span data-ttu-id="6d076-130">Créez une instance de la **SQLEXECUTEClient** classe et appeler le **SQLEXECUTE** méthode à exécuter des instructions SQL sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6d076-130">Create an instance of the **SQLEXECUTEClient** class, and invoke the **SQLEXECUTE** method to execute SQL statements on the Oracle database.</span></span>  
  
 <span data-ttu-id="6d076-131">Pour plus d’informations sur la façon de créer une classe de client WCF et d’appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [vue d’ensemble du modèle de service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="6d076-131">For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF service model with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="6d076-132">L’exemple suivant utilise le **SQLEXECUTEClient** pour obtenir la valeur suivante d’une séquence Oracle, TID_SEQ, en exécutant l’instruction SQL suivante : `SELECT tid_seq.nextval id from DUAL`.</span><span class="sxs-lookup"><span data-stu-id="6d076-132">The following example uses the **SQLEXECUTEClient** to get the next value of an Oracle SEQUENCE, TID_SEQ, by executing the following SQL statement: `SELECT tid_seq.nextval id from DUAL`.</span></span> <span data-ttu-id="6d076-133">La sortie est ensuite écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="6d076-133">The output is then written to the console.</span></span>  
  
```  
using (SQLEXECUTEClient sqlClient = new SQLEXECUTEClient("OracleDBBinding_SQLEXECUTE"))  
{  
    sqlClient.ClientCredentials.UserName.UserName = "SCOTT";  
    sqlClient.ClientCredentials.UserName.Password = "TIGER";  
    try  
    {  
        sqlClient.Open();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Error opening SQL client " + ex.Message);  
        throw;  
    }  
    microsoft.lobservices.oracledb._2007._03.GenRecordRow[] sequenceRec =   
        new microsoft.lobservices.oracledb._2007._03.GenRecordRow[0];  
  
    try  
    {  
        sequenceRec = sqlClient.SQLEXECUTE("SELECT tid_seq.nextval id from DUAL", null, null);  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Error executing SQL client " + ex.Message);  
        throw;  
    }  
  
    if (sequenceRec.Length > 0)  
    {  
        Console.WriteLine("TID_SEQUENCE value is {0}", sequenceRec[0].GenRecordColumn[0].ColumnValue);  
    }  
    else  
    {  
    Console.WriteLine("Couldn't get next TID_SEQUENCE value");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d076-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d076-134">See Also</span></span>  
 [<span data-ttu-id="6d076-135">Développer des applications de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="6d076-135">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)