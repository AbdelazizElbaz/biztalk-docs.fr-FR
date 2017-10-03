---
title: "Exécution des Tests de composant de Namespace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13768608-ade6-44c0-897f-d417c3408302
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae865e91fd6ff796cb870c71840bde8a95831e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-namespace-component-tests"></a>Exécution des Tests de composant de Namespace
La procédure suivante montre comment vous pouvez exécuter les quatre scénarios de test de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemple de composant de Namespace.  
  
 **Pour exécuter le composant Namespace exemples de scénarios de test**  
  
1.  Avant d’exécuter cet exemple pour la première fois, assurez-vous que la réception emplacement et envoyer une URL de port pointant vers les sous-dossiers appropriés dans les fichiers de distribution source. Spécifiez le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In pour l’emplacement de réception et le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out pour l’URL de port d’envoi.  
  
2.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
3.  Faites une copie du fichier nommé TEST_Add_to_PassThrough.0000.ns.xml (situé dans le sous-dossier \Source\Samples\Namespace\Test\Data\ de votre dossier d’installation ESB) et renommez la copie en supprimant le préfixe « TEST_ ».  
  
4.  Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.  
  
5.  Récupère le message, l’architecture ESB ajoute un espace de noms et dépose le message mis à jour dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out. Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.  
  
6.  Maintenant, exécutez le deuxième test. Faites une copie du fichier nommé TEST_Add_to_Remove.0000.ns.xml et renommez-la en supprimant le préfixe « TEST_ ».  
  
7.  Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.  
  
8.  L’architecture ESB récupère le message lui ajoute un espace de noms, supprime le nouvel espace de noms et dépose le message mis à jour dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out. Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.  
  
9. Maintenant exécuter le test de tiers. Faites une copie du fichier nommé TEST_PassThrough_to_Remove.0000.ns.xml et renommez-la en supprimant le préfixe « TEST_ ».  
  
10. Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.  
  
11. L’architecture ESB récupère le message, supprime l’espace de noms existant et dépose le message mis à jour dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out. Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.  
  
12. Enfin, exécutez la quatrième de tests. Faites une copie du fichier nommé TEST_AddViaExtraction_to_PassThrough.0000.ns.xml et renommez-la en supprimant le préfixe « TEST_ ».  
  
13. Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.  
  
14. Récupère le message de l’architecture ESB, extrait l’élément spécifié dans le **ExtractionNodeXPath** propriété, crée un message à partir de cet élément avec les valeurs de l’espace de noms spécifié et dépose le message mis à jour dans le \Source\Samples\ Namespace\Test\Filedrop\Out sous-dossier. Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.