---
title: "Utilisation de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, schemas
- schemas, developing
ms.assetid: 123c4b43-34e4-41c7-980d-5d518b1479c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1c12936f2883bfdbcdcd80d300d2ab5a9ff58d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-schemas"></a>Utilisation de schémas
Les schémas fournis dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sont le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] représentation XSD de la société pour les messages FIN de télécommunication financières Interbank (SWIFT) dans le monde entier. Chaque type de message possède son propre schéma, y compris l’en-tête SWIFT et le code de fin SWIFT (format d’échange). Ce schéma est suffisant pour envoyer ou recevoir un message SWIFT. Ces schémas sont une combinaison unique des enregistrements délimités et positionnels, en fournissant une représentation XML détaillée des structures FIN de fichier plat.  
  
 La plupart des clients SWIFT utilisent un sous-ensemble relativement faible des messages SWIFT FIN. Pour implémenter une solution pour ces clients, vous pouvez créer un projet de schéma BizTalk (comme dans [Module 2 : ajout d’un nouveau projet de schémas](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md) du didacticiel A4SWIFT). Ajoutez les schémas de message approprié (MT*xxx*.xsd) à partir de \\\ programme Files\Microsoft BizTalk Accelerator pour SWIFT \<version > MessagePack\SWIFT Messages\A4SWIFT-SRG\<version > \ Répertoire de xyy x\MT catégorie, où x est le premier chiffre de type de message FIN et xyy est le type de message de trois chiffres pour le message.  
  
 Vous pouvez ajouter plusieurs schémas pour le même projet. Pour maintenir la facilité de gestion, vous devez ajouter des schémas de message plus de 20 par projet. Vous devez également ajouter les schémas courants et de base pour le projet. Si vous avez déjà déployé les schémas courants et de base, vous devez faire référence à leur assembly, plutôt que de les déployer. Cette section décrit ces schémas. Les schémas de message prêts à utiliser comme pour les messages envoyés au réseau SWIFT et messages reçus de SWIFT.  
  
 Vous pouvez examiner le contenu de chaque schéma SWIFT dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] à l’aide de l’éditeur de schéma. Tous les schémas d’échange de message ont la structure courantes suivante :  
  
-   En-têtes  
  
-   Texte du message  
  
-   Codes de fin  
  
 Cette section décrit les schémas d’en-tête et le code de fin. Le texte du message comprend la charge utile du message FIN et contient tous les champs de données à l’exception des champs contenant l’expéditeur, le récepteur et le type de message. Ces trois champs sont contenus dans l’en-tête. Certains messages contiennent également un en-tête utilisateur facultatives qui peut-être également fournir des informations de traitement.  
  
 Chaque charge de message FIN se compose d’une série de champs dans un ordre défini. Ces champs sont conformes aux règles suivantes :  
  
-   Les champs peuvent être obligatoires ou facultatifs dans la séquence.  
  
-   Une séquence peut contenir sous-séquences, et une sous-séquence peut se répètent dans une séquence.  
  
-   Vous pouvez utiliser un champ dans plusieurs types de messages.  
  
-   Un champ peut comporter des éléments ou sous-champs. Un élément ou un sous-champ peut-être être commune à plusieurs champs.  
  
-   Un nœud de groupe représente chaque séquence extensible.  
  
-   Chaque champ peut lui-même avoir plusieurs noeuds niveaux, chacune décrite comme un enregistrement.  
  
-   Les éléments de schéma représentent uniquement les sous-champs au niveau le plus bas.  
  
-   Les schémas courants et de base définissent courantes des enregistrements et des éléments.  
  
-   Schémas représentent certains champs dans plusieurs formats (tels que les champs de tiers). Les schémas définissent les champs de ce type en tant que champs de choix.  
  
-   Certains champs ont limité des ensembles de valeurs. La plupart des cas, le schéma répertorie ces valeurs. Définitions de schéma également incluent la validation de jeu de caractères.  
  
 Contenu de cette section :  
  
-   [Base et des schémas courants](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  
  
-   [SWIFT schémas d’en-tête et code de fin](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
-   [Conventions d’affectation de noms de schéma SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)