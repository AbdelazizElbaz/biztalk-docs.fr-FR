---
title: Syntaxe pour une instruction EXEC dans SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EXEC statement, syntax for
ms.assetid: 406b1100-39a0-4321-89c9-ec1b8a3cfdc6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 362aa1f81158c9d9f1135c9bff25c64d7d745953
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-an-exec-statement-in-sap"></a>Syntaxe pour une instruction EXEC dans SAP
La section suivante décrit les spécifications de grammaire pour l’implémentation des instructions EXEC contre le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]. Notez que, dans certains cas, la syntaxe est différente de la syntaxe Transact-SQL.  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 où :  
  
-   **rfc_name** Spécifie le nom de l’appel de fonction à exécuter.  
  
-   **< argument_element >** :: = @param_name = [0,1] \<const\> {[entrée &#124; SORTIE]} [0,1]  
  
    -   **param_Name** Spécifie le nom du paramètre défini dans l’interface de la fonction.  
  
    -   **\<const\>**  :: = entier &#124; réel &#124; chaîne &#124; ? &#124; NULL &#124; xml_element  
  
-   **OPTION** fournit l’option sur la façon dont vous souhaitez présenter les données. Options disponibles :  
  
    -   **disabledatavalidation** option définit la **EnableSafeTyping** liaison de propriété sous-jacent [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Lors de la saisie sécurisée est activé, les types de données des fichiers DAT, Tim et NUMC sont représentées sous forme de chaînes. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    -   **firstresultset** Spécifie le premier jeu de résultats retourné par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. Lorsqu’une instruction est exécutée sur une source de fournisseur ADO, uniquement le premier jeu de résultats retourné est disponible. Pour les scénarios de RFC EXEC, généralement plusieurs paramètres de la table est retournée, mais si le premier jeu de résultats n’est disponibles pour le programme client qui ne peut pas être d’utilisation. En spécifiant le mot clé « firstresultset » dans le cadre de la clause OPTION, les clients peuvent désigner le premier paramètre de table qu’ils souhaitent le fournisseur à retourner. Exemple :  
  
        ```  
        EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
        ```  
  
         Dans cet exemple, l’instruction EXEC Spécifie que le premier paramètre de tableau retourné doit être TAB_ALLTYPES.  
  
    > [!IMPORTANT]
    >  Vous devez toujours fournir les valeurs pour le mot clé d’OPTION entre guillemets simples, par exemple, «*disabledatavalidation*'.  
  
 Dans la syntaxe précédente, xml_element peut être utilisé pour fournir une entrée pour les types complexes. La structure de l’élément xml sera différente pour les tables et les structures. Le xml_element pour structure ressemble à ceci :  
  
```  
<PARAM_NAME>  
    <FIELDNAME_1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_1>  
    <FIELDNAME_2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_2>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 Le xml_element pour la table ressemble à ceci :  
  
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
  
 Par exemple, l’élément XML pour un type de structure ressemble à ceci :  
  
```  
<INOUT_STRUCT>  
       <ACCPFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006</ACCPFIELD>  
       <CHARFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">John</CHARFIELD>                 
</INOUT_STRUCT>  
```  
  
 De même, l’élément XML pour un type de table ressemble à ceci :  
  
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
  
 Par exemple des instructions, consultez [exemples pour l’instruction EXEC](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).  
  
## <a name="handling-named-parameters"></a>Gestion des paramètres nommées  
 Les éléments suivants sont des recommandations pour la spécification des paramètres nommés dans les requêtes EXEC :  
  
-   Vous devez spécifier des paramètres en les nommant (par exemple, @param_name= value).  
  
    > [!NOTE]
    >  Les paramètres sans nom ne sont pas pris en charge.  
  
-   Lorsqu’un paramètre est défini à l’aide de la valeur par défaut, vous pouvez exécuter la procédure sans spécifier de paramètre.  
  
-   Les requêtes EXEC ne prennent pas en charge à l’aide des paramètres avec les propriétés suivantes :  
  
    -   Structures imbriquées (structures qui contiennent des structures en tant que leurs champs).  
  
    -   Tables imbriquées.  
  
    -   Une table contenant une structure.  
  
    -   Une structure contenant une table.  
  
    -   Une structure ou une table qui comporte des champs avec des types de chaîne composite, par exemple `SSTRING` ou `RAWSTRING`.  
  
     Le tableau suivant répertorie les mappages logiques entre les types de paramètre RFC et les directions de paramètre lors de l’exécution d’une demande de changement.  
  
    |Type de Param RFC|Mot clé de requête|Direction du paramètre|  
    |--------------------|-------------------|-------------------------|  
    |Paramètres d’importation|Nothing|Paramdirection.Input|  
    |Paramètres d’exportation|Sortie|Paramdirection.Output|  
    |Paramètres table|Sortie/Nothing|InputOutput|  
  
 Voici les recommandations générales pour la gestion des paramètres :  
  
-   Vous pouvez spécifier des valeurs de paramètre en tant que constantes ou à l’aide des espaces réservés dans la requête.  
  
-   Lorsque vous utilisez des espaces réservés dans la requête, vous devez créer un `SAPParameter` de l’objet et l’ajouter à l’objet de commande correspondant. Vous passez ensuite le nom de l’espace réservé au constructeur ; la direction et la valeur dépendant du contexte.  
  
    -   Pour `Input` paramètres, ne spécifiez pas dans la requête un mot clé pour la direction du paramètre. Le `value` champ de l’objet de paramètre doit être définie, ou le fournisseur lève une exception. Vous ne devez pas définir explicitement le `direction` champ de l’objet de paramètre, car le fournisseur par défaut est `Input`.  
  
    -   Pour les autres paramètres, utilisez la forme `@paramname=@placeholder` et spécifiez le `Output` mot clé explicitement dans la requête. Vous devez ensuite ajouter un `SAPParameter` qui correspond à l’espace réservé et que vous définissez explicitement la direction du paramètre soit `ParamDirection.Output` ou `ParamDirection.InputOutput`, selon le type de paramètre.  
  
-   Noms de paramètre et les noms des espaces réservés ne respectent pas la casse.  
  
-   Les noms de paramètres ne peuvent pas être répétés dans une requête, sauf si elles ont différentes directions.  
  
-   Noms d’espace réservé ne peut pas être répétés dans une requête.  
  
## <a name="considerations-when-calling-an-exec-statement"></a>Considérations lors de l’appel d’une instruction EXEC  
 Cette section répertorie les points que vous devez garder à l’esprit lorsque vous utilisez l’instruction EXEC avec [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
-   Pour une instruction EXEC, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne `TIMS` valeurs de champ en tant que .NET `System.DateTime` objets.  
  
    > [!NOTE]
    >  Pour une instruction SELECT, la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne `TIMS` valeurs de champ en tant que .NET `System.TimeSpan` objets. Pour plus d’informations sur l’instruction SELECT, consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À propos du fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)