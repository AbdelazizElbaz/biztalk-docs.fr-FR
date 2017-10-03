---
title: "Création d’un projet de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67e6278c-a597-4700-80bf-48e37aaa9c05
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58017b24f7b7464745f48cc202734217dfb327d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-schema-project"></a>Création d’un projet de schéma
Pour créer un projet de schéma :  
  
1.  Dans Visual Studio, créez le projet SWIFT MX schéma BizTalk.  
  
2.  Ajouter le schéma MX approprié (téléchargé à partir du site de ISO20022), que vous souhaitez tester, à ce projet.  
  
3.  Si vous souhaitez exécuter la fonctionnalité de Message Repair et New Submission pour le message MX ci-dessus, un schéma d’enveloppe correspond également au type de message ci-dessus doit être déployé sinon passez à l’étape 6.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de générer des schémas d’enveloppe de MX, reportez-vous à la Documentation du Générateur de formulaire.  
  
4.  Ajoutez le schéma d’enveloppe pour le projet SWIFT MX schéma.  
  
5.  Ouvrez le schéma d’enveloppe dans l’Éditeur BizTalk et promouvoir les propriétés « CorrelationToken » et « IsNewSubmission ». Cliquez sur les champs ci-dessus, sur **promouvoir -> Promotion rapide** pour promouvoir ces propriétés.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la promotion des propriétés d’un schéma, reportez-vous à la documentation de BizTalk Server.  
  
6.  Créer un fichier de clé (à l’aide de Sn – k key.snk), puis l’affecter au projet pour créer un nom fort nommé assembly.  
  
7.  Générez et déployez le projet.