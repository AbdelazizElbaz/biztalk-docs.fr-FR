---
title: "Appeler des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke functions and procedures using the WCF service model
- WCF service model, invoking functions and procedures
ms.assetid: 806fc803-3640-42d6-bdf9-53b08f9c7c50
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a6256491100939937113ac6f140adc031da0941
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model"></a>Appeler des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des procédures, fonctions et des packages en tant qu’opérations. Dans le modèle de service WCF, ces opérations sont représentées en tant que méthodes sur un client WCF. Le modèle de service WCF et le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
-   **Prend en charge les fonctions**. La valeur de retour de la fonction d’Oracle est présentée comme la valeur de retour de la méthode de client WCF. Paramètres Oracle sont signalées en tant que paramètres (avec la direction appropriée tel que défini ci-dessous) à la méthode de client WCF.  
  
-   **Prend en charge les procédures**. Le premier paramètre de la procédure d’Oracle est présenté comme la valeur de retour de la méthode de client WCF. Tous les autres paramètres Oracle sont signalées en tant que paramètres (avec la direction appropriée tel que défini ci-dessous) à la méthode de client WCF.  
  
-   **Prend en charge les packages Oracle**. Le nom de l’opération et l’espace de noms de ses types de paramètre sont qualifiés par le nom du package.  
  
-   **Surchargée de prise en charge des fonctions et procédures**.  
  
-   **Prise en charge IN, OUT et IN, OUT pour les types de données Oracle base pour les fonctions et procédures**. Les paramètres de sortie sont exposés en tant que **hors** paramètres dans la méthode de client WCF et dans les paramètres sont exposés en tant que **ref** paramètres.  
  
-   **IN de prise en charge, la sortie et dans les paramètres REF CURSOR pour les procédures et fonctions, ainsi que les valeurs de retour de fonction**. Pour plus d’informations, consultez [exécution d’opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).  
  
