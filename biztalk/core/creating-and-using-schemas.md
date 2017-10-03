---
title: "Création et utilisation de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas
- creating schemas
- schemas, generating
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f10275c5ed0b887907c7b26b7d1ce8ad5003b099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-using-schemas"></a>Création et utilisation de schémas
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) utilise les schémas que vous créez à l'aide d'un éditeur XML ou de l'Éditeur BizTalk Server dans Visual Studio (uniquement lorsque l'adaptateur est utilisé dans une orchestration). Le schéma décrit le type d'informations attendu. Cette rubrique contient des informations relatives aux gestionnaires d'envoi et de réception.  
  
 Les schémas que vous créez pour être utilisés avec l'adaptateur BizTalk pour TIBCO Enterprise Message Service doivent inclure un espace de noms cible. Celui-ci est nécessaire car il est la clé qui associe une instance de message donnée à une orchestration donnée. En d'autres termes, une orchestration s'abonne aux messages associés à un espace de noms cible spécifique et un message XML entrant associé à cet espace de noms cible est transmis à chaque orchestration abonnée au message. Si un schéma de document XML n'inclut pas d'espace de noms cible, BizTalk Server utilise le nom de l'élément racine comme clé.  
  
## <a name="generating-a-schema"></a>Génération d'un schéma  
 La procédure suivante décrit la génération d'un schéma et la définition de l'espace de noms cible.  
  
#### <a name="to-generate-a-schema-using-biztalk-editor"></a>Pour générer un schéma à l'aide de l'Éditeur BizTalk  
  
1.  Dans l'Éditeur BizTalk, ouvrez votre projet.  
  
2.  Dans l’Explorateur de solutions dans l’angle supérieur droit, sélectionnez **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
3.  Dans le **modèles** volet, sélectionnez **générer les schémas**, puis cliquez sur **ajouter**.  
  
4.  Dans le **générer les schémas** boîte de dialogue le **type de Document** liste, sélectionnez **XML bien formé**.  
  
5.  Cliquez sur **Parcourir** pour localiser le fichier d’entrée pour laquelle vous souhaitez générer un schéma, puis cliquez sur **OK**.  
  
     Vous devez ensuite définir l'espace de noms cible.  
  
#### <a name="to-set-the-target-namespace"></a>Pour définir l'espace de noms cible  
  
1.  Dans l’Éditeur BizTalk, ouvrez votre fichier de schéma, cliquez sur  **\<schéma >**, puis sélectionnez **propriétés**.  
  
2.  Dans le **propriétés** volet, recherchez le **Namespace** champ et tapez un nom, par exemple, `testNameSpace`.  
  
 Vous pouvez ensuite continuer à utiliser votre orchestration avec des messages. Lorsqu'un message est récupéré, BizTalk Server recherche une orchestration qui utilise un schéma avec un espace de noms cible défini, et le processus d'orchestration suit son cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’applications](../core/developing-applications5.md)