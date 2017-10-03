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
# <a name="examples-for-select-statement"></a><span data-ttu-id="de936-103">Exemples de l’instruction SELECT</span><span class="sxs-lookup"><span data-stu-id="de936-103">Examples for SELECT Statement</span></span>
<span data-ttu-id="de936-104">Cette rubrique montre un exemple de syntaxe pour les différentes instructions SELECT.</span><span class="sxs-lookup"><span data-stu-id="de936-104">This topic shows example syntax for various SELECT statements.</span></span>

## <a name="sample-statements"></a><span data-ttu-id="de936-105">Exemples d’instructions</span><span class="sxs-lookup"><span data-stu-id="de936-105">Sample statements</span></span> 
  
-   <span data-ttu-id="de936-106">Pour plus d’informations sur les vols répertoriés dans la table nommée SPFLI, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="de936-106">To list details about flights listed in the table named SPFLI, use the following syntax:</span></span>  
  
    ```  
    Select * from SPFLI  
    ```  
  
-   <span data-ttu-id="de936-107">Pour stocker les données extraites dans un fichier nommé flight.txt à \\\SAPServer\Extracts, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="de936-107">To store extracted data into a file named flight.txt at \\\SAPServer\Extracts, use the following syntax:</span></span>  
  
    ```  
    Select * Into file '\\SAPServer\Extracts\flight.txt' from SPFLI  
    ```  
  
-   <span data-ttu-id="de936-108">Pour répertorier les détails de tous les vols de New York et à San Francisco, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="de936-108">To list details of all flights from New York to San Francisco, use the following syntax:</span></span>  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto='SAN FRANCISCO'  
    ```  
  
-   <span data-ttu-id="de936-109">Pour répertorier les détails de tous les vols de New York et dont `connid` sont des valeurs de champ entre 1000 et 5000, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="de936-109">To list details of all flights from New York whose `connid` field values are between 1000 and 5000, use the following syntax:</span></span>  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and (connid>1000 and connid<5000)  
    ```  
  
-   <span data-ttu-id="de936-110">Pour répertorier les détails de tous les vols de New York et à une ville spécifiée par l’utilisateur, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="de936-110">To list details of all flights from New York to a user-specified city, use the following syntax:</span></span>  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto=@variable  
    ```  
  
     <span data-ttu-id="de936-111">Dans cette instance, créez un paramètre SAP nommé `@variable`, spécifiez la valeur et l’ajouter à l’objet de commande correspondant.</span><span class="sxs-lookup"><span data-stu-id="de936-111">In this instance, create an SAP parameter named `@variable`, specify the value, and add it to the corresponding command object.</span></span>  
  
-   <span data-ttu-id="de936-112">Dans la clause LIKE d’une requête SELECT, uniquement le signe de pourcentage « % » (pour n’importe quelle chaîne de zéro ou plusieurs caractères) et trait de soulignement « _ » (pour n’importe quel caractère unique), sont des caractères spéciaux autorisés.</span><span class="sxs-lookup"><span data-stu-id="de936-112">In the LIKE clause of a SELECT query, only the percent sign, "%" (for any string of zero or more characters), and underscore, "_" (for any single character), are allowable special characters.</span></span> <span data-ttu-id="de936-113">Tous les autres sont considérés comme des valeurs de chaîne et sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="de936-113">All others are considered string values and are ignored.</span></span>  
  
    -   <span data-ttu-id="de936-114">Exemple pour illustrer l’utilisation du pourcentage « % »</span><span class="sxs-lookup"><span data-stu-id="de936-114">Example to demonstrate the use of percentage "%"</span></span>  
  
        ```  
        SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
        ```  
  
         <span data-ttu-id="de936-115">Ici, le MODE % extrait tous les enregistrements où nom1 contient la chaîne « MODE ».</span><span class="sxs-lookup"><span data-stu-id="de936-115">Here, %MODE% fetches all records where Name1 contains the string "MODE".</span></span>  
  
    -   <span data-ttu-id="de936-116">Exemple pour illustrer l’utilisation d’un trait de soulignement « _ »</span><span class="sxs-lookup"><span data-stu-id="de936-116">Example to demonstrate the use of underscore "_"</span></span>  
  
        ```  
        SELECT NAME1  AS [MYANME],  LAND1, KUNNR  from KNA1 where (NAME1 LIKE 'D_' )  
        ```  
  
         <span data-ttu-id="de936-117">Ici, « D_ » extrait tous les enregistrements où nom1 commence par « D » et contient deux caractères.</span><span class="sxs-lookup"><span data-stu-id="de936-117">Here, "D_" fetches all records where Name1 starts with "D" and contains two characters.</span></span>  
  
-   <span data-ttu-id="de936-118">Exemple pour illustrer une clause de prédicat « entre »</span><span class="sxs-lookup"><span data-stu-id="de936-118">Example to demonstrate a "between" predicate clause</span></span>  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   <span data-ttu-id="de936-119">Exemple pour illustrer une clause de prédicat « pas entre »</span><span class="sxs-lookup"><span data-stu-id="de936-119">Example to demonstrate a "not between" predicate clause</span></span>  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT not between 596 AND 599) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   <span data-ttu-id="de936-120">Exemple d’instruction SELECT à l’aide de la jointure et une clause TOP</span><span class="sxs-lookup"><span data-stu-id="de936-120">Example for SELECT statement using Join and a TOP clause</span></span>  
  
    ```  
    SELECT TOP 1 * FROM spfli INNER JOIN sflight ON spfli.mandt = sflight.mandt  
    ```  
  
-   <span data-ttu-id="de936-121">Exemple d’instruction SELECT à l’aide de la clause OPTION</span><span class="sxs-lookup"><span data-stu-id="de936-121">Example for SELECT statement using the OPTION clause</span></span>  
  
    ```  
    SELECT top 50000 * from bseg option 'batchsize 20000'  
    ```  