-   **Prise en charge dans, OUT et dans les enregistrements pour les procédures et fonctions de paramètres de type, ainsi que des valeurs de retour de fonction**. Pour plus d’informations, consultez [exécution d’opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique utilisent le /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT surchargé procédure. Cette procédure lit un enregistrement de la table de SCOTT/compte basée sur un ID de compte ou un nom de compte. Un script pour générer cette procédure et le tableau est fourni avec les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le tableau suivant présente le nom du client WCF et la méthode générée pour les procédures, fonctions et des packages qui la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces. Sauf si une fonction ou procédure est surchargé, un seul client WCF est utilisé pour appeler toutes les fonctions dans un schéma, toutes les procédures dans un schéma, ou toutes les fonctions et procédures dans un package.  
  
|Artefact d’Oracle|Nom de l’opération Client WCF|Exemple|  
|---------------------|-------------------------------|-------------|  
|Procédure|[SCHÉMA] ProcedureClient. [NOM_PROC]|SCOTTProcedureClient.MYPROC|  
|Fonction|[SCHÉMA] FunctionClient. [FUNC_NAME]|SCOTTProcedureClient.MYFUNC|  
|Package (procédure ou fonction)|[SCHÉMA] Le package [PACKAGE_NAME] Client. [Nom_proc ou FUNC_NAME]|SCOTTPackageMYPACKAGEClient.MYPROC|  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_proc] = le nom d’une procédure d’Oracle ; par exemple, MYPROC.  
  
 [FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple, MYFUNC.  
  
 [PACKAGE_NAME] = le nom d’un package Oracle.  
  
 La [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] représente Oracle enregistrement paramètres de type et retourner des valeurs, ainsi que les jeux de résultats retournés par les paramètres REF CURSOR en tant que types XML complexes qui contiennent les données de ligne (ou champs) d’un enregistrement d’Oracle. Dans le modèle de service WCF, chacun de ces types XML est représentée comme une classe .NET ; les propriétés de la classe représentent les champs du type d’enregistrement ou du jeu de résultats REF CURSOR. Types d’enregistrements Oracle sont toujours représentés en tant que classes de .NET fortement typée. Un jeu de résultats REF CURSOR, toutefois, peut être représenté sous forme d’enregistrements faiblement typée soit fortement typée selon si le REF CURSOR elle-même est déclaré comme fortement typée ou faiblement typée. Les classes que représentent REF CURSOR ou enregistrement type paramètres (ou valeurs de retour) sont générées dans un espace de noms unique en fonction de la procédure, une fonction ou un package. Le tableau suivant présente ces espaces de noms.  
  
|Artefact d’Oracle|Espace de noms|Exemple|  
|---------------------|---------------|-------------|  
|Procédure|[BASE_NS]. [SCHÉMA]. Procédure. [NOM_PROC]|Microsoft.lobservices.OracleDB._2007._03.Scott. Procedure.MYPROC|  
|Fonction|[BASE_NS]. [SCHÉMA]. Fonction. [FUNC_NAME]|Microsoft.lobservices.OracleDB._2007._03.Scott. Function.MYFUNC|  
|Package (procédure)|[BASE_NS]. [SCHÉMA]. Package. [PACKAGE_NAME]. [NOM_PROC]|Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYPROC|  
|Package (fonction)|[BASE_NS]. [SCHÉMA]. Package. [PACKAGE_NAME]. [FUNC_NAME]|Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYFUNC|  
|Jeu d’enregistrements générique (faiblement typée)|[BASE_NS]|Microsoft.lobservices.OracleDB._2007._03|  
  
 [BASE_NS] = la base de l’adaptateur de l’espace de noms ; Microsoft.lobservices.OracleDB._2007._03.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_proc] = le nom d’une procédure d’Oracle ; par exemple : MYPROC.  
  
 [FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple MYFUNC.  
  
 [PACKAGE_NAME] = le nom d’un package Oracle.  
  
 Pour plus d’informations sur l’utilisent de ces espaces de noms pour les paramètres d’enregistrement, consultez [exécution d’opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md). Pour plus d’informations sur l’utilisent de ces espaces de noms de paramètres REF CURSOR, consultez [exécution d’opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).  
  
 En règle générale, les paramètres Oracle et les valeurs de retour mappés comme suit dans la méthode du client WCF :  
  
-   Paramètres Oracle IN sont mappées aux paramètres (entrées) de .NET.  
  
-   Paramètres OUT Oracle sont mappés vers .NET **hors** paramètres.  
  
-   Oracle dans les paramètres sont mappés à .NET **ref** paramètres.  
  
-   Les valeurs de retour de fonction sont mappées à la valeur de retour de méthode.  
  
 Toutefois, les deux exceptions importantes existent :  
  
-   Les paramètres dans des REF CURSOR Oracle sont divisées en une chaîne d’entrée et une sortie (**out**) enregistrer ensemble. C’est parce que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] représente les paramètres IN REF CUSROR comme des chaînes et des paramètres de sortie REF CURSOR en tant que types complexes (jeux d’enregistrements), elles ne peuvent pas être combinées dans un seul paramètre.  
  
-   Le premier paramètre dans une procédure Oracle est mappé à la valeur de retour de la méthode de client WCF. Il s’agit de comportement WCF standard.  
  
 L’exemple suivant montre la partie d’une procédure simple de Oracle (chargée dans le schéma SCOTT) et la signature de la méthode de client WCF qui est générée pour l’invoquer. La procédure Oracle a trois paramètres et trois paramètres OUT dans trois des paramètres ; Toutefois, la méthode du client WCF ne mappe pas un paramètre pour le premier paramètre de sortie. Au lieu de cela, il est mappé à la valeur de retour de méthode.  
  
