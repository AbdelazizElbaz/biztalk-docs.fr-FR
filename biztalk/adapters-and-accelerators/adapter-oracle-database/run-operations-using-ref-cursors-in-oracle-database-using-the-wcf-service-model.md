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
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="7a30e-102">Exécuter des opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="7a30e-102">Run Operations Using REF CURSORS in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="7a30e-103">Un REF CURSOR est un type de données Oracle PL/SQL qui représente un pointeur vers un jeu de résultats dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="7a30e-103">A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database.</span></span> <span data-ttu-id="7a30e-104">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge les paramètres REF CURSOR dans des procédures, fonctions et des packages.</span><span class="sxs-lookup"><span data-stu-id="7a30e-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports REF CURSOR parameters in procedures, functions, and packages.</span></span> <span data-ttu-id="7a30e-105">Paramètres REF CURSOR peuvent être fortement typés ou faiblement typée en fonction de la façon dont ils sont déclarés dans la procédure ou fonction.</span><span class="sxs-lookup"><span data-stu-id="7a30e-105">REF CURSOR parameters can be strongly-typed or weakly-typed depending on how they are declared in the procedure or function.</span></span> <span data-ttu-id="7a30e-106">Pour une explication détaillée de la façon dont les paramètres REF CURSOR sont représentées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [des schémas de Message pour REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md). Le tableau suivant récapitule la manière dont les paramètres REF CURSOR sont représentées dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="7a30e-106">For a detailed explanation of how REF CURSOR parameters are represented by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for REF CURSORS](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md).The following table summarizes how REF CURSOR parameters are represented in the WCF service model.</span></span>  
  
