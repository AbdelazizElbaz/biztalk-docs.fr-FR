---
title: "Créer et utiliser des schémas dans TIBCO | Documents Microsoft"
description: "Utiliser l’Éditeur BizTalk pour créer un schéma pour l’adaptateur BizTalk pour TIBCO Enterprise Message Service et définir l’espace de noms cible dans votre schéma pour BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 707067ed0c48abb62d567098cd472b59bad302b0
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="create-and-use-tibco-schemas"></a>Créer et utiliser des schémas TIBCO

## <a name="overview"></a>Vue d'ensemble
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) utilise les schémas que vous créez à l'aide d'un éditeur XML ou de l'Éditeur BizTalk Server dans Visual Studio (uniquement lorsque l'adaptateur est utilisé dans une orchestration). Le schéma décrit le type d'informations attendu. Cette rubrique contient des informations relatives aux gestionnaires d'envoi et de réception.  
  
Les schémas que vous créez pour être utilisés avec l'adaptateur BizTalk pour TIBCO Enterprise Message Service doivent inclure un espace de noms cible. Celui-ci est nécessaire car il est la clé qui associe une instance de message donnée à une orchestration donnée. En d'autres termes, une orchestration s'abonne aux messages associés à un espace de noms cible spécifique et un message XML entrant associé à cet espace de noms cible est transmis à chaque orchestration abonnée au message. Si un schéma de document XML n'inclut pas d'espace de noms cible, BizTalk Server utilise le nom de l'élément racine comme clé.  

Les étapes suivantes montrent comment générer un schéma et comment définir l’espace de noms cible.  
  
## <a name="generate-a-schema"></a>Générer un schéma    
 
1.  Dans l'Éditeur BizTalk, ouvrez votre projet.  
  
2.  Dans l’Explorateur de solutions dans l’angle supérieur droit, sélectionnez **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
3.  Dans le **modèles** volet, sélectionnez **générer les schémas**, puis cliquez sur **ajouter**.  
  
4.  Dans le **générer les schémas** boîte de dialogue le **type de Document** liste, sélectionnez **XML bien formé**.  
  
5.  Cliquez sur **Parcourir** pour localiser le fichier d’entrée pour laquelle vous souhaitez générer un schéma, puis cliquez sur **OK**.  
  
Ensuite, affectez à l’espace de noms cible.  
  
## <a name="set-the-target-namespace"></a>L’espace de noms cible  
  
1.  Dans l’Éditeur BizTalk, ouvrez votre fichier de schéma, cliquez sur  **\<schéma >**, puis sélectionnez **propriétés**.  
  
2.  Dans le **propriétés** volet, recherchez le **Namespace** champ et tapez un nom, par exemple, `testNameSpace`.  
  
 Vous pouvez ensuite continuer à utiliser votre orchestration avec des messages. Lorsqu'un message est récupéré, BizTalk Server recherche une orchestration qui utilise un schéma avec un espace de noms cible défini, et le processus d'orchestration suit son cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’applications](../core/developing-applications5.md)