```  
CREATE or REPLACE PROCEDURE Sample_Procedure   
    (  
     INNUMBER      IN         NUMBER,  
     INVARCHAR     IN         VARCHAR2,  
     INDATE        IN         DATE,  
     INOUTNUMBER   IN OUT     NUMBER,  
     INOUTVARCHAR  IN OUT     VARCHAR,  
     INOUTDATE     IN OUT     DATE,  
     OUTNUMBER     OUT        NUMBER,  
     OUTVARCHAR    OUT        VARCHAR2,  
     OUTDATE       OUT        DATE  
    ) AS   
    BEGIN  
  
        ...  
  
    END;  
    /  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTProcedureClient : System.ServiceModel.ClientBase<SCOTTProcedure>, SCOTTProcedure {  
  
    public System.Nullable<decimal> SAMPLE_PROCEDURE  
       (  
        System.Nullable<decimal> INNUMBER,   
        string INVARCHAR,   
        System.Nullable\<System.DateTime> INDATE,   
        ref System.Nullable<decimal> INOUTNUMBER,   
        ref string INOUTVARCHAR,   
        ref System.Nullable\<System.DateTime> INOUTDATE,   
        out string OUTVARCHAR,   
        out System.Nullable\<System.DateTime> OUTDATE  
        );  
}  
```  
  
### <a name="support-for-overloaded-procedures-functions-and-packages"></a>Prise en charge des Packages, des fonctions et procédures surchargées  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge surchargé procédures, fonctions et des packages en ajoutant une chaîne unique pour l’ID de nœud et l’espace de noms pour chaque artefact surchargé il met en évidence. Cette chaîne est « overload1 » pour la première surcharge, « overload2 » pour la surcharge suivante et ainsi de suite.  
  
 Dans le modèle de service WCF, chaque procédure surchargée ou une fonction est représentée par un client WCF unique. Cela est différent du cas de non surchargée dans laquelle toutes les fonctions dans un schéma, toutes les procédures dans un schéma, ou toutes les procédures et fonctions dans un PACKAGE sont appelées par le même client WCF. Le tableau suivant montre le client WCF nom et la méthode générée pour les packages, les fonctions et procédures surchargées.  
  
|Artefact d’Oracle|Nom de Client WCF|Exemple|  
|---------------------|---------------------|-------------|  
|Package surchargé (procédure)|[SCHÉMA] Package [PACKAGE_NAME] [nom_proc]] [OVERLOAD_ID] Client. [NOM_PROC]|SCOTTPackageMYPACKAGEMYPROCoverload1Client.MYPROC|  
|Package surchargé (fonction)|[SCHÉMA] Package [PACKAGE_NAME] [FUNC_NAME]] [OVERLOAD_ID] Client. [FUNC_NAME]|SCOTTPackageMYPACKAGEMYFUNCoverload1Client.MYFUNC|  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_proc] = le nom d’une procédure d’Oracle ; par exemple : MYPROC.  
  
 [FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple MYFUNC.  
  
 [PACKAGE_NAME] = le nom d’un package Oracle.  
  
 [OVERLOAD_ID] = la chaîne unique qui identifie l’artefact surchargé ; « overload1 », « overload2 » et ainsi de suite.  
  
 Le tableau suivant présente l’espace de noms généré pour les packages, les fonctions et procédures surchargées.  
  
|Artefact d’Oracle|Espace de noms|Exemple|  
|---------------------|---------------|-------------|  
|Package (procédure)|[BASE_NS]. [SCHÉMA]. Package. [PACKAGE_NAME]. [NOM_PROC] [OVERLOAD_ID]|Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYPROC.overload1|  
|Package (fonction)|[BASE_NS]. [SCHÉMA]. Package. [PACKAGE_NAME]. [FUNC_NAME]. [OVERLOAD_ID]|Microsoft.lobservices.OracleDB._2007._03.Scott. Package.MYPACKAGE.MYFUNC.overload1|  
|Jeu d’enregistrements générique (faiblement typée)|[BASE_NS]|Microsoft.lobservices.OracleDB._2007._03|  
  
 [BASE_NS] = la base de l’adaptateur de l’espace de noms ; Microsoft.lobservices.OracleDB._2007._03.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_proc] = le nom d’une procédure d’Oracle ; par exemple : MYPROC.  
  
 [FUNC_NAME] = le nom d’une fonction d’Oracle ; par exemple MYFUNC.  
  
 [PACKAGE_NAME] = le nom d’un package Oracle.  
  
 [OVERLOAD_ID] = la chaîne unique qui identifie l’artefact surchargé ; « overload1 », « overload2 » et ainsi de suite. La valeur numérique dans la chaîne est l’ID de la surcharge pour l’artefact gérée par la base de données Oracle.  
  
 L’exemple suivant montre les clients WCF et les signatures de méthode générés pour la procédure surchargée GET_ACCOUNT dans le package ACCOUNT_PKG. (Les déclarations d’Oracle sont incluses). Cet exemple montre comment un client WCF unique est généré pour chaque surcharge et comment la méthode générée pour chaque client renvoie un ensemble d’enregistrements d’un espace de noms unique.  
  