|<span data-ttu-id="7a30e-107">Direction du paramètre</span><span class="sxs-lookup"><span data-stu-id="7a30e-107">Parameter Direction</span></span>|<span data-ttu-id="7a30e-108">Fortement typée de REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7a30e-108">Strongly-typed REF CURSOR</span></span>|<span data-ttu-id="7a30e-109">Faiblement typée de REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7a30e-109">Weakly-typed REF CURSOR</span></span>|  
|-------------------------|--------------------------------|------------------------------|  
|<span data-ttu-id="7a30e-110">IN</span><span class="sxs-lookup"><span data-stu-id="7a30e-110">IN</span></span>|`string [PARAM_NAME]`<br /><br /> <span data-ttu-id="7a30e-111">Chaîne qui contient un bloc de PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="7a30e-111">String that contains a PL/SQL block.</span></span> <span data-ttu-id="7a30e-112">Le bloc de PL/SQL doit retourner un REF CURSOR ouvert par l’exécution d’une instruction « Ouvert pour SELECT » ou en appelant une fonction ou procédure.</span><span class="sxs-lookup"><span data-stu-id="7a30e-112">The PL/SQL block must return an opened REF CURSOR either by executing an "OPEN FOR SELECT" statement or by invoking a function or procedure.</span></span> <span data-ttu-id="7a30e-113">Un point d’interrogation ( ?) indique la position du curseur REF qui retourne le paramètre.</span><span class="sxs-lookup"><span data-stu-id="7a30e-113">A question mark (?) indicates the position of the REF CURSOR that returns the parameter.</span></span> <span data-ttu-id="7a30e-114">Par exemple, « BEGIN ouvrir ?</span><span class="sxs-lookup"><span data-stu-id="7a30e-114">For example, "BEGIN OPEN ?</span></span> <span data-ttu-id="7a30e-115">SÉLECTIONNEZ * À PARTIR DE MY_TABLE ; FIN », ou « BEGIN MY_PROC (Para1, ?, PARM2) ; FIN ; ».</span><span class="sxs-lookup"><span data-stu-id="7a30e-115">FOR SELECT * FROM MY_TABLE; END", or "BEGIN MY_PROC(PARM1, ?, PARM2); END;".</span></span>|<span data-ttu-id="7a30e-116">Identique à fortement typé</span><span class="sxs-lookup"><span data-stu-id="7a30e-116">Same as strongly-typed</span></span>|  
|<span data-ttu-id="7a30e-117">OUT</span><span class="sxs-lookup"><span data-stu-id="7a30e-117">OUT</span></span>|`out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`<br /><br /> <span data-ttu-id="7a30e-118">Un jeu d’enregistrements fortement typée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-118">A strongly-typed record set.</span></span>|`out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`<br /><br /> <span data-ttu-id="7a30e-119">Un faiblement typée générique jeu d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="7a30e-119">A weakly-typed generic record set.</span></span>|  
|<span data-ttu-id="7a30e-120">IN, OUT</span><span class="sxs-lookup"><span data-stu-id="7a30e-120">IN OUT</span></span>|<span data-ttu-id="7a30e-121">DANS des REF CURSOR, les paramètres sont divisées en un et un paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="7a30e-121">IN OUT REF CURSOR parameters are split into an IN and an OUT parameter.</span></span> <span data-ttu-id="7a30e-122">Le paramètre IN est ajouté avec « _IN » dans la signature de méthode pour distinguer le paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="7a30e-122">The IN parameter is appended with "_IN" in the method signature to distinguish it from the OUT parameter.</span></span> <span data-ttu-id="7a30e-123">Le paramètre OUT est représenté par un jeu d’enregistrements fortement typée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-123">The OUT parameter is represented by a strongly-typed record set.</span></span><br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`|<span data-ttu-id="7a30e-124">DANS des REF CURSOR, les paramètres sont divisées en un et un paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="7a30e-124">IN OUT REF CURSOR parameters are split into an IN and an OUT parameter.</span></span> <span data-ttu-id="7a30e-125">Le paramètre IN est ajouté avec « _IN » pour distinguer le paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="7a30e-125">The IN parameter is appended with "_IN" to distinguish it from the OUT parameter.</span></span> <span data-ttu-id="7a30e-126">Le paramètre OUT est représenté par un jeu d’enregistrements faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-126">The OUT parameter is represented by a weakly-typed record set.</span></span><br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`|  
  
 <span data-ttu-id="7a30e-127">[PARAM_NAME] = le nom du paramètre dans la définition de fonction ou une procédure sur la base de données Oracle ; par exemple, MYREFCURSOR.</span><span class="sxs-lookup"><span data-stu-id="7a30e-127">[PARAM_NAME] = the name of the parameter in the function or procedure definition on the Oracle database; for example, MYREFCURSOR.</span></span>  
  
 <span data-ttu-id="7a30e-128">[PROC_NS] = l’espace de noms unique généré pour contenir des paramètres de package, de la procédure ou de la fonction ; par exemple, « microsoft.lobservices.oracledb._2007._03.SCOTT. Package.ACCOUNT_PKG. GET_ACTIVITY ».</span><span class="sxs-lookup"><span data-stu-id="7a30e-128">[PROC_NS] = The unique namespace generated to contain parameters of the package, procedure, or function; for example, "microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY".</span></span>  
  
 <span data-ttu-id="7a30e-129">[GENERIC_NS] = l’espace de noms dans lequel le jeu d’enregistrements générique est défini, « microsoft.lobservices.oracledb._2007._03 ».</span><span class="sxs-lookup"><span data-stu-id="7a30e-129">[GENERIC_NS] = The namespace in which the generic record set is defined, "microsoft.lobservices.oracledb._2007._03".</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="7a30e-130">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="7a30e-130">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="7a30e-131">Les exemples de cette rubrique utilisent le PACKAGE Oracle SCOTT/Package/ACCOUNT_PKG.</span><span class="sxs-lookup"><span data-stu-id="7a30e-131">The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG Oracle PACKAGE.</span></span> <span data-ttu-id="7a30e-132">La procédure suivante est utilisée à partir de ACCOUNT_PKG :</span><span class="sxs-lookup"><span data-stu-id="7a30e-132">The following procedure is used from ACCOUNT_PKG:</span></span>  
  
```  
PROCEDURE get_activity(inrecs IN SYS_REFCURSOR, status OUT NUMBER, inoutrecs IN OUT activity_ref_type, outrecs OUT SYS_REFCURSOR);  
```  
  
 <span data-ttu-id="7a30e-133">Un script pour générer ce package est fourni avec les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="7a30e-133">A script to generate this package is supplied with the SDK samples.</span></span> <span data-ttu-id="7a30e-134">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="7a30e-134">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="ref-cursor-parameters-in-the-wcf-service-model"></a><span data-ttu-id="7a30e-135">Paramètres REF CURSOR dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="7a30e-135">REF CURSOR Parameters in the WCF Service Model</span></span>  
 <span data-ttu-id="7a30e-136">Les exemples suivants montrent les classes et un client WCF généré pour la procédure /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="7a30e-136">The following examples show the classes and WCF client generated for the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure.</span></span> <span data-ttu-id="7a30e-137">Cette procédure a faiblement typée IN et paramètres des REF CURSOR et un paramètre dans les REF CURSOR fortement typée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-137">This procedure has weakly-typed IN and OUT REF CURSOR parameters and a strongly-typed IN OUT REF CURSOR parameter.</span></span>  
  
 <span data-ttu-id="7a30e-138">Voici la signature de la méthode qui est générée par le client WCF pour appeler GET_ACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="7a30e-138">Here is the signature of the method that is generated in the WCF client to invoke GET_ACTIVITY.</span></span>  
  
```  
public System.Nullable<decimal> GET_ACTIVITY(string INRECS, string INOUTRECS_IN, out microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY.INOUTRECSRECORD[] INOUTRECS, out microsoft.lobservices.oracledb._2007._03.GenRecordRow[] OUTRECS);  
```  
  
 <span data-ttu-id="7a30e-139">Dans le **GET_ACTIVITY** (méthode), le paramètre OUT dans INOUTRECS est fractionnée en deux paramètres :</span><span class="sxs-lookup"><span data-stu-id="7a30e-139">In the **GET_ACTIVITY** method, the IN OUT parameter INOUTRECS is split into two parameters:</span></span>  
  
-   <span data-ttu-id="7a30e-140">INOUTRECS_IN est une chaîne qui représente un paramètre IN REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7a30e-140">INOUTRECS_IN is a string that represents an IN REF CURSOR parameter.</span></span>  
  
-   <span data-ttu-id="7a30e-141">INOUTRECS est un jeu d’enregistrements de fortement typé qui représente un paramètre de sortie REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7a30e-141">INOUTRECS is a strongly-typed record set that represents an OUT REF CURSOR parameter.</span></span>  
  
 <span data-ttu-id="7a30e-142">Le faiblement typée OUTRECS, le paramètre OUT est représentée comme un jeu d’enregistrements générique.</span><span class="sxs-lookup"><span data-stu-id="7a30e-142">The weakly-typed OUT parameter, OUTRECS, is represented as a generic record set.</span></span> <span data-ttu-id="7a30e-143">Le faiblement typée dans le paramètre, INRECS, est représentée sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7a30e-143">The weakly-typed IN parameter, INRECS, is represented as a string.</span></span>  
  
### <a name="strongly-typed-out-ref-cursor-parameters"></a><span data-ttu-id="7a30e-144">Fortement typée des paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7a30e-144">Strongly-Typed OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="7a30e-145">Fortement typée hors (ou en arrière) les paramètres REF CURSOR sont générés dans un espace de noms unique basé sur le schéma, le PACKAGE et le nom de la procédure ou fonction dans lequel ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="7a30e-145">Strongly-typed OUT (or IN OUT) REF CURSOR parameters are generated in a unique namespace based on the SCHEMA, PACKAGE, and name of the procedure or function in which they are used.</span></span> <span data-ttu-id="7a30e-146">Pour la procédure /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY, cet espace de noms est `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`.</span><span class="sxs-lookup"><span data-stu-id="7a30e-146">For the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure, this namespace is `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`.</span></span> <span data-ttu-id="7a30e-147">Le nom de classe est formé en ajoutant le nom du paramètre avec « Enregistrement » et la classe est composée de propriétés qui représentent les champs d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="7a30e-147">The class name is formed by appending the name of the parameter with "RECORD" and the class is composed of properties that represent the Oracle fields.</span></span> <span data-ttu-id="7a30e-148">Le code suivant illustre une partie de la classe qui représente les enregistrements fortement typé générés pour le paramètre INOUTRECS REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7a30e-148">The following shows a part of the class that represents the strongly-typed records generated for the INOUTRECS REF CURSOR parameter.</span></span>  
  
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
  
### <a name="weakly-typed-out-ref-cursor-parameters"></a><span data-ttu-id="7a30e-149">Faiblement typée des paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7a30e-149">Weakly-Typed OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="7a30e-150">Faiblement typée hors (ou en arrière) les paramètres REF CURSOR sont représentées par la classe d’enregistrement générique.</span><span class="sxs-lookup"><span data-stu-id="7a30e-150">Weakly-typed OUT (or IN OUT) REF CURSOR parameters are represented by the generic record class.</span></span> <span data-ttu-id="7a30e-151">Le jeu d’enregistrements générique est toujours généré dans le même espace de noms et portant le même nom de classe, quelle que soit la fonction ou procédure.</span><span class="sxs-lookup"><span data-stu-id="7a30e-151">The generic record set is always generated in the same namespace and with the same class name regardless of the function or procedure.</span></span> <span data-ttu-id="7a30e-152">Le code suivant illustre la classe d’enregistrement générique, **microsoft.lobservices.oracledb._2007._03.GenRecordRow**, qui représente les enregistrements pour le paramètre OUTRECS OUT SYS_REFCURSOR (faiblement typée).</span><span class="sxs-lookup"><span data-stu-id="7a30e-152">The following code shows the generic record class, **microsoft.lobservices.oracledb._2007._03.GenRecordRow**, which represents the records for the OUTRECS OUT SYS_REFCURSOR parameter (weakly-typed).</span></span>  
  
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
  
## <a name="using-ref-cursor-parameters-with-a-wcf-client"></a><span data-ttu-id="7a30e-153">À l’aide de paramètres REF CURSOR avec un Client WCF</span><span class="sxs-lookup"><span data-stu-id="7a30e-153">Using REF CURSOR Parameters with a WCF Client</span></span>  
 <span data-ttu-id="7a30e-154">Pour appeler une procédure ou une fonction avec des paramètres REF CURSOR à l’aide d’un client WCF, vous procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7a30e-154">To invoke a procedure or function with REF CURSOR parameters by using a WCF client, you do the following:</span></span>  
  
1.  <span data-ttu-id="7a30e-155">Passer une chaîne pour chacune d’elles dans ou bloc de paramètre dans les REF CURSOR qui contient la PL/SQL pour ouvrir le REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7a30e-155">Pass a string for each IN or IN OUT REF CURSOR parameter that contains the PL/SQL block to open the REF CURSOR.</span></span> <span data-ttu-id="7a30e-156">Ce bloc peut soit exécuter une instruction OPEN pour sélectionner ou appeler une fonction ou une procédure qui retourne une référence de curseur ouvert dans un paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="7a30e-156">This block can either execute an OPEN FOR SELECT statement or invoke a function or procedure that returns an opened REF CURSOR in an OUT parameter.</span></span>  
  
2.  <span data-ttu-id="7a30e-157">Lorsque la procédure ou fonction est retournée, traiter les données dans les jeux d’enregistrements retournés pour OUT ou IN des REF CURSOR de paramètres.</span><span class="sxs-lookup"><span data-stu-id="7a30e-157">When the procedure or function returns, operate on the data in the record sets returned for any OUT or IN OUT REF CURSOR parameters.</span></span> <span data-ttu-id="7a30e-158">Le jeu d’enregistrements sera un générique enregistrement défini pour les paramètres REF CURSOR faiblement typée ou fortement typée définie pour les paramètres de REF CURSOR fortement typée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-158">The record set will be a generic record set for weakly-typed REF CURSOR parameters or a strongly-typed record set for strongly-typed REF CURSOR parameters.</span></span>  
  
 <span data-ttu-id="7a30e-159">Pour plus d’informations sur la façon d’appeler des procédures et des fonctions à l’aide du modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="7a30e-159">For more information about how to invoke procedures and functions by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="7a30e-160">L’exemple suivant appelle la procédure GET_ACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="7a30e-160">The following example calls the GET_ACTIVITY procedure.</span></span> <span data-ttu-id="7a30e-161">Il illustre les deux méthodes pour spécifier un paramètre IN REF CURSOR :</span><span class="sxs-lookup"><span data-stu-id="7a30e-161">It demonstrates both ways of specifying an IN REF CURSOR parameter:</span></span>  
  
-   <span data-ttu-id="7a30e-162">Pour le paramètre IN REF CURSOR, une instruction ouvert pour SELECT est spécifiée pour retourner l’activité pour 100001 de compte.</span><span class="sxs-lookup"><span data-stu-id="7a30e-162">For the IN REF CURSOR parameter, an OPEN FOR SELECT statement is specified to return activity for ACCOUNT 100001.</span></span>  
  
-   <span data-ttu-id="7a30e-163">Pour le paramètre IN des REF CURSOR, la procédure /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY est appelée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-163">For the IN OUT REF CURSOR parameter, the /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY procedure is invoked.</span></span> <span data-ttu-id="7a30e-164">Cette procédure ouvre un REF CURSOR qui contient l’ensemble de l’activité dans la table ACCOUNTACTIVITY et la retourne comme un paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="7a30e-164">This procedure opens a REF CURSOR that contains all of the activity in the ACCOUNTACTIVITY table and returns it as an OUT parameter.</span></span>  
  
 <span data-ttu-id="7a30e-165">L’exemple montre également comment lire des données à partir de l’enregistrement renvoyé pour les paramètres REF CURSOR à la fois fortement typée et faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="7a30e-165">The example also demonstrates how to read data from the record set returned for both strongly-typed and weakly-typed REF CURSOR parameters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a30e-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a30e-166">See Also</span></span>  
 [<span data-ttu-id="7a30e-167">Développer des applications de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="7a30e-167">Develop Oracle Database Application Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)