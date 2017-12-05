---
title: Syntaxe pour une instruction EXEC dans SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: EXEC statement, syntax for
ms.assetid: 406b1100-39a0-4321-89c9-ec1b8a3cfdc6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 362aa1f81158c9d9f1135c9bff25c64d7d745953
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-an-exec-statement-in-sap"></a><span data-ttu-id="6a5e8-102">Syntaxe pour une instruction EXEC dans SAP</span><span class="sxs-lookup"><span data-stu-id="6a5e8-102">Syntax for an EXEC Statement in SAP</span></span>
<span data-ttu-id="6a5e8-103">La section suivante décrit les spécifications de grammaire pour l’implémentation des instructions EXEC contre le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a5e8-103">The following section describes grammar specifications for implementing EXEC statements against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span> <span data-ttu-id="6a5e8-104">Notez que, dans certains cas, la syntaxe est différente de la syntaxe Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-104">Notice that in several cases, the syntax is somewhat different from Transact-SQL syntax.</span></span>  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 <span data-ttu-id="6a5e8-105">où :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-105">where:</span></span>  
  
-   <span data-ttu-id="6a5e8-106">**rfc_name** Spécifie le nom de l’appel de fonction à exécuter.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-106">**rfc_name** specifies the name of the function call to execute.</span></span>  
  
