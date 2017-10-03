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
# <a name="examples-for-execquery-statement"></a><span data-ttu-id="08923-103">Exemples d’instruction EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="08923-103">Examples for EXECQUERY Statement</span></span>
<span data-ttu-id="08923-104">Cette rubrique fournit des exemples d’instructions EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="08923-104">This topic provides sample EXECQUERY statements.</span></span>  


## <a name="sample-statements"></a><span data-ttu-id="08923-105">Exemples d’instructions</span><span class="sxs-lookup"><span data-stu-id="08923-105">Sample statements</span></span>
-   <span data-ttu-id="08923-106">Commande à exécuter une requête qui accepte deux paramètres P1 et P2.</span><span class="sxs-lookup"><span data-stu-id="08923-106">Command to execute a query that takes two parameters P1 and P2.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
-   <span data-ttu-id="08923-107">Commande à exécuter une requête qui accepte une plage de valeur pour le paramètre P1.</span><span class="sxs-lookup"><span data-stu-id="08923-107">Command to execute a query that takes a range of value for parameter P1.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   <span data-ttu-id="08923-108">Commande à exécuter une requête qui accepte les valeurs de paramètre P1 en dehors d’une plage particulière.</span><span class="sxs-lookup"><span data-stu-id="08923-108">Command to execute a query that takes values for parameter P1 outside a particular range.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   <span data-ttu-id="08923-109">Commande à exécuter une requête qui peut prendre l’une des deux valeurs de paramètre P1.</span><span class="sxs-lookup"><span data-stu-id="08923-109">Command to execute a query that can take one of two values for parameter P1.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262', @P1 = '0000003263'  
    ```  
  
-   <span data-ttu-id="08923-110">Commande à exécuter une requête qui ne peut pas accepter les valeurs des paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="08923-110">Command to execute a query that cannot take specific values for parameters.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 = '0000003262', NOT @P2 = '0000003263'  
    ```  
  
     <span data-ttu-id="08923-111">Dans cet exemple, P1 peut avoir toute valeur autre que '0000003262'.</span><span class="sxs-lookup"><span data-stu-id="08923-111">In this example, P1 can have any value other than '0000003262'.</span></span> <span data-ttu-id="08923-112">De même, P2 peut avoir toute valeur autre que '0000003263'.</span><span class="sxs-lookup"><span data-stu-id="08923-112">Similarly, P2 can have any value other than '0000003263'.</span></span>  
  
-   <span data-ttu-id="08923-113">Commande à exécuter une requête qui contient les variantes définis dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="08923-113">Command to execute a query that has variants defined in the SAP system.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant = ‘variant1’  
    ```  
  
     <span data-ttu-id="08923-114">Variantes de faire référence à un jeu de critères de sélection que vous pouvez spécifier lors de l’exécution d’une requête SAP enregistré.</span><span class="sxs-lookup"><span data-stu-id="08923-114">Variants refer to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="08923-115">Par exemple, vous pouvez utiliser les variantes pour spécifier les valeurs par défaut pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="08923-115">For example, you can use variants to specify default values for queries.</span></span> <span data-ttu-id="08923-116">Pour les requêtes qui ont des variantes définies pour tous les paramètres, vous n’avez pas besoin de spécifier les paramètres dans le texte de commande.</span><span class="sxs-lookup"><span data-stu-id="08923-116">For queries that have variants defined for all parameters, you do not need to specify the parameters in the command text.</span></span>  
  
-   <span data-ttu-id="08923-117">Commande à exécuter une requête qui ne requiert pas un paramètre.</span><span class="sxs-lookup"><span data-stu-id="08923-117">Command to execute a query that does not require a parameter.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'some_dummy_value'  
    ```  
  
     <span data-ttu-id="08923-118">Pour les requêtes qui ne prennent pas de paramètre, vous devez spécifier un paramètre avec une valeur factice.</span><span class="sxs-lookup"><span data-stu-id="08923-118">For queries that do not take parameter, you must specify a parameter with a dummy value.</span></span>  
  
-   <span data-ttu-id="08923-119">Commande à exécuter une requête qui contient un paramètre attendu d’une valeur de date.</span><span class="sxs-lookup"><span data-stu-id="08923-119">Command to execute a query containing a parameter expecting a date value.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '20080606'  
    ```  
  
     <span data-ttu-id="08923-120">Pour les requêtes qui prennent des paramètres attendue des valeurs de date, vous devez spécifier la date selon le format AAAAMMJJ.</span><span class="sxs-lookup"><span data-stu-id="08923-120">For queries that take parameters expecting date values, you must specify the date as YYYYMMDD.</span></span>  
  
-   <span data-ttu-id="08923-121">Commande à exécuter une requête en spécifiant des valeurs null pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="08923-121">Command to execute a query by specifying null values for parameters.</span></span>  
  
     <span data-ttu-id="08923-122">De telles requêtes, vous ne pouvez pas spécifier une requête en tant que :</span><span class="sxs-lookup"><span data-stu-id="08923-122">For such queries, you cannot specify a query as:</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'null'  
    ```  
  
     <span data-ttu-id="08923-123">Au lieu de cela, si vous ne souhaitez pas spécifier une valeur, vous ne devez pas spécifier P1.</span><span class="sxs-lookup"><span data-stu-id="08923-123">Instead, if you do not want to specify a value, you should not specify P1 at all.</span></span>  
  
-   <span data-ttu-id="08923-124">Pour exécuter une requête contenant un paramètre attend une valeur supérieure à un certain nombre de commandes.</span><span class="sxs-lookup"><span data-stu-id="08923-124">Command to execute a query containing a parameter expecting a value greater than a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 > '0000003262'  
    ```  
  
-   <span data-ttu-id="08923-125">Commande à exécuter une requête qui contient un paramètre attendu d’une valeur inférieure à un certain nombre.</span><span class="sxs-lookup"><span data-stu-id="08923-125">Command to execute a query containing a parameter expecting a value lesser than a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 < '0000003262'  
    ```  
  
-   <span data-ttu-id="08923-126">Pour exécuter une requête contenant un paramètre attendu d’une valeur supérieure ou égale à un certain nombre de commandes.</span><span class="sxs-lookup"><span data-stu-id="08923-126">Command to execute a query containing a parameter expecting a value greater or equal to a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 >= '0000003262'  
    ```  
  
-   <span data-ttu-id="08923-127">Pour exécuter une requête contenant un paramètre attendu d’une valeur inférieure ou égale à un certain nombre de commandes.</span><span class="sxs-lookup"><span data-stu-id="08923-127">Command to execute a query containing a parameter expecting a value lesser or equal to a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 <= '0000003262'  
    ```  
  
-   <span data-ttu-id="08923-128">Pour exécuter une requête contenant un paramètre attend une valeur non égal à un certain nombre de commandes.</span><span class="sxs-lookup"><span data-stu-id="08923-128">Command to execute a query containing a parameter expecting a value not equal to a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 != '0000003262'  
    ```  
  