---
title: "Exportation de stratégies, les liaisons et les Applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, exporting
- exporting, policies
- bindings, exporting
- exporting, applications
- applications, exporting
- exporting, bindings
ms.assetid: ac101206-be49-47c9-a354-4f39e8b77acf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d6df445b0fefc132940a736870d66c62329ce60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-biztalk-applications-bindings-and-policies"></a>Exportation d'applications, de liaisons et de stratégies BizTalk
Cette section explique comment exporter une application, des liaisons ou des stratégies BizTalk. Vous pouvez exporter tout ou partie des artefacts contenus dans une application BizTalk, ou uniquement ses liaisons ou stratégies. L'exportation d'une application génère un fichier Windows Installer (.msi) contenant les artefacts qu'elle contient et que vous sélectionnez pour l'exportation. L'exportation de liaisons ou de stratégies génère un fichier .xml des liaisons ou stratégies. Pour plus d’informations sur ce processus, consultez [ce qui se produit lorsque artefacts sont exportées](../core/what-happens-when-artifacts-are-exported.md).  
  
 Vous pouvez importer le fichier .msi d'une application dans un autre groupe BizTalk pour y créer une nouvelle application contenant les artefacts de l'application. Vous pouvez importer un fichier .xml de liaison ou de stratégie dans une autre application BizTalk application afin d'utiliser les liaisons ou stratégies. Décrit comment importer des artefacts dans [l’importation des Applications BizTalk, les liaisons et les stratégies](../core/importing-biztalk-applications-bindings-and-policies.md).  
  
> [!IMPORTANT]
>  Stockez les fichiers de liaison dans un emplacement sécurisé, car ils peuvent contenir des données critiques telles que des informations de connexion et de configuration.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md)  
  
-   [L’exportation des liaisons](../core/exporting-bindings6.md)  
  
-   [Comment exporter une stratégie](../core/how-to-export-a-policy.md)