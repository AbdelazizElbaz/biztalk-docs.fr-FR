---
title: "Exécuter des opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations using REF CURSORS
- REF CURSORS, performing operations
ms.assetid: b4cb9ede-eae1-44d7-8ba5-7e1261ccfa3b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb527a4451388475ce69a5321d0d05616fc8afde
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model"></a>Exécuter des opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF
Un REF CURSOR est un type de données Oracle PL/SQL qui représente un pointeur vers un jeu de résultats dans la base de données Oracle. Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge les paramètres REF CURSOR dans des procédures, fonctions et des packages. Paramètres REF CURSOR peuvent être fortement typés ou faiblement typée en fonction de la façon dont ils sont déclarés dans la procédure ou fonction. Pour une explication détaillée de la façon dont les paramètres REF CURSOR sont représentées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [des schémas de Message pour REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md). Le tableau suivant récapitule la manière dont les paramètres REF CURSOR sont représentées dans le modèle de service WCF.  
  
|Direction du paramètre|Fortement typée de REF CURSOR|Faiblement typée de REF CURSOR|  
|-------------------------|--------------------------------|------------------------------|  
|IN|`string [PARAM_NAME]`<br /><br /> Chaîne qui contient un bloc de PL/SQL. Le bloc de PL/SQL doit retourner un REF CURSOR ouvert par l’exécution d’une instruction « Ouvert pour SELECT » ou en appelant une fonction ou procédure. Un point d’interrogation ( ?) indique la position du curseur REF qui retourne le paramètre. Par exemple, « BEGIN ouvrir ? SÉLECTIONNEZ * À PARTIR DE MY_TABLE ; FIN », ou « BEGIN MY_PROC (Para1, ?, PARM2) ; FIN ; ».|Identique à fortement typé|  
|OUT|`out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`<br /><br /> Un jeu d’enregistrements fortement typée.|`out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`<br /><br /> Un faiblement typée générique jeu d’enregistrements.|  
|IN, OUT|DANS des REF CURSOR, les paramètres sont divisées en un et un paramètre OUT. Le paramètre IN est ajouté avec « _IN » dans la signature de méthode pour distinguer le paramètre OUT. Le paramètre OUT est représenté par un jeu d’enregistrements fortement typée.<br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`|DANS des REF CURSOR, les paramètres sont divisées en un et un paramètre OUT. Le paramètre IN est ajouté avec « _IN » pour distinguer le paramètre OUT. Le paramètre OUT est représenté par un jeu d’enregistrements faiblement typée.<br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`|  
  
 [PARAM_NAME] = le nom du paramètre dans la définition de fonction ou une procédure sur la base de données Oracle ; par exemple, MYREFCURSOR.  
  
 [PROC_NS] = l’espace de noms unique généré pour contenir des paramètres de package, de la procédure ou de la fonction ; par exemple, « microsoft.lobservices.oracledb._2007._03.SCOTT. Package.ACCOUNT_PKG. GET_ACTIVITY ».  
  
 [GENERIC_NS] = l’espace de noms dans lequel le jeu d’enregistrements générique est défini, « microsoft.lobservices.oracledb._2007._03 ».  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique utilisent le PACKAGE Oracle SCOTT/Package/ACCOUNT_PKG. La procédure suivante est utilisée à partir de ACCOUNT_PKG :  
  
```  
PROCEDURE get_activity(inrecs IN SYS_REFCURSOR, status OUT NUMBER, inoutrecs IN OUT activity_ref_type, outrecs OUT SYS_REFCURSOR);  
```  
  
 Un script pour générer ce package est fourni avec les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="ref-cursor-parameters-in-the-wcf-service-model"></a>Paramètres REF CURSOR dans le modèle de Service WCF  
 Les exemples suivants montrent les classes et un client WCF généré pour la procédure /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY. Cette procédure a faiblement typée IN et paramètres des REF CURSOR et un paramètre dans les REF CURSOR fortement typée.  
  
 Voici la signature de la méthode qui est générée par le client WCF pour appeler GET_ACTIVITY.  
  
