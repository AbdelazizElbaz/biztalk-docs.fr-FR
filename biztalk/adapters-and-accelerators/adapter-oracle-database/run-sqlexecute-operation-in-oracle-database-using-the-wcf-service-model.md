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
# <a name="run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model"></a>Exécuter l’opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de Service WCF
Le[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un ensemble standard d’opérations sur les objets de base de données Oracle. À l’aide de ces opérations, vous pouvez effectuer les opérations appel une fonction Oracle ou une procédure ou effectuer base SQL opérations data manipulation language (DML) sur les tables. Toutefois, il peuvent y avoir scénarios pilotés par votre logique métier, vous devez effectuer les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] n’a pas été affiché. Par exemple, vous souhaiterez :  
  
-   Effectuer une opération sur les artefacts de base de données qui ne sont pas signalées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; par exemple, obtenir le CURVAL ou NEXTVAL d’une séquence Oracle.  
  
-   Effectuer des opérations de langage de définition de données ; par exemple, créer une table.  
  
-   Effectuer des opérations sur un objet de base de données qui n’était pas présente au moment du design ; par exemple, mettre à jour des enregistrements dans une table temporaire qui est créé par votre logique métier.  
  
-   Effectuer des opérations DML plus complexes sur les tables que les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces ; par exemple, pour exécuter une requête qui inclut une clause JOIN.  
  
 Pour ces types de scénarios, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence l’opération SQLEXECUTE. À l’aide de l’opération SQLEXECUTE, vous pouvez effectuer une instruction SQL paramétrable sur la base de données Oracle. L’opération SQLEXECUTE prend en charge un bloc de paramètre d’entrée composé des jeux de paramètres qui vous permettent d’exécuter la même instruction SQL une fois pour chaque jeu. L’opération SQLEXECUTE renvoie les résultats de l’instruction SQL dans un jeu d’enregistrements générique.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique utilisent une séquence Oracle nommé TID_SEQ. Un script pour générer cette séquence est fourni avec les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le modèle de service WCF génère un client WCF dédié, **SQLEXECUTEClient**, pour l’opération SQLEXECUTE. Le code suivant illustre la **SQLEXECUTEClient** et la signature de la méthode que vous appelez pour appeler l’opération SQLEXECUTE.  
  
```  
public partial class SQLEXECUTEClient : System.ServiceModel.ClientBase<SQLEXECUTE>, SQLEXECUTE {  
  
    ...  
  
    public microsoft.lobservices.oracledb._2007._03.GenRecordRow[] SQLEXECUTE(string SQLSTATEMENT, string PARAMETERSCHEMA, microsoft.lobservices.oracledb._2007._03.PARAMETERDATA[] PARAMETERSET);   
}  
```  
  
 L’opération SQLEXECUTE retourne un jeu d’enregistrements générique. Ce jeu d’enregistrements contient les valeurs (le cas échéant) qui sont retournés par les instructions que l’opération SQLEXECUTE s’exécute. Vous pouvez passer des jeux de paramètres d’entrée à l’opération SQLEXECUTE dans une collection d’objets PARAMETERDATA, chacun d’eux constituée une collection de paramètres d’entrée, représenté sous forme de chaînes. Le code suivant montre la définition d’un ensemble PARAMETERDATA.  
  
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
  
## <a name="invoking-the-sqlexecute-operation"></a>Appeler l’opération SQLEXECUTE  
 Pour appeler l’opération SQLEXECUTE à l’aide d’un client WCF, procédez comme suit.  
  
1.  Générer un **SQLEXECUTEClient** classe pour la table ou vue cible.  
  
    > [!IMPORTANT]
    >  L’opération SQLEXECUTE apparaissent sous le nœud racine (**/**) dans le **sélectionner une catégorie** volet dans le **ajouter une référence de Service de carte** boîte de dialogue.  
  
2.  Créez une instance de la **SQLEXECUTEClient** classe et appeler le **SQLEXECUTE** méthode à exécuter des instructions SQL sur la base de données Oracle.  
  
 Pour plus d’informations sur la façon de créer une classe de client WCF et d’appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [vue d’ensemble du modèle de service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).  
  
 L’exemple suivant utilise le **SQLEXECUTEClient** pour obtenir la valeur suivante d’une séquence Oracle, TID_SEQ, en exécutant l’instruction SQL suivante : `SELECT tid_seq.nextval id from DUAL`. La sortie est ensuite écrite dans la console.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)