---
title: "À l’aide de l’authentification unique efficacement dans la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, process management solutions
- SSO, configuration values
- caching, configuration values [SSO]
- SSO, caching
- process management solution tutorial, SSO
ms.assetid: 39fbc42d-caa4-4003-a13b-5cde578eb5e1
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99575e54b887124bfa4c33fc5257cd057ea818fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-sso-efficiently-in-the-business-process-management-solution"></a>À l’aide de l’authentification unique efficacement dans la Solution gestion des processus d’entreprise
Comme la solution orientée services, la solution de gestion des processus d'entreprise utilise le service d'authentification unique de l'entreprise (SSO) pour stocker les valeurs de configuration, telles que le nombre d'étapes de traitement d'une commande. Elle utilise le magasin des secrets car il est présent lorsque BizTalk est installé, SSO met en cache les informations de configuration afin que les valeurs soient immédiatement disponibles et il peut protéger des informations, telles que des chaînes de connexion à la base de données et des mots de passe. Pour toutes ces raisons, le magasin des secrets est un bon emplacement pour les informations de configuration, même si les authentifications uniques ne sont pas utilisées pour gérer les connexions aux applications principales.  
  
 Pour réduire la latence, la solution utilise un cache local pour les valeurs de configuration. La solution actualise le cache toutes les cinq minutes.  
  
 Cette rubrique décrit le mécanisme de mise en cache utilisé par la solution. Celle-ci adopte une approche légèrement différente de celle de la solution orientée services pour la mise en cache des valeurs SSO. Pour obtenir une description de la façon dont la solution orientée services met en cache les valeurs de l’authentification unique, consultez [à l’aide de l’authentification unique efficacement dans la Solution orientée services](../core/using-sso-efficiently-in-the-service-oriented-solution.md).  
  
## <a name="caching-configuration-values-locally"></a>Mise en cache locale des valeurs de configuration  
 La solution de gestion des processus d'entreprise utilise les propriétés d'un objet singleton pour fournir un accès aux valeurs SSO.  
  
> [!NOTE]
>  Rappelez-vous qu'un objet singleton est un objet qui ne peut avoir qu'une seule instance. Pour plus d’informations sur les objets singleton et leur création en c#, consultez [http://go.microsoft.com/fwlink/?LinkId=58806](http://go.microsoft.com/fwlink/?LinkId=58806).  
  
 Dans la solution, une orchestration récupère d'abord l'objet singleton, puis référence les valeurs à l'aide des propriétés de l'objet. Voici le code à partir de la **OrderManager** orchestration :  
  
```  
configData = Microsoft.Samples.BizTalk.SouthridgeVideo.Utilities  
                .SsoConfigHelper.Singleton;  
numStages = configData.TotalStages;  
```  
  
 L’orchestration appelle la **Singleton** méthode sur le **SsoConfigHelper** objet pour obtenir l’accès à une copie de l’objet. Avec l’objet, l’orchestration récupère le nombre d’étapes de traitement, **TotalStages**.  
  
 La solution suit une méthode courante de création d’un singleton : rendez le constructeur privé, que l’objet de créer une instance d’elle-même et assigner à une variable privée et, par une méthode ou une propriété, fournir un accès à la valeur de cette variable. Le **SsoConfigHelper** objet utilise une propriété, **Singleton**, pour fournir l’accès à la copie unique de lui-même.  
  
> [!NOTE]
>  Le **SsoConfigHelper** objet utilise un constructeur statique pour obtenir les valeurs initiales du cache SSO et définir le mécanisme d’actualisation. Comme il est impossible d'appeler un constructeur statique, celui-ci conserve la conception de l'objet singleton. Pour plus d’informations sur les constructeurs statiques, consultez [http://go.microsoft.com/fwlink/?LinkId=59142](http://go.microsoft.com/fwlink/?LinkId=59142).  
  
 Tous les objets référencés directement ou indirectement par une orchestration doivent être sérialisables. Pour plus d’informations, consultez « Sérialisation » dans [persistance et le moteur d’Orchestration](../core/persistence-and-the-orchestration-engine.md). Bien que le **SsoConfigHelper** objet est obligatoirement sérialisable, si le moteur met en attente l’orchestration, lorsque lorsqu’il est toujours utilise l’instance actuelle de l’objet unique. Pour plus d’informations sur la sérialisation et de variables de BizTalk Server, consultez [les Types de variables d’Orchestration](../core/orchestration-variable-types.md).  
  
> [!NOTE]
>  Toutes les méthodes publiques sur l'objet de la solution orientée services sont statiques. Aussi, l'orchestration n'a pas besoin d'affecter une instance à une variable et la classe n'a pas besoin d'être sérialisée.  
  
 Le **SsoConfigHelper** objet utilise les mêmes mécanismes pour récupérer et actualiser les valeurs de configuration comme la solution orientée services. Le même modèle de verrouillage est également utilisé. Pour plus d’informations sur ces mécanismes, consultez [à l’aide de l’authentification unique efficacement dans la Solution orientée services](../core/using-sso-efficiently-in-the-service-oriented-solution.md) et le code source pour **SsoConfigHelper**.  
  
 Comme l’authentification unique sur la mise en cache effectuée dans la solution orientée services, la solution de gestion des processus métier implémente la **IPropertyBag** de l’interface à partir de la **Microsoft.BizTalk.SSOClient.Interop** espace de noms pour stocker les valeurs. La solution gestion des processus d’entreprise utilise un **HybridDictionary** objet plutôt qu’un **NameValueCollection** objet.  
  
 Contrairement à la solution orientée services, la solution de gestion des processus d'entreprise expose un objet dont les propriétés correspondent aux données de configuration. Ceci évite à l'orchestration de devoir traiter les différences dans les types de messages.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)