```  
public System.Nullable<decimal> GET_ACTIVITY(string INRECS, string INOUTRECS_IN, out microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY.INOUTRECSRECORD[] INOUTRECS, out microsoft.lobservices.oracledb._2007._03.GenRecordRow[] OUTRECS);  
```  
  
 Dans le **GET_ACTIVITY** (méthode), le paramètre OUT dans INOUTRECS est fractionnée en deux paramètres :  
  
-   INOUTRECS_IN est une chaîne qui représente un paramètre IN REF CURSOR.  
  
-   INOUTRECS est un jeu d’enregistrements de fortement typé qui représente un paramètre de sortie REF CURSOR.  
  
 Le faiblement typée OUTRECS, le paramètre OUT est représentée comme un jeu d’enregistrements générique. Le faiblement typée dans le paramètre, INRECS, est représentée sous forme de chaîne.  
  
### <a name="strongly-typed-out-ref-cursor-parameters"></a>Fortement typée des paramètres REF CURSOR  
 Fortement typée hors (ou en arrière) les paramètres REF CURSOR sont générés dans un espace de noms unique basé sur le schéma, le PACKAGE et le nom de la procédure ou fonction dans lequel ils sont utilisés. Pour la procédure /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY, cet espace de noms est `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`. Le nom de classe est formé en ajoutant le nom du paramètre avec « Enregistrement » et la classe est composée de propriétés qui représentent les champs d’Oracle. Le code suivant illustre une partie de la classe qui représente les enregistrements fortement typé générés pour le paramètre INOUTRECS REF CURSOR.  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class INOUTRECSRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private System.Nullable<decimal> TIDField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public System.Nullable<decimal> TID {  
            get {  
                return this.TIDField;  
            }  
            set {  
                this.TIDField = value;  
            }  
        }  
  
        ...  
  
    }  
}  
```  
  
### <a name="weakly-typed-out-ref-cursor-parameters"></a>Faiblement typée des paramètres REF CURSOR  
 Faiblement typée hors (ou en arrière) les paramètres REF CURSOR sont représentées par la classe d’enregistrement générique. Le jeu d’enregistrements générique est toujours généré dans le même espace de noms et portant le même nom de classe, quelle que soit la fonction ou procédure. Le code suivant illustre la classe d’enregistrement générique, **microsoft.lobservices.oracledb._2007._03.GenRecordRow**, qui représente les enregistrements pour le paramètre OUTRECS OUT SYS_REFCURSOR (faiblement typée).  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordRow : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumnField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumn {  
            get {  
                return this.GenRecordColumnField;  
            }  
            set {  
                this.GenRecordColumnField = value;  
            }  
        }  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordColumn : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private string ColumnNameField;  
  
        private string ColumnValueField;  
  
        private string ColumnTypeField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false)]  
        public string ColumnName {  
            get {  
                return this.ColumnNameField;  
            }  
            set {  
                this.ColumnNameField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public string ColumnValue {  
            get {  
                return this.ColumnValueField;  
            }  
            set {  
                this.ColumnValueField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false, Order=2)]  
        public string ColumnType {  
            get {  
                return this.ColumnTypeField;  
            }  
            set {  
                this.ColumnTypeField = value;  
            }  
        }  
    }  
}  
```  
  
## <a name="using-ref-cursor-parameters-with-a-wcf-client"></a>À l’aide de paramètres REF CURSOR avec un Client WCF  
 Pour appeler une procédure ou une fonction avec des paramètres REF CURSOR à l’aide d’un client WCF, vous procédez comme suit :  
  
1.  Passer une chaîne pour chacune d’elles dans ou bloc de paramètre dans les REF CURSOR qui contient la PL/SQL pour ouvrir le REF CURSOR. Ce bloc peut soit exécuter une instruction OPEN pour sélectionner ou appeler une fonction ou une procédure qui retourne une référence de curseur ouvert dans un paramètre OUT.  
  
