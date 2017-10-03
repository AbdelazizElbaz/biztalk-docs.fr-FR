---
title: "Exécuter des opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RECORD types, performing operations
- WCF service model, performing operations using RECORD types
ms.assetid: e7118a86-7470-48bb-aca0-6200dc0bb67c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3de78290e29c4c1ddc1465e8a9463a6e9d7b86f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-using-record-types-in-oracle-database-using-the-wcf-service-model"></a>Exécuter des opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF
Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL. Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes. Dans le modèle de service WCF, des types d’enregistrements sont désérialisées à des classes de .NET fortement typée. Les champs d’enregistrement sont représentés en tant que propriétés sur la classe.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge les types de types d’enregistrements suivants :  
  
-   Types d’enregistrements qui sont déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.  
  
-   Types d’enregistrements qui sont déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL, par exemple,`TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`  
  
-   Types d’enregistrements qui contiennent des enregistrements imbriqués.  
  
-   Types d’enregistrements qui s’affichent, OUT ou paramètres dans des procédures ou des fonctions.  
  
-   Types d’enregistrements qui sont des valeurs de retour des fonctions.  
  
 Cette rubrique montre comment les types d’enregistrement sont représentés dans le modèle de service WCF. Pour plus d’informations sur la façon d’appeler des fonctions et procédures d’Oracle, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples dans cette rubrique utilisent le PACKAGE PL/SQL de Oracle SCOTT/ACCOUNT_PKG. Les éléments suivants sont utilisés à partir de ACCOUNT_PKG.  
  
```  
TYPE address_rec_type IS RECORD (street customer.street%TYPE, city customer.city%TYPE, state customer.state%TYPE);  
  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
  
TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);  
  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
```  
  
 Un script pour générer ce package est fourni avec les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples. Pour plus d’informations, consultez le script  
  
 Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="record-types-in-the-wcf-service-model"></a>Types d’enregistrements dans le modèle de Service WCF  
 Types d’enregistrements Oracle sont représentés en tant que types XML complexes par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Dans le modèle de service WCF, des types XML complexes sont représentées par une classe, et les propriétés de cette classe représentent les champs du type d’enregistrement d’Oracle. La classe qui représente un paramètre de type d’enregistrement est générée dans un espace de noms est qualifié par le PACKAGE (le cas échéant) et le schéma de la fonction ou la procédure. Cet espace de noms identifie de façon unique la fonction ou procédure du paramètre. Par exemple, les paramètres de type d’enregistrement à la procédure CREATE_ACCOUNT le ACCOUNT_PKG PACKAGE Oracle sont créés dans l’espace de noms suivant : `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT`. Pour plus d’informations sur les espaces de noms permet de représenter des types complexes dans les procédures et fonctions dans le modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
 Tandis que l’espace de noms d’un paramètre de type d’enregistrement est déterminé par la procédure ou fonction, le nom de la classe générée pour le paramètre de type d’enregistrement est déterminé de la façon dont dans lequel est déclaré le type d’enregistrement. Le tableau suivant montre la façon dont le nom de la classe est généré selon les deux façons de déclarer le paramètre de type d’enregistrement d’Oracle.  
  
|Type d’enregistrement Oracle|Nom|Exemple|  
|------------------------|----------|-------------|  
|Paramètre de procédure ou fonction ROWTYPE de % TABLE|[NOM_PARAMÈTRE] ENREGISTREMENT|ACCTRECORD|  
|TYPE du paramètre de package d’enregistrement|[PACKAGE_NAME] [RECORD_TYPE_NAME] ENREGISTREMENT|ACCOUNT_PKGACCTINFO_REC_TYPERECORD|  
  
 [Nom_paramètre] = le nom du paramètre de procédure ou fonction ; par exemple, Acct.  
  
 [PACKAGE_NAME] = le nom du package Oracle.  
  
 [RECORD_TYPE_NAME] = le nom spécifié dans la déclaration de TYPE d’enregistrement ; par exemple, ACCTINFO_REC_TYPE.  
  
 Le code suivant montre les signatures de méthode du client WCF généré pour les deux fonctions d’Oracle. La fonction /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT prend deux paramètres IN de type enregistrement simples, et la fonction /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO retourne un paramètre de type d’enregistrement qui contient deux types d’enregistrements imbriqués. Les déclarations de fonction Oracle sont incluses en haut du code. Les paramètres de chaque fonction sont qualifiés par un espace de noms unique.  
  