```  
/* Procedure that takes account ID and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aid IN account.acctid%TYPE, acct OUT account%ROWTYPE) ;  
  
/* Procedure that takes account name and returns record for existing account in the ACCOUNT table */  
PROCEDURE get_account(aname IN account.name%TYPE, acct OUT account%ROWTYPE) ;  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1.ACCTRECORD GET_ACCOUNT(System.Nullable<decimal> AID);  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2>, SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2 {  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2.ACCTRECORD GET_ACCOUNT(string ANAME);  
}  
```  
  
## <a name="invoking-functions-and-procedures"></a>Appel de fonctions et procédures  
 Pour appeler une fonction ou une procédure à l’aide d’un client WCF, procédez comme suit.  
  
1.  Générer une classe de client WCF pour la fonction cible, une procédure ou un package. Cette classe doit contenir des méthodes pour les opérations que vous appellerez sur l’artefact cible.  
  
    > [!NOTE]
    >  Dans le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], la surcharge fonctions et procédures s’affichent dans le **catégories et opérations disponibles** boîte [name].1, [nom].2, [nom].3 et ainsi de suite, où [NAME] est le nom de l’artefact surchargé et la valeur numérique est l’ID de la surcharge de la base de données Oracle.  
  
2.  Créer une instance de la classe de client WCF et appeler ses méthodes pour appeler la fonction ou procédure.  
  
 Pour plus d’informations sur la façon de créer une classe de client WCF et d’appeler des opérations sur le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [vue d’ensemble du modèle de Service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute chaque opération à l’intérieur d’une transaction sur la base de données Oracle.  
  
> [!IMPORTANT]
>  Les classes qui représentent des REF CURSOR et les paramètres de type d’enregistrement ou de valeurs de retour dans les fonctions ou procédures (et packages) qui sont déclarés dans un espace de noms unique pour chaque fonction ou une procédure. Cela signifie, par exemple, un type de PACKAGE REF CURSOR est utilisé comme valeur de retour dans les deux fonctions différentes sera déclaré dans un espace de noms unique pour chaque méthode de client WCF. Vous devez soit déclarer des variables distinctes pour contenir ces différentes valeurs de retour ou un effectué correctement la variable lorsque vous appelez une des méthodes de client WCF.  
  
 L’exemple suivant illustre l’appel de la procédure surchargée /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT pour obtenir des enregistrements de compte à partir de la table /SCOTT/ACCOUNT. Tout d’abord un nouvel enregistrement est créé en appelant la procédure /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT. Ensuite, le nouvel enregistrement est en lecture différée deux fois par appelant différentes surcharges de GET_ACCOUNT. Cet exemple utilise trois clients WCF, pour la procédure CREATE_ACCOUNT et un pour les surcharges GET_ACCOUNT. Alias sont utilisés pour faire la distinction entre les espaces de noms utilisés pour la valeur de retour de GET_ACCOUNT. Un exemple complet est disponible dans les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// Alias client namespaces to shorten declarations of "shared" types   
using CREATE_ACCOUNTns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT;  
using GET_ACCOUNT_BY_IDns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1;  
using GET_ACCOUNT_BY_NAMEns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload2;  
  
// This sample demonstrates calling overloaded packaged procedures on Oracle  
// First a new account is created by calling CREATE_ACCOUNT which takes two record parameters  
// Then the information for the new account is returned by calling an overloaded procedure GET_ACCOUNT  
// The first overload returns the account information by account ID  
// The second overload returns the account information by account name  
// Notice that different clients (and namespaces) are created for overloaded procedures and functions  
namespace OracleOverloadsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            decimal acctId;  
            string newAccountName = "Paula Bento";  
  
            Console.WriteLine("Creating clients");  
            // Create Client for CREATE_ACCOUNT Function  
            SCOTTPackageACCOUNT_PKGClient createAccountClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // NOTE: user name and password are case-sensitive  
            createAccountClient.ClientCredentials.UserName.UserName = "SCOTT";  
            createAccountClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 1 -- takes ACCOUNT ID parameter  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client getAccountByIdClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload1Client("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNT.overload1");  
            // NOTE: user name and password are case-sensitive  
            getAccountByIdClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByIdClient.ClientCredentials.UserName.Password = "TIGER";  
  
            // Create Client for GET_ACCOUNT Overload 2 -- takes ACCOUNT NAME parameter  
            // NOTE: this client can be created from configuration; detail provided here  
            // for demonstration  
            OracleDBBinding overload2Binding = new OracleDBBinding();  
            EndpointAddress overload2EndpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
            SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client getAccountByNameClient =   
                new SCOTTPackageACCOUNT_PKGGET_ACCOUNToverload2Client(overload2Binding, overload2EndpointAddress);  
            // NOTE: user name and password are case-sensitive  
            getAccountByNameClient.ClientCredentials.UserName.UserName = "SCOTT";  
            getAccountByNameClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
                Console.WriteLine("Opening clients -- please wait");  
                // Open clients  
                createAccountClient.Open();  
                getAccountByIdClient.Open();  
                getAccountByNameClient.Open();  
  
                Console.WriteLine("Creating new account");  
                // Create an account record  
                // NOTE: ACCTRECORD is defined in all three namespaces so specify the definition  
                // that corresponds to the client.  
                CREATE_ACCOUNTns.ACCTRECORD acctRec = new CREATE_ACCOUNTns.ACCTRECORD();  
  
                // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
                acctRec.ACCTID = 0;  
                acctRec.NAME = newAccountName;  
                acctRec.BALANCE = 10537;  
  
                // Create address record  
                CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new CREATE_ACCOUNTns.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
                addrRec.STREET = "456 Valley Rd";  
                addrRec.CITY = "New York";  
                addrRec.STATE = "NY";  
  
                // Create account  
                acctId = (decimal)createAccountClient.CREATE_ACCOUNT(acctRec, addrRec);  
                Console.WriteLine("New Account Created: AccountId = {0}, Name = {1}, Balance = {2:C}",  
                   acctId, acctRec.NAME, acctRec.BALANCE);  
  
                /* Get new account by Id */  
                GET_ACCOUNT_BY_IDns.ACCTRECORD acctById = getAccountByIdClient.GET_ACCOUNT(acctId);  
                Console.WriteLine("Account Returned by Id: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctById.ACCTID, acctById.NAME, acctById.BALANCE);  
  
                /* Get new account by Name */  
                GET_ACCOUNT_BY_NAMEns.ACCTRECORD acctByName = getAccountByNameClient.GET_ACCOUNT(newAccountName);  
                Console.WriteLine("Account Returned by Name: AccountId={0}, Name={1}, Balance={2:C}",  
                    acctByName.ACCTID, acctByName.NAME, acctByName.BALANCE);  
  
                Console.WriteLine("Hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close all the clients  
                createAccountClient.Close();  
                getAccountByIdClient.Close();  
                getAccountByNameClient.Close();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)