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
# <a name="run-operations-using-record-types-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="95e35-102">Exécuter des opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="95e35-102">Run Operations Using RECORD Types in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="95e35-103">Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="95e35-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="95e35-104">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes.</span><span class="sxs-lookup"><span data-stu-id="95e35-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> <span data-ttu-id="95e35-105">Dans le modèle de service WCF, des types d’enregistrements sont désérialisées à des classes de .NET fortement typée.</span><span class="sxs-lookup"><span data-stu-id="95e35-105">In the WCF service model, RECORD types are deserialized to strongly-typed .NET classes.</span></span> <span data-ttu-id="95e35-106">Les champs d’enregistrement sont représentés en tant que propriétés sur la classe.</span><span class="sxs-lookup"><span data-stu-id="95e35-106">The record fields are represented as properties on the class.</span></span>  
  
 <span data-ttu-id="95e35-107">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge les types de types d’enregistrements suivants :</span><span class="sxs-lookup"><span data-stu-id="95e35-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the following kinds of RECORD types:</span></span>  
  
-   <span data-ttu-id="95e35-108">Types d’enregistrements qui sont déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.</span><span class="sxs-lookup"><span data-stu-id="95e35-108">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="95e35-109">Types d’enregistrements qui sont déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL, par exemple,`TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`</span><span class="sxs-lookup"><span data-stu-id="95e35-109">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages for example, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`</span></span>  
  
-   <span data-ttu-id="95e35-110">Types d’enregistrements qui contiennent des enregistrements imbriqués.</span><span class="sxs-lookup"><span data-stu-id="95e35-110">RECORD types that contain nested records.</span></span>  
  
-   <span data-ttu-id="95e35-111">Types d’enregistrements qui s’affichent, OUT ou paramètres dans des procédures ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="95e35-111">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
-   <span data-ttu-id="95e35-112">Types d’enregistrements qui sont des valeurs de retour des fonctions.</span><span class="sxs-lookup"><span data-stu-id="95e35-112">RECORD types that are RETURN values of functions.</span></span>  
  
 <span data-ttu-id="95e35-113">Cette rubrique montre comment les types d’enregistrement sont représentés dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="95e35-113">This topic shows how RECORD types are represented in the WCF service model.</span></span> <span data-ttu-id="95e35-114">Pour plus d’informations sur la façon d’appeler des fonctions et procédures d’Oracle, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="95e35-114">For information about how to call Oracle procedures and functions, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="95e35-115">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="95e35-115">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="95e35-116">Les exemples dans cette rubrique utilisent le PACKAGE PL/SQL de Oracle SCOTT/ACCOUNT_PKG.</span><span class="sxs-lookup"><span data-stu-id="95e35-116">The examples in this topic use the /SCOTT/ACCOUNT_PKG Oracle PL/SQL PACKAGE.</span></span> <span data-ttu-id="95e35-117">Les éléments suivants sont utilisés à partir de ACCOUNT_PKG.</span><span class="sxs-lookup"><span data-stu-id="95e35-117">The following elements are used from ACCOUNT_PKG.</span></span>  
  
```  
TYPE address_rec_type IS RECORD (street customer.street%TYPE, city customer.city%TYPE, state customer.state%TYPE);  
  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
  
TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);  
  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
