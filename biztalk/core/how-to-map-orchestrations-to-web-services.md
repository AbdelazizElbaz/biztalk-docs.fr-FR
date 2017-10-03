---
title: Comment mapper des Orchestrations aux Services Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, Web services
- BizTalk Web Services Publishing Wizard, naming conventions
- Web services, orchestrations
- orchestrations, naming conventions
- Web services, naming conventions
ms.assetid: e6a58978-c81c-49f3-9428-9bff60f1ded7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f101a9a9ab6c0d99e9895433401de08b1380d1e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-orchestrations-to-web-services"></a>Comment mapper des Orchestrations aux Services Web
Une orchestration peut avoir plusieurs ports de réception. À l'aide de l'Assistant Publication de services Web BizTalk, vous sélectionnez les ports de réception à publier en tant que services Web. L'Assistant crée un seul service Web (fichier .asmx) pour chaque port de réception. L'Assistant peut également créer un service Web pour tous les ports de réception s'il s'agit du même type de port de réception (unidirectionnel ou requête-réponse). Les opérations deviennent des appels de fonction. Chaque opération au niveau du port de réception devient une méthode Web. Les opérations de requête deviennent des paramètres d'entrée. Les opérations de réponse deviennent des types de retours.  
  
 Si les opérations de demande et de réponse sont du même type de message Web, le paramètre d’entrée devient un **ref** et le type de retour est **void**. Les clients Web ASP.NET peuvent changer la signature de la méthode Web en combinant les paramètres d'entrée et de sortie du même type. Par exemple, un client Web ASP.NET peut changer une méthode BizTalk Web à partir de **string myService (partie de la chaîne)** à **void myService (partie de la chaîne ref)**.  
  
 Les types de messages d'opération définissent les signatures de méthode Web. Chaque partie de type de message est un paramètre dans la méthode Web.  
  
## <a name="message-type-part-names-and-target-namespaces"></a>Noms des parties de type de message et espaces de noms cibles  
 Schémas de document et les classes définies par l’utilisateur avec **XmlRootAttribute** spécifié sont des parties de type que vous ont défini les espaces de noms cible de message. Schémas EDI, les classes définies par l’utilisateur sans **XmlRootAttribute** spécifiés et les types intégrés, tels que **System.String** sont des parties du message de type sans les espaces de noms cible défini.  
  
|Si le nom de la partie de type de message a un|Nom de paramètre utilisé|  
|-----------------------------------------|-------------------------|  
|Espace de noms cible défini|Nom d'élément racine|  
|Aucun espace de noms cible défini|Nom de la partie de type de message|  
  
> [!NOTE]
>  Lorsqu'un type de message à parties multiples est utilisé pour le message de réponse, l'Assistant Publication de services Web BizTalk utilise la première partie de message pour la valeur de retour et les parties de message restantes sont utilisées en tant que paramètres de sortie.  
  
## <a name="orchestrations-with-multiple-operations"></a>Orchestrations avec plusieurs opérations  
 Si votre orchestration a plusieurs opérations, vous devez concevoir vos orchestrations pour avoir un seul port de réception à la place de plusieurs ports de réception. Cette conception empêche l'Assistant Publication de services Web BizTalk de créer plusieurs fichiers de service Web (.asmx) et fonctionne uniquement lorsque toutes les opérations ont le même modèle d'appel : toutes les opérations unidirectionnelles ou toutes les opérations de requête-réponse. Un port de réception unique ne peut pas contenir à la fois des opérations unidirectionnelles et de requête-réponse.  
  
> [!NOTE]
>  L'Assistant Publication de services Web BizTalk affiche des ports de réception publics. Les ports de réception publics sont des types de ports avec un modificateur de type public. Vous pouvez publier uniquement des ports publics en tant que service Web. Le type de port par défaut est interne.  
  
> [!NOTE]
>  Si votre réception port est défini en tant qu’unidirectionnel, le type de réponse de la méthode Web est **void** et aucune information n’est retournée au client Web. Les exceptions générées par l'adaptateur SOAP ou une orchestration ne sont pas renvoyées au client Web.  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a>Conventions d'affectation de noms des services Web pour les orchestrations publiées  
 L’Assistant de publication des Services Web BizTalk génère des noms de fichier (.asmx) de service Web en fonction de l’espace de noms d’orchestrations, suivi d’un trait de soulignement (_), le nom de type, suivi par un trait de soulignement (\_) et le suivi du nom de la réception port. Un trait de soulignement (\_) remplace un des éléments qui contiennent des points. Le nom du service Web a toujours le nom du port ajouté.  
  
 Le tableau suivant montre comment l'Assistant Publication de services Web BizTalk génère des noms de service Web.  
  
|Orchestration(s) avec port(s) Web|Nom de service Web généré|  
|-------------------------------------------|--------------------------------|  
|Une seule orchestration avec un seul port Web|orchestration1_port1.asmx|  
|Une orchestration avec deux ports Web|orchestration1_port1.asmx et orchestration1_port2.asmx|  
|Deux orchestrations avec un port Web chacune|orchestration1_port1.asmx et orchestration2_port2.asmx|  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’une Orchestration en tant que Service Web](../core/publishing-an-orchestration-as-a-web-service.md)   
 [Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier une Orchestration en tant que Service Web](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)