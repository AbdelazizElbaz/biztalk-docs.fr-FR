---
title: "Paramètres de requête SAP se traduire par des commandes EXECQUERY dans mySAP l’adaptateur dans BizTalk | Documents Microsoft"
description: "Conseils pour traduire des requêtes SAP à EXECQUERY, avec des exemples"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a545e20-2607-4946-a60d-0a227b86d093
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efb50db3e499970c0504f81467d382aee31c868f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="translate-sap-query-parameters-into-execquery-command"></a>Paramètres de requête SAP se traduire par des commandes EXECQUERY
Explique comment les paramètres d’une requête se traduire par un texte de commande EXECQUERY. Cette rubrique utilise l’exemple d’une requête personnalisée SAP, ZQUERY_TST_NEW.  
  
## <a name="open-the-query-in-sap-gui"></a>Ouvrir la requête dans l’interface utilisateur graphique SAP  
 Effectuez les opérations suivantes pour ouvrir la requête dans SAP. Les étapes décrites ici sont pour les requêtes ZQUERY_TST_NEW et sont spécifiques aux versions SAP.  
  
1.  Exécutez la transaction SQ01.  
  
2.  Dans le **requête à partir du groupe d’utilisateurs** , cliquez sur **aperçu rapide**.  
  
3.  Dans le **aperçu rapide** page, dans le **aperçu** zone de texte, tapez `ZQUERY_TST_NEW`, puis cliquez sur **affichage**.  
  
4.  Dans le **aperçu rapide** , cliquez sur le **champs de sélection** onglet pour répertorier tous les paramètres dans la requête.  
  
     La figure suivante montre tous les paramètres dans la définition de requête.  
  
     ![Liste de paramètres pour une requête SAP](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")  
  
5.  Cliquez sur **Exécuter**. La page suivante s’affiche.  
  
     ![Fournir des valeurs de paramètre pour une requête SAP](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")  
  
6.  Cliquez sur les flèches jaunes pour définir chaque paramètre. Vous pouvez soit définir des valeurs spécifiques autorisée/non autorisée, ou vous pouvez définir une plage de valeurs autorisée/non autorisée.  La syntaxe EXECQUERY doit être spécifiée selon les valeurs configurées dans l’interface utilisateur graphique SAP pour chaque paramètre.  
  
 La section suivante fournit une explication sur la façon dont les valeurs sont définies dans l’interface GUI SAP, et comment ces valeurs traduites en syntaxe EXECQUERY.  
  
## <a name="frame-an-execquery-syntax"></a>Une syntaxe EXECQUERY de frame  
 Voyons ce que la syntaxe EXECQUERY ressemble à selon les valeurs de paramètre définies dans la définition de requête. Pour comprendre cela, nous allons montrer des exemples de la façon dont les valeurs configurées pour le premier paramètre, **nombre à deux chiffres**, traduire les **ZQUERY_TST_NEW** requête.  
  
 Tout d’abord, supposons que les valeurs dans le **unique ourbes** onglet (avec un point vert) sont définies comme indiqué dans la capture d’écran suivante :  
  
 ![Liste de valeurs de paramètre qu’une requête peut accepter](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")  
  
> [!NOTE]
>  Cette boîte de dialogue s’affiche après avoir cliqué sur la flèche jaune dans la **nombre à deux chiffres** paramètre.  
  
 Dans ce cas, la syntaxe EXECQUERY ressemble à :  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5'  
```  
  
 Pour la même requête, en plus des valeurs dans le **unique ourbes** onglet (avec un point vert), vous pouvez également avoir des valeurs le **unique ourbes** onglet (avec un point rouge), défini comme suit :  
  
 ![Liste de valeurs de paramètre qu’une requête ne peut pas accepter](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")  
  
 Dans ce cas, la syntaxe EXECQUERY ressemble à :  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8'  
```  
  
 Maintenant, si vous ajoutez des valeurs à la **plages** onglet (avec un point vert), comme indiqué dans la capture d’écran suivante :  
  
 ![Plage de valeurs de paramètre qu’une requête peut accepter](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")  
  
 la syntaxe EXECQUERY ressemble à :  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5'  
```  
  
 De même, si vous ajoutez des valeurs à la **plages** onglet (avec un point rouge), comme indiqué dans la capture d’écran suivante :  
  
 ![Plage de valeurs de paramètre qu’une requête ne peut pas accepter](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")  
  
 la syntaxe EXECQUERY ressemble à :  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5', NOT @P1 BETWEEN '6' AND '8'  
```  
  
 Pour plus de simplicité et de compréhension, cette rubrique traite uniquement sur le premier paramètre, **nombre à deux chiffres**. Vous pouvez utiliser des méthodes semblables pour déterminer comment les valeurs définies pour les autres paramètres traduire en une syntaxe EXECQUERY.  
  
