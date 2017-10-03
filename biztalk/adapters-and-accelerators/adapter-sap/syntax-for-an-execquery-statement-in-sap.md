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
# <a name="syntax-for-an-execquery-statement-in-sap"></a>Syntaxe pour une instruction EXECQUERY dans SAP
Vous pouvez utiliser l’interface utilisateur graphique SAP pour créer des requêtes en sélectionnant graphiquement les tables que vous souhaitez interroger, les colonnes et l’ordre que vous souhaitez inclure dans le jeu de résultats, etc. de tri. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] permet aux utilisateurs d’exécuter ces requêtes à partir d’une application ADO.NET en fournissant une opération EXECQUERY qui permettent aux utilisateurs d’exécuter une requête définie dans le système SAP.  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise un Z_EXECUTE_SAP_QUERY RFC personnalisés pour exécuter les requêtes prédéfinies dans le système SAP. Le document RFC personnalisé exécute à son tour le RSAQ_REMOTE_QUERY_CALL, qui est une norme que RFC définie dans le système SAP. Par conséquent, avant de pouvoir utiliser l’opération EXECQUERY, vous devez installer le RFC personnalisé dans le système SAP que vous allez exécuter vos requêtes sur. Pour obtenir des instructions sur la façon d’installer le RFC personnalisé, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
 Cette rubrique fournit des informations sur la syntaxe de l’opération EXECQUERY et d’autres informations utiles relatives à l’opération EXECQUERY.  
  
## <a name="syntax-for-an-execquery-statement"></a>Syntaxe pour une instruction EXECQUERY  
 La section suivante décrit les spécifications de grammaire pour l’utilisation de l’opération EXECQUERY contre le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='\<value 1>’] [, @P2='\<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='\<value 3>'] [, @P1 > '\<value 4>'] [, @P1 <= '\<value 2>']   
[, NOT @P1 = '\<value 2>'] [, NOT @P1 != '\<value 2>'] [, NOT @P1 > '\<value 2>']   
[, @P1 BETWEEN '\<value 1>' AND '\<value 2>'] [, NOT @P1 BETWEEN '\<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 où :  
  
-   **\<Nom_requête >** est le nom de la requête définie dans le système SAP.  
  
-   **Groupe d’utilisateurs** fait référence au groupe d’utilisateurs dans lequel la requête est définie. Il s'agit d'un paramètre obligatoire.  
  
-   **Espace de travail** fait référence à l’espace de travail dans lequel la requête est définie. Dans SAP, il existe deux espaces de travail, Standard et Global. Fournir un espace vide pour spécifier l’espace de travail Standard. Fournir `X` pour spécifier l’espace de travail Global. Valeur par défaut est un espace vide.  
  
-   **VARIANT** fait référence à un jeu de critères de sélection que vous pouvez spécifier lors de l’exécution d’une requête SAP enregistré. Par exemple, vous pouvez utiliser les variantes pour spécifier les valeurs par défaut pour les requêtes.  
  
-   **@Pn**fait référence à n<sup>th</sup> champ de sélection dans la définition de requête SAP.  
  
-   **USEORIGINALCOLUMNNAMES** Spécifie si le fournisseur utilise les noms de colonne d’origine dans le jeu de données, tels qu’ils existent dans le système SAP. Par défaut, le fournisseur utilise les noms conviviaux définis dans la requête SAP. Toutefois, si les noms conviviaux dans la requête ne sont pas uniques, le client ADO.NET génère une erreur lors de la lecture des données à partir du DataSet. Dans de tels scénarios, vous devez spécifier l’option USEORIGINALCOLUMNNAMES, en indiquant que le fournisseur utilise les noms de colonne d’origine dans le jeu de données.  
  
    > [!IMPORTANT]
    >  Vous devez toujours fournir la valeur du mot clé d’OPTION entre guillemets simples, par exemple, «*USEORIGINALCOLUMNNAMES*'.  
  
> [!NOTE]
>  Pour plus d’informations sur la façon dont les paramètres d’une requête SAP se traduire par une syntaxe EXECQUERY, consultez [paramètres de requête de traduire la SAP dans la commande EXECQUERY](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).  
  
### <a name="framing-an-execquery-syntax"></a>Une syntaxe EXECQUERY de tramage  
 Tramage de syntaxe pour une opération EXECQUERY exécuter une requête SAP dépend de la façon dont la requête est définie dans le système SAP, y compris chaque valeur du paramètre défini dans SAP. Pour plus d’informations sur la manière de limiter la syntaxe EXECQUERY pour exécuter une requête SAP, consultez [paramètres de requête de traduire la SAP dans la commande EXECQUERY](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).  
  
### <a name="additional-considerations-while-using-the-execquery-operation"></a>Supplémentaires Considérations lors à l’aide de l’opération EXECQUERY  
 Cette section répertorie les points que vous devez garder à l’esprit lorsque vous utilisez l’instruction EXECQUERY avec [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
-   Les valeurs spécifiées pour le groupe d’utilisateurs, espace de travail et de type VARIANT sont transmises comme-consiste à la norme RFC SAP, RSAQ_REMOTE_QUERY_CALL. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne valide pas les valeurs spécifiées pour ces paramètres.  
  
-   Les valeurs retournées par l’opération EXECQUERY sont de type chaîne.  
  
-   Mots clés pour les noms de requêtes, groupe d’utilisateurs, espace de travail et les variantes ne respectent pas la casse. Toutefois, les noms de paramètre doivent toujours être dans caseP supérieur comme @P1, @P2, etc.. Exemple :  
  
    ```  
    EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
     est identique à  
  
    ```  
    EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
    ```  
  
-   Les opérateurs pris en charge par le EXECQUERY sont >, \<, > =, < =, ! =, NOT et BETWEEN.  
  
-   Les caractères génériques ne sont pas pris en charge par l’opération EXECQUERY. Par exemple, l’instruction suivante donne le résultat attendu :  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
     Toutefois, la même requête lors de l’exécution avec un caractère générique génère une erreur. Notez l’utilisation de caractères génériques pour  **@P2** .  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
    ```  
  
     Dans cet exemple, vous pouvez obtenir une erreur indiquant qu’aucune donnée n’a été trouvée. C’est parce que la requête recherche **'\*&\*'** sous forme de chaîne et ne tient pas compte de l’astérisque (*) comme caractère générique.  
  
-   Vous devez toujours spécifier une valeur de date au format AAAAMMJJ.  
  
-   Si vous exécutez une requête qui est une variante définie dans le système SAP, vous pouvez spécifier le nom de la variante en tant que partie de la commande. Exemple :  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
    ```  
  
    > [!NOTE]
    >  Vous n’avez pas besoin de spécifier un nom de type variant si une variante de la valeur par défaut est définie pour la requête dans le système SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)