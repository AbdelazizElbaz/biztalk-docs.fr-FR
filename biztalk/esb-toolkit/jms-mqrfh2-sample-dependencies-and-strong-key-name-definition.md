---
title: "Nom de définition de dépendances JMS MQRFH2 exemple et une clé forte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3a5cdce-dcdf-48df-91a5-8cf2afce9255
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f3e2f76a972f851322f82f2e89b285db907d799
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="jms-mqrfh2-sample-dependencies-and-strong-key-name-definition"></a>JMS MQRFH2 exemple dépendances et la définition de nom fort de la clé
Le projet Visual Studio ESB. JMS. PipelineComponents varie selon le dossier suivant :  
  
-   \<Répertoire d’Installation de BizTalk Server\>. Ce dossier permet d’accéder aux espaces de noms suivants :  
  
    -   **Microsoft::BizTalk::message::Interop**  
  
    -   **Microsoft::BizTalk::Component::Interop**  
  
## <a name="the-strong-name-key-definition"></a>La définition de clé de nom fort  
 En règle générale, la définition de clé de nom fort se trouve dans le fichier AssemblyInfo.cpp. Toutefois, cela serait en conflit avec le fichier de manifeste C++ qui le compilateur ajoute à l’assembly une fois qu’il lit le fichier AssemblyInfo.cpp. Ce conflit empêcherait toute tentative visant à placer le fichier dans le global assembly cache. Au lieu de cela, l’éditeur de liens détermine le fichier de clé de nom fort en spécifiant le fichier de clé à... /.. /.. /.. /.. /.. / Keys/Microsoft.Practices.ESB.snk. Pour modifier cette valeur, accédez au paramètre de l’option suivante :  
  
 ESB. JMS. Schémas  
  
 Projet \-  
  
 \--Propriétés  
  
 \-: Propriétés de configuration  
  
 \----L’éditeur de liens  
  
 \-----Avancé  
  
 \------Fichier de clé  
  
> [!NOTE]
>  Si vous construisez un composant de Pipeline JMS, vous devez modifier le fichier AssemblyInfo.cpp pour supprimer toutes les références au fichier de clé de nom fort, comme décrit précédemment. Après quoi, modifier le **fichier de clé** option dans les propriétés avancées de l’éditeur de liens pour spécifier le chemin d’accès et le nom du fichier de clé de nom fort.