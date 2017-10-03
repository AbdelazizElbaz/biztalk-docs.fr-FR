---
title: "Exemples d’instruction SELECT dans l’adaptateur dans BizTalk mySAP | Documents Microsoft"
description: "Sélectionnez les exemples et exemples à l’aide de l’adaptateur mySAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54a5a4ac-a994-4706-9735-a5a1a82b893b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 140e895bf8ec2fb65a848c8752dc8e141530bd85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="examples-for-select-statement"></a>Exemples de l’instruction SELECT
Cette rubrique montre un exemple de syntaxe pour les différentes instructions SELECT.

## <a name="sample-statements"></a>Exemples d’instructions 
  
-   Pour plus d’informations sur les vols répertoriés dans la table nommée SPFLI, utilisez la syntaxe suivante :  
  
    ```  
    Select * from SPFLI  
    ```  
  
-   Pour stocker les données extraites dans un fichier nommé flight.txt à \\\SAPServer\Extracts, utilisez la syntaxe suivante :  
  
    ```  
    Select * Into file '\\SAPServer\Extracts\flight.txt' from SPFLI  
    ```  
  
-   Pour répertorier les détails de tous les vols de New York et à San Francisco, utilisez la syntaxe suivante :  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto='SAN FRANCISCO'  
    ```  
  
-   Pour répertorier les détails de tous les vols de New York et dont `connid` sont des valeurs de champ entre 1000 et 5000, utilisez la syntaxe suivante :  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and (connid>1000 and connid<5000)  
    ```  
  
-   Pour répertorier les détails de tous les vols de New York et à une ville spécifiée par l’utilisateur, utilisez la syntaxe suivante :  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto=@variable  
    ```  
  
     Dans cette instance, créez un paramètre SAP nommé `@variable`, spécifiez la valeur et l’ajouter à l’objet de commande correspondant.  
  
-   Dans la clause LIKE d’une requête SELECT, uniquement le signe de pourcentage « % » (pour n’importe quelle chaîne de zéro ou plusieurs caractères) et trait de soulignement « _ » (pour n’importe quel caractère unique), sont des caractères spéciaux autorisés. Tous les autres sont considérés comme des valeurs de chaîne et sont ignorés.  
  
    -   Exemple pour illustrer l’utilisation du pourcentage « % »  
  
        ```  
        SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
        ```  
  
         Ici, le MODE % extrait tous les enregistrements où nom1 contient la chaîne « MODE ».  
  
    -   Exemple pour illustrer l’utilisation d’un trait de soulignement « _ »  
  
        ```  
        SELECT NAME1  AS [MYANME],  LAND1, KUNNR  from KNA1 where (NAME1 LIKE 'D_' )  
        ```  
  
         Ici, « D_ » extrait tous les enregistrements où nom1 commence par « D » et contient deux caractères.  
  
-   Exemple pour illustrer une clause de prédicat « entre »  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   Exemple pour illustrer une clause de prédicat « pas entre »  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT not between 596 AND 599) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   Exemple d’instruction SELECT à l’aide de la jointure et une clause TOP  
  
    ```  
    SELECT TOP 1 * FROM spfli INNER JOIN sflight ON spfli.mandt = sflight.mandt  
    ```  
  
-   Exemple d’instruction SELECT à l’aide de la clause OPTION  
  
    ```  
    SELECT top 50000 * from bseg option 'batchsize 20000'  
    ```  
