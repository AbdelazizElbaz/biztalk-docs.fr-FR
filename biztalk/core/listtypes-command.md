---
title: Commande ListTypes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94febe8a-4c1e-4581-a6d1-ef579633e745
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe2519fc5507ae0975d050a998faec78f2940a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listtypes-command"></a>Commande ListTypes
Répertorie tous les types d’artefacts que vous pouvez ajouter à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’aide de la **AddResource** commande. Pour plus d’informations sur la **AddResource** command, consultez [commande AddResource](../core/addresource-command.md).  
  
 Les noms complets des types d'artefact pris en charge sont les suivants :  
  
-   Assembly .NET : System.BizTalk : assembly  
  
-   Définition BAM : System.BizTalk : BAM  
  
-   L’assembly BizTalk : System.BizTalk : BiztalkAssembly  
  
-   Fichier de liaison BizTalk : System.BizTalk : biztalkbinding  
  
-   Certificat de sécurité : System.BizTalk : Certificate  
  
-   Composant COM : System.BizTalk : com  
  
-   Fichier ad hoc : System.BizTalk : file  
  
-   Script de post-traitement : System.BizTalk : postprocessingscript  
  
-   Script de prétraitement : System.BizTalk : preprocessingscript  
  
-   Stratégie ou règle : System.BizTalk : Rules  
  
-   Répertoire virtuel : System.BizTalk : WebDirectory  
  
> [!NOTE]
>  Pour éviter des conflits au niveau des espaces de noms, utilisez systématiquement le nom de type complet (System.BizTalk:Assembly, par exemple) et pas le nom du type uniquement (Assembly).  
  
## <a name="usage"></a>Utilisation  
 **BTSTask ListTypes**  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)