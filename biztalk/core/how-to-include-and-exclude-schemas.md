---
title: "Comment inclure et exclure des schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9206458-e5d6-48d7-87a6-9471ba60dca7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dfa1f610cef6e67f17ca14737c6ca853dd5cd16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-include-and-exclude-schemas"></a>Comment inclure et exclure des schémas
Un fichier de schéma peut exister dans un dossier de projet BizTalk sans être inclus dans le projet. On dit d'un tel schéma qu'il est exclu du projet. Les schémas exclus ne sont pas compilés lorsque vous générez le projet BizTalk. Cette rubrique décrit les étapes nécessaires pour inclure un schéma exclu dans un projet BizTalk et pour exclure un schéma d'un projet BizTalk.  
  
### <a name="to-include-a-schema-in-a-biztalk-project"></a>Pour inclure un schéma dans un projet BizTalk  
  
1.  Dans l'Explorateur de solutions, ouvrez le projet BizTalk qui contient le schéma à inclure dans le dossier correspondant.  
  
2.  Si tous les fichiers n’apparaissent pas déjà, sur le **projet** menu, cliquez sur **afficher tous les fichiers**.  
  
3.  Dans l’Explorateur de solutions, cliquez sur le schéma exclu que vous souhaitez inclure, puis cliquez sur **inclure dans le projet**.  
  
     L'icône correspondant au schéma précédemment exclu dans l'Explorateur de solutions passe de contours vides à l'icône de schéma normal.  
  
4.  Si vous le souhaitez, sur le **projet** menu, cliquez sur **afficher tous les fichiers** pour masquer tous les fichiers dans le dossier du projet qui ne sont pas inclus dans le projet.  
  
### <a name="to-exclude-a-schema-from-a-biztalk-project"></a>Pour exclure un schéma d'un projet BizTalk  
  
-   Dans l’Explorateur de solutions, cliquez sur le schéma que vous souhaitez exclure, puis cliquez sur **exclure du projet**.  
  
     Le schéma est maintenant exclu du projet BizTalk.  
  
    > [!NOTE]
    >  Lorsque vous excluez un schéma d'un projet, il n'est pas supprimé du système de fichiers. En revanche, il n'est plus inclus lorsque vous générez le projet. Vous pouvez choisir ou non d’afficher les fichiers exclus dans le dossier du projet en basculant le **afficher tous les fichiers** outil en haut de la fenêtre de l’Explorateur de solutions.  
  
    > [!NOTE]
    >  Si vous souhaitez supprimer le schéma du système de fichiers ainsi que retirer le fichier de schéma du projet, vous devez supprimer le schéma. Pour plus d’informations sur la suppression des schémas, consultez [suppression de schémas](../core/how-to-delete-schemas.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)