---
title: "Étendre le Concepteur d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f26b825b-ebab-4dac-b7ed-0608c79e146a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb44c851258cc623cf991a0b2be5c18d58e59770
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-itinerary-designer"></a>Étendre le Concepteur d’itinéraire
Le Concepteur d’itinéraire est un langage spécifique à un domaine visuel (DSL) pour Microsoft Visual Studio qui permet la modélisation graphique des itinéraires pour une utilisation avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Le concepteur expose plusieurs points d’extension pour laquelle les développeurs peuvent écrire des extensions personnalisées pour activer les nouvelles fonctionnalités et/ou de nouvelles options de configuration.  
  

  
 **Création d’un exportateur d’itinéraire personnalisé**  
  
 Permet à l’architecture du Concepteur d’itinéraire pour la création des exportateurs de modèle personnalisé qui sérialisent et conserver les données dans un modèle d’itinéraire.  
  
 **Création d’une extension personnalisée pour un Service de messagerie**  
  
 L’architecture du Concepteur d’itinéraire vous permet de créer des extensions personnalisées pour les éléments de modèle de Service de l’itinéraire qui peuvent être utilisés pour ajouter des propriétés pour le jeu de propriétés pour une utilisation par les Services de messagerie.  
  
 Pour obtenir un exemple montrant comment créer un extendeur de ce type, consultez [l’installation et l’exécution de l’exemple d’extensibilité de concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).  
  
 **Création d’une extension personnalisée pour un Service d’Orchestration d’itinéraire**  
  
 L’architecture du Concepteur d’itinéraire vous permet de créer des extensions personnalisées pour les éléments de modèle de Service de l’itinéraire qui peuvent être utilisés pour ajouter des propriétés pour le jeu de propriétés pour une utilisation par des services d’orchestration d’itinéraire.  
  
 Pour obtenir un exemple montrant comment créer un extendeur de ce type, consultez [l’installation et l’exécution de l’exemple d’extensibilité de concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).  
  
 **Création d’un extendeur de programme de résolution personnalisé**  
  
 L’architecture du Concepteur d’itinéraire vous permet de vous permet de créer des extensions personnalisées pour la configuration des programmes de résolution personnalisés. Ces extensions fournissent une interface graphique pour configurer les paires nom-valeur dans la chaîne de connexion de programme de résolution, qui correspondent aux propriétés de la classe d’extendeur de programme de résolution spécifique.  
  
 Pour obtenir un exemple montrant comment créer un extendeur de ce type, consultez [l’installation et l’exécution de l’exemple d’extensibilité de concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).  
  
 **Création d’un fichier Manifest pour les propriétés de l’adaptateur personnalisé**  
  
 Lorsque vous créez un fournisseur de l’adaptateur personnalisé, vous devez également fournir la prise en charge de concepteur pour le fournisseur de l’adaptateur pour les extendeurs de programme de résolution qui affichent une propriété de configuration de point de terminaison. Pour activer la prise en charge de concepteur, il est nécessaire créer un fichier de manifeste de fournisseur de carte.  
  
 Le fichier de manifeste du fournisseur adaptateur définit les propriétés associées à un fournisseur de l’adaptateur spécifique, leurs types, descriptions et l’assembly dans lequel ils se trouvent. Ces fichiers manifestes doivent être placés dans le même dossier que les fichiers binaires du Concepteur d’itinéraire (par exemple, Microsoft.Practices.Itineary.DslPackage.dll) avec un nom unique (par exemple, FTPPropertyManifest.xml).  
  
 Voici une instance de la référence d’un fichier manifeste de fournisseur d’adaptateur ; les fichiers manifeste personnalisés doivent être structurées de la même manière.  
  