2.  Lorsque la procédure ou fonction est retournée, traiter les données dans les jeux d’enregistrements retournés pour OUT ou IN des REF CURSOR de paramètres. Le jeu d’enregistrements sera un générique enregistrement défini pour les paramètres REF CURSOR faiblement typée ou fortement typée définie pour les paramètres de REF CURSOR fortement typée.  
  
 Pour plus d’informations sur la façon d’appeler des procédures et des fonctions à l’aide du modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
 L’exemple suivant appelle la procédure GET_ACTIVITY. Il illustre les deux méthodes pour spécifier un paramètre IN REF CURSOR :  
  
-   Pour le paramètre IN REF CURSOR, une instruction ouvert pour SELECT est spécifiée pour retourner l’activité pour 100001 de compte.  
  
-   Pour le paramètre IN des REF CURSOR, la procédure /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY est appelée. Cette procédure ouvre un REF CURSOR qui contient l’ensemble de l’activité dans la table ACCOUNTACTIVITY et la retourne comme un paramètre OUT.  
  
 L’exemple montre également comment lire des données à partir de l’enregistrement renvoyé pour les paramètres REF CURSOR à la fois fortement typée et faiblement typée.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// namespaces for strongly-typed and weakly typed REF CURSOR records  
using GET_ACTIVITYns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY;  
using GENERICns = microsoft.lobservices.oracledb._2007._03;  
  
// In this sample, INRECS is opened by using an OPEN FOR statement, and  
// INOUTRECS_IN is opened by calling the GET_ALL_ACTIVITY procedure on Oracle.  
  
namespace OracleRefCursorsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the client  
            SCOTTPackageACCOUNT_PKGClient accountPkgClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // Set credentials  
            accountPkgClient.ClientCredentials.UserName.UserName = "SCOTT";  
            accountPkgClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
  
                GET_ACTIVITYns.INOUTRECSRECORD[] strongCursor;  
                GENERICns.GenRecordRow[] weakCursor;  
  
                Console.WriteLine("Opening client");  
                // Open the client  
                accountPkgClient.Open();  
  
                Console.WriteLine("Invoking ACCOUNT_PKG.GET_ACTIVITY");  
                // Get  ACCOUNTACTIVITY records  
                // The IN REF CURSOR is set to all activity for account 100001  
                // The input part of the IN OUT ref cursor calls GET_ALL_ACTIVITY  
                // The weakly-typed OUT REF CURSOR parameter returns a list of activity for account 100001  
                // The strongly-typed IN OUT REF CURSOR parameter returns a list of all activity  
                string inRecsString = "BEGIN OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY WHERE ACCOUNT=100001; END;";  
                string inoutRecsString = "BEGIN ACCOUNT_PKG.GET_ALL_ACTIVITY(?); END;";  
  
                accountPkgClient.GET_ACTIVITY(  
                                inRecsString,  
                                inoutRecsString,  
                                out strongCursor,  
                                out weakCursor);  
  
                // Display strong ref cursor (all activity)  
                Console.WriteLine("\nList of all activity returned (strong ref cursor)");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < strongCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2:C}\t{3}\t{4}",strongCursor[i].TID,  
                        strongCursor[i].ACCOUNT,   
                        strongCursor[i].AMOUNT,   
                        strongCursor[1].TRANSDATE,  
                        strongCursor[i].DESCRIPTION);  
                }  
  
                // Display weak ref cursor (account 100001)  
                Console.WriteLine("\nList of activity for account 100001 returned (weak ref cursor)");  
                Console.WriteLine("Tx Id\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < weakCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1:C}\t{2}\t{3}", weakCursor[i].GenRecordColumn[0].ColumnValue,  
                        weakCursor[i].GenRecordColumn[2].ColumnValue,  
                        weakCursor[i].GenRecordColumn[4].ColumnValue,  
                        weakCursor[i].GenRecordColumn[3].ColumnValue);  
                }  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
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
                // Close the client  
                accountPkgClient.Close();  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)