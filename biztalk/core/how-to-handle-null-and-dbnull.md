---
title: Comment gérer les valeurs Null et DBNull | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, NULL
ms.assetid: d235c265-4947-470b-9f2d-9936ae1b88a1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b07ac74828a858b368cac5d401081a58b8602323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-handle-null-and-dbnull"></a>Comment gérer les valeurs Null et DBNull
Cette rubrique décrit les comportements que l'on peut attendre de valeurs nulles associées à différents types, et traite des options de vérification de l'absence ou de l'existence d'un champ ou membre donné.  
  
## <a name="xml"></a>XML  
 Les points suivants s'appliquent aux valeurs XML :  
  
-   Une valeur XML ne sera jamais retournée d'un document comme étant null. Elle correspond soit à une chaîne vide soit à une erreur « n'existe pas ». Lorsqu'il s'agit d'une chaîne vide, une erreur pourra se produire lors de la conversion de certains types, par exemple des champs spécifiés comme appartenant à un type entier au moment de la création des règles.  
  
-   L’éditeur des règles d’entreprise n’autorise pas la valeur null à un champ ou pour définir le type d’un champ à **objet**.  
  
-   Via le modèle objet, vous pouvez définir le type **objet**. Dans ce cas, la valeur retournée est le type auquel le XPath évalue : **float**, **booléenne**, ou **chaîne**, en fonction de l’expression XPath.  
  
## <a name="net-classes"></a>classes .NET  
 Les règles suivantes s'appliquent aux classes .NET :  
  
-   Vous n’êtes pas autorisé à comparer avec la valeur null si le type de retour n’est pas un **objet** type.  
  
-   Vous pouvez transmettre null comme paramètre pour les paramètres qui ne sont pas des types de valeur mais, selon l'implémentation du membre, une erreur d'exécution se produira.  
  
-   Vous pouvez définir des champs de types dérivés de **objet** avec la valeur null.  
  
## <a name="data-connection"></a>Connexion de données  
 L'exemple suivant s'applique à une connexion de données :  
  
-   Vous pouvez comparer toute colonne de table de base de données NULL, si la table autorise des valeurs NULL pour la colonne et le type de colonne n’est pas **texte**, **ntext**, et **image**.  
  
    > [!NOTE]
    >  L’éditeur des règles d’entreprise vous permet d’utiliser des colonnes de type, **texte** et **ntext**, dans les conditions. Toutefois, lorsque vous exécuterez la stratégie, vous recevrez un message d'erreur vous indiquant que les types de données text, ntext et image ne peuvent être comparés ou triés, hormis avec les opérateurs EST NULL ou COMME.  
  
-   Vous pouvez définir toute colonne de table de base de données sur la valeur null si la table autorise ce type de valeur pour la colonne.  
  
-   L’éditeur des règles d’entreprise définit automatiquement le type de membre dans la liaison à **objet**, si vous comparez ou la valeur null pour un type valeur ; elle les modifications dans le type d’origine si vous réinitialisez ou remplacez l’argument.  
  
-   Pour un type de chaîne, il modifie le type de **objet** si vous définissez sur null, mais laisse sous forme de chaîne si vous comparez par rapport à null.  
  
-   Vous ne pouvez pas comparer ou la valeur **DBNull.Value** à partir de l’éditeur des règles d’entreprise, car il ne changera pas le type de colonne à **objet**.  
  
-   Le moteur convertira une valeur DBNull en null à des fins de comparaison et convertira null en valeur DBNull en vue d'une insertion dans la base de données.  
  
-   Les tests ignoreront les valeurs null (c'est ainsi que fonctionne SQL Server). Par exemple, si vous avez la règle « IF db.column > 5 THEN . », seules les lignes qui comportent une valeur dans db.column sont testées et les lignes contenant la valeur null sont ignorées.  
  
## <a name="typeddatatable-and-typeddatarow"></a>TypedDataTable et TypedDataRow  
 Les points suivants s'appliquent à TypedDataTable et TypedDataRow :  
  
-   L’éditeur des règles d’entreprise change le type de champ à **objet** dans la même manière qu’avec **DataConnection**s.  
  
-   À moins que vous n'effectuiez des comparaisons avec null, les tests échoueront pour les valeurs null. Par exemple, une erreur se produira dans la règle « IF db.column > 5 THEN » si une ligne déclarée comporte une valeur null.  
  
     Notez que les conditions étant évaluées en parallèle, les tests tels que « IF db.column != NULL AND db.column > 5 THEN » continueront à échouer du fait que les deux tests sont potentiellement évalués pour chaque ligne.  
  
## <a name="checking-for-null-or-existence"></a>Vérification de l'absence ou de l'existence  
 Lorsque l'on écrit des règles d'entreprise, il est naturel de vérifier l'existence d'un champ avant de comparer sa valeur. Toutefois, si le champ est null ou qu'il n'existe pas, la comparaison de la valeur génèrera une erreur. Supposons que la règle suivante existe :  
  
 IF Product/Quantity Exists AND Product/Quantity > 1  
  
 Une erreur sera levée dans la règle si Product/Quantity n'existe pas. L'un des moyens de contourner ce problème est de transmettre un nœud parent à une méthode d'assistance qui retourne la valeur de l'élément si elle existe ou autre chose sinon. Voir les règles qui suivent.  
  
 **Règle 1**  
  
 IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)  
  
 **Règle 2**  
  
 IF Helper.Value == X THEN...  
  
 Une autre solution consiste à créer une règle telle que celle-ci :  
  
 IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)  
  
 Dans l'exemple précédent, la fonction CheckQuantityAndDoSomething vérifiera la valeur du paramètre et s'exécutera si la condition est remplie.  
  
> [!NOTE]
>  Vous pouvez également modifier le XPath **champ** propriété pour le fait XML intercepte toutes les erreurs, mais il n’est pas recommandé.