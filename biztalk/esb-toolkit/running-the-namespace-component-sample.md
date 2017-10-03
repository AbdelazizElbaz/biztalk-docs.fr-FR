---
title: "Exécution de l’exemple de composant de Namespace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f334a8-06de-4a56-a41a-3df088bf4a72
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fc142ca70971f023e491dbdeee693a8d41c42fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-namespace-component-sample"></a>L’exemple de composant de Namespace en cours d’exécution
L’exemple d’application Namespace composant contienne quatre paires de ports d’envoi / l’emplacement de réception. Chaque paire représente un test. Les quatre tests sont les suivants :  
  
-   **Ajouter à pass-through**. Ce test ajoute un espace de noms dans un document de message XML et écrit le message directement dans un fichier afin que vous puissiez voir le nouvel espace de noms. Le fichier d’entrée pour ce test est TEST_Add_to_PassThrough.0000.ns.xml. Ce test utilise le **NamespaceSampleReceivePipeline** qui contient un **AddNamespace** composant.  
  
-   **Ajouter à supprimer**. Ce test ajoute un espace de noms à un message de document XML, puis la supprime. Il écrit ensuite le message directement dans un fichier. Le fichier d’entrée pour ce test est TEST_ Add_to_Remove.0000.ns.xml. Ce test utilise le **NamespaceSampleReceivePipeline** qui contient un **AddNamespace** composant et le **NamespaceSampleSendPipeline** qui contient un **RemoveNamespace** composant.  
  
-   **Pass-through pour supprimer**. Ce test supprime tous les espaces de noms à partir d’un message de document XML et écrit le message directement dans un fichier afin que vous pouvez le vérifier. Le fichier d’entrée pour ce test est TEST_PassThrough_to_Remove.0000.ns.xml. Ce test utilise le **NamespaceSampleSendPipeline** qui contient un **RemoveNamespace** composant.  
  
-   **Ajouter par le biais d’Extraction pour pass-through**. Ce test extrait le **OrderDetails** élément d’un document XML de document message et écrit un message qui contient cet élément directement dans un fichier. Le fichier d’entrée pour ce test est TEST_AddViaExtraction_to_PassThrough.0000.ns.xml. Ce test utilise le **NamespaceSampleReceivePipeline** qui contient un **AddNamespace** composant portant le **ExtractionNodeXPath** propriété la valeur **/ CanonicalOrder/OrderDetails** (n’importe quel XPath valide qui retourne un élément est suffisante pour cette propriété).  
  
 Les emplacements de réception sous-jacent dans l’exemple d’application ont des masques de fichier qui sont appropriées pour chacun des types de tests, et le filtre de ports d’envoi sur le nom de port de réception. Par conséquent, pour exécuter un test, vous supprimez simplement le message correctement nommé dans le dossier d’entrée. L’exemple d’application exécute le test et dépose le message mis à jour dans le dossier de sortie à l’aide d’un nom approprié pour le test en cours, y compris l’ID du Message.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Exécution des Tests de composant de Namespace](../esb-toolkit/running-the-namespace-component-tests.md)  
  
-   [Comment l’ajouter Namespace exemple fonctionne](../esb-toolkit/how-the-add-namespace-sample-works.md)  
  
-   [Fonctionnement de l’exemple de Namespace supprimer](../esb-toolkit/how-the-remove-namespace-sample-works.md)