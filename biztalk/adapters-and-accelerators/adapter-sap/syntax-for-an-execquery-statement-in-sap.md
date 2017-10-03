---
title: Syntaxe pour une instruction EXECQUERY dans SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bd7fbb-64f2-4327-a8ae-ccb574e56150
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f1eb41d07ef6a6ac3577bf0ef6d3f5bffb874f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="syntax-for-an-execquery-statement-in-sap"></a><span data-ttu-id="0e6e8-102">Syntaxe pour une instruction EXECQUERY dans SAP</span><span class="sxs-lookup"><span data-stu-id="0e6e8-102">Syntax for an EXECQUERY Statement in SAP</span></span>
<span data-ttu-id="0e6e8-103">Vous pouvez utiliser l’interface utilisateur graphique SAP pour créer des requêtes en sélectionnant graphiquement les tables que vous souhaitez interroger, les colonnes et l’ordre que vous souhaitez inclure dans le jeu de résultats, etc. de tri. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] permet aux utilisateurs d’exécuter ces requêtes à partir d’une application ADO.NET en fournissant une opération EXECQUERY qui permettent aux utilisateurs d’exécuter une requête définie dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-103">You can use the SAP GUI to create queries by graphically selecting the tables you want to query, the columns and sort order you want included in the result set, etc. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] enables users to execute such queries from an ADO.NET application by providing an EXECQUERY operation that users can use to execute a query defined in the SAP system.</span></span>  
  
 <span data-ttu-id="0e6e8-104">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise un Z_EXECUTE_SAP_QUERY RFC personnalisés pour exécuter les requêtes prédéfinies dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC Z_EXECUTE_SAP_QUERY to execute the pre-defined queries in the SAP system.</span></span> <span data-ttu-id="0e6e8-105">Le document RFC personnalisé exécute à son tour le RSAQ_REMOTE_QUERY_CALL, qui est une norme que RFC définie dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-105">The custom RFC in turn executes the RSAQ_REMOTE_QUERY_CALL, which is a standard RFC defined in the SAP system.</span></span> <span data-ttu-id="0e6e8-106">Par conséquent, avant de pouvoir utiliser l’opération EXECQUERY, vous devez installer le RFC personnalisé dans le système SAP que vous allez exécuter vos requêtes sur.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-106">Hence, before you can use the EXECQUERY operation, you must install the custom RFC in the SAP system you will be running your queries against.</span></span> <span data-ttu-id="0e6e8-107">Pour obtenir des instructions sur la façon d’installer le RFC personnalisé, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="0e6e8-107">For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>  
  
 <span data-ttu-id="0e6e8-108">Cette rubrique fournit des informations sur la syntaxe de l’opération EXECQUERY et d’autres informations utiles relatives à l’opération EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-108">This topic provides information on the syntax of the EXECQUERY operation, and other useful information related to the EXECQUERY operation.</span></span>  
  
## <a name="syntax-for-an-execquery-statement"></a><span data-ttu-id="0e6e8-109">Syntaxe pour une instruction EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="0e6e8-109">Syntax for an EXECQUERY Statement</span></span>  
 <span data-ttu-id="0e6e8-110">La section suivante décrit les spécifications de grammaire pour l’utilisation de l’opération EXECQUERY contre le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e6e8-110">The following section describes the grammar specifications for using the EXECQUERY operation against the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='\<value 1>’] [, @P2='\<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='\<value 3>'] [, @P1 > '\<value 4>'] [, @P1 <= '\<value 2>']   
