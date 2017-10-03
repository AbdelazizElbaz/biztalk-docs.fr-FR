---
title: "Ajout d’artefacts à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9b5e92e-2e55-41d7-9959-f62753bbeb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c08fa95dddad06efb2c51d93df56b757ae4caca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-artifacts-to-an-application"></a>Ajout d’artefacts à une Application
Vous pouvez ajouter et configurer des artefacts tels que de l’envoi et ports de réception, orchestrations et les emplacements de réception, à l’aide de l’Administration de la console. Vous pouvez également générer des fichiers de liaison et les ajouter à l’application si vous souhaitez appliquer diverses liaisons pour les différents environnements que vous allez importer l’application dans.  
  
 Vous pouvez ajouter d’autres (en général, non - BizTalk Server) des artefacts tels que les scripts, les certificats et les fichiers Lisezmoi, à l’application sous le nœud de ressources. Pour ce faire, utilisez la console d’Administration ou de BTSTask.  
  
 Pour plus d’informations sur les artefacts, consultez [comment créer ou ajouter un artefact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.Microsoft.com/fwlink/?) LinkID = 154724), [la gestion des artefacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.Microsoft.com/fwlink/?) LinkID = 154725) et [fichiers de liaison et déploiement d’applications](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.Microsoft.com/fwlink/?) LinkID = 154726).  
  
## <a name="factoring-artifacts-into-multiple-biztalk-applications"></a>Factorisation des artefacts dans plusieurs Applications BizTalk  
 Pendant le processus de déploiement, vous pouvez avoir déployé vos assemblys dans une seule application à des fins pratiques. Pour diverses raisons, vous pouvez être amené à factoriser les artefacts dans plusieurs applications avant de les déployer en production.  
  
 Avant de déployer, vous devez effectuer une analyse approfondie de la conception d’un assembly. Déterminer si vous ne devez effectuer aucune factorisation, factorisation complète ou factorisation Optimal.  
  
 **Aucun factorisation**  
  
 Tous les artefacts BizTalk sont dans un assembly. Cela est très facile à comprendre et à déployer, mais fournit moins de flexibilité.  
  
 **Factorisation complète**  
  
 Chaque artefact BizTalk est dans son propre assembly. Cela offre davantage de souplesse, mais il est plus complexe à déployer et à comprendre.  
  
 **Factorisation optimal**  
  
 Factorisation optimal se situe entre non factorisation et factorisation complète basée sur une analyse approfondie de vos applications BizTalk. Outre le contrôle de version, cela permet que plus facilement implémentent votre conception de l’hôte BizTalk. Cela est possible en recherchant des relations entre les artefacts BizTalk. Si possible, placez les artefacts qui sont toujours gérées dans le même assembly. Si le contrôle de version indépendant des artefacts est requis, ils doivent être mis dans des assemblys différents. C’est le niveau de conception que vous souhaitez obtenir.