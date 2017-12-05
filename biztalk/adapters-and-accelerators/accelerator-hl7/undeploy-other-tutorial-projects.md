---
title: "Annuler le déploiement d’autres projets de didacticiel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fce837f-1853-4d5d-a680-8ae2a974c750
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e5c4d7e20fc4d8e7c8bea724625dde770b4aca2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="undeploy-other-tutorial-projects"></a>Annuler le déploiement d’autres projets de didacticiel
Lorsque vous déployez un BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) didacticiels, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] stocke les fichiers de l’assembly du didacticiel dans la base de données de Configuration (également appelée la base de données BizTalk Management) et le global assembly cache. Si vous avez exécuté une autre [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] didacticiel et déployé les assemblys que vous avez créé dans ce didacticiel, vous pouvez rencontrer les erreurs lorsque vous testez vos assemblys dans les trois parties du didacticiel de traitement par lot. Cela peut se produire, car vous ne pouvez déployer un schéma de message à la fois.  
  
 Vous pouvez éviter ces erreurs par l’annulation du déploiement des assemblys que vous avez déployé dans les didacticiels précédents. Vous pouvez redéployer l’assembly ultérieurement si nécessaire.  
  
 Avant l’annulation du déploiement d’un assembly, vous devez désinscrire les orchestrations dans l’assembly. Vous devez également supprimer toute référence à l’assembly que vous souhaitez annuler le déploiement, à partir de n’importe quel autre assembly que vous souhaitez conserver déployé. Une alternative consiste à supprimer toutes les DLL associées à un didacticiel, avant de démarrer un autre didacticiel.  
  
### <a name="to-undeploy-an-assembly"></a>Pour annuler le déploiement d’un assembly  
  
1.  Désinscrire les orchestrations utilisées dans l’assembly que vous souhaitez annuler le déploiement en cliquant sur l’orchestration dans l’Explorateur BizTalk de Visual Studio, puis en cliquant sur **désinscrire**.  
  
2.  Dans n’importe quel assembly que vous souhaitez conserver déployé, supprimez les références aux assemblys que vous souhaitez annuler le déploiement. Cliquez avec le bouton droit sur la référence dans l’Explorateur de solutions, puis cliquez sur **supprimer**.  
  
3.  Ouvrez l’Explorateur BizTalk, cliquez sur l’assembly que vous souhaitez annuler le déploiement, puis cliquez sur **annuler le déploiement**.  
  
 Pour plus d’informations sur l’annulation du déploiement d’un assembly, consultez « Annulation du déploiement un Assembly à l’aide de l’Explorateur BizTalk » dans l’aide de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Préparation à l’utilisation du didacticiel sur le traitement par lot](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)