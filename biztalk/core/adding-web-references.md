---
title: "Ajout de références Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- orchestrations, BPEL
- Web services, ports
- orchestrations, exporting
- Web services, projects
- Web services, references
- projects, Web services
ms.assetid: 7e40f215-f11a-4151-bcc6-e107bf36b6f6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cbf8cd4c21009190fc459312467656410dc663a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="adding-web-references"></a>Ajout de références web
Avant de pouvoir ajouter un port Web, vous devez ajouter une référence Web à votre projet BizTalk. Une référence Web est une description d'un service Web qui est disponible pour votre projet. Lorsque vous ajoutez une référence Web à votre projet, le projet BizTalk crée une orchestration Web type de port, les types de messages Web Reference.map (fichier de mappage), Reference.odx (fichier d’orchestration), \< *WebService*\>. disco (fichier de découverte) et \< *WebService*\>.wsdl (fichier Web Service Description Language) à votre projet. Si le fichier WSDL contient des types de messages Web de schéma, le projet BizTalk ajoute Reference.xsd à votre projet.  
  
 Une référence Web inclut les éléments suivants :  
  
-   une URL (Uniform Resource Locator) pour le service Web ;  
  
-   un fichier WSDL qui contient des informations sur le service, telles que les méthodes, ports et types de messages disponibles ;  
  
-   un mappage de référence (Reference.map).  
  
 Lorsque vous ajoutez une référence Web, toutes les méthodes Web pour ce service Web doivent être compatibles avec BizTalk Server. Il est impossible de spécifier des attributs conditionnels pour des méthodes Web spécifiques dans un service Web.  
  
 Vous ajoutez une référence Web à votre projet à l’aide de la **ajouter une référence Web** boîte de dialogue. Pour plus d’informations sur l’ajout de références Web, consultez [à l’aide de Visual Studio](../core/using-visual-studio.md).  
  
 Si vous envisagez d'exporter votre orchestration à l'aide du processus d'exportation BPEL (Business Process Execution Language), vous ne pouvez pas référencer une référence Web d'un projet existant. Si vous effectuez cette opération, le processus d'exportation BPEL génère automatiquement un second fichier WSDL et vous perdez vos informations de liaison.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Ports Web](../core/creating-web-ports.md)   
 [Consommation des services web](../core/consuming-web-services.md)