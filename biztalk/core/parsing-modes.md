---
title: "Modes d’analyse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- pipeline components [custom], parsing
ms.assetid: b1188720-e5ae-47ae-ab8e-16d7ed08b778
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf8f9b2618b8cafd7813f08217457227a0f21809
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="parsing-modes"></a><span data-ttu-id="65dee-102">Modes d’analyse</span><span class="sxs-lookup"><span data-stu-id="65dee-102">Parsing Modes</span></span>
<span data-ttu-id="65dee-103">Le mode d’analyse est un attribut de l’enregistrement schemaInfo, avec deux modes : vitesse et la complexité.</span><span class="sxs-lookup"><span data-stu-id="65dee-103">The parsing mode is an attribute on the schemaInfo record, with two modes: speed and complexity.</span></span> <span data-ttu-id="65dee-104">Vous pouvez configurer la propriété Optimisation de l'analyseur dans l'Éditeur de schéma BizTalk.</span><span class="sxs-lookup"><span data-stu-id="65dee-104">The Parser Optimization property can be configured within the BizTalk Schema Editor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65dee-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="65dee-105">Example</span></span>  
  
```  
<b:schemaInfo count_positions_by_byte="false" standard="Flat File"   
root_reference="document" parser_optimization="complexity" />.  
```  
  
 <span data-ttu-id="65dee-106">En mode vitesse, l'analyseur traite les données à mesure qu'elles apparaissent dans le flux.</span><span class="sxs-lookup"><span data-stu-id="65dee-106">In speed mode, the parser tries to fit data as they appear in the stream.</span></span> <span data-ttu-id="65dee-107">Voici par exemple le schéma suivant :</span><span class="sxs-lookup"><span data-stu-id="65dee-107">For example, given the following schema.</span></span>  
  
```  
<schema>  
   Root ("," prefix)  
      Field1   opt  
      Field2   opt  
      Field3   opt  
      Field4   opt  
      Record ("," infix)  
            Field5  
            Field6  
</schema>  
```  
  
 <span data-ttu-id="65dee-108">et le message entrant.</span><span class="sxs-lookup"><span data-stu-id="65dee-108">and input message.</span></span>  
  
```  
,1,2,3,4  
```  
  
 <span data-ttu-id="65dee-109">En mode vitesse, le document XML suivant est généré :</span><span class="sxs-lookup"><span data-stu-id="65dee-109">with speed mode the following XML document is obtained.</span></span>  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
   <Field3>3</Field3>  
   <Field4>4</Field4>  
</Root>  
```  
  
 <span data-ttu-id="65dee-110">En mode complexité, le même schéma produit le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="65dee-110">With complexity mode, the same schema produces the following output.</span></span>  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
      <Record>  
         <Field5>3</Field5>  
         <Field6>4</Field6>  
      </Record>  
</Root>  
```  
  
 <span data-ttu-id="65dee-111">En mode complexité, le moteur d'analyse de fichier plat utilise à la fois l'analyse descendante et ascendante, et essaie de traiter les données de manière plus précise.</span><span class="sxs-lookup"><span data-stu-id="65dee-111">In complexity mode, the flat file parsing engine uses both top-down and bottom-up parsing, and tries to fit data more accurately.</span></span> <span data-ttu-id="65dee-112">En mode vitesse, l'analyseur traite les données à mesure qu'elles apparaissent dans le flux.</span><span class="sxs-lookup"><span data-stu-id="65dee-112">In speed mode, the parser tries to fit data as they appear in the stream.</span></span>  
  
 <span data-ttu-id="65dee-113">Si des éléments facultatifs se trouvent avec des éléments obligatoires, par exemple :</span><span class="sxs-lookup"><span data-stu-id="65dee-113">If you have optional elements with required elements, for example.</span></span>  
  
```  
<schema>  
   Root  
      Record1 (required)  
  
      Record2 (optional)  
  
      Record3 (required)  
  
```  
  
 <span data-ttu-id="65dee-114">vous devez utiliser le mode complexité pour analyser correctement les données, car l'analyseur représente en interne le schéma tel que :</span><span class="sxs-lookup"><span data-stu-id="65dee-114">you must use complexity mode to correctly parse the data, because the parser represents the schema internally as.</span></span>  
  
```  
<schema>  
   Root  
      Record1 (required)  
      <sequence> (optional)  
         Record2 (required)  
         Record3 (required)  
```  
  
## <a name="see-also"></a><span data-ttu-id="65dee-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65dee-115">See Also</span></span>  
 [<span data-ttu-id="65dee-116">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="65dee-116">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)