---
title: "Comment ajouter des Variables d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: c387cd56-5443-4de2-bbda-be34b95cbe71
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4416534bdd73e8ae6eeeca28165ebc62c11bfc92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-orchestration-variables"></a>Ajout de variables d'orchestration
La fenêtre Vue Orchestration vous permet de gérer les propriétés d’une orchestration (également appelé **Service** propriétés), paramètres, ports, messages et autres variables. En plus des ports et des messages, vous pouvez créer des variables entières, des variables booléennes, des variables de chaînes ou des variables d'une classe .NET.  
  
 Vous pouvez aussi utiliser la fenêtre Vue Orchestration pour gérer les variables appartenant à vos étendues.  
  
### <a name="to-add-a-variable"></a>Pour ajouter une variable  
  
1.  Dans la fenêtre Vue Orchestration, cliquez sur le **Variables** dossier, puis cliquez sur **nouvelle Variable**.  
  
     Le **Variables** dossier se développe, s’il était réduit et une nouvelle variable est ajoutée.  
  
2.  Nommez la variable en tapant un nom dans la propriété Identificateur de la fenêtre Propriétés.  
  
3.  Associez cette variable à un type, tel qu'une classe .NET.  
  
    > [!NOTE]
    >  Le **Types** liste déroulante contienne les types de variables prédéfinies suivantes : **booléenne**, **octets**, **datetime**,  **décimal**, **double**, **int16**, **int32**, **int64**, **sbyte** , **unique**, **chaîne**, **timespan**, **uint16**, **uint32**et **uint64**. Vous pouvez également accéder aux classes et les types de données .NET en sélectionnant  **\<.NET classe.. >**, ce qui permet d’afficher le **sélectionner le Type d’artefact** boîte de dialogue.  
  
4.  Si vous sélectionnez un type de variable prédéfini, vous avez la possibilité de spécifier une valeur initiale pour la variable. Dans la fenêtre Propriétés, définissez la **valeur initiale** propriété.  
  
     Sinon, si le type sélectionné est une classe .NET, vous avez la possibilité d'utiliser un constructeur par défaut. Dans la fenêtre Propriétés, définissez la propriété suivante :  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |**Utiliser le constructeur par défaut**|Si un constructeur par défaut est disponible pour une classe .NET, cette propriété détermine s'il sera appelé lorsque vous utiliserez la variable pour la première fois :<br /><br /> True - Le constructeur par défaut sera appelé. Il s'agit de la valeur par défaut lorsqu'un constructeur par défaut est disponible.<br /><br /> False - Le constructeur par défaut ne sera pas appelé ; vous devez appeler un constructeur dans une expression ou réaliser une assignation pour la variable avant de pouvoir l'utiliser dans votre orchestration.|  
  
    > [!NOTE]
    >  Si le constructeur par défaut requiert des paramètres d’entrée, vous pouvez définir **utiliser le constructeur par défaut** à **False** , puis appelez le constructeur d’une **affectation** forme ; pour exemple, `myVariable = myNamespace.myClass (param1, param2)`.  
  
    > [!NOTE]
    >  Lorsque vous ajouterez une variable à l'orchestration, avant qu'elle ne soit entièrement définie, vous verrez apparaître des points d'exclamation dans cette dernière. Si vous supprimez cette variable avant qu'elle ne soit entièrement définie et que les points d'exclamation apparaissent toujours, vous pouvez obliger l'orchestration à supprimer ces points en créant puis supprimant un paramètre d'orchestration.  
  
### <a name="to-remove-a-variable"></a>Suppression d'une variable  
  
-   Dans la fenêtre Vue Orchestration, cliquez sur la variable que vous souhaitez supprimer, puis cliquez sur **supprimer**.