---
title: "Leçon 3 : Test d’une Instance XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, XML instances
- XML instances
ms.assetid: 19d7dd18-17dc-4355-a4f1-5c5e6750faf3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7fb7efbe41711213103224bdbcda11eeda6281
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-testing-an-xml-instance"></a>Leçon 3 : Test d’une Instance XML
Dans cette leçon, vous envoyez un MT103 valide créés dans les leçons précédentes de ports de réception de message au format XML dans le fichier. Cette action teste les pipelines d’envoi que vous avez créé dans les modules précédentes. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]écrit la sortie sous forme de fichier plat dans le dossier de sortie que vous avez sélectionnés pour le port d’envoi dans le module précédent.  
  
 Vous lancez le fichier de l’adaptateur de réception en copiant un fichier au format XML de SWIFT dans le dossier entrant. Cette action entraîne le système copie un fichier plat SWIFT valid dans le dossier sortant.  
  
### <a name="to-test-an-xml-instance"></a>Pour tester une Instance XML  
  
1.  Dans l’Explorateur Windows, ouvrez \< *lecteur*> : \Labs\Outbound. Vérifiez que ce dossier contient le fichier {GUID} .xml que vous avez envoyé à ce dossier dans [leçon 1 : envoi d’un exemple de fichier plat](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md) de ce module.  
  
2.  Copiez le fichier XML et collez-le dans \< *lecteur*> : \Labs\Inbound\XMLFile. Notez l’heure que vous avez collé à ce fichier.  
  
3.  Déplacer vers \< *lecteur*> : \Labs\Outbound. Vérifiez qu’il existe un fichier appelé {GUID} .txt dans ce dossier, et que l’heure dans la colonne de Date de modification pour ce fichier correspond à l’heure que vous avez collé dans le fichier de \< *lecteur*> : \Labs\Inbound\XMLFile.  
  
4.  Dans le bloc-notes, ouvrez MT103_Sample.txt dans \< *lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial.  
  
5.  Dans une autre instance du bloc-notes, ouvrez .txt {GUID} dans \< *lecteur*> : \Labs\Inbound\XMLFile.  
  
6.  Vérifiez que les deux fichiers dans le bloc-notes contiennent le même contenu.  
  
 Passez à [Module 8 : la réparation d’un Message non valide](http://msdn.microsoft.com/en-us/fb531b22-ac7a-4620-b395-87aebf56077d).