```  
  
 <span data-ttu-id="95e35-118">Un script pour générer ce package est fourni avec les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="95e35-118">A script to generate this package is supplied with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span> <span data-ttu-id="95e35-119">Pour plus d’informations, consultez le script</span><span class="sxs-lookup"><span data-stu-id="95e35-119">For more information, see the script</span></span>  
  
 <span data-ttu-id="95e35-120">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95e35-120">For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="record-types-in-the-wcf-service-model"></a><span data-ttu-id="95e35-121">Types d’enregistrements dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="95e35-121">RECORD Types in the WCF Service Model</span></span>  
 <span data-ttu-id="95e35-122">Types d’enregistrements Oracle sont représentés en tant que types XML complexes par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95e35-122">Oracle RECORD types are represented as complex XML types by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="95e35-123">Dans le modèle de service WCF, des types XML complexes sont représentées par une classe, et les propriétés de cette classe représentent les champs du type d’enregistrement d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="95e35-123">In the WCF service model, complex XML types are represented by a class, and the properties of this class represent the fields of the Oracle RECORD type.</span></span> <span data-ttu-id="95e35-124">La classe qui représente un paramètre de type d’enregistrement est générée dans un espace de noms est qualifié par le PACKAGE (le cas échéant) et le schéma de la fonction ou la procédure.</span><span class="sxs-lookup"><span data-stu-id="95e35-124">The class that represents a RECORD type parameter is generated in a namespace that is qualified by the PACKAGE (if any) and SCHEMA of the function or procedure.</span></span> <span data-ttu-id="95e35-125">Cet espace de noms identifie de façon unique la fonction ou procédure du paramètre.</span><span class="sxs-lookup"><span data-stu-id="95e35-125">This namespace uniquely identifies the function or procedure of the parameter.</span></span> <span data-ttu-id="95e35-126">Par exemple, les paramètres de type d’enregistrement à la procédure CREATE_ACCOUNT le ACCOUNT_PKG PACKAGE Oracle sont créés dans l’espace de noms suivant : `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT`.</span><span class="sxs-lookup"><span data-stu-id="95e35-126">For example, the RECORD type parameters to the CREATE_ACCOUNT procedure in the Oracle PACKAGE ACCOUNT_PKG are created in the following namespace: `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT`.</span></span> <span data-ttu-id="95e35-127">Pour plus d’informations sur les espaces de noms permet de représenter des types complexes dans les procédures et fonctions dans le modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="95e35-127">For more information about the namespaces used in the WCF service model to represent complex types in procedures and functions, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="95e35-128">Tandis que l’espace de noms d’un paramètre de type d’enregistrement est déterminé par la procédure ou fonction, le nom de la classe générée pour le paramètre de type d’enregistrement est déterminé de la façon dont dans lequel est déclaré le type d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="95e35-128">While the namespace of a RECORD type parameter is determined by the procedure or function, the name of the class generated for the RECORD type parameter is determined by the way in which the RECORD type is declared.</span></span> <span data-ttu-id="95e35-129">Le tableau suivant montre la façon dont le nom de la classe est généré selon les deux façons de déclarer le paramètre de type d’enregistrement d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="95e35-129">The following table shows how the name of the class is generated based on the two different ways of declaring the Oracle RECORD type parameter.</span></span>  
  
|<span data-ttu-id="95e35-130">Type d’enregistrement Oracle</span><span class="sxs-lookup"><span data-stu-id="95e35-130">Oracle RECORD type</span></span>|<span data-ttu-id="95e35-131">Nom</span><span class="sxs-lookup"><span data-stu-id="95e35-131">Name</span></span>|<span data-ttu-id="95e35-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="95e35-132">Example</span></span>|  
|------------------------|----------|-------------|  
|<span data-ttu-id="95e35-133">Paramètre de procédure ou fonction ROWTYPE de % TABLE</span><span class="sxs-lookup"><span data-stu-id="95e35-133">TABLE%ROWTYPE procedure or function parameter</span></span>|<span data-ttu-id="95e35-134">[NOM_PARAMÈTRE] ENREGISTREMENT</span><span class="sxs-lookup"><span data-stu-id="95e35-134">[PARAMETER_NAME]RECORD</span></span>|<span data-ttu-id="95e35-135">ACCTRECORD</span><span class="sxs-lookup"><span data-stu-id="95e35-135">ACCTRECORD</span></span>|  
|<span data-ttu-id="95e35-136">TYPE du paramètre de package d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="95e35-136">TYPE of RECORD package parameter</span></span>|<span data-ttu-id="95e35-137">[PACKAGE_NAME] [RECORD_TYPE_NAME] ENREGISTREMENT</span><span class="sxs-lookup"><span data-stu-id="95e35-137">[PACKAGE_NAME][RECORD_TYPE_NAME]RECORD</span></span>|<span data-ttu-id="95e35-138">ACCOUNT_PKGACCTINFO_REC_TYPERECORD</span><span class="sxs-lookup"><span data-stu-id="95e35-138">ACCOUNT_PKGACCTINFO_REC_TYPERECORD</span></span>|  
  
 <span data-ttu-id="95e35-139">[Nom_paramètre] = le nom du paramètre de procédure ou fonction ; par exemple, Acct.</span><span class="sxs-lookup"><span data-stu-id="95e35-139">[PARAMETER_NAME] = the name of the procedure or function parameter; for example, ACCT.</span></span>  
  
 <span data-ttu-id="95e35-140">[PACKAGE_NAME] = le nom du package Oracle.</span><span class="sxs-lookup"><span data-stu-id="95e35-140">[PACKAGE_NAME] = the name of the Oracle package.</span></span>  
  
 <span data-ttu-id="95e35-141">[RECORD_TYPE_NAME] = le nom spécifié dans la déclaration de TYPE d’enregistrement ; par exemple, ACCTINFO_REC_TYPE.</span><span class="sxs-lookup"><span data-stu-id="95e35-141">[RECORD_TYPE_NAME] = the name specified in the RECORD TYPE declaration; for example, ACCTINFO_REC_TYPE.</span></span>  
  
 <span data-ttu-id="95e35-142">Le code suivant montre les signatures de méthode du client WCF généré pour les deux fonctions d’Oracle.</span><span class="sxs-lookup"><span data-stu-id="95e35-142">The following code shows the method signatures of the WCF client generated for two Oracle functions.</span></span> <span data-ttu-id="95e35-143">La fonction /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT prend deux paramètres IN de type enregistrement simples, et la fonction /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO retourne un paramètre de type d’enregistrement qui contient deux types d’enregistrements imbriqués.</span><span class="sxs-lookup"><span data-stu-id="95e35-143">The /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT function takes two simple RECORD type IN parameters, and the /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO function returns a RECORD type parameter that contains two nested RECORD types.</span></span> <span data-ttu-id="95e35-144">Les déclarations de fonction Oracle sont incluses en haut du code.</span><span class="sxs-lookup"><span data-stu-id="95e35-144">The Oracle function declarations are included at the top of the code.</span></span> <span data-ttu-id="95e35-145">Les paramètres de chaque fonction sont qualifiés par un espace de noms unique.</span><span class="sxs-lookup"><span data-stu-id="95e35-145">The parameters of each function are qualified by a unique namespace.</span></span>  
  
```  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
  
