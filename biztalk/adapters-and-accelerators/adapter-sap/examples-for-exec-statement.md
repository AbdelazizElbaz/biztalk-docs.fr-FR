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
# <a name="examples-for-exec-statement"></a>Exemples de l’instruction EXEC
Cette rubrique montre un exemple de syntaxe pour les différentes instructions EXEC.

## <a name="sample-statements"></a>Exemples d’instructions 
  
-   Pour exécuter une commande BAPI qui ne prend aucun paramètre d’entrée, utilisez la syntaxe suivante : données retournées via un **DataReader** objet :  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST  
    ```  
  
-   Pour exécuter une commande RFC qui accepte des paramètres d’entrée, utilisez la syntaxe suivante :  
  
    ```  
    EXEC RFC_CUSTOMER_GET @NAME1='Contoso'  
    ```  
  
-   Pour exécuter une commande RFC qui accepte des paramètres d’entrée comme une variable, utilisez la syntaxe suivante :  
  
    ```  
    EXEC RFC_CUSTOMER_GET @var=@var  
    ```  
  
     Dans cet exemple, vous devez créer un paramètre nommé `@var` et définissez la valeur explicitement (par exemple, pour 1001), car le premier paramètre de RFC_CUSTOMER_GET correspond à KUNNR (numéro de client)  
  
-   Pour exécuter une commande RFC qui utilise une variable pour le nom du paramètre d’entrée, utilisez la syntaxe suivante :  
  
    ```  
    EXEC RFC_CUSTOMER_GET @KUNNR=@var1, @NAME1='Contoso'  
    ```  
  
     Vous devez créer un paramètre nommé `@var1`, spécifiez la valeur, puis le lier à l’objet de commande correspondant. La direction par défaut de l’objet de paramètre qui vient d’être créé est `input`.  
  
-   Pour exécuter une commande BAPI et les tables de retournés en tant que paramètre, utilisez la syntaxe suivante :  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST @COMPANYCODE_LIST=@var1 OUTPUT  
    ```  
  
     Vous devez créer un paramètre nommé `@var1`, spécifiez la valeur et la lier à l’objet de commande correspondant. La direction de l’objet de paramètre qui vient d’être créé doit être `InputOutput` ou `Output`.  
  
-   L’exemple suivant EXEC utilise un paramètre de type complexe de table. Dans l’exemple, @fields est un paramètre TABLE.  
  
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
  
-   L’exemple suivant EXEC utilise un type complexe de STRUCT. Dans l’exemple, @equimaster est un paramètre STRUCT.  
  
    ```  
    exec BAPI_EQMT_MODIFY @equipment='000000000000000637', @equimaster='<EQUIMASTER>           
                <EQUIPMENT xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">equip</EQUIPMENT>  
                <EQUICATGRY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">E</EQUICATGRY>  
                <MATERIAL xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">mat</MATERIAL>  
              </EQUIMASTER >', @equimaster=@em output  
    ```  
  
## <a name="support-for-complex-parameter-types"></a>Prise en charge des Types de paramètres complexes  
 Il existe deux façons pour prendre en charge des paramètres complexes RFC (tables et des structures) lorsque vous utilisez le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:  
  
-   Indiquez la valeur XML inline pour le type complexe. Cet exemple montre comment passer de XML pour le type de paramètre complexe *champs*. Dans l’exemple suivant, *@fields* est un paramètre table.  
  
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
  
-   Créer un **DataTable** paramètre avec des colonnes pour les champs dans le type complexe et le jeu de valeur pour le paramètre SAP **DataTable**. Cet exemple montre comment définir la @fields type complexe en utilisant un **DataTable**.  
  
    ```  
    cmd.CommandText = "exec rfc_read_table @query_table='BNKA', @fields = @p_fields";  
    DataTable dt = new DataTable();  
    dt.Columns.Add("FIELDNAME");  
    SAPParameter p = new SAPParameter("@p_fields");  
    p.Value = dt;  
    ```  
  
## <a name="limitations"></a>Limitations  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] présente les limitations suivantes pour les types complexes.  
  
-   Lorsque vous passez un type complexe dans un paramètre en utilisant un **DataTable**, vous devez inclure tous les champs (colonnes) du type complexe dans le **DataTable**.  
  
-   Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] ne prend pas en charge **DbNull**. Vous ne pouvez pas définir **DbNull** en tant que valeur pour les paramètres.  
  
