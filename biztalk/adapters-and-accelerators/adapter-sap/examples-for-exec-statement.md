---
title: Exemples d’instruction EXEC dans l’adaptateur dans BizTalk mySAP | Documents Microsoft
description: Exemples EXEC et les exemples à l’aide de l’adaptateur mySAP dans le Pack de l’adaptateur BizTalk (LOB)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad2691f4-34bb-423c-9b3e-4abe2d55ddac
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6eaae930d7d94d24bac9d484957ccf02718af60f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="examples-for-exec-statement"></a><span data-ttu-id="cb91a-103">Exemples de l’instruction EXEC</span><span class="sxs-lookup"><span data-stu-id="cb91a-103">Examples for EXEC Statement</span></span>
<span data-ttu-id="cb91a-104">Cette rubrique montre un exemple de syntaxe pour les différentes instructions EXEC.</span><span class="sxs-lookup"><span data-stu-id="cb91a-104">This topic shows example syntax for various EXEC statements.</span></span>

## <a name="sample-statements"></a><span data-ttu-id="cb91a-105">Exemples d’instructions</span><span class="sxs-lookup"><span data-stu-id="cb91a-105">Sample statements</span></span> 
  
-   <span data-ttu-id="cb91a-106">Pour exécuter une commande BAPI qui ne prend aucun paramètre d’entrée, utilisez la syntaxe suivante : données retournées via un **DataReader** objet :</span><span class="sxs-lookup"><span data-stu-id="cb91a-106">To execute a BAPI that takes no input parameters, use the following syntax; data is returned through a **DataReader** object:</span></span>  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST  
    ```  
  
-   <span data-ttu-id="cb91a-107">Pour exécuter une commande RFC qui accepte des paramètres d’entrée, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cb91a-107">To execute an RFC that takes input parameters, use the following syntax:</span></span>  
  
    ```  
    EXEC RFC_CUSTOMER_GET @NAME1='Contoso'  
    ```  
  
-   <span data-ttu-id="cb91a-108">Pour exécuter une commande RFC qui accepte des paramètres d’entrée comme une variable, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cb91a-108">To execute an RFC that takes input parameters specified as a variable, use the following syntax:</span></span>  
  
    ```  
    EXEC RFC_CUSTOMER_GET @var=@var  
    ```  
  
     <span data-ttu-id="cb91a-109">Dans cet exemple, vous devez créer un paramètre nommé `@var` et définissez la valeur explicitement (par exemple, pour 1001), car le premier paramètre de RFC_CUSTOMER_GET correspond à KUNNR (numéro de client)</span><span class="sxs-lookup"><span data-stu-id="cb91a-109">In this example, you must create a parameter named `@var` and set the value explicitly (for example, to 1001), because the first parameter for RFC_CUSTOMER_GET corresponds to KUNNR (Customer Number)</span></span>  
  
-   <span data-ttu-id="cb91a-110">Pour exécuter une commande RFC qui utilise une variable pour le nom du paramètre d’entrée, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cb91a-110">To execute an RFC that uses a variable for the input parameter name, use the following syntax:</span></span>  
  
    ```  
    EXEC RFC_CUSTOMER_GET @KUNNR=@var1, @NAME1='Contoso'  
    ```  
  
     <span data-ttu-id="cb91a-111">Vous devez créer un paramètre nommé `@var1`, spécifiez la valeur, puis le lier à l’objet de commande correspondant.</span><span class="sxs-lookup"><span data-stu-id="cb91a-111">You must create a parameter named `@var1`, specify the value, and then bind it to the corresponding command object.</span></span> <span data-ttu-id="cb91a-112">La direction par défaut de l’objet de paramètre qui vient d’être créé est `input`.</span><span class="sxs-lookup"><span data-stu-id="cb91a-112">The default direction of the newly created parameter object is `input`.</span></span>  
  
-   <span data-ttu-id="cb91a-113">Pour exécuter une commande BAPI et les tables de retournés en tant que paramètre, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="cb91a-113">To execute a BAPI and return tables as a parameter, use the following syntax:</span></span>  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST @COMPANYCODE_LIST=@var1 OUTPUT  
    ```  
  
     <span data-ttu-id="cb91a-114">Vous devez créer un paramètre nommé `@var1`, spécifiez la valeur et la lier à l’objet de commande correspondant.</span><span class="sxs-lookup"><span data-stu-id="cb91a-114">You must create a parameter named `@var1`, specify the value, and bind it to the corresponding command object.</span></span> <span data-ttu-id="cb91a-115">La direction de l’objet de paramètre qui vient d’être créé doit être `InputOutput` ou `Output`.</span><span class="sxs-lookup"><span data-stu-id="cb91a-115">The direction of the newly created parameter object should be `InputOutput` or `Output`.</span></span>  
  
