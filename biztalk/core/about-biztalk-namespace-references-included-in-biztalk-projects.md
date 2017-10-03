---
title: "À propos des références de Namespace de BizTalk inclus dans les projets BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- System.Xml namespace
- Microsoft.BizTalk.GlobalPropertySchemas namespace
- namespaces, System.Xml namespace
- System namespace
- namespaces, System namespace
- namespaces, Microsoft.BizTalk.GlobalPropertySchemas namespace
- Microsoft.BizTalk.DefaultPipelines namespace
- projects, namespaces
- namespaces, warnings
- namespaces, Microsoft.BIzTalk.DefaultPipelines namespace
- namespaces
ms.assetid: cb642eac-7307-44f8-bbba-3ae364e11ea2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 820e15eb3524713dfd7d3f86311ca262fde191d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-biztalk-namespace-references-included-in-biztalk-projects"></a>À propos des références aux espaces de noms BizTalk comprises dans les projets BizTalk
Lorsque vous ajoutez un nouveau projet BizTalk, les espaces de noms suivants sont inclus par défaut :  
  
-   **Microsoft.BizTalk.DefaultPipelines**  
  
-   **Microsoft.BizTalk.GlobalPropertySchemas**  
  
-   **Système**  
  
-   **System.Xml**  
  
 Vous pouvez également ajouter de nouvelles références et références Web à votre projet. Pour plus d’informations sur l’ajout de références à l’aide du **projet** menu, consultez [à l’aide de Visual Studio](../core/using-visual-studio.md). Pour plus d’informations sur l’ajout de références Web, consultez [Ajout de références Web](../core/adding-web-references.md).  
  
> [!CAUTION]
>  Ne supprimez pas les références par défaut. Vous risqueriez de rencontrer des problèmes en faisant référence à des éléments BizTalk dans votre projet. Vous pouvez restaurer les références par défaut dans l'Explorateur de solutions.  
  
> [!CAUTION]
>  Si votre projet BizTalk fait référence à un autre assembly et que ce dernier est mis à jour, les mises à jour ne sont pas sélectionnées automatiquement dans votre projet BizTalk. Vous devez supprimer la référence périmée dans l'Explorateur de solutions, puis la réintégrer (re-référencer l'assembly). Vous avez également la possibilité de fermer votre solution et de la rouvrir. Dans un cas comme dans l'autre, les mises à jour les plus récentes de l'assembly référencé sont disponibles pour votre projet.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Référence à Microsoft.BizTalk.DefaultPipelines](../core/microsoft-biztalk-defaultpipelines-reference.md)  
  
-   [Référence Microsoft.BizTalk.GlobalPropertySchemas](../core/microsoft-biztalk-globalpropertyschemas-reference.md)  
  
-   [Référence du système](../core/system-reference.md)  
  
-   [Référence System.Xml](../core/system-xml-reference.md)