```xml  
\<?xml version="1.0" encoding="utf-8" ?>  
<adapterPropertyManifest adapterName="FTP">  
     <aliases>  
          <alias name="globalPropertySchemas" value="Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     </aliases>  
     <properties>  
          <property name="UserName" type="FTP.UserName" description="The user name for the connection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="Password" type="FTP.Password" description="The password for the conection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="MaxConnections" type="FTP.MaxConnections" description="The maximun number of connections." assembly="globalPropertySchemas" />  
          <property name="EventArgs" type="System.EventArgs" assembly="mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
     </properties>  
</adapterPropertyManifest>  
```  
  
 **Création d’un extendeur de filtre personnalisé**  
  
 L’architecture du Concepteur d’itinéraire vous permet de créer des extensions personnalisées pour la configuration des filtres personnalisés. Ces extensions fournissent une interface graphique pour configurer les paires nom-valeur dans la chaîne de connexion de filtre, qui correspondent aux propriétés de la classe d’extendeur filtre spécifique.  
  
-   / Samples/concepteur extensibilité Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample  
  
-   / Samples/concepteur extensibilité Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample  
  
 **Création de règles de Validation personnalisées**  
  
 La dernière extension importantes introduite par le Concepteur d’itinéraire est un mécanisme de validation qui vous permet en externe, par rapport à un langage spécifique à un domaine (DSL), spécifier et implémenter des règles de validation du modèle. Le mécanisme « raccorde » l’infrastructure de validation DSL et est activé lorsque l’utilisateur clique sur **Validate** ou **valider tous les** dans le menu contextuel d’un modèle. Il appelle l’infrastructure DSL **DslCommandSet** objet qui, à son tour, appelle le moteur de validation dans le Concepteur d’itinéraire.  
  
 Le **ValidationEngine** classe effectue la validation d’élément de modèle à l’aide du bloc d’Application Enterprise Library Validation et consigne les erreurs de validation dans la fenêtre liste d’erreurs dans l’IDE de Microsoft Visual Studio. La validation doit être effectuée pour chaque type d’élément dans un modèle est définie dans le fichier de configuration Enterprise Library. Le fichier est nommé Ruleset.config et se trouve dans le dossier binaire dans lequel se trouvent tous les binaires de concepteur d’itinéraire. L’exemple suivant est un fragment du fichier de configuration et inclut les deux règles de validation (nommés validateurs) pour le **UddiResolver** extendeur, un pour le **ServerUrl** propriété et une pour le  **ServiceKey** propriété.  
  
```  
\<!--   
UddiResolver  
-->  
<type assemblyName="Microsoft.Practices.Services.Extenders.Resolvers.UDDI"  
 name="Microsoft.Practices.Services.Extenders.Resolvers.UDDI.UddiResolver">  
<ruleset name="Menu">  
<properties>  
<property name="ServerUrl">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServerUrl not null validator"/>  
</property>  
<property name="ServiceKey">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServiceKey not null validator"/>  
</property>  
</properties>  
</ruleset>  
</type>  
```  
  
 Chaque règle identifie le programme de validation qui implémente la règle. Le Concepteur d’itinéraire est fourni avec un grand ensemble de classes de validateur. Ils sont regroupés dans le projet Microsoft.Practices.Modeling.Validation dans le dossier binaire du concepteur.  
  
 Le résultat final de l’utilisation de ce mécanisme de validation est que les utilisateurs peuvent modifier la façon dont les modèles sont validés en modifiant les règles fournies et les validateurs ou en ajoutant leurs propres règles et les validateurs de concepteurs itinéraire. Cela peut être effectuée sans ouverture, la modification, la reconstruction et redéployer le DSL en effectuant le des deux étapes suivantes :  
  
1.  Créez une classe du programme de validation et le placer dans une bibliothèque dans le dossier binaire dans lequel le **Microsoft.Practices.Modeling.Validation.dll** se trouve la bibliothèque.  
  
2.  Ajouter des entrées dans le fichier Rules.config pour définir la propriété de quelle classe d’élément de modèle le validateur doit être appliqué.