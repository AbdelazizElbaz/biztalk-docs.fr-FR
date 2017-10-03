---
title: "Création de Services Web et méthodes Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, schemas
- orchestrations, naming conventions
- Web services, naming conventions
- schemas, Web services
ms.assetid: a7c47000-501c-47b1-bafa-82370585c1db
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74065489e427ae0612897f1f333e3c8e154a535f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-web-services-and-web-methods"></a>Création de Services Web et méthodes Web
Lorsque vous publiez des schémas en tant que service Web, vous contrôlez la création de services et de méthodes Web dans l'Assistant Publication de services Web BizTalk. Vous pouvez renommer la description du service Web, le service Web et la méthode Web à l'intérieur de l'arborescence disponible sur la page des services Web. Vous pouvez ajouter et supprimer des services et des méthodes Web. L'Assistant utilise les noms d'élément racines des schémas de demande sélectionnés comme noms de paramètre d'entrée. La valeur de retour de la méthode Web renvoie le schéma de réponse.  
  
> [!NOTE]
>  Les clients Web ASP.NET peuvent changer la signature de la méthode Web en combinant les paramètres d'entrée et de sortie du même type. Par exemple, un client Web ASP.NET peut changer une méthode BizTalk Web à partir de **string myService (partie de la chaîne)** à **void myService (partie de la chaîne ref)**.  
  
> [!NOTE]
>  Si votre réception port est défini en tant qu’unidirectionnel, le type de réponse de la méthode Web est **void** et aucune information n’est retournée au client Web. L'adaptateur SOAP et l'orchestration ne renvoient pas d'exceptions levées au client Web.  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a>Conventions d'affectation de noms des services Web pour les orchestrations publiées  
 L'Assistant Publication de services Web BizTalk génère des noms de fichier de service Web (.asmx) basés sur la description des services Web que vous définissez dans la page de service Web. Le tableau suivant affiche les valeurs par défaut pour les noms de fichier de service Web.  
  
|Service Web généré|Nom de fichier|  
|---------------------------|---------------|  
|BizTalkWebService|Nom du projet de service Web Visual Studio|  
|WebService1|Nom de fichier du service Web (.asmx)|  
|WebMethod1|Nom de méthode Web|  
  
 Le service Web généré ne reflète pas les noms des nœuds restants.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de schémas comme un Service Web](../core/publishing-schemas-as-a-web-service.md)   
 [Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier des schémas en tant qu’un Service Web](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)