---
title: "Exemples d’instruction EXECQUERY dans mySAP l’adaptateur dans BizTalk | Documents Microsoft"
description: "Exemples EXECQUERY et les exemples à l’aide de l’adaptateur mySAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4139af16-7c38-4ea2-b3e5-5acf8fc1f3c4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77c5d5877ff502b8fdca620d8b92e4427d3b73b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="examples-for-execquery-statement"></a>Exemples d’instruction EXECQUERY
Cette rubrique fournit des exemples d’instructions EXECQUERY.  


## <a name="sample-statements"></a>Exemples d’instructions
-   Commande à exécuter une requête qui accepte deux paramètres P1 et P2.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
-   Commande à exécuter une requête qui accepte une plage de valeur pour le paramètre P1.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   Commande à exécuter une requête qui accepte les valeurs de paramètre P1 en dehors d’une plage particulière.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   Commande à exécuter une requête qui peut prendre l’une des deux valeurs de paramètre P1.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262', @P1 = '0000003263'  
    ```  
  
-   Commande à exécuter une requête qui ne peut pas accepter les valeurs des paramètres spécifiques.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 = '0000003262', NOT @P2 = '0000003263'  
    ```  
  
     Dans cet exemple, P1 peut avoir toute valeur autre que '0000003262'. De même, P2 peut avoir toute valeur autre que '0000003263'.  
  
-   Commande à exécuter une requête qui contient les variantes définis dans le système SAP.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant = ‘variant1’  
    ```  
  
     Variantes de faire référence à un jeu de critères de sélection que vous pouvez spécifier lors de l’exécution d’une requête SAP enregistré. Par exemple, vous pouvez utiliser les variantes pour spécifier les valeurs par défaut pour les requêtes. Pour les requêtes qui ont des variantes définies pour tous les paramètres, vous n’avez pas besoin de spécifier les paramètres dans le texte de commande.  
  
-   Commande à exécuter une requête qui ne requiert pas un paramètre.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'some_dummy_value'  
    ```  
  
     Pour les requêtes qui ne prennent pas de paramètre, vous devez spécifier un paramètre avec une valeur factice.  
  
-   Commande à exécuter une requête qui contient un paramètre attendu d’une valeur de date.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '20080606'  
    ```  
  
     Pour les requêtes qui prennent des paramètres attendue des valeurs de date, vous devez spécifier la date selon le format AAAAMMJJ.  
  
-   Commande à exécuter une requête en spécifiant des valeurs null pour les paramètres.  
  
     De telles requêtes, vous ne pouvez pas spécifier une requête en tant que :  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'null'  
    ```  
  
     Au lieu de cela, si vous ne souhaitez pas spécifier une valeur, vous ne devez pas spécifier P1.  
  
-   Pour exécuter une requête contenant un paramètre attend une valeur supérieure à un certain nombre de commandes.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 > '0000003262'  
    ```  
  
-   Commande à exécuter une requête qui contient un paramètre attendu d’une valeur inférieure à un certain nombre.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 < '0000003262'  
    ```  
  
-   Pour exécuter une requête contenant un paramètre attendu d’une valeur supérieure ou égale à un certain nombre de commandes.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 >= '0000003262'  
    ```  
  
-   Pour exécuter une requête contenant un paramètre attendu d’une valeur inférieure ou égale à un certain nombre de commandes.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 <= '0000003262'  
    ```  
  
-   Pour exécuter une requête contenant un paramètre attend une valeur non égal à un certain nombre de commandes.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 != '0000003262'  
    ```  
  