-   <span data-ttu-id="cb91a-116">L’exemple suivant EXEC utilise un paramètre de type complexe de table.</span><span class="sxs-lookup"><span data-stu-id="cb91a-116">The following EXEC example uses a table complex type parameter.</span></span> <span data-ttu-id="cb91a-117">Dans l’exemple, @fields est un paramètre TABLE.</span><span class="sxs-lookup"><span data-stu-id="cb91a-117">In the example, @fields is a TABLE parameter.</span></span>  
  
    ```  
    exec rfc_read_table @query_table='BNKA', @fields='<FIELDS xmlns='http://Microsoft.LobServices.Sap/2007/03/Rfc/'>  
                <RFC_DB_FLD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                  <FIELDNAME>BANKL</FIELDNAME>  
                </RFC_DB_FLD>  
                <RFC_DB_FLD  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                    <FIELDNAME>BANKS</FIELDNAME>  
                </RFC_DB_FLD>  
              </FIELDS>', @fields=@flds output  
    ```  
  
-   <span data-ttu-id="cb91a-118">L’exemple suivant EXEC utilise un type complexe de STRUCT.</span><span class="sxs-lookup"><span data-stu-id="cb91a-118">The following EXEC example uses a STRUCT complex type.</span></span> <span data-ttu-id="cb91a-119">Dans l’exemple, @equimaster est un paramètre STRUCT.</span><span class="sxs-lookup"><span data-stu-id="cb91a-119">In the example, @equimaster is a STRUCT parameter.</span></span>  
  
    ```  
    exec BAPI_EQMT_MODIFY @equipment='000000000000000637', @equimaster='<EQUIMASTER>           
                <EQUIPMENT xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">equip</EQUIPMENT>  
                <EQUICATGRY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">E</EQUICATGRY>  
                <MATERIAL xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">mat</MATERIAL>  
              </EQUIMASTER >', @equimaster=@em output  
    ```  
  
## <a name="support-for-complex-parameter-types"></a><span data-ttu-id="cb91a-120">Prise en charge des Types de paramètres complexes</span><span class="sxs-lookup"><span data-stu-id="cb91a-120">Support for Complex Parameter Types</span></span>  
 <span data-ttu-id="cb91a-121">Il existe deux façons pour prendre en charge des paramètres complexes RFC (tables et des structures) lorsque vous utilisez le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="cb91a-121">There are two ways to support complex RFC parameters (tables and structures) when you use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:</span></span>  
  
-   <span data-ttu-id="cb91a-122">Indiquez la valeur XML inline pour le type complexe.</span><span class="sxs-lookup"><span data-stu-id="cb91a-122">Provide an inline XML value for the complex type.</span></span> <span data-ttu-id="cb91a-123">Cet exemple montre comment passer de XML pour le type de paramètre complexe *champs*.</span><span class="sxs-lookup"><span data-stu-id="cb91a-123">This example shows how to pass XML to the complex parameter type *fields*.</span></span> <span data-ttu-id="cb91a-124">Dans l’exemple suivant, *@fields* est un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="cb91a-124">In the following example, *@fields* is a table parameter.</span></span>  
  
    ```  
    exec rfc_read_table @query_table='BNKA', @fields='<FIELDS xmlns='http://Microsoft.LobServices.Sap/2007/03/Rfc/'>  
                <RFC_DB_FLD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                  <FIELDNAME>BANKL</FIELDNAME>  
                </RFC_DB_FLD>  
                <RFC_DB_FLD  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                    <FIELDNAME>BANKS</FIELDNAME>  
                </RFC_DB_FLD>  
              </FIELDS>', @fields=@flds output  
    ```  
  
-   <span data-ttu-id="cb91a-125">Créer un **DataTable** paramètre avec des colonnes pour les champs dans le type complexe et le jeu de valeur pour le paramètre SAP **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="cb91a-125">Create a **DataTable** parameter with columns for the fields in the complex type and set the SAP parameter value to **DataTable**.</span></span> <span data-ttu-id="cb91a-126">Cet exemple montre comment définir la @fields type complexe en utilisant un **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="cb91a-126">This example shows how to set the @fields complex type by using a **DataTable**.</span></span>  
  
    ```  
    cmd.CommandText = "exec rfc_read_table @query_table='BNKA', @fields = @p_fields";  
    DataTable dt = new DataTable();  
    dt.Columns.Add("FIELDNAME");  
    SAPParameter p = new SAPParameter("@p_fields");  
    p.Value = dt;  
    ```  
  
## <a name="limitations"></a><span data-ttu-id="cb91a-127">Limitations</span><span class="sxs-lookup"><span data-stu-id="cb91a-127">Limitations</span></span>  
 <span data-ttu-id="cb91a-128">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] présente les limitations suivantes pour les types complexes.</span><span class="sxs-lookup"><span data-stu-id="cb91a-128">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] has the following limitations for complex types.</span></span>  
  
-   <span data-ttu-id="cb91a-129">Lorsque vous passez un type complexe dans un paramètre en utilisant un **DataTable**, vous devez inclure tous les champs (colonnes) du type complexe dans le **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="cb91a-129">When you pass a complex type in a parameter by using a **DataTable**, you must include all fields (columns) of the complex type in the **DataTable**.</span></span>  
  
-   <span data-ttu-id="cb91a-130">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] ne prend pas en charge **DbNull**.</span><span class="sxs-lookup"><span data-stu-id="cb91a-130">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] does not support **DbNull**.</span></span> <span data-ttu-id="cb91a-131">Vous ne pouvez pas définir **DbNull** en tant que valeur pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb91a-131">You cannot set **DbNull** as a value for parameters.</span></span>  
  