-   <span data-ttu-id="6a5e8-107">**< argument_element >** :: = @param_name = [0,1] \<const\> {[entrée &#124; SORTIE]} [0,1]</span><span class="sxs-lookup"><span data-stu-id="6a5e8-107">**<argument_element>** ::= @param_name = [0,1] \<const\> {[ INPUT &#124; OUTPUT ]}[0,1]</span></span>  
  
    -   <span data-ttu-id="6a5e8-108">**param_Name** Spécifie le nom du paramètre défini dans l’interface de la fonction.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-108">**param_name** specifies the parameter name defined in the function interface.</span></span>  
  
    -   <span data-ttu-id="6a5e8-109">**\<const\>**  :: = entier &#124; réel &#124; chaîne &#124; ?</span><span class="sxs-lookup"><span data-stu-id="6a5e8-109">**\<const\>** ::= integer &#124; real &#124; string &#124; ?</span></span> <span data-ttu-id="6a5e8-110">&#124; NULL &#124; xml_element</span><span class="sxs-lookup"><span data-stu-id="6a5e8-110">&#124; NULL &#124; xml_element</span></span>  
  
-   <span data-ttu-id="6a5e8-111">**OPTION** fournit l’option sur la façon dont vous souhaitez présenter les données.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-111">**OPTION**  provides option on how you want to present the data.</span></span> <span data-ttu-id="6a5e8-112">Options disponibles :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-112">The available options are:</span></span>  
  
    -   <span data-ttu-id="6a5e8-113">**disabledatavalidation** option définit la **EnableSafeTyping** liaison de propriété sous-jacent [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a5e8-113">**disabledatavalidation** option sets the **EnableSafeTyping** binding property in the underlying [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="6a5e8-114">Lors de la saisie sécurisée est activé, les types de données des fichiers DAT, Tim et NUMC sont représentées sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-114">When safe typing is enabled the DATS, TIMS, and NUMC data types are represented as strings.</span></span> <span data-ttu-id="6a5e8-115">Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6a5e8-115">For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    -   <span data-ttu-id="6a5e8-116">**firstresultset** Spécifie le premier jeu de résultats retourné par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a5e8-116">**firstresultset** specifies the first result set that is returned by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="6a5e8-117">Lorsqu’une instruction est exécutée sur une source de fournisseur ADO, uniquement le premier jeu de résultats retourné est disponible.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-117">When any statement is executed on an ADO Provider source, only the first result set returned is available.</span></span> <span data-ttu-id="6a5e8-118">Pour les scénarios de RFC EXEC, généralement plusieurs paramètres de la table est retournée, mais si le premier jeu de résultats n’est disponibles pour le programme client qui ne peut pas être d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-118">For RFC EXEC scenarios, usually multiple table parameters are returned but if only the first result set is available for the client program, which might not be of use.</span></span> <span data-ttu-id="6a5e8-119">En spécifiant le mot clé « firstresultset » dans le cadre de la clause OPTION, les clients peuvent désigner le premier paramètre de table qu’ils souhaitent le fournisseur à retourner.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-119">By specifying the “firstresultset” keyword as part of the OPTION clause, clients can specify the first table parameter that they want the Provider to return.</span></span> <span data-ttu-id="6a5e8-120">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-120">For example:</span></span>  
  
        ```  
        EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
        ```  
  
         <span data-ttu-id="6a5e8-121">Dans cet exemple, l’instruction EXEC Spécifie que le premier paramètre de tableau retourné doit être TAB_ALLTYPES.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-121">In this example, the EXEC statement specifies that the first table parameter returned should be TAB_ALLTYPES.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6a5e8-122">Vous devez toujours fournir les valeurs pour le mot clé d’OPTION entre guillemets simples, par exemple, «*disabledatavalidation*'.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-122">You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.</span></span>  
  
 <span data-ttu-id="6a5e8-123">Dans la syntaxe précédente, xml_element peut être utilisé pour fournir une entrée pour les types complexes.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-123">In the preceding syntax, xml_element can be used to provide input for complex types.</span></span> <span data-ttu-id="6a5e8-124">La structure de l’élément xml sera différente pour les tables et les structures.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-124">The xml element structure will be different for structures and tables.</span></span> <span data-ttu-id="6a5e8-125">Le xml_element pour structure ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-125">The xml_element for structure resembles the following:</span></span>  
  
```  
<PARAM_NAME>  
    <FIELDNAME_1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_1>  
    <FIELDNAME_2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_2>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 <span data-ttu-id="6a5e8-126">Le xml_element pour la table ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-126">The xml_element for table resembles the following:</span></span>  
  
```  
<PARAM_NAME>  
    <STRUCT_NAME  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
        <FIELDNAME_1>value</FIELDNAME_1>  
    <STRUCT_NAME/>  
    <STRUCT_NAME  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
        <FIELDNAME_1>value</FIELDNAME_1>  
    <STRUCT_NAME/>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 <span data-ttu-id="6a5e8-127">Par exemple, l’élément XML pour un type de structure ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-127">For example, the XML element for a structure type resembles the following:</span></span>  
  
```  
<INOUT_STRUCT>  
       <ACCPFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006</ACCPFIELD>  
       <CHARFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">John</CHARFIELD>                 
</INOUT_STRUCT>  
```  
  
 <span data-ttu-id="6a5e8-128">De même, l’élément XML pour un type de table ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-128">Similarly, the XML element for a table type resembles the following:</span></span>  
  
```  
<TAB_ALLTYPES>   
<ZZSTRUCTALLTYPES_RFC xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
       <ACCPFIELD>2006</ACCPFIELD>  
       <CHARFIELD>John</CHARFIELD>                          
</ZZSTRUCTALLTYPES_RFC>  
<ZZSTRUCTALLTYPES_RFC xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
       <ACCPFIELD>2007</ACCPFIELD>  
       <CHARFIELD>James</CHARFIELD>                          
</ZZSTRUCTALLTYPES_RFC>  
</TAB_ALLTYPES>  
```  
  
 <span data-ttu-id="6a5e8-129">Par exemple des instructions, consultez [exemples pour l’instruction EXEC](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6a5e8-129">For example statements, see [Examples for EXEC Statement](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).</span></span>  
  
## <a name="handling-named-parameters"></a><span data-ttu-id="6a5e8-130">Gestion des paramètres nommées</span><span class="sxs-lookup"><span data-stu-id="6a5e8-130">Handling Named Parameters</span></span>  
 <span data-ttu-id="6a5e8-131">Les éléments suivants sont des recommandations pour la spécification des paramètres nommés dans les requêtes EXEC :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-131">The following are guidelines for specifying named parameters in EXEC queries:</span></span>  
  
-   <span data-ttu-id="6a5e8-132">Vous devez spécifier des paramètres en les nommant (par exemple, @param_name= value).</span><span class="sxs-lookup"><span data-stu-id="6a5e8-132">You must specify parameters by naming them (for example, @param_name=value).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a5e8-133">Les paramètres sans nom ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-133">Unnamed parameters are not supported</span></span>  
  
-   <span data-ttu-id="6a5e8-134">Lorsqu’un paramètre est défini à l’aide de la valeur par défaut, vous pouvez exécuter la procédure sans spécifier de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-134">When a parameter is defined using a default value, you can execute the procedure without specifying a parameter.</span></span>  
  
-   <span data-ttu-id="6a5e8-135">Les requêtes EXEC ne prennent pas en charge à l’aide des paramètres avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-135">EXEC queries do not support using parameters with the following properties:</span></span>  
  
    -   <span data-ttu-id="6a5e8-136">Structures imbriquées (structures qui contiennent des structures en tant que leurs champs).</span><span class="sxs-lookup"><span data-stu-id="6a5e8-136">Nested structures (structures that contain structures as their fields).</span></span>  
  
    -   <span data-ttu-id="6a5e8-137">Tables imbriquées.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-137">Nested tables.</span></span>  
  
    -   <span data-ttu-id="6a5e8-138">Une table contenant une structure.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-138">A table containing a structure.</span></span>  
  
    -   <span data-ttu-id="6a5e8-139">Une structure contenant une table.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-139">A structure containing a table.</span></span>  
  
    -   <span data-ttu-id="6a5e8-140">Une structure ou une table qui comporte des champs avec des types de chaîne composite, par exemple `SSTRING` ou `RAWSTRING`.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-140">A structure or table that has fields with composite string types, for example `SSTRING` or `RAWSTRING`.</span></span>  
  
     <span data-ttu-id="6a5e8-141">Le tableau suivant répertorie les mappages logiques entre les types de paramètre RFC et les directions de paramètre lors de l’exécution d’une demande de changement.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-141">The following table lists logical mappings between RFC parameter types and parameter directions when executing an RFC.</span></span>  
  
    |<span data-ttu-id="6a5e8-142">Type de Param RFC</span><span class="sxs-lookup"><span data-stu-id="6a5e8-142">RFC Param Type</span></span>|<span data-ttu-id="6a5e8-143">Mot clé de requête</span><span class="sxs-lookup"><span data-stu-id="6a5e8-143">Query Keyword</span></span>|<span data-ttu-id="6a5e8-144">Direction du paramètre</span><span class="sxs-lookup"><span data-stu-id="6a5e8-144">Parameter Direction</span></span>|  
    |--------------------|-------------------|-------------------------|  
    |<span data-ttu-id="6a5e8-145">Paramètres d’importation</span><span class="sxs-lookup"><span data-stu-id="6a5e8-145">Import parameters</span></span>|<span data-ttu-id="6a5e8-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="6a5e8-146">Nothing</span></span>|<span data-ttu-id="6a5e8-147">Paramdirection.Input</span><span class="sxs-lookup"><span data-stu-id="6a5e8-147">Paramdirection.Input</span></span>|  
    |<span data-ttu-id="6a5e8-148">Paramètres d’exportation</span><span class="sxs-lookup"><span data-stu-id="6a5e8-148">Export parameters</span></span>|<span data-ttu-id="6a5e8-149">Sortie</span><span class="sxs-lookup"><span data-stu-id="6a5e8-149">Output</span></span>|<span data-ttu-id="6a5e8-150">Paramdirection.Output</span><span class="sxs-lookup"><span data-stu-id="6a5e8-150">Paramdirection.Output</span></span>|  
    |<span data-ttu-id="6a5e8-151">Paramètres table</span><span class="sxs-lookup"><span data-stu-id="6a5e8-151">Table parameters</span></span>|<span data-ttu-id="6a5e8-152">Sortie/Nothing</span><span class="sxs-lookup"><span data-stu-id="6a5e8-152">Output/Nothing</span></span>|<span data-ttu-id="6a5e8-153">InputOutput</span><span class="sxs-lookup"><span data-stu-id="6a5e8-153">InputOutput</span></span>|  
  
 <span data-ttu-id="6a5e8-154">Voici les recommandations générales pour la gestion des paramètres :</span><span class="sxs-lookup"><span data-stu-id="6a5e8-154">The following are general guidelines for handling parameters:</span></span>  
  
-   <span data-ttu-id="6a5e8-155">Vous pouvez spécifier des valeurs de paramètre en tant que constantes ou à l’aide des espaces réservés dans la requête.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-155">You can specify parameter values either as constants or by using placeholders in the query.</span></span>  
  
-   <span data-ttu-id="6a5e8-156">Lorsque vous utilisez des espaces réservés dans la requête, vous devez créer un `SAPParameter` de l’objet et l’ajouter à l’objet de commande correspondant.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-156">When using placeholders in the query, you must create a `SAPParameter` object and add it to the corresponding command object.</span></span> <span data-ttu-id="6a5e8-157">Vous passez ensuite le nom de l’espace réservé au constructeur ; la direction et la valeur dépendant du contexte.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-157">You then pass the placeholder name to the constructor; the direction and value depend on the context.</span></span>  
  
    -   <span data-ttu-id="6a5e8-158">Pour `Input` paramètres, ne spécifiez pas dans la requête un mot clé pour la direction du paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-158">For `Input` parameters, do not specify in the query a keyword for the parameter direction.</span></span> <span data-ttu-id="6a5e8-159">Le `value` champ de l’objet de paramètre doit être définie, ou le fournisseur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-159">The `value` field of the parameter object must be set, or the provider will throw an exception.</span></span> <span data-ttu-id="6a5e8-160">Vous ne devez pas définir explicitement le `direction` champ de l’objet de paramètre, car le fournisseur par défaut est `Input`.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-160">You must not explicitly set the `direction` field of the parameter object, because the provider defaults to `Input`.</span></span>  
  
    -   <span data-ttu-id="6a5e8-161">Pour les autres paramètres, utilisez la forme `@paramname=@placeholder` et spécifiez le `Output` mot clé explicitement dans la requête.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-161">For other parameters, use the form `@paramname=@placeholder` and specify the `Output` keyword explicitly in the query.</span></span> <span data-ttu-id="6a5e8-162">Vous devez ensuite ajouter un `SAPParameter` qui correspond à l’espace réservé et que vous définissez explicitement la direction du paramètre soit `ParamDirection.Output` ou `ParamDirection.InputOutput`, selon le type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-162">You must then add a `SAPParameter` that corresponds with the placeholder and explicitly set the parameter direction to either `ParamDirection.Output` or `ParamDirection.InputOutput`, depending on the parameter type.</span></span>  
  
-   <span data-ttu-id="6a5e8-163">Noms de paramètre et les noms des espaces réservés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-163">Parameter names and placeholder names are not case-sensitive.</span></span>  
  
-   <span data-ttu-id="6a5e8-164">Les noms de paramètres ne peuvent pas être répétés dans une requête, sauf si elles ont différentes directions.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-164">Parameter names cannot be repeated in a query unless they have different directions.</span></span>  
  
-   <span data-ttu-id="6a5e8-165">Noms d’espace réservé ne peut pas être répétés dans une requête.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-165">Placeholder names cannot be repeated in a query.</span></span>  
  
## <a name="considerations-when-calling-an-exec-statement"></a><span data-ttu-id="6a5e8-166">Considérations lors de l’appel d’une instruction EXEC</span><span class="sxs-lookup"><span data-stu-id="6a5e8-166">Considerations When Calling an EXEC Statement</span></span>  
 <span data-ttu-id="6a5e8-167">Cette section répertorie les points que vous devez garder à l’esprit lorsque vous utilisez l’instruction EXEC avec [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a5e8-167">This section lists the points that you must keep in mind when using the EXEC statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="6a5e8-168">Pour une instruction EXEC, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne `TIMS` valeurs de champ en tant que .NET `System.DateTime` objets.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-168">For an EXEC statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.DateTime` objects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a5e8-169">Pour une instruction SELECT, la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne `TIMS` valeurs de champ en tant que .NET `System.TimeSpan` objets.</span><span class="sxs-lookup"><span data-stu-id="6a5e8-169">For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.TimeSpan` objects.</span></span> <span data-ttu-id="6a5e8-170">Pour plus d’informations sur l’instruction SELECT, consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="6a5e8-170">For more information about the SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5e8-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a5e8-171">See Also</span></span>  
 [<span data-ttu-id="6a5e8-172">À propos du fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="6a5e8-172">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)