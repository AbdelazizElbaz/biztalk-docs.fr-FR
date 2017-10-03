---
title: "Glossaire de l’accélérateur HL7 dans BizTalk Server | Documents Microsoft"
description: "Termes et définitions de connaître et d’apprendre à utiliser BizTalk Accelerator pour HL7 de courantes"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffb9c18a-5fe5-448f-b115-0973e9d12952
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d90a98fd1c30aed5bb38cca99774f610a59dedaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>Glossaire
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 utilise les termes et définitions suivants.

## <a name="a"></a>Un    
 **artefact**    
 Les artefacts qui composent le vote HL7 V3.0 sont les livrables résultant de la découverte, l’analyse et les activités de conception menant à la création de spécifications de message.  
  
 Dans les normes HL7 V3.0, les composants qui composent la documentation sont des artefacts. Cela inclut les animations, les rôles d’application, déclencher des événements, spécifications de modèle d’informations de domaine Message (D-MIMs), spécifications de modèle d’informations Message affiné (MIMs-R), Description du Message hiérarchique specificatins(HMDs), types de messages, et les interactions.  
  
 **identificateur d’artefact**    
 Un comité technique soumet ainsi que chaque artefact un identificateur unique affecté par la concaténation de la sous-section code de domaine et chaque artefact, un nombre à 6 chiffres non significatifs, un code de domaine à 2 chiffres et un numéro de version de 2 chiffres.  

## <a name="c"></a>C
  
 **cardinalité**    
 La propriété d’un élément de données (le nombre de fois où qu'un élément de données peut se répètent dans une seule occurrence d’une vue de l’objet) ou de la colonne dans la Description du Message hiérarchique (nombre minimal et maximal d’occurrences de l’élément de message). Consultez la Description du Message hiérarchique.  
  
## <a name="d"></a>D   
 **domaine**    
 1. Le problème ou l’objet à être traités par un ensemble de messages de HL7 ou par un système (« domaine d’application »). Une zone particulière d’intérêt de soins de santé. 
 2. Le jeu de valeurs possibles d’un type de données, un attribut ou un composant de type de données. Consultez le domaine du vocabulaire. 
 3. Un groupe d’intérêt dans HL7, telles que pharmacie, laboratoire, Patient Administration.  
  
## <a name="e"></a>E 
 **événement**    
 1. Impulsion qui entraîne un changement d’état importantes d’un objet. Signal qui appelle le comportement d’un objet. Consultez l’événement déclencheur. 
 2. Une valeur de domaine de vocabulaire pour humeur.  
  
 
## <a name="h"></a>H
**Description du Message hiérarchique (HMD)**    
 Spécification des champs exactes d’un message et leur regroupement, séquence, caractère facultatif et de la cardinalité. Contient des types de message pour un ou plusieurs des interactions ou représente un ou plusieurs types courants de l’élément message. Il s’agit de la structure normative principale pour les messages de HL7.  
  
## <a name="m"></a>M  
 **obligatoire**    
 Une colonne dans la Description de Message hiérarchique (HMD). Si l’inclusion d’un attribut obligatoire, tous les éléments de message en fonction de cet attribut doit contenir une valeur non null, ou ils doivent avoir une valeur par défaut n’est pas null.  
  
  
 **Message**    
 Un ensemble d’informations communiquées à partir d’une application vers un autre. Consultez le type de message et l’instance de message.  
  
 **Infrastructure de développement de message (MDF)**    
 Collection de modèles, des méthodes et des outils qui composent la méthodologie pour spécifier les messages HL7 V3.0. Les développeurs des normes HL7 utilisent cette infrastructure. Le Guide V3.0 résume le contenu de la méthode.  
  
 **élément message**    
 Une unité de structure dans un type de message.  
  
 **type d’élément de message**    
 Une partie d’un type de message qui décrit un des éléments du message.  
  
 **instance de message**    
 Un message mis en forme d’une transmission spécifique. Le même type de message peut décrivent deux messages identifier avec la même interaction et encore varient dans l’instance en raison des variations de valeurs, présence ou absence de données envoyées et cardinalités différents des collections. Dans le cas contraire, les messages identiques peuvent être des instances différentes si elles sont envoyées à des moments différents, ou par un autre expéditeur.  
  
 **charge utile du message**    
 Données contenues dans un message.  
  
 **type de message**    
 L’organisation des éléments de message qui est spécifiée dans une Description de Message hiérarchique (HMD). Chaque type de message est communiqué dans le cadre d’un ou plusieurs des interactions dans le modèle d’interaction. En effet, un type de message constitue un ensemble de règles permettant de construire un message donné un ensemble spécifique de données d’instance. Il définit également les règles pour l’analyse d’un message pour récupérer les données d’instance. Le type de message est indépendant de la spécification de la technologie de mise en œuvre, afin que si les mêmes données sont envoyées à l’aide du même type de message et les spécifications de technologie de mise en œuvre différents, le type de message peut être transcription d’un à l’autre.  

## <a name="p"></a>P  
 **propriété**    
 N’importe quel attribut, association, méthode ou modèle d’état définis pour une classe ou un objet. Dans un HMD, la colonne qui indique le nom du nom de rôle de classe, un attribut ou association tel qu’il apparaît dans le modèle d’informations de référence (RIM).  

## <a name="r"></a>R  
 **Modèle d’informations de référence (RIM)**    
 Le modèle d’informations HL7 à partir de toutes les autres informations dérivent des modèles (par exemple, R-MIMs) et les messages.  
  
 **Modèle d’informations soigné Message (MIM-R)**    
 Une structure d’informations qui représente la configuration requise pour un ensemble de messages. Un sous-ensemble de contraint de l’anneau qui peut contenir des classes supplémentaires qui sont clonés à partir des classes RIM. Contient les types de classes, des attributs, des associations et des données qui sont nécessaires pour prendre en charge un ou plusieurs messages Description hiérarchique (HMDs). Un seul message peut être représentée sous une voie particulière via les classes au sein d’une R-MIM.  

## <a name="s"></a>S  
 **scénario**    
 En langage UML (Unified Modeling), « un seul chemin d’accès d’exécution au sein d’un cas d’usage unique ». Une déclaration d’événements définie comme une séquence d’interactions pertinentes dans les soins de santé. Le scénario fournit un ensemble d’interactions le comité de modélisation s’attend à se produisent généralement dans le domaine. En règle générale, un diagramme de séquence est construit pour afficher un groupe d’interactions pour un seul scénario. Chaque scénario est affiché comme un sous-ensemble du modèle d’interaction.  
  
 **schéma**    
 1. Une présentation sous forme de schéma, une structure ou un plan. 
 2. Un ensemble d’exigences qui doivent être remplies dans l’ordre d’un document ou d’un jeu de données pour être une expression valide dans le contexte de cette grammaire. Un schéma XML est une spécification de langage SGML (Standard Generalized Markup Language) de la structure d’un document ou un ensemble de données.

## <a name="next-steps"></a>Étapes suivantes
[Parties - Explorateur de Configuration de BTAHL7](parties-tab.md)  
[Paramètres globaux - Explorateur de Configuration de BTAHL7](global-settings-tab.md)  
[Aide des UI zone boîte de dialogue Propriétés du Transport MLLP](mllp-transport-properties-dialog-box-ui-help.md)