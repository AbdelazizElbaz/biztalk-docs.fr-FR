---
title: "Écriture de scripts à l’aide des assemblys externes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, warnings
- Scripting functoids, external assemblies
ms.assetid: 0bdf6adc-91b9-462e-8fd0-9cb48bfa7817
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 475a3b9781eecb0ccc79165bbe54e6dfd542ecfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-external-assemblies"></a>Scripts utilisant les assemblys externes
L'utilisation de scripts avec assemblys externes est recommandée dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les assemblys externes présentent plusieurs avantages :  
  
-   le partage de code ;  
  
-   la maintenance ;  
  
-   le débogage.  
  
> [!NOTE]
>  Tester le mappage échoue si le **script** fonctoid utilise un assembly externe qui n’est pas enregistré dans le GAC. Il fonctionne si l'assembly externe se trouve dans le même dossier bin que l'assembly du projet en cours (placé après la génération).  
  
 Nouveau en utilisant le script suffit de définir la **Script** propriété de la **script** fonctoid. Le script étant conservé à l’extérieur du mappage, vous pouvez le modifier sans avoir besoin de changer le mappage. Vous pouvez également utiliser toute la variété d’outils de débogage de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour garantir le bon fonctionnement de votre script.  
  
> [!WARNING]
>  Le code contenu dans l’assembly externe doit être exempt de tout thread. Dans les situations de forte charge, il est possible d’exécuter plusieurs instances d’un mappage en même temps.  
  
 Pour un exemple de fonction hébergée dans un assembly externe, consultez [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid script](../core/scripting-functoid.md)   
 [Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)   
 [Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [Comment configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md)