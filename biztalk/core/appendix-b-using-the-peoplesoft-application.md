---
title: "Annexe b : à l’aide de l’Application PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PeopleSoft, using
- using PeopleSoft application
ms.assetid: 36475836-1d23-4bb4-a3c1-cdd3fff28476
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ff5c7b2b15c709064174371f1fcab9beb95e42d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-b-using-the-peoplesoft-application"></a>Annexe b : à l’aide de l’Application PeopleSoft
Cette section décrit l'utilisation de différentes composantes de PeopleSoft qui peuvent être utiles pour tester votre orchestration.  
  
 Lorsque vous utilisez PeopleSoft pour les ports de réception, vous devez utiliser PeopleTools pour créer un document XML. L'interaction avec PeopleSoft ne requiert pas de configuration spéciale. Pour un événement, vous devez être en mesure d’accéder à un **http\\\\:\<hôte > :\<port >** pour écouter les événements à partir de PeopleSoft. Si un hôte et un port ne sont pas accessibles, vous pouvez définir un hôte et un port HTTP spécifiques en configurant PeopleSoft Integration Broker.  
  
 Pour terminer le test d’un PeopleSoft port de réception, [génération ou schéma XML dans PeopleSoft](../core/generating-xml-or-schema-in-peoplesoft.md) explique comment déclencher un événement PeopleSoft via la modification dans un environnement PeopleSoft. La modification active un fichier XML qui est envoyé au dossier que vous définissez dans l'orchestration pour être surveillé.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Génération XML ou schéma dans PeopleSoft](../core/generating-xml-or-schema-in-peoplesoft.md)  
  
-   [Création d’un Port et l’hôte de HTTP PeopleSoft](../core/creating-a-peoplesoft-http-host-and-port.md)