[, NOT @P1 = '\<value 2>'] [, NOT @P1 != '\<value 2>'] [, NOT @P1 > '\<value 2>']   
[, @P1 BETWEEN '\<value 1>' AND '\<value 2>'] [, NOT @P1 BETWEEN '\<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 <span data-ttu-id="0e6e8-111">où :</span><span class="sxs-lookup"><span data-stu-id="0e6e8-111">where:</span></span>  
  
-   <span data-ttu-id="0e6e8-112">**\<Nom_requête >** est le nom de la requête définie dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-112">**\<QueryName>** is the name of the query defined in the SAP system.</span></span>  
  
-   <span data-ttu-id="0e6e8-113">**Groupe d’utilisateurs** fait référence au groupe d’utilisateurs dans lequel la requête est définie.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-113">**USERGROUP** refers to the user group in which the query is defined.</span></span> <span data-ttu-id="0e6e8-114">Il s'agit d'un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-114">This is a mandatory parameter.</span></span>  
  
-   <span data-ttu-id="0e6e8-115">**Espace de travail** fait référence à l’espace de travail dans lequel la requête est définie.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-115">**WORKSPACE** refers to the workspace in which the query is defined.</span></span> <span data-ttu-id="0e6e8-116">Dans SAP, il existe deux espaces de travail, Standard et Global.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-116">In SAP, there are two workspaces—Standard and Global.</span></span> <span data-ttu-id="0e6e8-117">Fournir un espace vide pour spécifier l’espace de travail Standard.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-117">Provide an empty space to specify the Standard workspace.</span></span> <span data-ttu-id="0e6e8-118">Fournir `X` pour spécifier l’espace de travail Global.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-118">Provide `X` to specify the Global workspace.</span></span> <span data-ttu-id="0e6e8-119">Valeur par défaut est un espace vide.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-119">Default is empty space.</span></span>  
  
-   <span data-ttu-id="0e6e8-120">**VARIANT** fait référence à un jeu de critères de sélection que vous pouvez spécifier lors de l’exécution d’une requête SAP enregistré.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-120">**VARIANT** refers to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="0e6e8-121">Par exemple, vous pouvez utiliser les variantes pour spécifier les valeurs par défaut pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-121">For example, you can use variants to specify default values for queries.</span></span>  
  
-   <span data-ttu-id="0e6e8-122">**@Pn**fait référence à n<sup>th</sup> champ de sélection dans la définition de requête SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-122">**@Pn** refers to the n<sup>th</sup> selection field in the SAP query definition.</span></span>  
  
-   <span data-ttu-id="0e6e8-123">**USEORIGINALCOLUMNNAMES** Spécifie si le fournisseur utilise les noms de colonne d’origine dans le jeu de données, tels qu’ils existent dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-123">**USEORIGINALCOLUMNNAMES** specifies whether the provider uses the original column names in the DataSet, as they exist in the SAP system.</span></span> <span data-ttu-id="0e6e8-124">Par défaut, le fournisseur utilise les noms conviviaux définis dans la requête SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-124">By default, the provider uses the friendly names defined in the SAP query.</span></span> <span data-ttu-id="0e6e8-125">Toutefois, si les noms conviviaux dans la requête ne sont pas uniques, le client ADO.NET génère une erreur lors de la lecture des données à partir du DataSet.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-125">However, if the friendly names within the query are not unique, the ADO.NET client will throw an error while reading the data from the DataSet.</span></span> <span data-ttu-id="0e6e8-126">Dans de tels scénarios, vous devez spécifier l’option USEORIGINALCOLUMNNAMES, en indiquant que le fournisseur utilise les noms de colonne d’origine dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-126">In such scenarios, you must specify the USEORIGINALCOLUMNNAMES option, indicating that the provider uses the original column names in the DataSet.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0e6e8-127">Vous devez toujours fournir la valeur du mot clé d’OPTION entre guillemets simples, par exemple, «*USEORIGINALCOLUMNNAMES*'.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-127">You must always provide the value for the OPTION keyword within single quotes, for example, '*USEORIGINALCOLUMNNAMES*'.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e6e8-128">Pour plus d’informations sur la façon dont les paramètres d’une requête SAP se traduire par une syntaxe EXECQUERY, consultez [paramètres de requête de traduire la SAP dans la commande EXECQUERY](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span><span class="sxs-lookup"><span data-stu-id="0e6e8-128">For information about how the parameters of an SAP Query translate into an EXECQUERY syntax, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span></span>  
  
### <a name="framing-an-execquery-syntax"></a><span data-ttu-id="0e6e8-129">Une syntaxe EXECQUERY de tramage</span><span class="sxs-lookup"><span data-stu-id="0e6e8-129">Framing an EXECQUERY Syntax</span></span>  
 <span data-ttu-id="0e6e8-130">Tramage de syntaxe pour une opération EXECQUERY exécuter une requête SAP dépend de la façon dont la requête est définie dans le système SAP, y compris chaque valeur du paramètre défini dans SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-130">Framing syntax for an EXECQUERY operation to execute an SAP query depends on how the query is defined in the SAP system, including each parameter value defined in SAP.</span></span> <span data-ttu-id="0e6e8-131">Pour plus d’informations sur la manière de limiter la syntaxe EXECQUERY pour exécuter une requête SAP, consultez [paramètres de requête de traduire la SAP dans la commande EXECQUERY](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span><span class="sxs-lookup"><span data-stu-id="0e6e8-131">For information about how to frame EXECQUERY syntax to execute an SAP query, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).</span></span>  
  
### <a name="additional-considerations-while-using-the-execquery-operation"></a><span data-ttu-id="0e6e8-132">Supplémentaires Considérations lors à l’aide de l’opération EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="0e6e8-132">Additional Considerations While Using the EXECQUERY operation</span></span>  
 <span data-ttu-id="0e6e8-133">Cette section répertorie les points que vous devez garder à l’esprit lorsque vous utilisez l’instruction EXECQUERY avec [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e6e8-133">This section lists the points that you must keep in mind when using the EXECQUERY statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="0e6e8-134">Les valeurs spécifiées pour le groupe d’utilisateurs, espace de travail et de type VARIANT sont transmises comme-consiste à la norme RFC SAP, RSAQ_REMOTE_QUERY_CALL.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-134">The values specified for USERGROUP, WORKSPACE, and VARIANT are passed on as-is to the standard SAP RFC, RSAQ_REMOTE_QUERY_CALL.</span></span> <span data-ttu-id="0e6e8-135">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne valide pas les valeurs spécifiées pour ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-135">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values specified for these parameters.</span></span>  
  
-   <span data-ttu-id="0e6e8-136">Les valeurs retournées par l’opération EXECQUERY sont de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-136">All values returned by the EXECQUERY operation are of string type.</span></span>  
  
-   <span data-ttu-id="0e6e8-137">Mots clés pour les noms de requêtes, groupe d’utilisateurs, espace de travail et les variantes ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-137">Keywords for query names, user group, workspace, and variants are not case sensitive.</span></span> <span data-ttu-id="0e6e8-138">Toutefois, les noms de paramètre doivent toujours être dans caseP supérieur comme @P1, @P2, etc.. Exemple :</span><span class="sxs-lookup"><span data-stu-id="0e6e8-138">However, the parameter names must always be in upper caseP such as @P1, @P2, etc. For example:</span></span>  
  
    ```  
    EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
     <span data-ttu-id="0e6e8-139">est identique à</span><span class="sxs-lookup"><span data-stu-id="0e6e8-139">is the same as</span></span>  
  
    ```  
    EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
-   <span data-ttu-id="0e6e8-140">Les opérateurs pris en charge par le EXECQUERY sont >, \<, > =, < =, ! =, NOT et BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-140">The operators supported by the EXECQUERY are >, \<, >=, <=, !=, NOT, and BETWEEN.</span></span>  
  
-   <span data-ttu-id="0e6e8-141">Les caractères génériques ne sont pas pris en charge par l’opération EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-141">Wildcard characters are not supported by the EXECQUERY operation.</span></span> <span data-ttu-id="0e6e8-142">Par exemple, l’instruction suivante donne le résultat attendu :</span><span class="sxs-lookup"><span data-stu-id="0e6e8-142">For example, the following statement gives the expected output:</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
     <span data-ttu-id="0e6e8-143">Toutefois, la même requête lors de l’exécution avec un caractère générique génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-143">However, the same query when executed with a wildcard character gives an error.</span></span> <span data-ttu-id="0e6e8-144">Notez l’utilisation de caractères génériques pour  **@P2** .</span><span class="sxs-lookup"><span data-stu-id="0e6e8-144">Notice the use of wildcard characters for **@P2**.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
    ```  
  
     <span data-ttu-id="0e6e8-145">Dans cet exemple, vous pouvez obtenir une erreur indiquant qu’aucune donnée n’a été trouvée.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-145">In this example, you might get an error stating that no data was found.</span></span> <span data-ttu-id="0e6e8-146">C’est parce que la requête recherche **'\*&\*'** sous forme de chaîne et ne tient pas compte de l’astérisque (*) comme caractère générique.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-146">This is because the query searches for **'\*&\*'** as a string and does not consider asterisk (*) as a wildcard character.</span></span>  
  
-   <span data-ttu-id="0e6e8-147">Vous devez toujours spécifier une valeur de date au format AAAAMMJJ.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-147">You must always specify a date values in YYYYMMDD format.</span></span>  
  
-   <span data-ttu-id="0e6e8-148">Si vous exécutez une requête qui est une variante définie dans le système SAP, vous pouvez spécifier le nom de la variante en tant que partie de la commande.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-148">If you are executing a query that has a variant defined in the SAP system, you can specify the name of the variant as part of the command.</span></span> <span data-ttu-id="0e6e8-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0e6e8-149">For example:</span></span>  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0e6e8-150">Vous n’avez pas besoin de spécifier un nom de type variant si une variante de la valeur par défaut est définie pour la requête dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="0e6e8-150">You do not need to specify a variant name if a default variant is defined for the query in the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e6e8-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e6e8-151">See Also</span></span>  
 [<span data-ttu-id="0e6e8-152">Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="0e6e8-152">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)