public partial class SCOTTPackageACCOUNT_PKGClient : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKG>, SCOTTPackageACCOUNT_PKG {  
  
    ...  
  
    public System.Nullable<decimal> CREATE_ACCOUNT(microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD ACCT, microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDR);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD GET_ACCOUNTINFO(System.Nullable<decimal> AID);  
}  
```  
  
 <span data-ttu-id="95e35-146">Le code suivant montre les classes générées pour les paramètres de la fonction CREATE_ACCOUNT :`FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;`</span><span class="sxs-lookup"><span data-stu-id="95e35-146">The following code shows the classes generated for the parameters of the CREATE_ACCOUNT function: `FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;`</span></span>  
  
 <span data-ttu-id="95e35-147">Cette fonction a un paramètre déclaré avec une TABLE % ROWTYPE et un paramètre déclaré avec un type de package de TYPE d’enregistrement (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).</span><span class="sxs-lookup"><span data-stu-id="95e35-147">This function has a parameter declared with a TABLE%ROWTYPE and a parameter declared with a TYPE of RECORD package type (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).</span></span>  
  
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
  
### <a name="representation-of-a-simple-record-type"></a><span data-ttu-id="95e35-148">Représentation sous forme d’un Type d’enregistrement Simple</span><span class="sxs-lookup"><span data-stu-id="95e35-148">Representation of a Simple Record Type</span></span>  
 <span data-ttu-id="95e35-149">Le code suivant montre comment un type d’enregistrement simple est représenté dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="95e35-149">The following code shows how a simple RECORD type is represented in the WCF service model.</span></span> <span data-ttu-id="95e35-150">Ce code affiche la vue développée de la **ACCOUNTRECORD** classe qui représente le paramètre de compte ROWTYPE dans la fonction CREATE_ACCOUNT.</span><span class="sxs-lookup"><span data-stu-id="95e35-150">This code shows the expanded view of the **ACCOUNTRECORD** class that represents the ACCOUNT%ROWTYPE parameter in the CREATE_ACCOUNT function.</span></span> <span data-ttu-id="95e35-151">Dans cette classe, les champs d’enregistrement (colonnes de la ligne) sont représentés en tant que propriétés.</span><span class="sxs-lookup"><span data-stu-id="95e35-151">In this class, the record fields (row columns) are represented as properties.</span></span>  
  
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
  
### <a name="representation-of-a-record-type-that-contains-nested-records"></a><span data-ttu-id="95e35-152">Représentation sous forme d’un Type d’enregistrement qui contient des enregistrements imbriqués</span><span class="sxs-lookup"><span data-stu-id="95e35-152">Representation of a Record Type that Contains Nested Records</span></span>  
 <span data-ttu-id="95e35-153">Le code suivant illustre la représentation sous forme d’un type d’enregistrement qui contient des enregistrements imbriqués.</span><span class="sxs-lookup"><span data-stu-id="95e35-153">The following code shows the representation of a RECORD type that contains nested records.</span></span> <span data-ttu-id="95e35-154">Ce type d’enregistrement particulier est la valeur de retour de la fonction GET_ACCOUNTINFO (`FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;`).</span><span class="sxs-lookup"><span data-stu-id="95e35-154">This particular RECORD type is the RETURN value of the GET_ACCOUNTINFO function (`FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;`).</span></span> <span data-ttu-id="95e35-155">Le ACCTINFO_REC_TYPE est un paramètre de package déclaré à l’aide d’une construction de TYPE d’enregistrement (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).</span><span class="sxs-lookup"><span data-stu-id="95e35-155">The ACCTINFO_REC_TYPE is a package parameter declared using a TYPE of RECORD construct (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).</span></span> <span data-ttu-id="95e35-156">Il contient deux types d’enregistrement simple imbriqué, un enregistrement de ligne de TABLE % et un TYPE d’enregistrement du package.</span><span class="sxs-lookup"><span data-stu-id="95e35-156">It contains two nested simple record types, a TABLE%ROW record and a package TYPE of RECORD record.</span></span> <span data-ttu-id="95e35-157">Ces deux enregistrements simples sont déclarées dans le même espace de noms en tant que leur enregistrement parent et suivent la convention d’affectation de noms attendue.</span><span class="sxs-lookup"><span data-stu-id="95e35-157">These two simple records are declared in the same namespace as their parent record and follow the expected naming convention.</span></span>  
  
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
  
## <a name="using-record-types-in-your-code"></a><span data-ttu-id="95e35-158">À l’aide des Types d’enregistrements dans votre Code</span><span class="sxs-lookup"><span data-stu-id="95e35-158">Using RECORD Types in Your Code</span></span>  
 <span data-ttu-id="95e35-159">À l’aide des types d’enregistrements dans votre code est simple.</span><span class="sxs-lookup"><span data-stu-id="95e35-159">Using RECORD types in your code is straightforward.</span></span> <span data-ttu-id="95e35-160">Pour appeler une procédure ou une fonction avec un paramètre de type d’enregistrement, vous créez une instance du type d’enregistrement ou de types et passez à la méthode appropriée sur le client WCF.</span><span class="sxs-lookup"><span data-stu-id="95e35-160">To invoke a procedure or function with a RECORD type parameter, you create an instance of the RECORD type or types and pass it to the appropriate method on the WCF client.</span></span> <span data-ttu-id="95e35-161">Lorsque retour de la procédure ou fonction, vous pouvez lire des propriétés sur n’importe quel OUT ou IN des paramètres ou retour de fonction de valeurs qui sont déclarés comme des types d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="95e35-161">When the procedure or function returns, you can read properties on any OUT or IN OUT parameters or function RETURN values that are declared as RECORD types.</span></span> <span data-ttu-id="95e35-162">Pour plus d’informations sur la façon d’appeler des procédures et des fonctions à l’aide du modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="95e35-162">For more information about how to invoke procedures and functions by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95e35-163">Paramètres de type enregistrement Oracle (et les retours de fonction) sont qualifiés par l’espace de noms de leur fonction ou procédure (et de package).</span><span class="sxs-lookup"><span data-stu-id="95e35-163">Oracle RECORD type parameters (and function returns) are qualified by the namespace of their function or procedure (and package).</span></span> <span data-ttu-id="95e35-164">Cela signifie qu’un espace de noms différent pour chaque procédure ou une fonction dans un type d’enregistrement qui est utilisé dans les deux procédures différentes ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="95e35-164">This means that a RECORD type that is used in two different procedures or functions will have a different namespace for each procedure or function.</span></span> <span data-ttu-id="95e35-165">Vous devez être sûr de qualifier le type d’enregistrement correctement lorsque vous l’utilisez pour une fonction ou une procédure spécifique.</span><span class="sxs-lookup"><span data-stu-id="95e35-165">You must be sure to qualify the RECORD type correctly when you use it for a specific procedure or function.</span></span> <span data-ttu-id="95e35-166">Par exemple, un type d’enregistrement (déclaration de TYPE d’enregistrement) qui est utilisé comme paramètre à deux fonctions différentes du package sera déclaré deux fois dans le code du client WCF avec chaque déclaration correspondant à l’espace de noms unique généré pour chaque fonction.</span><span class="sxs-lookup"><span data-stu-id="95e35-166">For example, a package RECORD type (RECORD of TYPE declaration) that is used as an IN parameter to two different functions will be declared twice in the WCF client code with each declaration corresponding to the unique namespace generated for each function.</span></span> <span data-ttu-id="95e35-167">Veillez à utiliser l’espace de noms correct sur le paramètre que vous passez à chaque fonction respectif.</span><span class="sxs-lookup"><span data-stu-id="95e35-167">You must be sure to use the correct namespace on the parameter that you pass to each respective function.</span></span>  
  
 <span data-ttu-id="95e35-168">Dans l’exemple suivant, la fonction CREATE_ACCOUNT est appelée avec deux paramètres d’enregistrement simple.</span><span class="sxs-lookup"><span data-stu-id="95e35-168">In the following example, the CREATE_ACCOUNT function is called with two simple record parameters.</span></span> <span data-ttu-id="95e35-169">Ensuite, la fonction GET_ACCOUNTINFO est appelée.</span><span class="sxs-lookup"><span data-stu-id="95e35-169">Next, the GET_ACCOUNTINFO function is called.</span></span> <span data-ttu-id="95e35-170">Cette fonction retourne un type d’enregistrement qui contient des enregistrements imbriqués.</span><span class="sxs-lookup"><span data-stu-id="95e35-170">This function returns a RECORD type that contains nested records.</span></span> <span data-ttu-id="95e35-171">Sélectionné un champ valeurs à partir de l’enregistrement retourné sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="95e35-171">Selected field values from the returned RECORD are written to the console.</span></span> <span data-ttu-id="95e35-172">Étapes à suivre pour définir les informations d’identification pour la base de données Oracle et ouvrez le client WCF sont omis dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="95e35-172">Steps to set credentials for the Oracle database and to open the WCF client are omitted from this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95e35-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95e35-173">See Also</span></span>  
 [<span data-ttu-id="95e35-174">Développer des applications de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="95e35-174">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)