```  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
  
public partial class SCOTTPackageACCOUNT_PKGClient : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKG>, SCOTTPackageACCOUNT_PKG {  
  
    ...  
  
    public System.Nullable<decimal> CREATE_ACCOUNT(microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD ACCT, microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDR);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD GET_ACCOUNTINFO(System.Nullable<decimal> AID);  
}  
```  
  
 Le code suivant montre les classes générées pour les paramètres de la fonction CREATE_ACCOUNT :`FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;`  
  
 Cette fonction a un paramètre déclaré avec une TABLE % ROWTYPE et un paramètre déclaré avec un type de package de TYPE d’enregistrement (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT {  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCOUNT_PKGADDRESS_REC_TYPERECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
  
}  
```  
  
### <a name="representation-of-a-simple-record-type"></a>Représentation sous forme d’un Type d’enregistrement Simple  
 Le code suivant montre comment un type d’enregistrement simple est représenté dans le modèle de service WCF. Ce code affiche la vue développée de la **ACCOUNTRECORD** classe qui représente le paramètre de compte ROWTYPE dans la fonction CREATE_ACCOUNT. Dans cette classe, les champs d’enregistrement (colonnes de la ligne) sont représentés en tant que propriétés.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Runtime.Serialization.DataContractAttribute()]  
public partial class ACCTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
    private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
    private System.Nullable<decimal> ACCTIDField;  
  
    private string NAMEField;  
  
    private System.Nullable<decimal> BALANCEField;  
  
    public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
        get {  
            return this.extensionDataField;  
        }  
        set {  
            this.extensionDataField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute()]  
    public System.Nullable<decimal> ACCTID {  
        get {  
            return this.ACCTIDField;  
        }  
        set {  
            this.ACCTIDField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute()]  
    public string NAME {  
        get {  
            return this.NAMEField;  
        }  
        set {  
            this.NAMEField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute(Order=2)]  
    public System.Nullable<decimal> BALANCE {  
        get {  
            return this.BALANCEField;  
        }  
        set {  
            this.BALANCEField = value;  
        }  
    }  
}  
```  
  
### <a name="representation-of-a-record-type-that-contains-nested-records"></a>Représentation sous forme d’un Type d’enregistrement qui contient des enregistrements imbriqués  
 Le code suivant illustre la représentation sous forme d’un type d’enregistrement qui contient des enregistrements imbriqués. Ce type d’enregistrement particulier est la valeur de retour de la fonction GET_ACCOUNTINFO (`FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;`). Le ACCTINFO_REC_TYPE est un paramètre de package déclaré à l’aide d’une construction de TYPE d’enregistrement (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`). Il contient deux types d’enregistrement simple imbriqué, un enregistrement de ligne de TABLE % et un TYPE d’enregistrement du package. Ces deux enregistrements simples sont déclarées dans le même espace de noms en tant que leur enregistrement parent et suivent la convention d’affectation de noms attendue.  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCOUNT_PKGACCTINFO_REC_TYPERECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCTRECORD ACCTField;  
  
        private microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDRESSField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCTRECORD ACCT {  
            get {  
                return this.ACCTField;  
            }  
            set {  
                this.ACCTField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDRESS {  
            get {  
                return this.ADDRESSField;  
            }  
            set {  
                this.ADDRESSField = value;  
            }  
        }  
    }  
```  
  
## <a name="using-record-types-in-your-code"></a>À l’aide des Types d’enregistrements dans votre Code  
 À l’aide des types d’enregistrements dans votre code est simple. Pour appeler une procédure ou une fonction avec un paramètre de type d’enregistrement, vous créez une instance du type d’enregistrement ou de types et passez à la méthode appropriée sur le client WCF. Lorsque retour de la procédure ou fonction, vous pouvez lire des propriétés sur n’importe quel OUT ou IN des paramètres ou retour de fonction de valeurs qui sont déclarés comme des types d’enregistrements. Pour plus d’informations sur la façon d’appeler des procédures et des fonctions à l’aide du modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
> [!IMPORTANT]
>  Paramètres de type enregistrement Oracle (et les retours de fonction) sont qualifiés par l’espace de noms de leur fonction ou procédure (et de package). Cela signifie qu’un espace de noms différent pour chaque procédure ou une fonction dans un type d’enregistrement qui est utilisé dans les deux procédures différentes ou des fonctions. Vous devez être sûr de qualifier le type d’enregistrement correctement lorsque vous l’utilisez pour une fonction ou une procédure spécifique. Par exemple, un type d’enregistrement (déclaration de TYPE d’enregistrement) qui est utilisé comme paramètre à deux fonctions différentes du package sera déclaré deux fois dans le code du client WCF avec chaque déclaration correspondant à l’espace de noms unique généré pour chaque fonction. Veillez à utiliser l’espace de noms correct sur le paramètre que vous passez à chaque fonction respectif.  
  
 Dans l’exemple suivant, la fonction CREATE_ACCOUNT est appelée avec deux paramètres d’enregistrement simple. Ensuite, la fonction GET_ACCOUNTINFO est appelée. Cette fonction retourne un type d’enregistrement qui contient des enregistrements imbriqués. Sélectionné un champ valeurs à partir de l’enregistrement retourné sont écrites dans la console. Étapes à suivre pour définir les informations d’identification pour la base de données Oracle et ouvrez le client WCF sont omis dans cet exemple.  
  
```  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
…  
  
// Create the client from configuration  
using (SCOTTPackageACCOUNT_PKGClient accountPkgClient = new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG"))  
{  
  
    ...  
  
    decimal acctId;  
  
    // Create an account record  
    // Note: ACCTRECORD is defined in both namespaces so specify the definition  
    // that corresponds to the client.  
  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD acctRec =   
        new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD();  
  
    // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
    acctRec.ACCTID = 0;  
    acctRec.NAME = "Anton Kirilov";  
    acctRec.BALANCE = 9583;  
  
    // Create address record  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
    addrRec.STREET = "234 Main St";  
    addrRec.CITY = "Boston";  
    addrRec.STATE = "MA";  
  
    // Create account  
    try  
    {  
        acctId = (decimal)accountPkgClient.CREATE_ACCOUNT(acctRec, addrRec);  
    }  
    catch (Exception ex)  
    {  
        // handle exception  
        ...  
    }  
  
    ...  
  
    // Account info record  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD acctInfo =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD();  
  
    // Get account info for the account just created  
    // acctInfo is returned as a nested record type  
    try  
    {  
     acctInfo = accountPkgClient.GET_ACCOUNTINFO(acctId);  
    }  
    catch (Exception ex)  
    {  
    // handle exception  
    ...  
    }  
  
    // Write the account info to the console  
    Console.WriteLine("The account info is:");  
    Console.WriteLine("Name:\t\t\t{0}", acctInfo.ACCT.NAME);  
    Console.WriteLine("Street:\t\t\t{0}", acctInfo.ADDRESS.STREET);  
    Console.WriteLine("City:\t\t\t{0}", acctInfo.ADDRESS.CITY);  
    Console.WriteLine("State:\t\t\t{0}", acctInfo.ADDRESS.STATE);  
    Console.WriteLine("Account Id:\t\t{0}", acctInfo.ACCT.ACCTID);  
    Console.WriteLine("Account Balance:\t{0:C}", acctInfo.ACCT.BALANCE);  
  
    Console.WriteLine("\nHit <RETURN> to finish");  
    Console.ReadLine();  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)